# Projektstatus P0 „Genesis" — Fortschreibung über Sessions

*Dieses Dokument ist der Übergabepunkt zwischen Cowork-Sessions: aktueller Stand, nächste Schritte, offene Punkte. Zuletzt aktualisiert: 2026-08-06 (Sprint 4 ABGESCHLOSSEN UND ABGENOMMEN, D020). Bitte als `aspice-team/10-projektstatus.md` ins Claude-Projekt übernehmen.*

## Aktueller Stand

**Sprint 0–4: abgeschlossen und abgenommen.** Sprint 4 „Generalprobe: Übungsprodukt, Teil 1" (**G4/D020**, Baseline **`genesis-v0.4`** getaggt): erster kompletter SWE.1–SWE.4-Durchlauf am fremden Produkt — Mensch-Beteiligung nur Clarifications, Gates, DRs (P0-Abnahmekriterium 1, Teil 1 belegt). Details:

- **D016 (via Session-Dialog):** Übungsprodukt = **CSV↔JSON-Konverter „datakonv"** (CLI, Python stdlib, ~15 Anforderungen) im **eigenen privaten Repo `DiOflOrds/produkt-datakonv`** (DR T-0041, A1+B1).
- **Retro-CRs Sprint 3 umgesetzt (T-0037–T-0039):** trace-matrix-Gate in der platform-CI (p0-Checkout, Secret `P0_READ_TOKEN` nötig — analog R8); Zweiphasen-Tick idempotent (Warte-Lauf ohne Statuswechsel-Commits); DR-Optionen maschinenlesbar (Frontmatter `optionen`/`frist`/`default`, Inbox-API validiert → HTTP 400 bei ungültiger Option). Suite 81 → **90 Tests grün**; zusätzlich CM-Hygiene: `__pycache__` aus der platform-Versionskontrolle.
- **T-0042 done:** Produkt-Repo-Skelett `produkt-datakonv` lokal gebaut (README EN, requirements/src/tests/docs+adr, CI, Smoke-Test) + CM-Strategie-Eintrag.
- **D017 (via Session-Dialog):** Hub-VM entfällt für P0 — **Betrieb bleibt lokal auf Team-Node-1**; R2 geschlossen, E5 revidiert, T-0047 rejected; Wiedervorlage zum P0-Abschluss/P1-Intake.
- **T-0043 done + G1 erteilt (D018):** SWE.1-Set datakonv (STK-D01–D05 + SWR-D01–D17, EN, reviewed, Traceability vollständig) nach Clarifications erstellt; Baseline **`req-v1.0`** auf produkt-datakonv getaggt.
- **T-0044 done + G2 erteilt (D019):** Architektur (4 Units, reine str→str-Konvertierung, ADR-D01–D03). **T-0045 done:** Implementierung stdlib-only. **T-0046 done:** 31 Unit-Tests, alle 17 SWRs abgedeckt — Matrix `datakonv-swr-test-matrix.md`: **0 Lücken**. **T-0048 done** (CR aus T-0046): trace_matrix generalisiert (`--tests/--swr/--ziel/--id-muster`), Suite 92 Tests grün.
- **Alle Sprint-4-Tickets abgeschlossen** (T-0037–T-0046, T-0048 done; T-0047 rejected/D017). API-Kosten Sprint 0–4: 0,00 €.
- **Abschluss:** Report + Retro in `p0/management/sprint-4/`; Retro-CRs für Sprint 5: **T-0049** (Matrix-CI-Gate Produkt-Repo), **T-0050** (Preflight räumt Git-Locks, R7), **T-0051** (optionen-Frontmatter für neue DRs erzwingen).
- Betriebsnotiz: R7 (Git-Locks) trat zweimal auf und wurde per Freigabe der Datei-Löschung in der Session behoben; Preflight lief zu Session-Beginn grün.

## Warten auf Auftraggeber

1. **`sprint4-abschluss.cmd` ausführen** — prüft alles und pusht alle vier Repos inkl. Tags `genesis-v0.4` + `req-v1.0` (Sandbox darf nicht pushen, D007); danach Actions prüfen (platform-CI jetzt mit Matrix-Gate).
2. Offene Fragen F6, F8–F13; T-0008 bleibt bewusst verschoben (D015).

## Nächste Session (Sprint 5 — „Generalprobe Teil 2 + Release")

1. Sprint-5-Planning (PL): Retro-CRs T-0049–T-0051; SWE.5/SWE.6 (Integrations-/SW-Verifikation gegen Anforderungen); Problem- und CR-Zyklus real am Produkt durchlaufen; **Release datakonv** (SPL.2, Baseline, Release Notes, G3) inkl. Produktkatalog v0 (`catalog/`); Feedback-Routing v1 (P0 Kap. 5).
2. Autonome Ticks am Team-Node fortführen (T-0038-Wirkung messen: 0 Statuswechsel-Zyklen je Warte-Lauf); Inbox wieder real nutzen (QM-Punkt 4 Sprint 4).

## Offene Fragen

F6 Zielprodukte · F8 parallele Projekte · F9 weitere Nutzer · F10 Vertraulichkeit · F11 Arbeitsteam-Domäne · F12 Geräte-Landschaft/Hub-Gerät · F13 Copilot-Abo/Ollama-Hardware

## Referenzen

Masterplan 0.6 · Playbook 0.6 · P0: `aspice-team/02-initialprojekt-p0.md` · Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv} · Decision Log: D000–**D020** · Baseline **genesis-v0.4** · Sprint-4-Report: `p0/management/sprint-4/report.md` · Sprint-4-Plan: `p0/management/sprint-4/plan.md` · Sprint-3-Report: `p0/management/sprint-3/report.md`
