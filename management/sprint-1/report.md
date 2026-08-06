# Sprint-1-Report — P0 „Genesis" (ENTWURF — final nach T-0009)

*Stand: 2026-08-06, Engineering-Session (Cowork auf Team-Node). Rolle: PL. Finalisierung nach dem ersten autonomen Tick (T-0009) und Mensch-Review.*

## Sprint-Ziel und Erreichung

Ziel: Erster autonomer Tick läuft end-to-end auf dem Team-Node. **Stand: Alles vorbereitet; Ausführung API-frei möglich (Ollama oder Session-Austausch, T-0011/T-0012) — wartet nur noch auf den Start durch den Menschen.**

## Ticket-Bilanz

in_review 9: T-0001 (Rollenkarten v1), T-0002 (Skills v1 + 8 Gold-Beispiele), T-0003 (Registry v1), T-0004 (Gateway v1), T-0005 (Orchestrator-MVP), T-0006 (Guardrails v1), T-0007 (board.py v1), T-0011 (Ollama-Executor v1, vorgezogen), T-0012 (Session-Austausch-Provider) — Reviewer benannt, finale Abnahme = dieses Sprint-Review. open 3: T-0008 (Mensch, nur noch für Claude-Stufe nötig), T-0009 (Abnahme-Tick), T-0010 (CM-Strategie, Ziel des Ticks, entblockt).

## Gelieferte Artefakte

process: Rollenkarten v1 (roles/), Skills v1 (skills/), Gold-Beispiele (knowledge/{pl,cm,coach}/gold-beispiele/), Registry v1 (roles/registry.yaml, cm-strategie-Kette [ollama, session, claude]). platform: board.py v1 + 19 Tests, gateway/ (execute-Schnittstelle, Claude-Executor headless, Ollama-Executor v1, Session-Austausch-Provider, Copilot-Stub, Datei-Block-Konvention, Guardrails hart + Run-Registry JSONL) + 24 Tests, orchestrator/tick.py (inkl. wartet-Zustand, --provider-Override) + 13 Tests, requirements.txt. p0: Ticket-Updates, BOARD.md, Sprint-0-Report (nachgereicht), dieser Entwurf.

**Scope-Änderung auf Auftraggeber-Wunsch (2026-08-06):** Ollama-Executor aus Sprint 6 vorgezogen (T-0011) und Session-Austausch-Provider ergänzt (T-0012), damit T-0009 ohne Anthropic-API laufen kann; T-0008 bleibt offen für die spätere Claude-Stufe. Entscheidung des Auftraggebers, dokumentationspflichtig im Decision Log beim nächsten PL-Durchgang.

## Kosten

Diese Session: 0 € API-Kosten (kein Gateway-Lauf; Cowork-Session zählt nicht aufs 20-€-Limit). Erster Tick: erwartet < 1 € (Tick-Limit), protokolliert in `management/runs/run-registry.jsonl`.

## Risiken (Delta)

Neu R7: Cowork-Sandbox-Instabilität (Linux-VM startete nicht) — Wirkung: Engineering ohne Testlauf in der Session; Maßnahme: Verifikations-Skript auf Team-Node (`sprint1-abschluss.cmd`), Eigentümer CM. Kein Einfluss auf Team-Node-Betrieb.

## QM-Abschnitt (ungefiltert)

QM-Rolle weiter unbesetzt (Sprint 2). Abweichungen dieser Session: (1) Alle Sprint-1-Tickets wurden von einer Session in mehreren Rollen-Kontexten bearbeitet — Vier-Augen-Prinzip nur über Reviewer-Felder + Mensch-Review abgebildet. (2) Unit-Tests wurden geschrieben, aber in der Session nicht ausgeführt (Sandbox-Ausfall) — Ausführung ist Pflichtschritt vor dem Push (Anleitung). (3) BP-Mapping in den Skills ist ein Arbeits-Mapping; Wortlaut-Verifikation gegen das lizenzierte PAM 4.0 als COACH-Ticket in Sprint 2 nötig. (4) BOARD.md wurde manuell im Generator-Format erstellt; board.py-Lauf vor dem Push verifiziert es.

## Retrospektive (vorläufig; final nach T-0009, max. 3 CRs)

Kandidaten: (1) CI-Workflow (GitHub Actions) für board.py --check + Tests je Push — skriptifiziert die Verifikation; (2) PAM-4.0-Wortlaut-Abgleich der Skills; (3) Sandbox-Ausfall-Runbook (Team-Node als Standard-Ausführungsort dokumentieren).

## Anstehende Entscheidungen

T-0008 (API-Key ~20 €, console.anthropic.com) — einziger Blocker für T-0009/T-0010. Offene Fragen F5–F13 (bis Ende Sprint 2).
