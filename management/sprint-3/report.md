# Sprint-3-Report — P0 „Genesis" (PL)

*2026-08-06. Sprint-Motto: „Backend & Frontend MVP — Mission Control v1". An: Mensch (G4-Review). Von: PL, mit QM-/TEST-Abschnitten.*

## Sprint-Ziel: erreicht

Der Backend/Frontend-MVP existiert und läuft (Smoke-Test gegen die echten Repos: Board 36 Tickets, Inbox listet T-0035, KPI aus Run-Registry) — requirements-first gebaut: erst SWR-020–024 reviewed (T-0030), dann Architektur mit ADRs (T-0031), dann Code mit SWR-getraceten Tests (T-0032/33), dann Verifikation (T-0034). ARCH/DEV/TEST sind aktive Rollen; der Tick-Pfad ist wieder in Betrieb.

## Ergebnis je Ticket (11 done, 2 offen beim Menschen)

| Ticket | Ergebnis |
|---|---|
| T-0024 | Preflight-Skript (Locks/Status/Board/Tests) + Tick-Precondition + Geräteregister-Hinweis; R7-Fall in dieser Session real abgefangen |
| T-0025 | Requirements-first-Regel: Playbook 0.6 Kap. 5 + task-Template „SWR-Bezug"; 100 % der Sprint-3-Plattform-Tickets mit Referenz |
| T-0026 | SWR-Docstring-IDs in allen Tests + `trace_matrix.py`; G1-Punkt 1 geschlossen |
| T-0028 | Rollenkarten v1 ARCH/DEV/TEST + Registry v1.2 (10 aktive Rollen) |
| T-0029 | Skills v1 SWE.2/SWE.3/SWE.4–6 + 3 Gold-Beispiele aus realen Sprint-3-Fällen |
| T-0030 | STK-012 + SWR-020–024 reviewed; G1-Erweiterungsvorlage (`requirements/g1-erweiterung-sprint3.md`) |
| T-0031 | Architektur v1 + ADR-001..003 + G2-Vorlage (`platform/architecture/`) |
| T-0032 | Backend-MVP: API (Board/Reports/KPI/Inbox), Inbox-Schreibpfad mit Git-Commit, Mailer, Infra-as-Code |
| T-0033 | Frontend-MVP: no-build PWA, 4 Ansichten + Entscheidungsformular |
| T-0034 | Verifikationsstrategie v1, UI-Abnahme SWR-021, Matrix: **24 SWRs, 0 Lücken** |
| T-0036 | Tick-Pfad reaktiviert: Session-Zweiphasen-Tick end-to-end, Betriebsdaten-Doku (`platform/docs/betriebsdaten-ticks.md`) |
| T-0035 | **offen — erster echter Inbox-DR an dich** (Hub-VM, Deployment-Ziel, D006-Review; Optionen/Frist/Default im Ticket) |
| T-0008 | offen — Anthropic-API-Key (~20 €, für Claude-Stufe und Kostendaten Budget-Review Sprint 4) |

## KPIs

Tests 62 → **81** (alle grün) · SWRs 21 → 24 (23 reviewed, **0 Verifikationslücken**) · API-Kosten Sprint 0–3: **0,00 €** von 20 €/Monat (D012) · autonome Ticks gesamt: 3 (1× ollama, 2× session) · Commits mit Ticket-ID: 100 %.

## TEST-Abschnitt (Verifikation)

Matrix vollständig, einzige manuelle Abnahme (SWR-021) dokumentiert mit 2 Restpunkten: Gerätetest durch dich im Review; PWA-Installierbarkeit außerhalb MVP-Scope. Verifikationsschulden (ehrlich): SMTP-Erfolgspfad ungetestet (kein Zugang), Docker-Deployment ungebaut bis VM, GitHub-CI-Läufe stehen bis zum Push aus.

## QM-Abschnitt (ungefiltert)

1. Reviews erfolgten durch Rollen-Kontexte derselben Session (Bootstrap-Modus wie Sprint 1/2); finale Abnahme = dieses G4. 2. **G1-Erweiterung und G2 stehen aus** — deshalb wurde bewusst noch keine Baseline `genesis-v0.3` getaggt; Tag folgt nach deiner Freigabe (CM). 3. R7 trat vor Preflight-Verfügbarkeit erneut auf (Zählung des Erwartungswerts ab Skript-Verfügbarkeit: 0 Blöcke). 4. Sandbox war extern voll blockiert (auch Git-Read, strenger als D007) — Betriebsnotiz im Geräteregister und in `betriebsdaten-ticks.md`. 5. Status-Rauschen des Zweiphasen-Ticks: als T-0038 adressiert.

## Entscheidungsbedarf an dich (G4)

1. **G1-Erweiterung** freigeben (STK-012, SWR-020–024) — `p0/requirements/g1-erweiterung-sprint3.md`
2. **G2** Architektur/Technologie freigeben (inkl. ADR-001-Abweichung stdlib statt FastAPI) — `platform/architecture/g2-vorlage.md`
3. **T-0035** beantworten (Hub-VM/Deployment/D006) — per Mission Control (`python platform\backend\server.py --repos .` → http://127.0.0.1:8080) oder klassisch
4. **G4** Sprint 3 abnehmen; danach taggt CM `genesis-v0.3`
5. Weiterhin offen: T-0008 (API-Key) sowie F6, F8–F13

## Retro

3 CRs für Sprint 4: T-0037 (Matrix-Gate in CI), T-0038 (Zweiphasen-Tick ohne Status-Rauschen), T-0039 (DR-Optionen maschinenlesbar + Inbox-Validierung). Details: `retro.md`.
