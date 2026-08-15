# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-15 — **VIER PROJEKTE ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Das Team ist im Regelbetrieb — kein aktives Projekt.** Bilanz: **4 abgeschlossene Projekte**, 1 released Produkt, 153 + 42 grüne Tests, Matrix 47 SWRs / 0 Lücken, 4 Konsistenz-Gates in abschluss.cmd (Tests, Matrix, Katalog, Architekturbild), **0,00 € API** über alles.

| Projekt | Ergebnis | Baseline | Abnahme |
|---|---|---|---|
| **P0 „Genesis"** | Team + Plattform + Prozess, Übungsprodukt datakonv 1.0.0 released | genesis-v1.0 | D024 |
| **P1 „Mission Control 2.0"** | Multi-Projekt-Leitstand, Inbox-Regelkanal, E-Mail-Benachrichtigung | p1-v1.0 | D009 via Inbox |
| **P2 „Betriebshärtung"** | Frist-Warnmails, Katalog-Gate, Nutzer-Registry/Entscheider, Inbox-Härtung, Aufwandsschätzung | p2-v1.0 | D004 via Inbox (K2-Realnachweis durch eigenes Feature) |
| **P3 „Mission Control 3.0"** | Jira-like HMI: Router, Ticket-Detail, Board-Spalten+Filter, Options-Buttons + Historie, Tabellen, Architekturbild mit Drift-Gate, Cockpit mit Frist-Ampel, Versions-Banner | p3-v1.0 | D004 via Inbox-**Button** |

Bemerkenswert am 15.08.: P2 und P3 liefen komplett an einem Tag — inkl. 3 realer SUP.9-Zyklen (Test-Mails/Windows-Pfade, CI-Tag-Rauschen/fetch-tags, Hermetik-Nachzügler), deren Lehren als Runbook-Regeln (Kap. 8/9), Gold-Beispiel und Anforderung SWR-047 im System gelandet sind. Copilot-PoC ehrlich als extern blockiert geschlossen (p0/D026: Abo abgelaufen; Reaktivierung per CR).

**P4 „Mission Control 3.1" ist ABGESCHLOSSEN (G4a/D003, 2026-08-15 — vom Handy aus entschieden), Baseline `p4-v1.0`** (p4 + platform). Alle 5 Stichproben real: LAN-Zugriff vom Handy, Falsch-PIN-Ablehnung, erster echter Briefkasten-Roundtrip (p0/N-0001: Handy-Brief → Commit → Team-Antwort in derselben Datei = K4), Handy-Button-Entscheidung. Mission Control läuft jetzt vom Sofa: `mission-control-lan.cmd`, PIN-Schutz, Team-Chat, Mobile-PWA. Leitplanke fürs Leben: **nur Heim-LAN, nie Port-Forwarding** (Runbook Kap. 10).

**Das Team ist im Regelbetrieb.** Fünf Projekte abgeschlossen (P0 Genesis, P1 MC 2.0, P2 Betriebshärtung, P3 MC 3.0, P4 MC 3.1), 1 Produkt released, 156+42 Tests, 52 SWRs / 0 Lücken, 0,00 € API über alles. Session-Routine ab jetzt: **Briefkasten zuerst.**

## Warten auf Auftraggeber

Nur noch: **`abschluss.cmd`** — pusht den P4-Abschluss inkl. Tags `p4-v1.0` und die Briefantwort. Danach: Team-Chat neu laden — die erste Team-Antwort wartet dort schon.

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: Live-API-Chat mit Budgetfreigabe, „Briefkasten zuerst" ins Playbook, JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1). Neues Projekt per **„Starte Intake"** — oder einfach per Brief vom Sofa.

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: Live-API-Chat mit Budgetfreigabe (P4-Rest), JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; Decision Logs: p0 D000–D026, p1 D000–D009, p2 D000–D004, p3 D000–D004.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2,p3} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0**, **p3-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/…/p1-abschlussbericht.md`, `p2/…/p2-abschlussbericht.md`, `p3/…/p3-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
