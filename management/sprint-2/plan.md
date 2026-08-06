# Sprint-2-Plan — P0 „Genesis" (PL)

*Erstellt 2026-08-06, Rolle PL (Session-Kontext). Sprint-Motto (P0 Kap. 5): „Prozesse & Selbstübernahme". Planning gemäß Playbook Kap. 4.*

## Sprint-Ziel

Das Team führt P0 ab jetzt selbst (Bootstrap-Stufe 2: PL/CM/COACH aktiv, QM/RM/PROB/CHG werden scharfgeschaltet); die Requirements-Mechanik steht — nachgewiesen am ersten echten SWE.1-Set: den Anforderungen an die eigene Plattform.

## Sprint-Backlog (Reihenfolge)

| # | Ticket | Inhalt | Rolle |
|---|---|---|---|
| 1 | T-0015 | CI-Workflow: board-check + Unit-Tests je Push (Retro-CR 1/3) | CM |
| 2 | T-0016 | Wissensbasen-Erstbefüllung aus T-0013/T-0014 (Retro-CR 2/3) | COACH |
| 3 | T-0017 | BP-Mapping-Plausibilitäts-Review, pragmatisch per D010 (Retro-CR 3/3) | COACH |
| 4 | T-0019 | Rollenkarten v1 QM/RM/PROB/CHG + Registry-Aktivierung | COACH |
| 5 | T-0020 | Skills v1 SUP.1, SWE.1, SUP.9 (+ Gold-Beispiele) | COACH |
| 6 | T-0018 | CM-Strategie v1.1 (Review-Nacharbeit aus Sprint 1) | CM |
| 7 | T-0021 | SWE.1-Requirements-Set Plattform (EN, D011) + G1-Vorlage | RM |
| 8 | T-0022 | Budget-Review (D003) als Decision Request | PL→Mensch |
| 9 | T-0023 | Prozess-Baseline genesis-v0.2 (Tags + Manifest) | CM |
| — | T-0008 | Anthropic-API-Key (bleibt beim Menschen, kein Sprint-Blocker) | Mensch |

## Human-Gates dieses Sprints

**G1:** Freigabe der Plattform-Anforderungs-Baseline (T-0021). **G4:** Sprint-Review. Dazu: Antwort auf T-0022 (Budget) sowie — soweit möglich — F6, F8–F13.

## Kapazität und Budget

API-Budget-Stand: 0,00 € von 20 € (Testphase, D003). Sprint 2 arbeitet in der Cowork-Session (Abo, API-frei); autonome Ticks optional auf dem Team-Node. Erwartete API-Kosten Sprint 2: 0 €.

## Arbeitsweise

Alle Statuswechsel über board.py + BOARD.md-Commit; Commits referenzieren Ticket-IDs; Reviews durch zweiten Rollen-Kontext (Reviewer ≠ Autor, QM ab T-0019 verfügbar); finale Abnahme der in_review-Tickets im Sprint-Review (G4). Sprint-1-Bootstrap-Artefakte gelten mit den Reviews aus dem Sprint-1-G4 als nachreviewt (P0 Kap. 4).
