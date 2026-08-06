# Software Requirements — P0 "Genesis" Platform (v1, Sprint 2, T-0021)

*Derived from `../stakeholder/stakeholder-requirements.md`. Components: BRD = board tooling (`platform/scripts/board.py`), GW = LLM gateway (`platform/gateway/`), GRD = guardrails, ORC = orchestrator (`platform/orchestrator/tick.py`), REG = run registry, CI = workflows. Language: English (D011). Status `reviewed` = implemented in Sprint 1/2 and covered by unit tests or CI; `draft` = future (Sprint 3+).*

## Board tooling (BRD)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-001 | board.py shall validate every ticket file against the ticket schema (required fields, ID format `T-\d{4}`, allowed type/status/prio values, date format) and reject invalid tickets with file-level error messages. | STK-003, STK-011 | Unit tests `test_board.py` (schema cases) | high | reviewed |
| SWR-002 | board.py shall validate status transitions of changed tickets against the versions in Git HEAD and reject transitions not allowed by the playbook workflow. | STK-011 | Unit tests (transition matrix); `--no-git` documented for CI | high | reviewed |
| SWR-003 | board.py shall validate that every `blocked_by` reference points to an existing ticket. | STK-003 | Unit test (dangling reference) | medium | reviewed |
| SWR-004 | board.py shall generate BOARD.md deterministically (stable ordering by status, prio, ID) so that repeated runs on the same input produce identical output. | STK-003 | Unit test (double run, byte-identical) | medium | reviewed |
| SWR-005 | board.py shall provide a `--check` mode that validates without writing, returning exit code 0/1/2 for ok/validation error/IO error, usable as a CI gate. | STK-010 | CI workflow run + unit test | high | reviewed |

## LLM gateway (GW)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-006 | The gateway shall expose `execute(role, task, context) → result` returning artifacts, log, cost, and the provider actually used. | STK-001, STK-006 | Unit tests `test_gateway.py` | high | reviewed |
| SWR-007 | The gateway shall resolve the provider chain per role and task type from the role registry (script route first; task-type override; role default) and fall back to the next chain element if a provider is unavailable. | STK-005 | Unit tests (chain resolution, fallback) | high | reviewed |
| SWR-008 | The gateway shall support the executors claude (Agent SDK), ollama (local HTTP API), and session (two-phase markdown prompt exchange); copilot shall report NotImplemented until Sprint 6. | STK-005, STK-009 | Unit tests `test_provider_apifrei.py` | high | reviewed |
| SWR-009 | File artifacts returned by text-only providers shall follow the file-block convention with path protection: paths are repo-root-relative, known repo prefixes are stripped, and path traversal outside the repo is rejected. | STK-002, STK-008 | Unit tests (prefix strip, traversal) — lesson T-0013 | high | reviewed |
| SWR-010 | Task-types marked gate-relevant shall be executed exclusively on the configured strong Claude tier, never on a weaker provider. | STK-005, STK-007 | Unit test (routing gate_relevant) | high | reviewed |

## Guardrails and run registry (GRD/REG)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-011 | The platform shall abort a tick before further LLM calls when its accumulated cost exceeds `budget.limit_tick_eur`, and record the abort with reason in the run registry. | STK-004, STK-006 | Unit test (mocked cost overrun) | high | reviewed |
| SWR-012 | The platform shall stop all autonomous operation and produce an emergency notification when accumulated monthly cost exceeds `budget.limit_month_eur`. | STK-004, STK-007 | Unit test (monthly limit) | high | reviewed |
| SWR-013 | Every executed action shall append one run-registry entry (JSONL) with role, ticket, timestamp, device, provider/execution path, and cost; the registry file shall be append-only for the platform. | STK-006 | Unit test (entry written, fields complete) | high | reviewed |
| SWR-014 | The platform shall refuse forbidden actions (force-push, tag deletion, baseline deletion, external communication) regardless of role or provider. | STK-008 | Unit test (forbidden action rejected) | high | reviewed |

## Orchestrator (ORC)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-015 | A tick shall only start on a clean working copy; otherwise it aborts with a diagnostic and no changes. | STK-011 | Unit test — lesson T-0014 | high | reviewed |
| SWR-016 | The orchestrator shall select the next ticket by priority and unblocked state (`blocked_by` resolved), respecting the script route before any LLM call. | STK-001, STK-005 | Unit tests `test_orchestrator.py` | high | reviewed |
| SWR-017 | Tick results shall be committed on a branch `feature/t-xxxx-<slug>` containing only the tick's own artifacts (selective staging), with the ticket ID in the commit message, plus ticket status update and regenerated BOARD.md. | STK-002, STK-011 | Unit test (selective add) — lesson T-0014 | high | reviewed |
| SWR-018 | The orchestrator CLI shall support `--dry-run`, `--ticket <id>`, and `--provider <name>` overrides for controlled manual runs. | STK-009 | Unit tests (CLI flags) | medium | reviewed |

## CI (CI)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-019 | On every push/PR to platform, CI shall run all unit tests; on every push/PR to p0, CI shall run board validation (`--check --no-git`) and verify BOARD.md is up to date. | STK-010 | Workflow files (T-0015) + first CI runs on GitHub | high | reviewed |

## Backend/Frontend (outlook Sprint 3 — not part of the G1 baseline scope)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-020 | The backend shall serve the decision inbox (open DRs with options/deadline/default) and accept human decisions, recording them to the decision log. | STK-007, STK-012 | API tests (Sprint 3) | medium | draft |
| SWR-021 | The frontend shall display board status, sprint reports, cost/KPI trends, and the decision inbox without requiring Git access. | STK-012 | UI acceptance (Sprint 3) | medium | draft |

## Traceability summary

STK-001 → SWR-006, 016 · STK-002 → SWR-009, 017 · STK-003 → SWR-001, 003, 004 · STK-004 → SWR-011, 012 · STK-005 → SWR-007, 008, 010, 016 · STK-006 → SWR-006, 011, 013 · STK-007 → SWR-010, 012, 020 · STK-008 → SWR-009, 014 · STK-009 → SWR-008, 018 · STK-010 → SWR-005, 019 · STK-011 → SWR-002, 015, 017 · STK-012 → SWR-020, 021. All STK covered; SWR without STK trace: none.
