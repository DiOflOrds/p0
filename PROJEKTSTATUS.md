# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-15 — **P0 UND P1 ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**P0 ist fertig.** Sprints 0–6 abgeschlossen, P0-Abnahme gegen Kap. 3 erteilt (D024), Baseline **`genesis-v1.0`** getaggt. Das Team ist einsatzbereit: 10 aktive Rollen, Plattform mit 112 grünen Tests und 3 CI-Matrix-Gates, released Produkt **datakonv 1.0.0** (42 Tests, Katalog-Eintrag), Runbook, Intake-Workflow, P1-Hülle mit priorisiertem Backlog (B1–B10). Gesamtkosten: **0,00 € API** — alles über Abo-Session, Ollama und Skript-Routen.

Sprint-6-Ergebnis: Retro-CRs T-0062–64 (status-Subkommando, Feedback-Auto-Abschluss, produkte.yaml), Self-Check (12 Gebiete belegt, Lücken adressiert), KPI-Baseline mit Wirksamkeitsnachweis über 14 Prozess-CRs, Copilot-Executor v1 (D023: Abo vorhanden), Betriebs-Runbook, Intake + P1-Hülle, Abschlussbericht. Abweichungen der Abnahme (Kriterien 4/5/9 teilweise) transparent dokumentiert und nachverfolgt (B5/B6/B9, T-0072).

**P1 „Mission Control 2.0" ist ABGESCHLOSSEN (G4a/D009 via Inbox, 2026-08-15), Baseline `p1-v1.0`** (p1 + platform). Ergebnis: Multi-Projekt-Leitstand (ADR-004-Discovery, 8 Tabs), Inbox als Gate-Regelkanal (3 reale Inbox-Entscheidungen D006/D007/D009), E-Mail-Benachrichtigung live (Zustellnachweis T-0020; Empfänger per D008 dimitri.john83@gmail.com). Kriterien K1–K5 erfüllt (Abschlussbericht mit Evidenz). Ehrliche Abweichung: Benachrichtigt-Marker der T-0022-Mail fehlt im Repo → BB-6.

**P2 „Betriebshärtung": Sprint 2 (Abnahmesprint) fertig (2026-08-15) — nur noch der Abnahme-DR offen.** Sprint 1 abgenommen (G4a/**D003** via gehärtete Inbox, mit Entscheider im Log), Baseline `p2-v0.1`. Sprint 2: **Aufwandsschätzung eingeführt und gelebt** (E5/K4: 70 min geschätzt, 63 min Ist), Retro-Maßnahmen dokumentiert (Runbook Kap. 9 **Team-Node-Gate**, Gold-Beispiel „hermetische Tests"), zwei reale SUP.9-Zyklen im Projekt (T-0002 Suite-Mails/Windows, T-0013 CI-Tag-Rauschen/fetch-tags — beide gefixt). Abnahmebilanz K1–K5 im Report. **Abnahme-DR T-0017 liegt in der Inbox** — Frist **2026-08-17** bewusst in der Warnschwelle: der nächste abschluss-Lauf verschickt Neu-Mail UND Frist-Warnmail (= K2-Realnachweis; Dry-Run zeigt beide).

## Warten auf Auftraggeber (~3 Min)

1. **`abschluss.cmd`** — pusht Sprint 2 (inkl. Tags `p2-v0.1`) und verschickt **zwei Mails** zu T-0017 an dimitri.john83@gmail.com: „Neuer Decision Request" und „FRIST-WARNUNG" mit Default-Hinweis. Beide im Posteingang = K2 erfüllt.
2. **T-0017 in der Inbox beantworten** (Projekt p2): G4a = Sprint 2 abnehmen + P2 abschließen. Achtung: Frist ist der 17.08. — danach greift der Default G4a automatisch.

## Nächste Session

Nach der Antwort (oder dem Default): D004 verbuchen, **Baseline `p2-v1.0`**, P2-Abschlussbericht — drittes Projekt fertig, Team wieder im Regelbetrieb. Danach offen nur Betrieb: BB-1 (Copilot CLI + T-0072-Lauf), BB-5 (PAT-Erneuerung ab 2026-09-05), neues Projekt jederzeit per Intake.

## Betriebs-Backlog (Runbook Kap. 7)

BB-1 Copilot CLI installieren + T-0072-Lauf (schließt P0-K9) · BB-2/3/4 → in P2 (E1/E2/E3) · BB-5 PAT-Erneuerung ab 2026-09-05 · BB-6 **erledigt** (Marker + Zustellung T-0001, 2026-08-15).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; P0 (D000–D025) und P1 (D000–D009) abgeschlossen.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1} (+p2 lokal, Remote anlegen) · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/management/p1-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
