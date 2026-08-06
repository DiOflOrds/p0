# Integrations-/Gesamtverifikation datakonv (SWE.5/6, T-0052)

*2026-08-06, TEST. Prüfling: datakonv (Stand nach T-0053-Fix, vor Release 1.0.0). Methode: reales CLI als Subprozess (`tests/test_e2e.py`, 8 Szenarien) gegen die Stakeholder-Szenarien STK-D01–D04 — echte Dateien, Pipes, Exit-Codes, realistische Eingaben.*

## Ergebnis

| Szenario | STK/SWR | Ergebnis |
|---|---|---|
| Pipe stdin→stdout (Shell-Nutzung) | STK-D04, SWR-D02/D05 | bestanden |
| Datei→Datei-Roundtrip byte-identisch | STK-D01/D02, SWR-D17 | bestanden |
| Delimiter `;` durchgängig | SWR-D03 | bestanden |
| Exit-Codes + stdout/stderr-Trennung | STK-D03, SWR-D15 | bestanden |
| UTF-8/Umlaute | SWR-D14 | bestanden |
| **Excel-Export mit BOM** | SWR-D14 | **Befund → Problem T-0053** (BOM im ersten Header-Key); behoben (utf-8-sig), SWR-D14 präzisiert (v1.1), Regressionstests unit+E2E; Wiederholung: bestanden |
| `--version` | SWR-D04 | bestanden |

Suite produkt: 31 → **39 Tests grün** (inkl. E2E). Bewertung: Produkt erfüllt die Stakeholder-Szenarien; releasefähig aus TEST-Sicht nach Abschluss von T-0054 (CR --indent) und erneutem Suite-/Matrix-Lauf.
