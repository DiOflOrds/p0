# KPI-Baseline + Retro-Wirksamkeitsnachweis — P0 (T-0068, PL)

*2026-08-07. Datenquellen: Sprint-Reports 0–5, Run-Registry, Board, Testsuiten, Decision Log. Grundlage für Abnahmekriterium 6/7 (P0 Kap. 3) und Vergleichsbasis für P1.*

## KPI-Baseline (Sprint 0–6)

| KPI | Wert | Quelle/Anmerkung |
|---|---|---|
| API-Kosten gesamt | **0,00 €** von 20 €/Monat (D012) | Run-Registry; gesamte Arbeit über Abo-Session, Ollama, Skripte |
| Tests plattform / produkt | 0 → **112** / 0 → **42** (alle grün, CI-Pflicht) | Suiten; Wachstum je Sprint in den Reports |
| Traceability | Plattform 24 SWRs / **0 Lücken** · Produkt 18 SWRs / **0 Lücken** | Matrizen, CI-Gates in beiden Repos |
| Tickets | 72 angelegt · 64 done · 1 rejected (D017) · Rest offen (T-0008 Mensch, T-0071/72 Sprint 6) | BOARD.md |
| Commits mit Ticket-ID | **100 %** (Stichproben je Report) | Git-Historie |
| Wiederöffnungsquote | 1 Fall (T-0040-Problem nach Sprint-3-Abnahme), sonst 0 | Board-Historie |
| Autonome Ticks | 3 (1× ollama, 2× session); Statuswechsel-Rauschen seit T-0038: **0 Zyklen** (keine Warte-Läufe seither — Messung läuft in P1 weiter) | Run-Registry, Betriebsdaten-Doku |
| Mensch-Interaktionen | 24 Entscheidungen D000–D023 (Gates G0–G4 alle real, 1× Inbox, Rest Session-Dialog), 2 Clarification-Runden, 1 Feedback | Decision Log |
| Automatisierungsgrad (Skript-Routen) | 8 Skripte: board(+status), preflight, trace_matrix(+produkt), feedback_route(+abschluss), catalog, tick, gateway, dateiblock | platform/scripts, Kriterium 6 (Skriptifizierung) |
| Released Produkte | 1 (datakonv 1.0.0, Katalog-Eintrag) | catalog/products.yaml |

## Retro-Wirksamkeitsnachweis (Kriterium 6: umgesetzte Prozess-CRs mit gemessener Wirkung)

| CR (Sprint) | Erwartungswert | Ist (gemessen) |
|---|---|---|
| T-0015 (S1→2) CI-Workflows | kein roter Stand unbemerkt | CI-Gates aktiv in 3 Repos; rote Läufe nur bei fehlendem Secret (dokumentiert) |
| T-0016 (S1→2) Wissensbasis CM | Lernzyklus | L-001–L-004 + Gold-Beispiele (T-0029) — **Wissensbasis-Update-Nachweis** |
| T-0024 (S2→3) Preflight | 0 Analyse-Blöcke | R7-Fall in S3 real abgefangen; S4-Fälle traten vor Wiederholungslauf auf → T-0050 |
| T-0025 (S2→3) Requirements-first | 100 % SWR-Bezug | 100 % seit S3 (Reports), SWR-D18 reviewed vor Code |
| T-0026 (S2→3) Matrix | Lücken sichtbar | fand einzige Lücke (SWR-021) in S3; seither 0 — **Skriptifizierung** |
| T-0037/T-0049 (S3/S4) Matrix-CI-Gates | Lücken brechen CI | Gates aktiv (platform + produkt) |
| T-0038 (S3→4) Tick idempotent | 0 Statuszyklen je Warte-Lauf | 0 seit Einführung (keine Warte-Läufe — Weitermessung P1) |
| T-0039/T-0051 (S3/S4) DR maschinenlesbar | ungültig → 400; 100 % neue DRs | Validierung fand real T-0022; T-0061/T-0071 maschinenlesbar |
| T-0048/T-0064 (S4/S5) Matrix generalisiert | Produkt-Matrix 1 Parameter | `--produkt datakonv --check` real verifiziert |
| T-0050 (S4→5) Preflight+Produktrepos | 0 manuelle Lock-Eingriffe | seit Einführung 0 (S6-Session: Locks nur vor Verfügbarkeit) |
| T-0055/T-0063 (S5/S6) Feedback-Routing | korrekte Klassifikation, 0 manuelle Abschlüsse | Erstlauf korrekt (T-0059→T-0060); Auto-Abschluss ab jetzt |
| T-0062 (S5→6) Status-Subkommando | 0 geblockte Status-Versuche | seit Einführung 0 (alle S6-Wechsel über Subkommando; davor 1 geblockter sed-Versuch in S5 = Referenzwert) |

**Fazit:** 14 umgesetzte Prozess-CRs, davon 12 mit bereits gemessener Wirkung, 2 mit laufender Messung (T-0038, T-0063) — Kriterium 6 inkl. Wissensbasis-Update (T-0016/T-0029) und mehrfacher Skriptifizierung (T-0026, T-0062, T-0064) erfüllt.
