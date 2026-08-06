# Sprint-4-Report — P0 „Genesis" (PL)

*2026-08-06. Sprint-Motto: „Generalprobe: Übungsprodukt, Teil 1". An: Mensch (G4-Review). Von: PL, mit QM-/TEST-Abschnitten.*

## Sprint-Ziel: erreicht

Das volle Team hat erstmals eine fremde Aufgabe abgearbeitet: Übungsprodukt **datakonv** (D016) durchlief SWE.1–SWE.4 requirements-first — Clarifications → STK/SWR-Set mit **G1** (D018, `req-v1.0`) → Architektur mit ADRs und **G2** (D019) → Implementierung (stdlib-only) → automatisierte Unit-Verifikation mit Matrix **17/17 SWRs, 0 Lücken**. Mensch-Beteiligung ausschließlich: Auftrag präzisieren, Gates freigeben, DRs beantworten (P0-Abnahmekriterium 1, Teil 1 belegt).

## Ergebnis je Ticket (11 done, 1 rejected)

| Ticket | Ergebnis |
|---|---|
| T-0037 | Matrix-Gate in platform-CI (p0-Checkout via `P0_READ_TOKEN`); Secret vom Menschen gesetzt |
| T-0038 | Zweiphasen-Tick idempotent: Warte-Lauf ohne Statuswechsel-Commits (Phase-1-Erkennung) |
| T-0039 | DR-Optionen maschinenlesbar (Frontmatter) + Inbox-Validierung (ungültig → 400 ohne Log-Eintrag) |
| T-0041 | DR Übungsprodukt → **D016**: CSV↔JSON-CLI „datakonv", eigenes Repo |
| T-0042 | Produkt-Repo-Skelett + CI + CM-Eintrag; GitHub-Repo vom Menschen angelegt und gepusht |
| T-0043 | SWE.1: STK-D01–D05 + SWR-D01–D17 (EN, reviewed, DoD) → **G1/D018**, Tag `req-v1.0` |
| T-0044 | SWE.2: Architektur (4 Units, reine str→str-Konvertierung) + ADR-D01–D03 → **G2/D019** |
| T-0045 | SWE.3: Units implementiert (cli/c2j/j2c/errors), zentrales Exit-Code-Mapping |
| T-0046 | SWE.4: 31 Tests, Matrix `datakonv-swr-test-matrix.md` — 0 Lücken, 0 Tests ohne Bezug |
| T-0048 | CR aus laufender Arbeit: trace_matrix generalisiert (Produkt-Repos), Defaults unverändert |
| T-0047 | **rejected per D017** — Hub-VM entfällt für P0, Betrieb bleibt lokal (R2 geschlossen, E5 revidiert) |

## KPIs

Tests platform 81 → **92** + produkt **31** (alle grün) · Matrizen: platform 24 SWRs/0 Lücken, datakonv 17 SWRs/0 Lücken · API-Kosten Sprint 0–4: **0,00 €** (D012) · Commits mit Ticket-ID: 100 % · Entscheidungen: D016–D019 (2 via Session-Dialog-Gates, alle im Log) · CM-Hygiene: `__pycache__` aus platform-Versionskontrolle entfernt.

## TEST-Abschnitt (Verifikation)

datakonv: alle 17 SWRs unit-verifiziert inkl. sämtlicher Fehlerfälle (Exit-Codes, UTF-8, RFC-4180, Verschachtelung mit JSON-Pfad); Round-Trip-Eigenschaft (SWR-D17) bestanden. Verifikationsschulden (ehrlich): Produkt-Matrix ohne CI-Gate (T-0049, Retro), SMTP-Erfolgspfad weiter ungetestet (seit Sprint 3), Windows-Konsolen-Encoding nur über `buffer`-Pfad abgedeckt.

## QM-Abschnitt (ungefiltert)

1. Reviews weiterhin durch Rollen-Kontexte derselben Session (Bootstrap-Modus); finale Abnahme = dieses G4. 2. R7 trat zweimal auf (Locks), behoben nach Freigabe der Datei-Löschung — als Retro-CR T-0050 adressiert. 3. T-0041 nutzte Freitext-Optionen (T-0039 kam im selben Sprint) — T-0051 erzwingt das Frontmatter für neue DRs. 4. Gates G1/G2 liefen über den Session-Dialog statt über die Inbox — zulässig (Präzedenz D009/D015), aber die Inbox blieb diesen Sprint ungenutzt.

## Entscheidungsbedarf an dich (G4)

**G4 Sprint 4:** Abnahme der 11 done-Tickets + Retro (T-0049–T-0051 für Sprint 5). Nach Freigabe taggt CM die Baseline **`genesis-v0.4`** (process/platform/p0; produkt-datakonv trägt bereits `req-v1.0`). Optionen: abnehmen / mit Auflagen / zurückweisen.
