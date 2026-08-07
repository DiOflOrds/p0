# Projektstatus P0 „Genesis" — Fortschreibung über Sessions

*Dieses Dokument ist der Übergabepunkt zwischen Cowork-Sessions: aktueller Stand, nächste Schritte, offene Punkte. Zuletzt aktualisiert: 2026-08-07 (Sprint 5 ABGESCHLOSSEN UND ABGENOMMEN, D022). Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert; im Claude-Projekt ersetzt es `aspice-team/10-projektstatus.md` (oder p0-Repo als GitHub-Quelle verbinden).*

## Aktueller Stand

**Sprint 0–5: abgeschlossen und abgenommen.** Sprint 5 „Generalprobe Teil 2 + Release" (**G4/D022**, Baseline **`genesis-v0.5`**): **datakonv 1.0.0 released** (G3/D021, Tags `v1.0.0` + `req-v1.1`, Produktkatalog-Eintrag) — **P0-Abnahmekriterium 1 (E2E-Nachweis) ist erfüllt:** SWE.1–SWE.6, realer Problem-Zyklus und realer Feedback→CR-Zyklus liefen ohne operative Mensch-Arbeit (nur Clarifications, Gates, Feedback). Kernstand:

- **Realer Problem-Zyklus (T-0053):** BOM-Befund aus der Integrationsverifikation (T-0052, E2E-Suite) → Fix + SWR-D14-Präzisierung + Regressionstests.
- **Realer CR-Zyklus (T-0054/T-0059/T-0060):** Mensch-Feedback (--indent) → Routing-Skript v1 (T-0055, Erstlauf korrekt) → Impact-Analyse → SWR-D18 reviewed vor Code → Umsetzung.
- **Produktkatalog v0** (`process/catalog/`, Masterplan 5.5) mit Generator-Skript; erster Eintrag live.
- **Retro-CRs S4 umgesetzt** (T-0049 Matrix-Gate produkt-CI, T-0050 Preflight+Produkt-Repos, T-0051 DR-optionen-Pflicht — fand real den Bestands-DR T-0022).
- KPIs: Tests 101 (platform) + 42 (produkt) grün · Matrizen 24/0 und 18/0 · API-Kosten Sprint 0–5: **0,00 €** · Gates G1–G4 alle real durchlaufen · Entscheidungen D000–D022.
- Retro-CRs für Sprint 6: **T-0062** (board.py Status-Subkommando), **T-0063** (Feedback-Auto-Abschluss), **T-0064** (produkte.yaml + `trace_matrix --produkt`).

## Warten auf Auftraggeber

1. **Secret `PLATFORM_READ_TOKEN` in DiOflOrds/produkt-datakonv anlegen** (gleiche PAT wie p0/board-check; Anleitung im CI-Workflow-Kopf), dann **`sprint5-abschluss.cmd` ausführen** — prüft alles, pusht alle vier Repos inkl. Tags, öffnet die Actions.
2. Offene Fragen F6, F8–F13; T-0008 (API-Key) bleibt bewusst verschoben (D015) — Wiedervorlage in Sprint 6 (Copilot-/Ollama-PoC braucht ihn nicht, der erste Claude-Tick schon).

## Nächste Session (Sprint 6 — „Härtung, Self-Check & Abnahme", letzter P0-Sprint)

1. Sprint-6-Planning (PL): Retro-CRs T-0062–T-0064; **Self-Check** gegen die Basispraktiken aller Stufe-1-Prozesse (QM+COACH, Report mit Fundstellen/Lücken); Lücken schließen oder als P1-Backlog dokumentieren.
2. **Betriebs-Runbook** (CM): Backup, Monitoring, Update, Störungsbehandlung, Geräte-Onboarding; KPI-Baseline + Retro-Wirksamkeitsnachweis (Kriterium 6).
3. **Team-Node-PoC-Vervollständigung:** Copilot-CLI-Executor (F13: gh-Login nötig) und Ollama-Executor-Nachweis; Intake-Workflow P1 + P1-Hülle.
4. **P0-Abschlussbericht** → P0-Abnahme gegen Kap. 3 (= G3 für P0 selbst) durch den Menschen.

## Offene Fragen

F6 Zielprodukte · F8 parallele Projekte · F9 weitere Nutzer · F10 Vertraulichkeit · F11 Arbeitsteam-Domäne · F12 Geräte-Landschaft/Hub-Gerät · F13 Copilot-Abo/Ollama-Hardware (relevant für Sprint 6-PoC)

## Referenzen

Masterplan 0.6 · Playbook 0.6 · Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv} · Baselines: **genesis-v0.5**, datakonv **v1.0.0**/req-v1.1 · Decision Log: D000–**D022** · Sprint-5-Report: `p0/management/sprint-5/report.md` · Katalog: `process/catalog/products.yaml`
