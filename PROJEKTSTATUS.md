# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-15 — **P0 UND P1 ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**P0 ist fertig.** Sprints 0–6 abgeschlossen, P0-Abnahme gegen Kap. 3 erteilt (D024), Baseline **`genesis-v1.0`** getaggt. Das Team ist einsatzbereit: 10 aktive Rollen, Plattform mit 112 grünen Tests und 3 CI-Matrix-Gates, released Produkt **datakonv 1.0.0** (42 Tests, Katalog-Eintrag), Runbook, Intake-Workflow, P1-Hülle mit priorisiertem Backlog (B1–B10). Gesamtkosten: **0,00 € API** — alles über Abo-Session, Ollama und Skript-Routen.

Sprint-6-Ergebnis: Retro-CRs T-0062–64 (status-Subkommando, Feedback-Auto-Abschluss, produkte.yaml), Self-Check (12 Gebiete belegt, Lücken adressiert), KPI-Baseline mit Wirksamkeitsnachweis über 14 Prozess-CRs, Copilot-Executor v1 (D023: Abo vorhanden), Betriebs-Runbook, Intake + P1-Hülle, Abschlussbericht. Abweichungen der Abnahme (Kriterien 4/5/9 teilweise) transparent dokumentiert und nachverfolgt (B5/B6/B9, T-0072).

**P1 „Mission Control 2.0" ist ABGESCHLOSSEN (G4a/D009 via Inbox, 2026-08-15), Baseline `p1-v1.0`** (p1 + platform). Ergebnis: Multi-Projekt-Leitstand (ADR-004-Discovery, 8 Tabs), Inbox als Gate-Regelkanal (3 reale Inbox-Entscheidungen D006/D007/D009), E-Mail-Benachrichtigung live (Zustellnachweis T-0020; Empfänger per D008 dimitri.john83@gmail.com). Kriterien K1–K5 erfüllt (Abschlussbericht mit Evidenz). Ehrliche Abweichung: Benachrichtigt-Marker der T-0022-Mail fehlt im Repo → BB-6.

**P2 „Betriebshärtung" ist ABGESCHLOSSEN (G4a/D004 via Inbox, 2026-08-15), Baseline `p2-v1.0`** (p2 + platform) — drittes Projekt in den Büchern, komplett an einem Tag. K1–K5 erfüllt mit Evidenz (Abschlussbericht); Höhepunkt: der K2-Realnachweis lief über das in P2 selbst gebaute Feature (Neu-Mail + FRIST-WARNUNG zu T-0017, beide Marker im Ticket, Zustellung bestätigt). 5 Entscheidungen, 4 davon via Inbox mit Entscheider-Protokoll.

**Das Team ist im Regelbetrieb.** Kein aktives Projekt. Werkzeuge: Intake für neue Projekte, Feedback-Route für Produkte, Inbox mit Mail + Frist-Warnung + Default für alle Gates, Katalog-Gate, Team-Node-Gate-Regel, Aufwandsschätzung.

**Nachtrag Betrieb (2026-08-15 abends): BB-1 geschlossen — extern blockiert (p0/D026).** Copilot CLI 1.0.80 wurde installiert + eingeloggt und der Executor real durchgemessen (Aufruf, Antwort, Diagnose) — die wörtliche Ursache steht in Registry und Ticket: **das Copilot-Abo ist abgelaufen** (revidiert D023/F13). Auftraggeber-Entscheidung: schließen, 0-€-Prinzip; Wiedereröffnung per CR bei neuem Abo. T-0072 + p1/T-0018 rejected mit voller Evidenz. Nebengewinn: Executor gehärtet (ANSI-Strip, Zaun-Toleranz, Rohantwort-Diagnose in der Registry, +3 Tests → Suite 141).

**P3 „Mission Control 3.0: Jira-like HMI" — Sprint 0 gelaufen (2026-08-15).** G0 erteilt (D000 via Inbox, nach Server-Neustart — Befund als Runbook-Eintrag UND als Anforderung SWR-047 verwertet). Requirements-first steht: **STK-015 + SWR-040–047** reviewed (Ticket-Detail + klickbare Querverweise, Board Jira-like mit Filtern, Inbox-Options-Buttons + DR-Historie, Requirements-/Traceability-Tabellen, Architektur-SVG aus versionierter Quelle, Projekt-Cockpit mit Frist-Ampel, Versions-/Neustart-Hinweis). **Architektur-Delta v1.2 + ADR-005** (Hash-Routing, komponenten.yaml → SVG-Generator, 4 neue Read-only-Endpunkte). Matrix 47/0 (UI-Checklisten-Regel), Preflight STARTKLAR. **G1-DR T-0005 und G2-DR T-0006 liegen in der Inbox** (Frist 2026-08-22, Defaults G1a/G2a).

## Warten auf Auftraggeber (~4 Min)

1. **`abschluss.cmd`** — pusht Sprint 0 und mailt **zwei** DRs (G1 + G2).
2. **In der Inbox beantworten** (Projekt p3): **T-0005** (G1, Stichprobe: SWR-Set kurz lesen — deckt es deinen Wunsch?) und **T-0006** (G2, Stichprobe: ADR-005, 2 Min).

## Nächste Session

Nach beiden Antworten: **„Starte P3 Sprint 1"** — Verbuchen, Baseline `p3-req-v1.0`, dann Umsetzung „Klickbarkeit": Ticket-Detail (SWR-040), Board Jira-like (041), Inbox-Buttons + Historie (042), Versions-Hinweis (047).

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. R1 (P2-Retro): Aufwandsschätzung nach 2–3 Sprints kalibrieren → Playbook-Standard.

## Betriebs-Backlog (Runbook Kap. 7)

BB-1 Copilot CLI installieren + T-0072-Lauf (schließt P0-K9) · BB-2/3/4 → in P2 (E1/E2/E3) · BB-5 PAT-Erneuerung ab 2026-09-05 · BB-6 **erledigt** (Marker + Zustellung T-0001, 2026-08-15).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; P0 (D000–D025) und P1 (D000–D009) abgeschlossen.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/management/p1-abschlussbericht.md`, `p2/management/p2-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
