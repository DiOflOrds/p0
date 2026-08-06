# UI-Abnahme SWR-021 — Frontend-MVP (T-0034, 2026-08-06)

*Nachweisart: dokumentierte manuelle Abnahme (Verifikationsstrategie Kap. „Abnahme"). Umgebung: Backend `server.py --repos .` gegen die echten Arbeitskopien, Chromium-basierter Browser (Sandbox) bzw. curl für HTTP-Belege.*

| # | Kriterium (aus SWR-021) | Schritt | Ergebnis |
|---|---|---|---|
| 1 | Board-Status ohne Git-Zugriff | GET `/` → Tab „Board" | ✅ 36 Tickets, gruppiert nach Status, Rollen-/Prio-Pillen |
| 2 | Sprint-Reports sichtbar | Tab „Reports" | ✅ sprint-2/sprint-1/sprint-0-Reports gerendert |
| 3 | Kosten/KPI-Trends | Tab „Kosten/KPI" | ✅ Läufe, Gesamtkosten, je Monat, je Provider aus Run-Registry |
| 4 | Decision-Inbox listet offene DRs | Tab „Inbox" | ✅ T-0035 mit Body (Optionen/Frist) angezeigt |
| 5 | Entscheidung abgebbar | POST-Formular (Option + Begründung) | ✅ per API-Test verifiziert (`HttpTest::test_post_entscheidung`, D-ID + Commit); im UI nicht gegen echte Repos ausgelöst, um keine Testentscheidung ins echte Log zu schreiben |
| 6 | Smartphone-tauglich | Viewport-Meta, responsives Raster, Buttons ≥ 40 px | ✅ per Code-Review; **Gerätetest durch Mensch ausstehend** |
| 7 | PWA-Basis | `manifest.webmanifest` ausgeliefert (200) | ✅; installierbar erst mit Icons/SW — bewusst außerhalb MVP (ADR-002) |
| 8 | Pfadschutz Statik | GET `/../server.py` | ✅ 404 |

**Bewertung (TEST):** SWR-021 abgenommen mit zwei ehrlichen Restpunkten: (6) echter Gerätetest durch den Menschen im Sprint-Review, (7) PWA-Installierbarkeit außerhalb MVP-Scope. Keine Blocker.
