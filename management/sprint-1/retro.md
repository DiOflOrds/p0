# Retrospektive Sprint 1 — P0 „Genesis"

*2026-08-06, moderiert im COACH-Kontext, datenbasiert. Teilnehmer: PL/CM/COACH/DEV-Kontexte der Session, Befunde des Menschen.*

## Daten

14 Tickets Sprint 1: 13 done, 1 offen (T-0008, Mensch, bewusst verschoben). Kosten: 0,00 € API (Budget 20 € unangetastet) — Engineering im Session-Abo, erster Tick auf Ollama lokal. Probleme: 2 (T-0013, T-0014 — beide am selben Tag erfasst, analysiert, behoben). Tests: 62, alle grün. Scope-Änderungen durch Mensch: 1 (Provider-Vorziehung T-0011/T-0012 statt T-0008).

## Was lief gut

Skript-vor-LLM hat sich ausgezahlt: board.py fing invalide Zustände mehrfach ab. Der erste autonome Tick lief beim ersten Versuch technisch durch (Auswahl, Gateway, Branch, Registry). Die Provider-Kette mit Fallback (ollama → session → claude) machte den Sprint unabhängig vom API-Key. Findings des Menschen wurden am selben Tag zu behobenen SUP.9-Problemen.

## Was Ticks/Zeit verschwendet hat

Cowork-Sandbox-Ausfall (VM startete zeitweise nicht) → Verifikation musste zweimal verschoben werden; Mount-Artefakte (filemode, CRLF, stale index.lock) kosteten einen Analyse-Block. Default-Ollama-Modell (llama3.1:8b) war auf dem Team-Node nicht installiert → manueller Override nötig. Uncommittete Session-Arbeit + `git add -A` erzeugte den Misch-Commit (T-0014).

## Beschlossene Verbesserungen (max. 3, als Prozess-CRs)

1. **T-0015** CI-Workflow: board.py --check + Unit-Tests je Push (Erwartung: 0 manuelle Testläufe, kein invalider Board-Zustand auf main).
2. **T-0016** Wissensbasen-Erstbefüllung mit den Lessons aus T-0013/T-0014 + Modell-/Kontext-Heuristiken (Erwartung: Wiederholungsquote 0).
3. **T-0017** PAM-4.0-Wortlaut-Abgleich der Skill-BP-Mappings (Erwartung: belastbare BP-Referenzen, F7 entschieden).

Nicht aufgenommen (bewusst, Limit 3): Scheduler für Ticks (Sprint 3 ohnehin), E-Mail-Versand der Reports (Sprint 3, Backend).
