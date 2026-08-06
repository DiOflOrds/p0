# Sprint-3-Plan — P0 „Genesis" (PL)

*Erstellt 2026-08-06, Rolle PL (Session-Kontext). Sprint-Motto (P0 Kap. 5): „Backend & Frontend MVP — Mission Control v1". Planning gemäß Playbook Kap. 4; Requirements-first ab diesem Sprint (T-0025).*

## Sprint-Ziel

Das Team baut erstmals Produkt-Software nach der eigenen Mechanik: Backend/Frontend-MVP (Decision-Inbox, Reports, Board-Sicht) entsteht requirements-first (STK-012, SWR-020/021 → reviewed vor Implementierung), mit aktivierten SWE-Rollen (ARCH/DEV/TEST), Architektur mit ADRs (G2) und automatisierter Verifikation inkl. SWR↔Test-Matrix. Parallel wird der Betrieb Richtung Hub-VM vorbereitet (E5, R2).

## Sprint-Backlog (Reihenfolge)

| # | Ticket | Inhalt | Rolle | blocked_by |
|---|---|---|---|---|
| 1 | T-0024 | Session-Preflight als Skript-Route (Retro-CR 1/3) | CM | — |
| 2 | T-0025 | Requirements-first-Regel für Plattform-/Produkt-Tickets (Retro-CR 2/3) | CHG | — |
| 3 | T-0026 | SWR↔Test-Traceability: Docstring-IDs + Matrix-Generator (Retro-CR 3/3) | DEV | — |
| 4 | T-0028 | Rollenkarten v1 ARCH/DEV/TEST + Registry v1.2 | COACH | — |
| 5 | T-0029 | Skills v1 SWE.2, SWE.3, SWE.4–6 (+ Gold-Beispiele) | COACH | T-0028 |
| 6 | T-0030 | SWE.1: STK-012 + SWR-020/021 draft → reviewed; G1-Erweiterungsvorlage | RM | — |
| 7 | T-0031 | SWE.2: Architektur Backend/Frontend-MVP + ADRs → G2-Vorlage | ARCH | T-0028, T-0030 |
| 8 | T-0032 | Backend-MVP: Decision-Inbox, Board/Report-Aggregation, E-Mail (SWR-020) | DEV | T-0031 |
| 9 | T-0033 | Frontend-MVP: lesende PWA + Decision-Inbox (SWR-021) | DEV | T-0031 |
| 10 | T-0034 | SWE.4: Verifikation Backend/Frontend + SWR↔Test-Matrix | TEST | T-0032, T-0033 |
| 11 | T-0035 | DR: Hub-VM-Beschaffung (E5, R2) + Deployment-Ziel + D006-Review | PL→Mensch | — |
| 12 | T-0036 | Autonome Ticks nachholen (Betriebsdaten); Claude-Tick sofern T-0008 | CM | — |
| — | T-0008 | Anthropic-API-Key (bleibt beim Menschen, kein Sprint-Blocker) | Mensch | — |

**Bewusst nicht gezogen:** WebSocket-Live-Board und PWA-Push (P0 Kap. 5, Sprint 3-Langform) — MVP-Schnitt bleibt „lesend + Decision-Inbox" (P0 Kap. 8, Scope-Leitplanke); Deployment auf der VM erfolgt erst nach T-0035-Entscheidung (Infra-as-Code wird mitgeliefert, Ausführung folgt).

## Human-Gates dieses Sprints

**G1-Erweiterung:** Freigabe STK-012 + SWR-020/021 als Baseline-Erweiterung (T-0030). **G2:** Plattform-Architektur/Technologie (T-0031). **G4:** Sprint-Review. Dazu: Entscheidung T-0035 (Hub-VM), T-0008 (API-Key) sowie — soweit möglich — F6, F8–F13.

## Kapazität und Budget

API-Budget-Stand: 0,00 € von 20 €/Monat (D012). Sprint 3 arbeitet in der Cowork-Session (Abo, API-frei); autonome Ticks auf dem Team-Node (Ollama/Session-Kette). Erwartete API-Kosten: 0 € ohne T-0008; mit T-0008 ≤ 2 € (erster Claude-Tick, Kostendaten für Budget-Review Sprint 4).

## Arbeitsweise

Alle Statuswechsel über board.py + BOARD.md-Commit; Commits referenzieren Ticket-IDs; jedes Plattform-Ticket referenziert SWR-IDs oder einen CR (T-0025, ab sofort); Reviews durch zweiten Rollen-Kontext (Reviewer ≠ Autor); Preflight-Skript (T-0024) läuft ab Verfügbarkeit zu jedem Session-/Tick-Start. Sandbox-Betriebsmodell dieser Session: Arbeitskopien des User-PCs gemountet, Commits lokal, Push am Sprint-Ende durch den Menschen (D007; Sandbox hat in dieser Session keinen GitHub-Zugriff, auch kein Read — als Betriebsnotiz für R7 dokumentiert).
