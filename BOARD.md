# Board (generiert von platform/scripts/board.py — nicht von Hand editieren)

Stand: 2026-08-06 · Tickets: 36


## open (11)

| ID | Titel | Typ | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|
| [T-0008](tickets/T-0008.md) | Anthropic-API-Key als Secret hinterlegen | task | mensch | hoch | 1 | — |
| [T-0028](tickets/T-0028.md) | Rollenkarten v1 für ARCH, DEV, TEST + Registry v1.2 (SWE-Rollen aktivieren) | task | coach | hoch | 3 | — |
| [T-0029](tickets/T-0029.md) | Prozess-Skills v1 für SWE.2, SWE.3, SWE.4–6 schreiben (+ Gold-Beispiele) | task | coach | hoch | 3 | T-0028 |
| [T-0030](tickets/T-0030.md) | SWE.1: STK-012 + SWR-020/021 draft → reviewed; G1-Erweiterungsvorlage | task | rm | hoch | 3 | — |
| [T-0031](tickets/T-0031.md) | SWE.2: Architektur Backend/Frontend-MVP + ADRs → G2-Vorlage | task | arch | hoch | 3 | T-0028, T-0030 |
| [T-0032](tickets/T-0032.md) | Backend-MVP: Decision-Inbox, Board/Report-Aggregation, E-Mail-Versand (SWR-020) | task | dev | hoch | 3 | T-0031 |
| [T-0035](tickets/T-0035.md) | DR: Hub-VM-Beschaffung (E5, R2) — Anbieter/Größe/Kosten + Deployment-Ziel + D006-Review | decision-request | pl | hoch | 3 | — |
| [T-0026](tickets/T-0026.md) | Prozess-CR (Retro S2): SWR-Test-Traceability — Docstring-IDs + Matrix-Generator | change-request | dev | mittel | 3 | — |
| [T-0033](tickets/T-0033.md) | Frontend-MVP: lesende PWA + Decision-Inbox (SWR-021) | task | dev | mittel | 3 | T-0031 |
| [T-0034](tickets/T-0034.md) | SWE.4: Verifikation Backend/Frontend + SWR↔Test-Matrix vollständig | task | test | mittel | 3 | T-0032, T-0033 |
| [T-0036](tickets/T-0036.md) | Autonome Ticks nachholen: Betriebsdaten sammeln; Claude-Tick sofern T-0008 | task | cm | mittel | 3 | — |

## in_review (1)

| ID | Titel | Typ | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|
| [T-0025](tickets/T-0025.md) | Prozess-CR (Retro S2): Requirements-first-Regel für Plattform-/Produkt-Tickets | change-request | chg | mittel | 3 | — |

## done (24)

| ID | Titel | Typ | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|
| [T-0001](tickets/T-0001.md) | Rollenkarten v1 für PL, CM, COACH ausarbeiten | task | coach | hoch | 1 | — |
| [T-0002](tickets/T-0002.md) | Prozess-Skills v1 für MAN.3, SUP.8, SUP.10 schreiben | task | coach | hoch | 1 | — |
| [T-0004](tickets/T-0004.md) | LLM-Gateway v1: Executor-Schnittstelle + Claude-Executor | task | dev | hoch | 1 | — |
| [T-0005](tickets/T-0005.md) | Orchestrator-MVP: Tick-Loop | task | dev | hoch | 1 | T-0004, T-0007 |
| [T-0006](tickets/T-0006.md) | Guardrails v1 durchsetzen | task | dev | hoch | 1 | T-0004 |
| [T-0007](tickets/T-0007.md) | Board-Tooling: Validierung + BOARD.md-Generator als Skript-Route | task | cm | hoch | 1 | — |
| [T-0011](tickets/T-0011.md) | Ollama-Executor v1 (vorgezogen aus Sprint 6) | task | dev | hoch | 1 | — |
| [T-0012](tickets/T-0012.md) | Session-Austausch-Provider (Prompt-Austausch via Markdown) | task | dev | hoch | 1 | — |
| [T-0013](tickets/T-0013.md) | Problem: Artefakt-Pfad mit Repo-Präfix (process/process/…) beim Ollama-Tick | problem | dev | hoch | 1 | — |
| [T-0014](tickets/T-0014.md) | Problem: Tick-Commit sammelt unbeteiligte Arbeitskopie-Änderungen ein (git add -A) | problem | dev | hoch | 1 | — |
| [T-0015](tickets/T-0015.md) | Prozess-CR (Retro S1): CI-Workflow — board.py --check + Unit-Tests je Push | change-request | cm | hoch | 2 | — |
| [T-0019](tickets/T-0019.md) | Rollenkarten v1 für QM, RM, PROB, CHG + Registry-Aktivierung | task | coach | hoch | 2 | — |
| [T-0020](tickets/T-0020.md) | Prozess-Skills v1 für SUP.1, SWE.1, SUP.9 schreiben (+ Gold-Beispiele) | task | coach | hoch | 2 | T-0019 |
| [T-0021](tickets/T-0021.md) | SWE.1: Plattform-Anforderungen als erstes Requirements-Set (EN) + G1-Vorlage | task | rm | hoch | 2 | T-0019 |
| [T-0022](tickets/T-0022.md) | Budget-Review (D003): Ist-Daten der Testphase → Budget-Festlegung | decision-request | pl | hoch | 2 | — |
| [T-0024](tickets/T-0024.md) | Prozess-CR (Retro S2): Session-Preflight als Skript-Route (Locks, Status, Board, Tests) | change-request | cm | hoch | 3 | — |
| [T-0027](tickets/T-0027.md) | Problem: platform-CI rot — pyyaml fehlt auf dem GitHub-Runner (Umgebungs-Drift zu Sandbox/Team-Node) | problem | dev | hoch | 2 | — |
| [T-0003](tickets/T-0003.md) | Rollen-Registry v1: Aufgaben-Typen und Provider-Ketten verfeinern | task | coach | mittel | 1 | T-0001 |
| [T-0009](tickets/T-0009.md) | Sprint-1-Abnahme: Erster autonomer Tick (CM erstellt CM-Strategie-Entwurf) | task | pl | mittel | 1 | T-0001, T-0002, T-0005, T-0006 |
| [T-0010](tickets/T-0010.md) | CM-Strategie v1 erstellen (Ziel des ersten autonomen Ticks) | task | cm | mittel | 1 | — |
| [T-0016](tickets/T-0016.md) | Prozess-CR (Retro S1): Lessons aus T-0013/T-0014 in die Wissensbasen | change-request | coach | mittel | 2 | — |
| [T-0017](tickets/T-0017.md) | Prozess-CR (Retro S1): PAM-4.0-Wortlaut-Abgleich der Skill-BP-Mappings | change-request | coach | mittel | 2 | — |
| [T-0018](tickets/T-0018.md) | CM-Strategie v1.1: an reale Repo-Struktur und Rollen angleichen (Review-Nacharbeit) | task | cm | mittel | 2 | — |
| [T-0023](tickets/T-0023.md) | Prozess-Baseline genesis-v0.2 (Tags + Manifest) | task | cm | mittel | 2 | T-0015, T-0016, T-0017, T-0018, T-0019, T-0020, T-0021 |
