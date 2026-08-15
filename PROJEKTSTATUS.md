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

**P4 „Mission Control 3.1: Fernzugriff & Briefkasten-Chat" per Intake angelegt (2026-08-15, CR auf P3).** Dreifach-Wunsch des Auftraggebers: LAN-Sichtbarkeit (mit PIN-Schutz für Schreibzugriffe), volle Handy-Bedienung (Android/Chrome, realer Gerätetest), Team-Konversation im Browser — im Intake als **Briefkasten-Chat** entschieden (Session-Austausch, 0 €, asynchron; Live-API-Chat als Folge-CR zurückgestellt). 3 Epics, 5 Abnahmekriterien, 2 Sprints, Leitplanke: nur LAN, kein Internet-Expose. Hülle `p4/` valide, platform-CI um p4 erweitert. **G0 wartet als Inbox-DR T-0001** (Frist 2026-08-22, Default G0a).

## Warten auf Auftraggeber (~5 Min)

1. GitHub-Repo **p4** anlegen (privat, ohne README): [github.com/new](https://github.com/new) → dann: `git -C p4 remote add origin https://github.com/DiOflOrds/p4.git`
2. Secret: [github.com/DiOflOrds/p4/settings/secrets/actions](https://github.com/DiOflOrds/p4/settings/secrets/actions) → `PLATFORM_READ_TOKEN` (gleicher Wert wie bisher).
3. PAT `p0-read-fuer-platform-ci` um **p4** erweitern: [github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens).
4. **`abschluss.cmd`** — pusht P3-Abschluss (Tags `p3-v1.0`) + p4 und mailt den G0-DR.
5. **T-0001 in der Inbox beantworten** (Projekt p4) — per Button, versteht sich.

## Nächste Session

Nach der G0-Antwort: **„Starte P4 Sprint 0"** — Anforderungen ab SWR-048 (→ G1) + ADR-006 (LAN-Bind, PIN-Mechanik, Briefkasten-Ablage → G2).

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: Live-API-Chat mit Budgetfreigabe (P4-Rest), JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1).

## Offene Fragen

Keine — F1–F13 vollständig entschieden; Decision Logs: p0 D000–D026, p1 D000–D009, p2 D000–D004, p3 D000–D004.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2,p3} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0**, **p3-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/…/p1-abschlussbericht.md`, `p2/…/p2-abschlussbericht.md`, `p3/…/p3-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
