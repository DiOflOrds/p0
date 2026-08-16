# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-16 (Routine-Session) — **NEUN PROJEKTE ABGESCHLOSSEN, TEAM IM REGELBETRIEB**. Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

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

**Fünf Projekte abgeschlossen** (P0 Genesis, P1 MC 2.0, P2 Betriebshärtung, P3 MC 3.0, P4 MC 3.1), 1 Produkt released, 156+42 Tests, 52 SWRs / 0 Lücken, 0,00 € API über alles. Session-Routine: **Briefkasten zuerst.**

**P5 „Genesis 2.0 — Organisationsrahmen" ist ABGESCHLOSSEN (G4a/D002, 2026-08-15), Baseline `p5-v1.0`** (p5 + platform). Geliefert: Playbook Kap. 15 (drei Prozessprofile) + Kap. 16 (Entscheidungsklassen A/B/C, F17-Guardrails), Team-Registry, Gründungs-Template, intake.md v2 — und als erster Vollzug das **PM-Team** (`pm`: Charter, SLAs, Kanban, Session-Agenda, Klasse-B-Log). 0 Zeilen Plattform-Code, 0 € API, 1 Tag. **Die Organisation läuft ab jetzt über die PM-Session-Agenda** (`pm/management/session-agenda.md`). Sechs Projekte abgeschlossen.

**team-mail ist LIVE (TG-a + D001, 2026-08-15)** — erstes Projekt-Team der Organisation im echten Betrieb: Postfach dimitri.john83@gmail.com, Zugang über vorhandene Mail-Einrichtung (SMTP-Fallback), IMAP-Test real grün (57 Mails), T-0002 done, **erster Digest geliefert** (`team-mail/digest/2026-08-15-digest.md` — 3 Reaktionspunkte, Sicherheits-Check, Rest kompakt). Repo lokal ohne GitHub-Remote (Datenklasse sensibel, `.kein-remote`). Takt T-0001 läuft ab jetzt je Session; Pilotreview ab 2026-08-29 (B002/B003).

**P7 „Teams im HMI" ist ABGESCHLOSSEN (G4a/D003, 2026-08-15), Baseline `p7-v1.0`** (p7 + platform). Teams sind vollwertig in Mission Control: Tab „Team" (formatierter Digest-Verlauf per eigenem Markdown-Renderer — SWR-059 aus deinem Sprint-1-Befund, noch am selben Tag behoben), Cockpit-Kachel, PIN-geschützter Konfigurator mit Sofort-Commit, **PIN-Lesegate** für sensible Team-Inhalte (ADR-006-Delta, architektur v1.4), **Digest-Mailversand** idempotent im abschluss-Schritt [2c/5]. 166+42 Tests, Matrix 59/0, ~300 min Ist (−13 %). **Sieben Projekte abgeschlossen.** K4-Restpunkt im Betrieb: Mail-Zustellung im Konfigurator aktivieren → erster Lauf liefert den Realnachweis (PM prüft als Klasse-B-Stichprobe).

**Auto-Abschluss ist AKTIV (D028, Wunsch pm/N-0001):** Session schreibt `PUSH-ANFORDERUNG.txt`, die Windows-Aufgabenplanung führt `abschluss-auto.cmd` alle 15 Min aus (nur bei Anforderung; Log `abschluss-auto.log`). Einmalige Registrierung nötig — Befehl in der Briefantwort pm/N-0001 und Runbook Kap. 11. **Session-Pflicht ab jetzt: an jedem Abschlusspunkt die Anforderung schreiben.**

*Ursprünglicher Intake-Vermerk:* Auftraggeber-Update vom 15.08.: Die Organisation wächst — neben dem ASPICE-Team entstehen ein **PM-Team** und beliebige **Projekt-Teams** (Steuer, Mail, Trading-Analyse, Wissenschaft …). Grundlage: Orgkonzept v1.0 (`process/docs/02-genesis-2.0-orgkonzept.md`, Lücken L1–L9) + **p0/D027** (F14 Session-Takt 0 €, F15 Klasse B an PM, F16 Pilot = Mail-Zusammenfassung, F17 harte Guardrails: KI handelt nie mit Außenwirkung, sensible Daten nie in Repos mit GitHub-Remote). P5 baut den Rahmen: Prozessprofile (entwicklung/dienstleistung/wiederkehrend), Entscheidungsklassen A/B/C, Team-Registry + Template, PM-Repo `pm`. 2 Sprints, 0 €. Danach P6: reale Gründung des Pilot-Teams. G0-DR: `p5/T-0001` (Frist 2026-08-22, Default G0a).

## Warten auf Auftraggeber

**P8 „Mail-Autopilot" ist ABGESCHLOSSEN (G4a/D002, 2026-08-16), Baseline `p8-v1.0`** (p8 + platform) — team-mail verdichtet per lokalem Ollama, Mehrfach-Takt, Sofort-Knopf, `--auto` in der Aufgabenplanung. **Acht Projekte abgeschlossen.** 171+42 Tests, Matrix 65/0, 0,00 € API.

**BUGFIX (N-0006/pm-T-0009, SUP.9):** Auto-Push scheiterte seit 15.08. 17:36 an einem cmd-Klammern-Fehler in abschluss.cmd (:repo_push) — **behoben**; Erfolgsnachweis: PUSH-ANFORDERUNG.txt verschwindet beim nächsten Wächter-Lauf. Voraussetzung: GitHub-Repos **p7 + p8** existieren (+ Secret, PAT). Lesson L-2026-08-16 verankert.

**P9 „Org-Cockpit" ist ABGESCHLOSSEN (G4a/D002, 2026-08-16), Baseline `p9-v1.0`** (p9 + platform). Cockpit gruppiert: Feste Teams (ASPICE + PM) / Projekt-Teams / aktiv / abgeschlossen (eingeklappt, automatisch über Baselines erkannt), jede Karte mit Beschreibung (13 Steckbriefe, SWR-069), Status-Pille und offenen Aufgaben; **projects-Sammelrepo wird entdeckt** (SWR-070) — P10 ist nur noch ein Ordner. **Neun Projekte abgeschlossen.** Vor der Stichprobe: Server per ⟳ neu starten; die drei Cockpit-Stichproben aus `p9/T-0004` stehen als Betriebs-Nachweis noch offen (werden nicht vom Team abgehakt).

**Betriebs-CRs T-0006/T-0007 ERLEDIGT (Routine-Session, PM-Beschluss B010):** Der Konfigurator bietet jetzt die **Ollama-Modellwahl** (Liste live vom lokalen Ollama, „automatisch" bleibt Default, aktives Modell wird angezeigt — SWR-071) und ein **KI-Hinweisfeld** (freier Zusatz-Auftrag an die KI, z. B. „achte auf Bewerbungen"; ergänzt den Prompt, ersetzt die feste Digest-Struktur nie — SWR-072). Umsetzung als p8/T-0009 + p8/T-0010 auf der P8-Fläche, **ohne neue Projekt-Baseline**. **181 Tests, Matrix 73/0, 0,00 € API.** Deine Stichprobe: Modell wählen, Hinweis eintragen, speichern, „Jetzt zusammenfassen" — und den Digest inhaltlich bewerten.

**Briefe N-0010/N-0011 beantwortet und erledigt (B013):** Mission Control **startet sich jetzt selbst neu**, wenn eine Session neuen Code auf die Platte legt (SWR-073, p7/T-0016) — abgesichert dreifach: nur mit Startskript (`mission-control[-lan].cmd`), nur bei Ruhe (kein Abbruch mitten in Entscheidung oder Digest-Lauf) und entprellt gegen Neustart-Flattern; die Seite lädt sich danach von allein nach. Zum Status-Wunsch: `in_progress` **existierte bereits** (open → in_analysis → in_progress → in_review → done, eigene Board-Spalte, erzwungene Übergänge) — der echte Befund war die Sichtbarkeit, deshalb neue Playbook-Regel (Kap. 5): `in_progress` wird beim Arbeitsbeginn gesetzt, nicht am Ende nachgezogen. **181 Tests, Matrix 73/0.** Deine Stichprobe: Server einmal manuell neu starten, damit die neue Fassung läuft.

Sonst: Pilotreview team-mail 29.08., BB-5 PAT ab 5.9.; `pm/T-0010` (board-check-Flake) bleibt `in_review`, bis ein GitHub-Actions-Lauf nach dem Fix grün ist.

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: Live-API-Chat mit Budgetfreigabe, „Briefkasten zuerst" ins Playbook, JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1).

## Offene Fragen

Keine — F1–F17 vollständig entschieden; Decision Logs: p0 D000–D027, p1 D000–D009, p2 D000–D004, p3 D000–D004, p4 D000–D003.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2,p3,p4,p5} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0**, **p3-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/…/p1-abschlussbericht.md`, `p2/…/p2-abschlussbericht.md`, `p3/…/p3-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`
