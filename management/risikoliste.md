# Risikoliste P0 (Eigentümer: PL; Review je Sprint — zuletzt Sprint 2, 2026-08-06)

| ID | Risiko | Wirkung | W'keit | Maßnahme | Eigentümer | Status |
|---|---|---|---|---|---|---|
| R1 | Bootstrap-Zirkel: Team soll Prozesse bauen, die es zum Bauen bräuchte | Stillstand Sprint 1–2 | gering | Drei-Stufen-Bootstrap; Stufe 2 erreicht (Sprint 2: 7 Rollen aktiv, Team führt P0 selbst) | PL | entschärft (S2) |
| R2 | Cloud-VM-Beschaffung verzögert sich | Deployment Sprint 3 rutscht | gering | D017: Betrieb für P0 bewusst lokal auf Team-Node-1 — Risiko gegenstandslos; Infra-as-Code bleibt bereit | Mensch/CM | geschlossen (D017, 2026-08-06) |
| R3 | Frontend-Scope wuchert | P0 wird nicht fertig | mittel | MVP-Schnitt fixiert (lesend + Decision-Inbox); Rest → P1-Backlog | PL | offen |
| R4 | Agent-Qualität schwankt je Rolle | Nacharbeit, Kosten | mittel | Kleine Rollenkarten, Lernzyklus, Doppel-Review kritischer Outputs | COACH | offen |
| R5 | Testphasen-Budget (~20 €) zu knapp für Sprint 0–1 | Ticks stoppen | gering | 0 € Ist nach 3 Sprints (D012); Kette [ollama, session, claude] | PL | entschärft (S2) |
| R6 | Token-/Zugangsdaten-Handhabung unsauber | Sicherheitsrisiko | gering | Secrets nur in GitLab-CI-Variablen/Hub-Vault, nie in Repos; Geräte-Tokens einzeln widerrufbar | CM | offen |
| R7 | Cowork-Sandbox-/Mount-Artefakte (VM-Ausfall, stale index.lock, CRLF/filemode) | Zeitverlust je Session-Start | hoch | Preflight-Skript T-0024; Löschrechte früh anfordern; Verifikation auf Team-Node | CM | mitigiert S3: Preflight T-0024 aktiv als Session-/Tick-Precondition; Lösch-Berechtigung früh anfordern (Geräteregister); 1x eingetreten S3 vor Skript-Verfügbarkeit, danach 0 |
| R8 | p0-CI hängt am Secret PLATFORM_READ_TOKEN (Cross-Repo-Zugriff auf board.py) | board-check auf GitHub rot bis Secret da | hoch | klare Fehlermeldung im Workflow; Mensch-Aktion in Abschluss-Anleitung; Alternative (vendored copy) dokumentiert im Ticket T-0015 | Mensch/CM | geschlossen S2/S3: Secret gesetzt, board-check auf GitHub grün (T-0027) |
