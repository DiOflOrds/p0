# Risikoliste P0 (Eigentümer: PL; Review je Sprint)

| ID | Risiko | Wirkung | W'keit | Maßnahme | Eigentümer | Status |
|---|---|---|---|---|---|---|
| R1 | Bootstrap-Zirkel: Team soll Prozesse bauen, die es zum Bauen bräuchte | Stillstand Sprint 1–2 | mittel | Drei-Stufen-Bootstrap; Bootstrap-Ausnahme mit Nachreview | PL | offen |
| R2 | Cloud-VM-Beschaffung verzögert sich | Deployment Sprint 3 rutscht | gering | Sprint 1–2 laufen in Cowork-Sessions; VM erst Sprint 3 nötig | Mensch/CM | offen |
| R3 | Frontend-Scope wuchert | P0 wird nicht fertig | mittel | MVP-Schnitt fixiert (lesend + Decision-Inbox); Rest → P1-Backlog | PL | offen |
| R4 | Agent-Qualität schwankt je Rolle | Nacharbeit, Kosten | mittel | Kleine Rollenkarten, Lernzyklus, Doppel-Review kritischer Outputs | COACH | offen |
| R5 | Testphasen-Budget (~20 €) zu knapp für Sprint 0–1 | Ticks stoppen | mittel | Skript-Route maximieren; cheap-Modelle; Budget-Review notfalls vorziehen (DR) | PL | offen |
| R6 | Token-/Zugangsdaten-Handhabung unsauber | Sicherheitsrisiko | gering | Secrets nur in GitLab-CI-Variablen/Hub-Vault, nie in Repos; Geräte-Tokens einzeln widerrufbar | CM | offen |
