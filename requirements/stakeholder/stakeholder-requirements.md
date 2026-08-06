# Stakeholder Requirements — P0 "Genesis" Platform (v1, Sprint 2, T-0021)

*Stakeholders: the client (E. John) and the virtual team itself (the platform is the team's own tooling). Sources: Masterplan, P0 project description, Decision Log D000–D011, Sprint-1 operational experience. Language: English (D011).*

| ID | Title | Requirement | Source | Prio | Status |
|---|---|---|---|---|---|
| STK-001 | Autonomous role-based operation | The platform shall enable AI agents acting in defined roles to process tickets autonomously in ticks, with the human involved only through gates, decision requests, and clarifications. | Masterplan ch. 1–2, D000 | high | reviewed |
| STK-002 | Git as single source of truth | All work products, tickets, decisions, and operational state shall live in Git repositories; no relevant state outside Git. | Playbook ch. 1, D006 | high | reviewed |
| STK-003 | File-based ticket board | Tickets shall be managed as versioned files with a generated, human-readable board, validated automatically; usable over plain Git from any environment (sandbox, PC, VM). | D006, D007 | high | reviewed |
| STK-004 | Hard cost limits | LLM/API spending shall be capped by hard limits (per tick and per month) with automatic stop and human notification; test-phase budget ~20 EUR until data-based revision. | D003, guardrails | high | reviewed |
| STK-005 | Cost-efficient provider pyramid | Work shall be routed by the escalation pyramid script → local LLM (Ollama) → subscription (Copilot CLI) → API (Claude) → human, configurable per role and task type. | Masterplan ch. 5.8, D008 | high | reviewed |
| STK-006 | Full action traceability | Every agent action shall be recorded with role, task, timestamp, device, execution path/provider, and cost. | Guardrails (logging) | high | reviewed |
| STK-007 | Human gates and decisions | The platform shall support gates G0–G4 and decision requests (context, options, recommendation, deadline, low-risk default), with notification via e-mail (decision inbox from Sprint 3). | Playbook ch. 7, D004 | high | reviewed |
| STK-008 | Safety guardrails | Destructive or out-of-scope actions (force-push, tag/baseline deletion, external communication, unapproved devices) shall be technically prevented; write scope limited per role. | Guardrails | high | reviewed |
| STK-009 | Distributed, sandbox-tolerant operation | Autonomous ticks shall run on approved team nodes (user PC, later hub VM); read-only environments (Cowork sandbox) shall still support engineering, planning, and review. | D007 | high | reviewed |
| STK-010 | Enforced verification in CI | Board validity and platform unit tests shall be enforced automatically on every push, so that no invalid state reaches main unnoticed. | Retro Sprint 1 (T-0015) | medium | reviewed |
| STK-011 | Process-conformant workflow | The platform shall enforce the team's workflow: no work without a ticket, reviewer ≠ author, status transitions per playbook, baselines as tags + manifests. | Playbook ch. 5, 9 | medium | reviewed |
| STK-012 | Human-facing backend/frontend | The platform shall provide a backend and frontend (decision inbox, reports, KPIs, board view) so the human can steer the team without reading raw Git. MVP scope is fixed (P0 ch. 8): read-only views plus the decision inbox; live updates and push notifications are out of scope until after P0. | Masterplan (Sprint 3), D004 | medium | reviewed |
