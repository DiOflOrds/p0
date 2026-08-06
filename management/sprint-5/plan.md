# Sprint-5-Plan — P0 „Genesis" (PL)

*Erstellt 2026-08-06, Rolle PL (Session-Kontext). Sprint-Motto (P0 Kap. 5): „Generalprobe Teil 2 + Release". Basis: Baseline `genesis-v0.4` (D020), datakonv `req-v1.0` mit verifizierten Units.*

## Sprint-Ziel

Der E2E-Nachweis (P0-Abnahmekriterium 1) wird vollendet: datakonv durchläuft SWE.5/SWE.6 (Integrations-/Gesamtverifikation gegen STK/SWR), einen realen Problem-Zyklus (SUP.9) und einen realen CR mit Impact-Analyse (SUP.10, angestoßen über den neuen Feedback-Weg), und wird released (SPL.2: Version 1.0.0, Release Notes, **G3**) mit Registrierung im Produktkatalog v0 (Masterplan 5.5). Vorab wirken die drei Retro-CRs aus Sprint 4.

## Sprint-Backlog (Reihenfolge)

| # | Ticket | Inhalt | Rolle | blocked_by |
|---|---|---|---|---|
| 1 | T-0049 | Matrix-CI-Gate im Produkt-Repo (Retro-CR 1/3) | CM | — |
| 2 | T-0050 | Preflight räumt verwaiste Git-Locks (Retro-CR 2/3, R7) | DEV | — |
| 3 | T-0051 | board.py erzwingt optionen-Frontmatter für neue DRs (Retro-CR 3/3) | CHG | — |
| 4 | T-0052 | SWE.5/6: Integrations-/Gesamtverifikation datakonv (CLI-E2E gegen STK/SWR) + Report | TEST | — |
| 5 | T-0053 | SUP.9: realen Befund aus T-0052 als Problem-Ticket bis Abschluss führen | PROB | T-0052 |
| 6 | T-0055 | Feedback-Ticket-Routing v1: Skript Feedback → Problem/CR (Masterplan 5.5) | DEV | — |
| 7 | T-0054 | SUP.10: realer CR am Produkt mit Impact-Analyse (Quelle: Feedback des Menschen via T-0055-Routing) | CHG | T-0055 |
| 8 | T-0056 | Produktkatalog v0: `process/catalog/products.yaml` + Detailseite, Eintrag skript-generiert | CM | — |
| 9 | T-0057 | Release datakonv 1.0.0: SPL.2 — Packaging, Release Notes, Tag, Katalog-Eintrag → **G3** | CM | T-0052, T-0053, T-0054, T-0056 |
| 10 | T-0058 | Sprint-5-Report + Retro → G4 | PL | T-0057 |

**Bewusst nicht gezogen:** MCP-Verpackung des Produkts und Produkt-KPIs (Masterplan 5.5 — P3-Zielbild); CI-generierter Katalog-Eintrag als Automatik (v0 = Skript-Route beim Release, dokumentierte Abweichung); Copilot-/Ollama-PoC (Sprint 6, F13).

## Human-Gates dieses Sprints

**G3 (Release datakonv)** — deine Freigabe vor dem Release-Tag. **G4** (Sprint-Review). Dazu erbeten: ein echter Änderungswunsch von dir als Feedback (Input für T-0054/T-0055) und — gern gebündelt — F6, F8–F13.

## Kapazität und Budget

API-Budget-Stand: 0,00 € von 20 €/Monat (D012, Review weiter vertagt per D015). Arbeit in Cowork-Session + Team-Node-Ticks; erwartete API-Kosten 0 €.

## Arbeitsweise

Wie Sprint 4 (Statuswechsel über board.py, Commits mit Ticket-ID, requirements-first, Reviewer ≠ Autor, Preflight je Start — in dieser Session grün). Neue DRs nutzen das optionen-Frontmatter (T-0039/T-0051). Betriebsmodell: Arbeitskopien gemountet, Commits lokal, Push per `sprint5-abschluss.cmd` (D007).
