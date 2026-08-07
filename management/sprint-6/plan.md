# Sprint-6-Plan — P0 „Genesis" (PL)

*Erstellt 2026-08-07, Rolle PL (Session-Kontext). Sprint-Motto (P0 Kap. 5): „Härtung, Self-Check & Abnahme" — letzter P0-Sprint. Basis: `genesis-v0.5` (D022), datakonv 1.0.0 released, E2E-Nachweis erbracht.*

## Sprint-Ziel

P0 wird abnahmereif: Self-Check gegen die Basispraktiken aller Stufe-1-Prozesse (mit ehrlicher Lückenliste), Betriebs-Runbook, KPI-Baseline mit Retro-Wirksamkeitsnachweis, Vervollständigung des Provider-PoCs (Copilot/Ollama, F13-abhängig), Intake-Workflow + P1-Hülle — abgeschlossen mit dem P0-Abschlussbericht und deiner **P0-Abnahme gegen Kap. 3** (= G3 für P0 selbst).

## Sprint-Backlog (Reihenfolge)

| # | Ticket | Inhalt | Rolle | blocked_by |
|---|---|---|---|---|
| 1 | T-0062 | board.py Status-Subkommando mit Übergangsprüfung (Retro-CR 1/3) | DEV | — |
| 2 | T-0063 | feedback_route v1.1: automatischer Feedback-Abschluss (Retro-CR 2/3) | DEV | — |
| 3 | T-0064 | produkte.yaml + `trace_matrix --produkt` (Retro-CR 3/3) | DEV | — |
| 4 | T-0065 | Self-Check gegen Basispraktiken aller Stufe-1-Prozesse → Report mit Fundstellen/Lücken | QM | — |
| 5 | T-0066 | Self-Check-Lücken schließen oder als P1-Backlog dokumentieren | PL | T-0065 |
| 6 | T-0067 | Betriebs-Runbook: Backup, Monitoring, Update, Störungsbehandlung, Geräte-Onboarding | CM | — |
| 7 | T-0068 | KPI-Baseline + Retro-Wirksamkeitsnachweis (P0-Kriterium 6) | PL | — |
| 8 | T-0069 | Provider-PoC vervollständigen: Copilot-CLI-Executor (F13) + Ollama-Nachweis-Doku | DEV | Mensch: F13 |
| 9 | T-0070 | Intake-Workflow für neue Projekte + P1-Hülle | PL | — |
| 10 | T-0071 | P0-Abschlussbericht → **P0-Abnahme** (DR an den Menschen) | PL→Mensch | T-0062–T-0068, T-0070 |

**Bewusst nicht gezogen:** voller Multi-Node-Betrieb und datenbasierte Routing-Politik (P2), MCP-Produktverpackung und Produkt-KPIs (P3), Self-Assessment CL1 (D010: pragmatisch — Weg bleibt offen).

## Human-Gates dieses Sprints

**P0-Abnahme** (Kap. 3, via T-0071-DR). Dazu erbeten: **F13** (Copilot-Abo/Ollama — bestimmt den T-0069-Schnitt) und die restlichen offenen Fragen **F6, F8–F12** (fließen in P1-Intake, T-0070).

## Kapazität und Budget

API-Budget-Stand: 0,00 € von 20 €/Monat (D012). T-0008 (API-Key) bleibt optional — der Copilot-PoC braucht ihn nicht; ohne Copilot-Abo wird T-0069 als dokumentierter Verzicht mit Ollama-Nachweis abgeschlossen.

## Arbeitsweise

Wie Sprint 5; ab T-0062-Verfügbarkeit laufen Statuswechsel über das neue board.py-Subkommando (Erwartungswert: 0 geblockte Status-Commit-Versuche). Push per `sprint6-abschluss.cmd` inkl. Projektstatus-Automatik (D007).
