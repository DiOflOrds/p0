# Board (generiert von platform/scripts/board.py — nicht von Hand editieren)

Stand: 2026-08-16 · Tickets: 72


## open (1)

| ID | Titel | Typ | Takt | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|---|
| [T-0008](tickets/T-0008.md) | Anthropic-API-Key als Secret hinterlegen | task | einmalig | mensch | hoch | 1 | — |

## done (69)

| ID | Titel | Typ | Takt | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|---|
| [T-0001](tickets/T-0001.md) | Rollenkarten v1 für PL, CM, COACH ausarbeiten | task | einmalig | coach | hoch | 1 | — |
| [T-0002](tickets/T-0002.md) | Prozess-Skills v1 für MAN.3, SUP.8, SUP.10 schreiben | task | einmalig | coach | hoch | 1 | — |
| [T-0004](tickets/T-0004.md) | LLM-Gateway v1: Executor-Schnittstelle + Claude-Executor | task | einmalig | dev | hoch | 1 | — |
| [T-0005](tickets/T-0005.md) | Orchestrator-MVP: Tick-Loop | task | einmalig | dev | hoch | 1 | T-0004, T-0007 |
| [T-0006](tickets/T-0006.md) | Guardrails v1 durchsetzen | task | einmalig | dev | hoch | 1 | T-0004 |
| [T-0007](tickets/T-0007.md) | Board-Tooling: Validierung + BOARD.md-Generator als Skript-Route | task | einmalig | cm | hoch | 1 | — |
| [T-0011](tickets/T-0011.md) | Ollama-Executor v1 (vorgezogen aus Sprint 6) | task | einmalig | dev | hoch | 1 | — |
| [T-0012](tickets/T-0012.md) | Session-Austausch-Provider (Prompt-Austausch via Markdown) | task | einmalig | dev | hoch | 1 | — |
| [T-0013](tickets/T-0013.md) | Problem: Artefakt-Pfad mit Repo-Präfix (process/process/…) beim Ollama-Tick | problem | einmalig | dev | hoch | 1 | — |
| [T-0014](tickets/T-0014.md) | Problem: Tick-Commit sammelt unbeteiligte Arbeitskopie-Änderungen ein (git add -A) | problem | einmalig | dev | hoch | 1 | — |
| [T-0015](tickets/T-0015.md) | Prozess-CR (Retro S1): CI-Workflow — board.py --check + Unit-Tests je Push | change-request | einmalig | cm | hoch | 2 | — |
| [T-0019](tickets/T-0019.md) | Rollenkarten v1 für QM, RM, PROB, CHG + Registry-Aktivierung | task | einmalig | coach | hoch | 2 | — |
| [T-0020](tickets/T-0020.md) | Prozess-Skills v1 für SUP.1, SWE.1, SUP.9 schreiben (+ Gold-Beispiele) | task | einmalig | coach | hoch | 2 | T-0019 |
| [T-0021](tickets/T-0021.md) | SWE.1: Plattform-Anforderungen als erstes Requirements-Set (EN) + G1-Vorlage | task | einmalig | rm | hoch | 2 | T-0019 |
| [T-0022](tickets/T-0022.md) | Budget-Review (D003): Ist-Daten der Testphase → Budget-Festlegung | decision-request | einmalig | pl | hoch | 2 | — |
| [T-0024](tickets/T-0024.md) | Prozess-CR (Retro S2): Session-Preflight als Skript-Route (Locks, Status, Board, Tests) | change-request | einmalig | cm | hoch | 3 | — |
| [T-0027](tickets/T-0027.md) | Problem: platform-CI rot — pyyaml fehlt auf dem GitHub-Runner (Umgebungs-Drift zu Sandbox/Team-Node) | problem | einmalig | dev | hoch | 2 | — |
| [T-0028](tickets/T-0028.md) | Rollenkarten v1 für ARCH, DEV, TEST + Registry v1.2 (SWE-Rollen aktivieren) | task | einmalig | coach | hoch | 3 | — |
| [T-0029](tickets/T-0029.md) | Prozess-Skills v1 für SWE.2, SWE.3, SWE.4–6 schreiben (+ Gold-Beispiele) | task | einmalig | coach | hoch | 3 | T-0028 |
| [T-0030](tickets/T-0030.md) | SWE.1: STK-012 + SWR-020/021 draft → reviewed; G1-Erweiterungsvorlage | task | einmalig | rm | hoch | 3 | — |
| [T-0031](tickets/T-0031.md) | SWE.2: Architektur Backend/Frontend-MVP + ADRs → G2-Vorlage | task | einmalig | arch | hoch | 3 | T-0028, T-0030 |
| [T-0032](tickets/T-0032.md) | Backend-MVP: Decision-Inbox, Board/Report-Aggregation, E-Mail-Versand (SWR-020) | task | einmalig | dev | hoch | 3 | T-0031 |
| [T-0035](tickets/T-0035.md) | DR: Hub-VM-Beschaffung (E5, R2) — Anbieter/Größe/Kosten + Deployment-Ziel + D006-Review | decision-request | einmalig | pl | hoch | 3 | — |
| [T-0040](tickets/T-0040.md) | Problem: Frontend rendert nicht (hängt bei „Lade …", keine Tabs, keine API-Calls) | problem | einmalig | dev | hoch | 3 | — |
| [T-0041](tickets/T-0041.md) | DR: Übungsprodukt wählen (P0 Kap. 5, Sprint 4) — Produkt + Repo-Ort | decision-request | einmalig | pl | hoch | 4 | — |
| [T-0042](tickets/T-0042.md) | Produkt-Repo-Skelett produkt-datakonv (lokal) + CM-Setup (CI, Baseline-Struktur) | task | einmalig | cm | hoch | 4 | — |
| [T-0043](tickets/T-0043.md) | SWE.1 datakonv: Clarifications + STK/SWR-Set (EN, 10–20 SWRs) → G1-Vorlage | task | einmalig | rm | hoch | 4 | T-0042 |
| [T-0044](tickets/T-0044.md) | SWE.2 datakonv: Architektur (Units, Schnittstellen, ADRs) → G2-Vorlage | task | einmalig | arch | hoch | 4 | T-0043 |
| [T-0045](tickets/T-0045.md) | SWE.3 datakonv: Implementierung Units (Python stdlib, requirements-first) | task | einmalig | dev | hoch | 4 | T-0044 |
| [T-0046](tickets/T-0046.md) | SWE.4 datakonv: Unit-Verifikation automatisiert in CI + SWR↔Test-Matrix | task | einmalig | test | hoch | 4 | T-0045 |
| [T-0052](tickets/T-0052.md) | SWE.5/6: Integrations-/Gesamtverifikation datakonv (CLI-E2E gegen STK/SWR) + Report | task | einmalig | test | hoch | 5 | — |
| [T-0053](tickets/T-0053.md) | SUP.9: realen Befund aus der Integrationsverifikation als Problem bis Abschluss führen | problem | einmalig | prob | hoch | 5 | T-0052 |
| [T-0057](tickets/T-0057.md) | Release datakonv 1.0.0 (SPL.2): Packaging, Release Notes, Tag, Katalog → G3 | task | einmalig | cm | hoch | 5 | T-0052, T-0053, T-0054, T-0056 |
| [T-0061](tickets/T-0061.md) | DR: G3 — Release datakonv 1.0.0 freigeben | decision-request | einmalig | pl | hoch | 5 | — |
| [T-0065](tickets/T-0065.md) | Self-Check gegen Basispraktiken aller Stufe-1-Prozesse → Report (Fundstellen/Lücken) | task | einmalig | qm | hoch | 6 | — |
| [T-0066](tickets/T-0066.md) | Self-Check-Lücken schließen oder als P1-Backlog dokumentieren | task | einmalig | pl | hoch | 6 | T-0065 |
| [T-0067](tickets/T-0067.md) | Betriebs-Runbook: Backup, Monitoring, Update, Störungsbehandlung, Geräte-Onboarding | task | einmalig | cm | hoch | 6 | — |
| [T-0071](tickets/T-0071.md) | DR: P0-Abschlussbericht → P0-Abnahme gegen Kap. 3 | decision-request | einmalig | pl | hoch | 6 | T-0062, T-0063, T-0064, T-0065, T-0066, T-0067, T-0068, T-0070 |
| [T-0003](tickets/T-0003.md) | Rollen-Registry v1: Aufgaben-Typen und Provider-Ketten verfeinern | task | einmalig | coach | mittel | 1 | T-0001 |
| [T-0009](tickets/T-0009.md) | Sprint-1-Abnahme: Erster autonomer Tick (CM erstellt CM-Strategie-Entwurf) | task | einmalig | pl | mittel | 1 | T-0001, T-0002, T-0005, T-0006 |
| [T-0010](tickets/T-0010.md) | CM-Strategie v1 erstellen (Ziel des ersten autonomen Ticks) | task | einmalig | cm | mittel | 1 | — |
| [T-0016](tickets/T-0016.md) | Prozess-CR (Retro S1): Lessons aus T-0013/T-0014 in die Wissensbasen | change-request | einmalig | coach | mittel | 2 | — |
| [T-0017](tickets/T-0017.md) | Prozess-CR (Retro S1): PAM-4.0-Wortlaut-Abgleich der Skill-BP-Mappings | change-request | einmalig | coach | mittel | 2 | — |
| [T-0018](tickets/T-0018.md) | CM-Strategie v1.1: an reale Repo-Struktur und Rollen angleichen (Review-Nacharbeit) | task | einmalig | cm | mittel | 2 | — |
| [T-0023](tickets/T-0023.md) | Prozess-Baseline genesis-v0.2 (Tags + Manifest) | task | einmalig | cm | mittel | 2 | T-0015, T-0016, T-0017, T-0018, T-0019, T-0020, T-0021 |
| [T-0025](tickets/T-0025.md) | Prozess-CR (Retro S2): Requirements-first-Regel für Plattform-/Produkt-Tickets | change-request | einmalig | chg | mittel | 3 | — |
| [T-0026](tickets/T-0026.md) | Prozess-CR (Retro S2): SWR-Test-Traceability — Docstring-IDs + Matrix-Generator | change-request | einmalig | dev | mittel | 3 | — |
| [T-0033](tickets/T-0033.md) | Frontend-MVP: lesende PWA + Decision-Inbox (SWR-021) | task | einmalig | dev | mittel | 3 | T-0031 |
| [T-0034](tickets/T-0034.md) | SWE.4: Verifikation Backend/Frontend + SWR↔Test-Matrix vollständig | task | einmalig | test | mittel | 3 | T-0032, T-0033 |
| [T-0036](tickets/T-0036.md) | Autonome Ticks nachholen: Betriebsdaten sammeln; Claude-Tick sofern T-0008 | task | einmalig | cm | mittel | 3 | — |
| [T-0037](tickets/T-0037.md) | Prozess-CR (Retro S3): trace-matrix-Gate in CI (p0-Checkout im platform-Workflow) | change-request | einmalig | cm | mittel | 4 | — |
| [T-0038](tickets/T-0038.md) | Prozess-CR (Retro S3): Zweiphasen-Tick idempotent — Phase 1 ohne Statuswechsel-Commits | change-request | einmalig | dev | mittel | 4 | — |
| [T-0039](tickets/T-0039.md) | Prozess-CR (Retro S3): DR-Optionen maschinenlesbar (Frontmatter) + Inbox-Validierung | change-request | einmalig | chg | mittel | 4 | — |
| [T-0048](tickets/T-0048.md) | Prozess-CR: trace_matrix generalisieren — Produkt-Repos via --tests/--swr/--ziel/--id-muster | change-request | einmalig | dev | mittel | 4 | — |
| [T-0049](tickets/T-0049.md) | Prozess-CR (Retro S4): Matrix-CI-Gate im Produkt-Repo produkt-datakonv | change-request | einmalig | cm | mittel | 5 | — |
| [T-0050](tickets/T-0050.md) | Prozess-CR (Retro S4): Preflight räumt verwaiste Git-Locks selbst (R7) | change-request | einmalig | dev | mittel | 5 | — |
| [T-0054](tickets/T-0054.md) | SUP.10: realer CR am Produkt mit Impact-Analyse (Quelle: Mensch-Feedback via Routing) | change-request | einmalig | chg | mittel | 5 | T-0055 |
| [T-0055](tickets/T-0055.md) | Feedback-Routing v1: Skript Feedback-Ticket → Problem/CR (Masterplan 5.5) | task | einmalig | dev | mittel | 5 | — |
| [T-0056](tickets/T-0056.md) | Produktkatalog v0: process/catalog/products.yaml + Detailseite, Eintrag skript-generiert | task | einmalig | cm | mittel | 5 | — |
| [T-0058](tickets/T-0058.md) | Sprint-5-Report + Retro (max. 3 CRs) → G4 | task | einmalig | pl | mittel | 5 | T-0057 |
| [T-0059](tickets/T-0059.md) | Feedback (Mensch): --indent-Option für die JSON-Ausgabe | feedback | einmalig | mensch | mittel | 5 | — |
| [T-0060](tickets/T-0060.md) | CR (aus Feedback T-0059): Feedback (Mensch): --indent-Option für die JSON-Ausgabe | change-request | einmalig | chg | mittel | 5 | — |
| [T-0062](tickets/T-0062.md) | Prozess-CR (Retro S5): board.py Status-Subkommando mit Übergangsprüfung | change-request | einmalig | dev | mittel | 6 | — |
| [T-0068](tickets/T-0068.md) | KPI-Baseline + Retro-Wirksamkeitsnachweis (P0-Kriterium 6) | task | einmalig | pl | mittel | 6 | — |
| [T-0069](tickets/T-0069.md) | Provider-PoC vervollständigen: Copilot-CLI-Executor (F13) + Ollama-Nachweis-Doku | task | einmalig | dev | mittel | 6 | — |
| [T-0070](tickets/T-0070.md) | Intake-Workflow für neue Projekte + P1-Hülle | task | einmalig | pl | mittel | 6 | — |
| [T-0051](tickets/T-0051.md) | Prozess-CR (Retro S4): board.py erzwingt optionen-Frontmatter für neue DRs | change-request | einmalig | chg | niedrig | 5 | — |
| [T-0063](tickets/T-0063.md) | Prozess-CR (Retro S5): feedback_route v1.1 — automatischer Feedback-Abschluss | change-request | einmalig | dev | niedrig | 6 | — |
| [T-0064](tickets/T-0064.md) | Prozess-CR (Retro S5): Produkt-Konfig produkte.yaml + trace_matrix --produkt | change-request | einmalig | dev | niedrig | 6 | — |

## rejected (2)

| ID | Titel | Typ | Takt | Rolle | Prio | Sprint | blockiert durch |
|---|---|---|---|---|---|---|---|
| [T-0047](tickets/T-0047.md) | Hub-VM (D014, E5): Beschaffung begleiten — Runbook, Deployment, Geräteregister | task | einmalig | cm | mittel | 4 | — |
| [T-0072](tickets/T-0072.md) | Copilot-PoC-Lauf am Team-Node: DEV-Routineaufgabe via --provider copilot (Kriterium 9) | task | einmalig | dev | mittel | 6 | — |
