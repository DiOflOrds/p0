# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-15 — **P0 UND P1 ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**P0 ist fertig.** Sprints 0–6 abgeschlossen, P0-Abnahme gegen Kap. 3 erteilt (D024), Baseline **`genesis-v1.0`** getaggt. Das Team ist einsatzbereit: 10 aktive Rollen, Plattform mit 112 grünen Tests und 3 CI-Matrix-Gates, released Produkt **datakonv 1.0.0** (42 Tests, Katalog-Eintrag), Runbook, Intake-Workflow, P1-Hülle mit priorisiertem Backlog (B1–B10). Gesamtkosten: **0,00 € API** — alles über Abo-Session, Ollama und Skript-Routen.

Sprint-6-Ergebnis: Retro-CRs T-0062–64 (status-Subkommando, Feedback-Auto-Abschluss, produkte.yaml), Self-Check (12 Gebiete belegt, Lücken adressiert), KPI-Baseline mit Wirksamkeitsnachweis über 14 Prozess-CRs, Copilot-Executor v1 (D023: Abo vorhanden), Betriebs-Runbook, Intake + P1-Hülle, Abschlussbericht. Abweichungen der Abnahme (Kriterien 4/5/9 teilweise) transparent dokumentiert und nachverfolgt (B5/B6/B9, T-0072).

**P1 „Mission Control 2.0" ist ABGESCHLOSSEN (G4a/D009 via Inbox, 2026-08-15), Baseline `p1-v1.0`** (p1 + platform). Ergebnis: Multi-Projekt-Leitstand (ADR-004-Discovery, 8 Tabs), Inbox als Gate-Regelkanal (3 reale Inbox-Entscheidungen D006/D007/D009), E-Mail-Benachrichtigung live (Zustellnachweis T-0020; Empfänger per D008 dimitri.john83@gmail.com). Kriterien K1–K5 erfüllt (Abschlussbericht mit Evidenz). Ehrliche Abweichung: Benachrichtigt-Marker der T-0022-Mail fehlt im Repo → BB-6.

**P2 „Betriebshärtung": Sprint 1 fertig (2026-08-15), G4 wartet in der Inbox.** G1 erteilt (D002 via Session-Dialog), Baseline `p2-req-v1.0`. Alle 6 SWRs umgesetzt und verifiziert: **Frist-Warnmails** (SWR-034/035, 2-Tage-Schwelle, Default-Hinweis), **Katalog-Check** (SWR-036) als Gate in abschluss.cmd + platform-CI, **Nutzer-Registry + Entscheider-Pflicht + Inbox-Härtung** (SWR-037–039 — entschiedene DRs verschwinden sofort, dein D001-Doppelklick ist damit unmöglich). E1/E3-Doku: Runbook Kap. 8 (Dienst-Checkliste), Geräteregister mit Soll-Toolchain. Tests **138+42 grün**, Matrix **39/0**. Betriebs-Backlog: nur noch BB-1 (Copilot CLI) und BB-5 (PAT-Termine) offen. **G4-DR T-0012 liegt in der Inbox** (Frist 2026-08-22, Default G4a).

## Warten auf Auftraggeber (~5 Min)

1. **PAT erweitern** (für die neue Katalog-CI): [github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens) → `p0-read-fuer-platform-ci` → Repository access um **p2, process, produkt-datakonv** ergänzen. Ohne das wird der nächste platform-CI-Lauf rot (klare Meldung beim Checkout).
2. **`abschluss.cmd`** — pusht Sprint 1 und mailt den G4-DR (T-0012).
3. **T-0012 in der Inbox beantworten** (Projekt p2) — dabei siehst du live die neue Entscheider-Auswahl, und der DR verschwindet nach der Antwort sofort (SWR-039-Stichprobe).

## Nächste Session

Nach der G4-Antwort: D003 verbuchen, Baseline `p2-v0.1` (p2 + platform), **„Starte P2 Sprint 2"** — Aufwandsschätzung (E5, erstmals selbst gelebt), K2-Realnachweis (Warnmail), Windows-Gate-Schritt (Retro-Maßnahme 1), dann Abnahme G3/G4.

## Betriebs-Backlog (Runbook Kap. 7)

BB-1 Copilot CLI installieren + T-0072-Lauf (schließt P0-K9) · BB-2/3/4 → in P2 (E1/E2/E3) · BB-5 PAT-Erneuerung ab 2026-09-05 · BB-6 **erledigt** (Marker + Zustellung T-0001, 2026-08-15).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; P0 (D000–D025) und P1 (D000–D009) abgeschlossen.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1} (+p2 lokal, Remote anlegen) · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/management/p1-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
