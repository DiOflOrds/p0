# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-15 — **P0 UND P1 ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**P0 ist fertig.** Sprints 0–6 abgeschlossen, P0-Abnahme gegen Kap. 3 erteilt (D024), Baseline **`genesis-v1.0`** getaggt. Das Team ist einsatzbereit: 10 aktive Rollen, Plattform mit 112 grünen Tests und 3 CI-Matrix-Gates, released Produkt **datakonv 1.0.0** (42 Tests, Katalog-Eintrag), Runbook, Intake-Workflow, P1-Hülle mit priorisiertem Backlog (B1–B10). Gesamtkosten: **0,00 € API** — alles über Abo-Session, Ollama und Skript-Routen.

Sprint-6-Ergebnis: Retro-CRs T-0062–64 (status-Subkommando, Feedback-Auto-Abschluss, produkte.yaml), Self-Check (12 Gebiete belegt, Lücken adressiert), KPI-Baseline mit Wirksamkeitsnachweis über 14 Prozess-CRs, Copilot-Executor v1 (D023: Abo vorhanden), Betriebs-Runbook, Intake + P1-Hülle, Abschlussbericht. Abweichungen der Abnahme (Kriterien 4/5/9 teilweise) transparent dokumentiert und nachverfolgt (B5/B6/B9, T-0072).

**P1 „Mission Control 2.0" ist ABGESCHLOSSEN (G4a/D009 via Inbox, 2026-08-15), Baseline `p1-v1.0`** (p1 + platform). Ergebnis: Multi-Projekt-Leitstand (ADR-004-Discovery, 8 Tabs), Inbox als Gate-Regelkanal (3 reale Inbox-Entscheidungen D006/D007/D009), E-Mail-Benachrichtigung live (Zustellnachweis T-0020; Empfänger per D008 dimitri.john83@gmail.com). Kriterien K1–K5 erfüllt (Abschlussbericht mit Evidenz). Ehrliche Abweichung: Benachrichtigt-Marker der T-0022-Mail fehlt im Repo → BB-6.

**P2 „Betriebshärtung" per Intake angelegt (2026-08-15):** Projektwahl durch Auftraggeber (Session-Dialog), Repo-Hülle `p2/` valide (board-check grün), Projektauftrag v0.1 mit 6 Epics (BB-2/3/4, B7, B3, F9) und 5 Abnahmekriterien. **G0 wartet als Inbox-DR T-0001** (Frist 2026-08-22, Default G0a) — dessen Mail ist zugleich der BB-6-Nachweis. `abschluss.cmd` pusht jetzt generisch jedes Repo mit Remote.

## Warten auf Auftraggeber (~5 Min)

1. GitHub-Repo **p2** anlegen (privat): [github.com/new](https://github.com/new) → Name `p2`, Private, ohne README. Dann im cmd-Fenster im Repo-Ordner: `git -C p2 remote add origin https://github.com/DiOflOrds/p2.git`
2. Secret setzen: [github.com/DiOflOrds/p2/settings/secrets/actions](https://github.com/DiOflOrds/p2/settings/secrets/actions) → `PLATFORM_READ_TOKEN` (gleiche PAT wie bei p0/p1).
3. **`abschluss.cmd`** — pusht alles (inkl. p1-v1.0-Tags + p2) und mailt den G0-DR an dimitri.john83@gmail.com.
4. **T-0001 in der Inbox beantworten** (Projekt p2): G0a = Projektauftrag freigeben.

## Nächste Session

Nach der G0-Antwort: D000 verbuchen, Sprint-0-Planning P2 (Anforderungen E2/E4/E6 requirements-first → G1). Aufruf: **„Starte P2 Sprint 0"**.

## Betriebs-Backlog (Runbook Kap. 7)

BB-1 Copilot CLI installieren + T-0072-Lauf (schließt P0-K9) · BB-2/3/4 → **in P2 übernommen** (E1/E2/E3) · BB-5 PAT-Erneuerung ab 2026-09-05 · BB-6 Mail-Zustellung beobachten → **Nachweis mit dem G0-DR T-0001**.

## Offene Fragen

Keine — F1–F13 vollständig entschieden; P0 (D000–D025) und P1 (D000–D009) abgeschlossen.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1} (+p2 lokal, Remote anlegen) · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/management/p1-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
