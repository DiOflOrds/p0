# Sprint-4-Plan — P0 „Genesis" (PL)

*Erstellt 2026-08-06, Rolle PL (Session-Kontext). Sprint-Motto (P0 Kap. 5): „Generalprobe: Übungsprodukt, Teil 1". Planning gemäß Playbook Kap. 4; requirements-first verbindlich (Playbook 0.6).*

## Sprint-Ziel

Das volle Team (10 Rollen) arbeitet erstmals eine fremde Aufgabe ab: Übungsprodukt **„datakonv"** (CSV↔JSON-Konverter-CLI, Python stdlib, eigenes Repo `produkt-datakonv` — D016) durchläuft SWE.1–SWE.3 requirements-first mit automatisierter Unit-Verifikation (SWE.4) in CI. Vorab werden die drei Retro-CRs aus Sprint 3 umgesetzt. Parallel wird die Hub-VM-Beschaffung (D014) begleitet.

## Sprint-Backlog (Reihenfolge)

| # | Ticket | Inhalt | Rolle | blocked_by |
|---|---|---|---|---|
| 1 | T-0037 | trace-matrix-Gate in CI: p0-Checkout im platform-Workflow (Retro-CR 1/3) | CM | — |
| 2 | T-0038 | Zweiphasen-Tick idempotent: Phase 1 ohne Statuswechsel-Commits (Retro-CR 2/3) | DEV | — |
| 3 | T-0039 | DR-Optionen maschinenlesbar (Frontmatter) + Inbox-Validierung (Retro-CR 3/3) | CHG | — |
| 4 | T-0041 | DR: Übungsprodukt wählen — **beantwortet (D016)** | PL→Mensch | — |
| 5 | T-0042 | Produkt-Repo-Skelett `produkt-datakonv` (lokal) + CM-Setup (CI, Baseline-Struktur) | CM | T-0041 |
| 6 | T-0043 | SWE.1: Clarifications + STK/SWR-Set datakonv (EN, 10–20 SWRs, D011) → G1-Vorlage | RM | T-0042 |
| 7 | T-0044 | SWE.2: Architektur datakonv (Units, ADRs) → G2-Vorlage | ARCH | T-0043 |
| 8 | T-0045 | SWE.3: Implementierung Units (stdlib, requirements-first) | DEV | T-0044 |
| 9 | T-0046 | SWE.4: Unit-Verifikation automatisiert in CI + SWR↔Test-Matrix datakonv | TEST | T-0045 |
| 10 | T-0047 | Hub-VM (D014): Beschaffung begleiten — Runbook, Deployment `platform/infra/`, Geräteregister | CM | Mensch: VM |

**Re-Planung 2026-08-06 (PL, D017):** T-0047 entfällt — Hub-VM für P0 gestrichen („bleiben wir lokal"), Betrieb bleibt auf Team-Node-1; R2 geschlossen, E5 revidiert. Der VM-Punkt in den Human-Gates entfällt entsprechend.

**Bewusst nicht gezogen:** SWE.5/SWE.6, Problem-/CR-Zyklus am Produkt, Release + Produktkatalog (P0 Kap. 5 → Sprint 5); Budget-Review D012 bleibt vertagt bis Claude-Kostendaten existieren (D015); T-0008 bleibt beim Menschen.

## Human-Gates dieses Sprints

**G1 (Übungsprodukt):** Freigabe der Anforderungs-Baseline datakonv (T-0043). **G2 (ggf.):** Architektur datakonv (T-0044). **G4:** Sprint-Review. Dazu vom Menschen erbeten: GitHub-Repo `produkt-datakonv` (privat) anlegen (D016), VM-Beschaffung gemäß T-0035/A1-Empfehlung (D014: Sprint 4), Secret für T-0037 (platform-CI liest p0), F6/F8–F13.

## Kapazität und Budget

API-Budget-Stand: 0,00 € von 20 €/Monat (D012). Arbeit in Cowork-Session (Abo, API-frei) + autonome Ticks am Team-Node (Ollama/Session-Kette). Erwartete API-Kosten: 0 € (T-0008 verschoben, D015).

## Arbeitsweise

Alle Statuswechsel über board.py + BOARD.md-Commit; Commits referenzieren Ticket-IDs; Produkt-Tickets referenzieren SWR-IDs des datakonv-Sets (requirements-first, T-0025); Reviews durch zweiten Rollen-Kontext; Preflight zu jedem Session-/Tick-Start (in dieser Session grün gelaufen). Betriebsmodell wie Sprint 3: Arbeitskopien des User-PCs gemountet, Commits lokal, Push durch den Menschen (D007).
