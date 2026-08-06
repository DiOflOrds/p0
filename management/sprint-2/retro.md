# Retrospektive Sprint 2 — P0 „Genesis"

*2026-08-06, moderiert im COACH-Kontext, datenbasiert. Teilnehmer: Rollen-Kontexte der Session (PL, CM, COACH, QM, RM, PROB, CHG), Entscheidungen des Menschen.*

## Daten

9 team-seitige Tickets, 9 done (100 %); 1 Mensch-Ticket offen (T-0008, bewusst). Kosten: 0,00 € API. Neue Rollen: 4 aktiviert. Erstes SWE.1-Set: 12 STK + 21 SWR, G1 am selben Tag. Probleme: 0 neue SUP.9-Tickets; 1 wiederkehrendes Betriebs-Ärgernis (Mount-Locks, R7) ohne Ticket-würdigen Schaden. Retro-CR-Wirkung aus Sprint 1: T-0015/T-0016/T-0017 alle umgesetzt; Erwartungswerte (0 manuelle Testlauf-Aufforderungen, 0 Fehlerbild-Wiederholungen) im Sprint gehalten — CI-Wirkung auf GitHub steht noch aus.

## Was lief gut

Sprint-1-Lessons griffen messbar: kein Repo-Präfix-Fehler, keine Misch-Commits, saubere Status-Transitionen über board.py bei jedem Commit. Die neuen Gold-Beispiele aus realen Sprint-1-Fällen (statt erfundener) machten die Rollen-Reviews konkret. G1/G4/Budget als gebündelte Entscheidung an den Menschen (statt tröpfelnd) funktionierte.

## Was Ticks/Zeit verschwendet hat

Stale `index.lock` in allen drei Repos nach Session-Start (Mount-Artefakt, R7) — kostete einen Analyse-/Freigabe-Block. Der Tick-Pfad (Orchestrator) wurde erneut nicht genutzt, weil die Sandbox Ollama auf dem Team-Node nicht erreicht — Session-Arbeit war der Fallback; damit fehlen weiter Betriebsdaten vom autonomen Pfad. Requirements nachlaufend zur Implementierung zu schreiben erzeugte Mehraufwand beim Belegen der Verifikationskriterien.

## Beschlossene Verbesserungen (max. 3, als Prozess-CRs, Sprint 3)

1. **T-0024** Session-Preflight als Skript-Route: ein Lauf prüft/behebt Locks, git status, board --check, Tests. **Erwartung:** 0 Analyse-Blöcke durch Mount-Artefakte in Sprint 3.
2. **T-0025** Requirements-first-Regel: neue platform-/Produkt-Tickets referenzieren SWR oder CR; erster Verstoß = QM-Finding. **Erwartung:** 100 % neue Plattform-Tickets mit Referenz in Sprint 3.
3. **T-0026** SWR↔Test-Traceability: Test-Docstrings tragen SWR-IDs, Skript generiert die Matrix (Vorstufe der CI-Matrix). **Erwartung:** Matrix vollständig generierbar, Lücken sichtbar.

Nicht aufgenommen (Limit 3): E-Mail-Report-Versand (Sprint 3 Backend), Tick-Scheduler (Sprint 3 ohnehin).
