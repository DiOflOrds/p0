# Decision Log — Projekt P0 „Genesis" (append-only)

| ID | Datum | Entscheider | Entscheidung | Optionen | Begründung | Betroffene Artefakte |
|---|---|---|---|---|---|---|
| D000 | 2026-08-05 | Mensch (E. John) | **Gate G0: Projektauftrag P0 freigegeben** („ok, fangen wir an" nach Vorlage von Masterplan 0.4, Playbook 0.4, P0-Beschreibung 0.4) | Freigabe / Überarbeitung / Ablehnung | Konzept in 4 Iterationen präzisiert (Arbeitsteam, Lernzyklus, Produktkatalog, verteilte Infrastruktur eingearbeitet) | Projektauftrag P0, alle Baseline-Dokumente |
| D001 | 2026-08-05 | Mensch (E. John) | **F1 Betriebsumgebung: Cloud-VM** (z.B. Hetzner, Docker Compose); Sprint 0–2 übergangsweise in Cowork-Sessions | Cloud-VM / Heimserver / Cowork-Übergang | Immer erreichbar, kein Heimnetz-Aufwand; Setup-Anleitung wird geliefert | Masterplan E5, platform/infra |
| D002 | 2026-08-05 | Mensch (E. John) | **F2 Git-Backbone: gitlab.com** (kostenlose Gruppe) | gitlab.com / GitLab CE self-hosted / GitHub | Sofort startklar ohne Betriebsaufwand; Umzug bleibt möglich | Masterplan E6, CM-Strategie |
| D003 | 2026-08-05 | Mensch (E. John) | **F3 Budget: Testphase zuerst** — Sprint 0–1 mit Mini-Budget ~20 €, Ist-Kosten messen, Budget-Festlegung datenbasiert in Sprint 2 (als Decision Request) | 50 € / 150–250 € / 500 €+ / Testphase | Datenbasierte Entscheidung statt Schätzung; hartes Limit ab erstem Tick | Masterplan E7, guardrails.yaml |
| D004 | 2026-08-05 | Mensch (E. John) | **F4 Benachrichtigung: E-Mail** (geraldine.john90@gmail.com) **+ Frontend-Decision-Inbox** (ab Sprint 3) | E-Mail / PWA-Push / nur Inbox | E-Mail sofort verfügbar; Inbox ab Frontend-MVP; PWA-Push optional später | Masterplan E8, Backend HITL-Queue |
