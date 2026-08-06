# Sprint-1-Report — P0 „Genesis" (FINAL)

*Stand: 2026-08-06, Rolle: PL. **Sprint 1 abgenommen (G4, D009):** Mensch-Review 2026-08-06 („mergen und sprint1 abschluss bestätigen"), Merge nach main erfolgt, CM-Strategie an Storage-Location `cm/` korrigiert, Review-Nacharbeit als T-0018 (Sprint 2). Retrospektive: `retro.md` (3 Prozess-CRs T-0015–T-0017).*

## Sprint-Ziel und Erreichung

Ziel: Erster autonomer Tick läuft end-to-end auf dem Team-Node. **ERREICHT (2026-08-06):** Tick lief auf dem User-PC (`--provider ollama`, gemma3:27b): T-0010 gewählt, CM-Strategie als Branch `feature/t-0010-cm-strategie-v1-erstellen-ziel` im process-Repo, Ticket-Update in_review, Run-Registry-Eintrag, Kosten 0,00 €. Offen: Mensch-Review des Artefakts (= dieses Sprint-Review, G4).

## Ticket-Bilanz

in_review 12: T-0001 (Rollenkarten v1), T-0002 (Skills v1 + 8 Gold-Beispiele), T-0003 (Registry v1), T-0004 (Gateway v1), T-0005 (Orchestrator-MVP), T-0006 (Guardrails v1), T-0007 (board.py v1), T-0010 (CM-Strategie, autonom via Ollama erstellt), T-0011 (Ollama-Executor v1), T-0012 (Session-Austausch-Provider), T-0013 + T-0014 (SUP.9-Probleme aus dem ersten Tick, behoben) — Reviewer benannt, finale Abnahme = dieses Sprint-Review. in_progress 1: T-0009 (Nachweis erbracht, wartet auf Mensch-Review). open 1: T-0008 (Mensch, nur noch für Claude-Stufe nötig).

## Gelieferte Artefakte

process: Rollenkarten v1 (roles/), Skills v1 (skills/), Gold-Beispiele (knowledge/{pl,cm,coach}/gold-beispiele/), Registry v1 (roles/registry.yaml, cm-strategie-Kette [ollama, session, claude]). platform: board.py v1 + 19 Tests, gateway/ (execute-Schnittstelle, Claude-Executor headless, Ollama-Executor v1, Session-Austausch-Provider, Copilot-Stub, Datei-Block-Konvention, Guardrails hart + Run-Registry JSONL) + 24 Tests, orchestrator/tick.py (inkl. wartet-Zustand, --provider-Override) + 13 Tests, requirements.txt. p0: Ticket-Updates, BOARD.md, Sprint-0-Report (nachgereicht), dieser Entwurf.

**Scope-Änderung auf Auftraggeber-Wunsch (2026-08-06):** Ollama-Executor aus Sprint 6 vorgezogen (T-0011) und Session-Austausch-Provider ergänzt (T-0012), damit T-0009 ohne Anthropic-API laufen kann; T-0008 bleibt offen für die spätere Claude-Stufe. Entscheidung des Auftraggebers, dokumentationspflichtig im Decision Log beim nächsten PL-Durchgang.

## Kosten

0,00 € API-Kosten gesamt — Engineering in Cowork-Sessions (Abo), erster autonomer Tick auf Ollama (lokal, kostenlos), protokolliert in `management/runs/run-registry.jsonl`. Das 20-€-Testbudget ist unangetastet.

## Risiken (Delta)

Neu R7: Cowork-Sandbox-Instabilität (Linux-VM startete nicht) — Wirkung: Engineering ohne Testlauf in der Session; Maßnahme: Verifikations-Skript auf Team-Node (`sprint1-abschluss.cmd`), Eigentümer CM. Kein Einfluss auf Team-Node-Betrieb.

## QM-Abschnitt (ungefiltert)

QM-Rolle weiter unbesetzt (Sprint 2). Abweichungen: (1) Alle Sprint-1-Tickets wurden von einer Session in mehreren Rollen-Kontexten bearbeitet — Vier-Augen-Prinzip nur über Reviewer-Felder + Mensch-Review abgebildet. (2) Unit-Tests wurden geschrieben, aber in der Session nicht ausgeführt (Sandbox-Ausfall) — Ausführung ist Pflichtschritt vor dem Push (Anleitung). (3) BP-Mapping in den Skills ist ein Arbeits-Mapping; Wortlaut-Verifikation gegen das lizenzierte PAM 4.0 als COACH-Ticket in Sprint 2 nötig. (4) BOARD.md wurde manuell im Generator-Format erstellt; board.py-Lauf vor dem Push verifiziert es. (5) Erster Tick erzeugte zwei Prozessverletzungen: Artefakt-Pfad mit Repo-Präfix (T-0013) und Ergebnis-Commit mit unbeteiligten Änderungen durch `add -A` auf unsauberer Arbeitskopie (T-0014) — beide Ursachen im Tooling behoben; die betroffenen Artefakte bleiben auf Mensch-Entscheidung unverändert auf dem Branch. (6) Der Misch-Commit auf `feature/t-0010-…` schwächt die Traceability dieses einen Commits (v1-Prozessartefakte + CM-Strategie unter einer Ticket-ID); akzeptiert per Mensch-Entscheidung, Merge löst den Zustand nach main auf.

## Retrospektive (durchgeführt 2026-08-06, siehe retro.md)

Beschlossen (max. 3): T-0015 CI-Workflow (board.py --check + Tests je Push), T-0016 Wissensbasen-Erstbefüllung aus T-0013/T-0014, T-0017 PAM-4.0-Wortlaut-Abgleich. Review-Nacharbeit zusätzlich als T-0018 (CM-Strategie an reale Struktur angleichen).

## Anstehende Entscheidungen

T-0008 (API-Key ~20 €, console.anthropic.com) — einziger Blocker für T-0009/T-0010. Offene Fragen F5–F13 (bis Ende Sprint 2).
