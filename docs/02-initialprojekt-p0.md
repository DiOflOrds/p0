# Projekt P0 „Genesis" — Initiales Projekt: Das Team befähigt sich selbst

**Version:** 0.5 (Entwurf) · **Datum:** 2026-08-05 · **Projektleiter:** PL-Agent (ab Sprint 2; davor Bootstrap durch Setup-Agent/Claude-Session)
**Auftraggeber:** Engelchen John · **Status:** Wartet auf Gate G0 (Auftragsfreigabe + Antworten F1–F4 aus dem Masterplan)

---

## 1. Projektauftrag

**Ziel:** Aufbau eines arbeitsfähigen, halb-autonomen virtuellen Entwicklungsteams (Rollen, Prozesse, Infrastruktur, Software), das anschließend Software-Projekte nach Automotive SPICE 4.0 (Scope Stufe 1 gemäß Masterplan Kap. 3) eigenständig abwickeln kann — inklusive Frontend/Backend zur Projektverwaltung, Visualisierung und als HMI für den Menschen.

**Begründung:** Ohne P0 gibt es kein Team, dem man Projekte geben kann. P0 ist zugleich der Realitätstest: Das Team wendet die entstehende Arbeitsweise **auf sich selbst** an („eat your own dogfood") — P0 wird selbst als ASPICE-Projekt geführt, soweit die Mittel jeweils schon existieren.

**Randbedingungen:** Kostenrahmen je Sprint (Wert aus F3); keine sicherheits-/security-kritischen Inhalte in Stufe 1; alle Artefakte in Git; Mensch-Einbindung nur über Gates, Decision-Inbox und Clarifications.

**Bootstrap-Prinzip:** Henne-Ei-Auflösung in drei Stufen — (1) In Sprint 0–1 arbeitet ein einzelner Setup-Agent (bzw. eine Claude-Cowork-Session) mit dem Menschen und erzeugt die minimale Infrastruktur und die ersten Rollenkarten. (2) Ab Sprint 2 übernehmen PL, CM und COACH als echte Agenten die Projektführung von P0 selbst. (3) Ab Sprint 4 arbeitet das volle Team und weist seine Arbeitsfähigkeit an einem Übungsprodukt nach.

## 2. Scope

**In Scope:** GitLab-Struktur und CM-Grundgerüst; Rollenkarten und Prozess-Skills für alle Stufe-1-Rollen; Orchestrator (Tick-Mechanik, Delegation, Guardrails); Issue-Templates und Workflows; Requirements-Mechanik inkl. Traceability-CI; DoD/Checklisten; Backend-MVP; Frontend-MVP (Dashboard, Board, Requirements, Traceability, Decision-Inbox); CI/CD für Übungs- und Folgeprojekte; KPI-Basiserhebung; End-to-End-Nachweis am Übungsprodukt; Self-Check gegen PAM-4.0-Scope.

**Out of Scope (P0):** SYS.3–SYS.5, VAL.1 voll; HWE/MLE; CL2-Formalisierung; Multi-Projekt-Parallelität; externe Nutzer; Embedded-Targets; formales externes Assessment; produktiver Multi-Node-Betrieb über mehrere Geräte (P0 liefert die verteilungsfähige Architektur, PWA-Frontend und einen Team-Node-Proof-of-Concept; der Vollausbau ist Phase P2).

## 3. Erfolgs- und Abnahmekriterien (Gate am P0-Ende)

P0 gilt als erfolgreich, wenn der Mensch Folgendes abnimmt:

1. **E2E-Nachweis:** Das Übungsprodukt (Kap. 5, Sprint 4–5) wurde vom Team ohne operative Mensch-Arbeit von der Erwartungshaltung bis zum Release gebracht; Mensch-Beteiligung ausschließlich: Auftrag präzisieren, G1/G2/G3 freigeben, DRs beantworten.
2. **Vollständige Kette:** Für das Übungsprodukt existieren durchgängig verlinkt: Stakeholder-Anforderungen → SW-Anforderungen → Architektur → Units/Code → Verifikationsmaßnahmen (3 Ebenen) → Ergebnisse; Traceability-Matrix im Frontend ohne Lücken (CI-geprüft).
3. **Prozess-Evidenz:** Je Stufe-1-Prozessgebiet sind die Basispraktiken durch reale Artefakte belegt (Self-Check-Report des QM/COACH mit Fundstellen).
4. **HITL funktioniert:** Mindestens 5 echte Decision Requests/Clarifications durchliefen die Decision-Inbox inkl. Benachrichtigung, Antwort, Decision Log und Entblockung.
5. **Frontend nutzbar:** Der Mensch kann Status, Aufgaben, Requirements, Traceability, Baselines, Entscheidungen und Kosten ohne Rückfrage einsehen.
6. **Selbstverbesserung belegt:** Mindestens 3 Retro-Verbesserungen wurden als Prozess-CRs umgesetzt und ihre Wirkung gemessen — darunter mindestens ein Wissensbasis-Update einer KI-Rolle (Lernzyklus durchlaufen inkl. Gold-Beispiel-Regressionstest) und mindestens eine Skriptifizierung (Tätigkeit von KI- auf Skript-Route verlagert, Automatisierungsgrad-KPI sichtbar gestiegen).
7. **Kosten transparent:** Ist-Kosten je Sprint erfasst und im Rahmen (F3).
8. **Wiederholbarkeit:** Ein neues Projekt kann per dokumentiertem Intake (Projekt-Template + „Projekt anlegen"-Workflow) gestartet werden — nachgewiesen durch Anlage des Pilot-Projekts P1 als leere Hülle.
9. **Drei LLM-Provider nachgewiesen:** Jeder der drei Executor hat mindestens eine echte Aufgabe erledigt — Claude (Hub, laufend ab Sprint 1), GitHub Copilot CLI und Ollama (Team-Node-PoC in Sprint 6) — mit Provider-Protokollierung am Ticket und identischen DoD-/Review-Checks.

## 4. Organisation und Arbeitsweise in P0

P0 arbeitet nach dem Team-Playbook (01), mit einer Ausnahme-Regelung für die Bootstrap-Phase: In Sprint 0–1 dürfen Artefakte direkt (ohne Agenten-Review) entstehen, werden aber in Sprint 2 nachreviewt und in die Baseline „Genesis-Foundation" überführt. Sprint-Kadenz: 1 Woche. Alle P0-Artefakte liegen in den Repos `process/`, `platform/` und `p0/` (Projektführung).

## 5. Sprint-Plan

### Sprint 0 — „Auftrag & Fundament-Entscheidungen" (mit Mensch, kurz)
**Ziel:** G0 erreichen; Infrastruktur bereit.
**Inhalte:** Antworten F1–F10 einsammeln (mind. F1–F4); GitLab-Instanz/Gruppe einrichten, API-Keys/Zugänge hinterlegen; Kosten-Limits konfigurieren; Repos anlegen (`process/`, `platform/`, `p0/`); Masterplan + Playbook als initiale Prozess-Baseline v0.1 taggen.
**Deliverables:** Freigegebener Projektauftrag (dieses Dokument, Gate G0); lauffähiger GitLab-Zugang; Repo-Skelett.
**Human-Gates:** G0.

### Sprint 1 — „Rollen & Orchestrator-MVP"
**Ziel:** Erste Agenten laufen und arbeiten ticket-basiert.
**Inhalte:** Rollenkarten v1 für PL, CM, COACH (System-Prompts); Prozess-Skills v1 für MAN.3, SUP.8, SUP.10 (aus Playbook abgeleitet); **Rollen-Registry v1** (Besetzungstyp script/ki/mensch je Rolle und Aufgaben-Typ, inkl. Provider-Präferenzketten); **LLM-Gateway v1**: einheitliche Executor-Schnittstelle mit dem Claude-Executor als erster Implementierung (Copilot-/Ollama-Executor folgen als PoC in Sprint 6); Orchestrator-MVP auf Claude Agent SDK: Tick-Loop, Board lesen (GitLab-API), **Skript-Route zuerst prüfen**, sonst Aufgabe über das Gateway an Rollen-Agent delegieren, Ergebnis als Kommentar/MR zurückschreiben; Guardrails v1 (Kosten-Limit je Tick, Schreibrechte, Aktions-Log inkl. Ausführungsweg Skript/Provider); Issue-Templates (Task, Problem, CR, DR, Clarification, Finding, Skriptifizierung) und Label-Schema.
**Deliverables:** Erster autonomer Tick, der ein echtes Ticket bearbeitet (z.B. CM erstellt CM-Strategie-Entwurf als MR).
**DoD:** Tick reproduzierbar; jede Agent-Aktion geloggt; Kosten je Tick sichtbar (Rohdaten reichen).

### Sprint 2 — „Prozesse & Selbstübernahme"
**Ziel:** Das Team führt P0 ab jetzt selbst; Requirements-Mechanik steht.
**Inhalte:** PL-Agent übernimmt P0-Board (Planung, Priorisierung, Sprint-Report); Rollenkarten + Skills für RM, QM, PROB, CHG; **Wissensbasis-Mechanik v1** (`process/knowledge/<rolle>/`, Lade-Logik, Feedback-Zuordnung per Skript, erster Lernzyklus in der Sprint-2-Retro); Requirements-Format (IDs, Attribute, Links) festlegen und Tool-Entscheid (Eigenbau vs. Doorstop/StrictDoc) als dokumentierte Evaluation; Traceability-Generator + CI-Checks v1; DoD-Checklisten v1 (Anforderung, Code, Sprint); CM-Strategie und Storage-/Tool-Übersicht finalisieren; Nachreview der Sprint-0/1-Artefakte; Baseline „Genesis-Foundation".
**Deliverables:** Von PL-Agent erstellter Sprint-Report; Requirements-Pipeline am Beispiel der **eigenen** Plattform-Anforderungen (die Anforderungen an Backend/Frontend werden als erstes echtes Requirements-Set nach SWE.1 geführt!).
**Human-Gates:** G1 für die Plattform-Anforderungen (Backend/Frontend) — du gibst die Anforderungs-Baseline der eigenen Werkzeuge frei.

### Sprint 3 — „Backend & Frontend MVP"
**Ziel:** Mission Control v1 online.
**Inhalte:** ARCH- und DEV-Rollen aktivieren; Architektur (SWE.2) für die Plattform inkl. ADRs — **Architektur-Anforderung: verteilungsfähig** (API-first, Aufgaben-Queue mit Lease-Mechanik, kein Zustand außerhalb des Hubs), damit Rollen später auf beliebigen Team-Nodes im Netzwerk laufen können; Backend-MVP (FastAPI: GitLab-Aggregation, HITL-Queue, Run-Registry, Traceability-API, Geräteregister-Stub); Frontend-MVP als **PWA** (smartphone-tauglich: Dashboard, **Live-Board mit Echtzeit-Status via WebSocket** inkl. „wer/was arbeitet gerade woran und auf welchem Gerät", Requirements-Browser, Decision-Inbox mit Benachrichtigung via F4-Kanal); Deployment auf Zielumgebung (F1) als Infra-as-Code; TEST-Rolle aktivieren: Verifikationsstrategie und erste automatisierte Verifikation für die Plattform selbst.
**Deliverables:** Erreichbares Frontend; erster über die Decision-Inbox beantworteter echter DR.
**Human-Gates:** G2 (Plattform-Architektur/Technologie), erste echte Inbox-Nutzung.

### Sprint 4 — „Generalprobe: Übungsprodukt, Teil 1"
**Ziel:** Volles Team arbeitet erstmals eine fremde Aufgabe ab.
**Inhalte:** Übungsprodukt-Auftrag durch den Menschen (bewusst klein, aber echt; Vorschlag: eine CLI-/Bibliotheks-Aufgabe mit 10–20 Anforderungen, z.B. ein Datenkonverter mit definierten Formaten und Fehlerfällen — finaler Vorschlag kommt vom Team als DR); RM präzisiert per Clarifications; SWE.1–SWE.3 durchlaufen; SWE.4 automatisiert in CI; alle Playbook-Mechanismen scharf (Reviews, QM-Checks, Probleme, CRs).
**Deliverables:** Anforderungs-Baseline (G1), Architektur, implementierte Units mit Unit-Verifikation.
**Human-Gates:** G1 (Übungsprodukt), ggf. G2.

### Sprint 5 — „Generalprobe Teil 2 + Release"
**Ziel:** E2E-Nachweis erbracht.
**Inhalte:** SWE.5/SWE.6 (Integrations-/SW-Verifikation gegen Anforderungen); Problem-Zyklus real durchlaufen (gefundene Fehler als SUP.9-Tickets bis Abschluss); mindestens ein Change Request mit Impact-Analyse real durchlaufen; Release des Übungsprodukts (SPL.2, Baseline, Release Notes, G3) **inkl. automatischer Registrierung im Produktkatalog v0** (`catalog/`, Eintrag CI-generiert); Feedback-Ticket-Typ + Routing-Skript v1 (Feedback → Problem/CR) am Übungsprodukt real erproben; Verifikations- und QM-Report.
**Deliverables:** Released Übungsprodukt; vollständige Traceability im Frontend.
**Human-Gates:** G3 (Release Übungsprodukt).

### Sprint 6 — „Härtung, Self-Check & Abnahme"
**Ziel:** P0-Abnahme.
**Inhalte:** Self-Check gegen die Basispraktiken aller Stufe-1-Prozesse (QM+COACH; Report mit Fundstellen und Lücken); Lücken schließen oder als Backlog für P1 dokumentieren; KPI-Baseline und Retro-Wirksamkeitsnachweis (Kriterium 6); Betriebs-Runbook (CM): Backup, Monitoring, Update-Prozedur, Störungsbehandlung, Geräte-Onboarding; **Team-Node-Proof-of-Concept**: der Runner-Dienst wird auf einem deiner Geräte (Laptop/PC) installiert und zieht mindestens eine echte Aufgabe per Lease aus der Hub-Queue; dabei werden auch die beiden weiteren LLM-Executor als PoC nachgewiesen — **Copilot-CLI-Executor** (eine DEV-Routineaufgabe auf dem Node mit gh-Login) und **Ollama-Executor** (eine Text-Aufgabe, z.B. Ticket-Vorklassifikation, auf lokalem Modell) — voller Multi-Node-Betrieb und datenbasierte Routing-Politik bleiben Phase P2; Intake-Workflow für neue Projekte + Anlage der P1-Hülle; P0-Abschlussbericht.
**Deliverables:** Self-Check-Report, Runbook, P0-Abschlussbericht, P1 bereit.
**Human-Gates:** P0-Abnahme gegen Kapitel 3 (= G3 für P0 selbst).

**Puffer/Realismus:** Sprints sind Zielbilder; PL darf per Re-Planung Inhalte verschieben (transparent im Report). Erwartete Gesamtdauer 6–8 Wochen Kalenderzeit, primär limitiert durch Mensch-Feedback-Zyklen und bewusst kleine Sprint-Budgets.

## 6. Initiales Product Backlog (Epics)

| # | Epic | Sprint(s) |
|---|---|---|
| EP1 | Infrastruktur & CM-Fundament (GitLab, Repos, Rechte, Backup, Kosten-Limits) | 0–2 |
| EP2 | Rollen & Skills (Rollenkarten, Rollen-Registry, Prozess-Skills, Templates, Checklisten, Wissensbasen + Lernzyklus) | 1–3 |
| EP3 | Orchestrierung & Guardrails (Tick-Loop, Skript-Route zuerst, Delegation, Logs, Limits, Skriptifizierungs-Workflow) | 1–3 |
| EP4 | Requirements & Traceability (Format, Tooling, CI-Checks, Matrix) | 2–4 |
| EP5 | Backend Mission Control (Aggregation, HITL-Queue, Run-Registry, KPI) | 3–5 |
| EP6 | Frontend Mission Control (Dashboard, Board, Requirements, Inbox, Baselines) | 3–6 |
| EP7 | Verifikation & CI/CD (Pipelines, 3 Verifikationsebenen, Reports) | 3–5 |
| EP8 | Übungsprodukt E2E (SWE.1–SWE.6, SUP.9/10 real, SPL.2, Produktkatalog v0 + Feedback-Routing v1) | 4–5 |
| EP9 | Selbstverbesserung & Self-Check (Retros, KPIs, PAM-Self-Check, Runbook, Intake P1) | 2–6 |

## 7. Was du bereitstellen musst (Einkaufsliste des Auftraggebers)

1. Antworten F1–F4 (Masterplan Kap. 10); F5–F10 bis Ende Sprint 2.
2. Zielumgebung gemäß F1 (Server/VM mit Docker) **oder** Entscheidung für die Übergangslösung.
3. GitLab-Zugang (Gruppe/Token) gemäß F2.
4. Anthropic-API-Key und monatliches Kostenbudget gemäß F3.
5. Benachrichtigungskanal gemäß F4 (z.B. E-Mail-Adresse für DR-Notifications).
6. Pro Sprint: geschätzt 1–2 Stunden deiner Zeit (Reviews, DRs, Gates) — in Sprint 0 und 4 etwas mehr (Auftrag/Übungsprodukt präzisieren).

## 8. Projektrisiken P0 (Auszug, PL führt die Liste weiter)

| Risiko | Gegenmaßnahme |
|---|---|
| Bootstrap-Zirkel (Team soll Prozesse bauen, die es zum Bauen bräuchte) | Drei-Stufen-Bootstrap (Kap. 1), Ausnahme-Regelung mit Nachreview (Kap. 4) |
| Zielumgebung verzögert sich (F1) | Sprint 1–2 laufen notfalls in Cowork-Sessions; Deployment erst Sprint 3 nötig |
| Frontend-Scope wuchert | MVP-Schnitt fixiert: lesend + Decision-Inbox; alles Weitere ins P1-Backlog |
| Agent-Qualität schwankt je Rolle | Rollenkarten klein halten, Skills iterativ per Retro schärfen; kritische Outputs doppelt reviewen |
| ASPICE-Tiefe vs. Pragmatismus | Leitplanke: CL1-Basispraktiken ja, Dokumenten-Barock nein; Self-Check in Sprint 6 objektiviert |

## 9. Nach P0: Projekt P1 (Ausblick)

P1 = erstes echtes Produkt deiner Wahl im Intake-Workflow: Du übergibst die Erwartungshaltung im Frontend (oder als Dokument), RM startet die Präzisierung, das Team liefert nach der in P0 bewiesenen Mechanik. Parallel läuft der Ausbau-Backlog (Masterplan Kap. 8, Phase P2) als zweiter Arbeitsstrang mit niedrigerer Priorität weiter.

---

*Änderungshistorie: 0.1 initialer Entwurf; 0.2 +Rollen-Registry, Skript-Route, Wissensbasen/Lernzyklus, Live-Board, verschärfte Abnahmekriterien; 0.3 +Produktkatalog v0 und Feedback-Routing im Übungsprodukt-Release; 0.4 +verteilungsfähige Architektur, PWA, Team-Node-PoC; 0.5 +LLM-Gateway (Claude/Copilot/Ollama), Abnahmekriterium 9 (Claude, 2026-08-05). Gate G0 wurde am 2026-08-05 erteilt (D000).*
