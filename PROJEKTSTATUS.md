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

**P4 „Mission Control 3.1" — Sprint 1 fertig (2026-08-15), nur noch der Abnahme-DR offen.** G1+G2 erteilt (D001/D002 via Inbox), Baseline `p4-req-v1.0`. Umgesetzt und getestet: **PIN-Schutz** (localhost frei, remote nur mit `MC_PIN`, ohne PIN gesperrt — 6 Schutzregel-Tests), **`mission-control-lan.cmd`** (0.0.0.0-Bind, zeigt Handy-Adresse) + Runbook Kap. 10 (Firewall, Leitplanke kein Internet), **Briefkasten** (Briefe als versionierte Dateien + Commit, Team-Chat-Tab, Cockpit-Pille, Preflight „Briefkasten zuerst"), **Mobile-Feinschliff** (Touch-Buttons, Ein-Spalten-Board, PWA). Tests **156** grün, Matrix 52/0, alle 4 Gates konsistent. **Abnahme-DR T-0012 liegt in der Inbox** — die 5 Stichproben sind die LAN/Handy-Premiere selbst (Frist 2026-08-22, Default G4a).

## Warten auf Auftraggeber (~10 Min — das Sofa-Abenteuer)

1. **`abschluss.cmd`** — pusht Sprint 1 und mailt den Abnahme-DR.
2. `setx MC_PIN <deine-PIN>` → dann **`mission-control-lan.cmd`** starten (Firewall: zulassen).
3. Am **Handy** die angezeigte Adresse öffnen → ohne PIN entscheiden versuchen (Ablehnung sehen) → PIN eintragen → im **Team-Chat (p4)** einen echten Brief schreiben → **T-0012 vom Handy per G4a-Button** beantworten.

## Nächste Session

Beginnt mit **„Briefkasten zuerst"**: dein Handy-Brief wird beantwortet (schließt K4), dann D003 verbuchen, **Baseline `p4-v1.0`**, P4-Abschlussbericht — fünftes Projekt fertig.

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: Live-API-Chat mit Budgetfreigabe (P4-Rest), JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; Decision Logs: p0 D000–D026, p1 D000–D009, p2 D000–D004, p3 D000–D004.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2,p3} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0**, **p3-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/…/p1-abschlussbericht.md`, `p2/…/p2-abschlussbericht.md`, `p3/…/p3-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
