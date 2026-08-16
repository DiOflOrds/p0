# Projektstatus — Fortschreibung über Sessions

*Übergabepunkt zwischen Cowork-Sessions. Zuletzt aktualisiert: 2026-08-16 15:35 (Routine-Session) — **ELF TEAMS/PROJEKTE IM SYSTEM: `team-dashboard` IST GEGRÜNDET (D006/TG-a, entschieden 15:21 mitten in der Session), `pm/T-0030` TEIL 1 IST ERLEDIGT (SWR-091 — offene Aufgaben lassen sich ab jetzt terminieren), UND EIN NEUER KLASSE-A-ENTSCHEID LIEGT IN DER INBOX (pm/T-0033, G0 für Projekt P11 „Widget-Dashboard").** Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Routine-Session 15:35:** Briefkasten **leer** (zweimal geprüft, alle 36 Briefe beantwortet).
Inbox: **eine Entscheidung fiel während der Session** — `pm/T-0031` → **D006/TG-a um 15:21**,
also nach dem ersten Inbox-Check dieser Session um 15:11. Gefunden hat sie die **Zweitprüfung
aus B036**; das ist der vierte Fund dieser Regel und der erste an einem **Klasse-A-Entscheid**,
der sonst 30 Minuten unverbucht geblieben wäre.

**`pm/T-0030` Teil 1 ist ERLEDIGT (SWR-091) — das Ticket gegen das Liegenbleiben war selbst
der oberste liegengebliebene Punkt.** Die Session begann frei: kein offener Brief, kein
entschiedener DR. `T-0030` stand seit der 14:05-Session als „Design-Session nötig" oben auf
der Agenda. Es ein sechstes Mal weiterzureichen wäre die Wiederholung genau des Befunds
gewesen, den es beschreibt (B043).

Was der Auftraggeber in `pm/N-0025` bemängelt hatte, war strukturell richtig: Nur
Decision-Requests hatten ein Zeitkonzept. Ein CR mit `prio: mittel` konnte beliebig lange
offen bleiben, ohne dass **irgendein Werkzeug** das gemeldet hätte — die Priorität steuert
die Reihenfolge *innerhalb* einer Session, nicht *ob* eine Session sich das Ticket vornimmt.
Geliefert:

- **`frist` gilt für jeden Tickettyp und wird für jeden geprüft.** Bis hierher stand die
  Datumsprüfung im `decision-request`-Zweig; ein Tippfehler in der Frist eines CR fiel
  **lautlos auf „keine Frist" zurück**. Ein Termin, den niemand prüft, ist keiner.
- **Die Ampel-Regel liegt jetzt einmal** in `board.frist_ampel` und wird von den offenen
  Entscheidungen **und** den Backlog-Fristen benutzt. Sie stand inline im Cockpit; sie ein
  zweites Mal zu schreiben wäre die Falle aus B033 gewesen. Ein Test vergleicht alte
  Inline-Formel und neue Funktion **einen ganzen Monat lang Tag für Tag**.
- **`board.ist_ueberfaellig` gilt nur für offene Tickets** — eine gerissene Frist an einem
  erledigten Ticket ist Historie, kein Vorwurf.
- **Die Cockpit-Kachel zeigt überfällige Tickets vollständig und vor den Statuszahlen**, jedes
  mit Frist und „n Tage über", dazu einen Zähler „n ohne Frist" für unterminierte
  Backlog-Tickets. Sie in die auf drei Einträge gekürzte Aufgabenliste zu legen wäre die
  Unsichtbarkeit aus B038 in neuem Gewand gewesen: *„Wo wird ein Fehlschlag sichtbar für
  jemanden, der nicht danach sucht?"*

**Nebenbefund, mitbehoben:** `DATUM_MUSTER` prüfte nur die **Form**. „2026-13-01" kam durch —
und wäre über die Ampel als **„grau" = keine Frist** gelaufen. Ein falsch terminiertes Ticket
hätte damit wie ein unterminiertes ausgesehen. Jetzt eine gemeinsame Prüfung `board.ist_datum`
für `frist` und `erstellt`, nicht zwei.

**Bewusst nicht angefasst: das generierte `BOARD.md`.** Eine Frist-Spalte wäre eine
Formatänderung, und genau die hat heute früh alle board-check-Workflows rot gemacht
(`pm/T-0013`) — das gehört gebündelt, nicht nebenbei.

**Die Eskalationsregel — die offene Frage des Tickets — ist festgelegt (B044):** Ein
überfälliges Backlog-Ticket ist der **erste Arbeitspunkt der nächsten Session nach dem
Briefkasten**. Nimmt eine Session es trotzdem nicht auf, **schreibt sie den Grund beim Ticket
in die Agenda**. Ab dem **zweiten** übergangenen Mal geht ein Vermerk an den Auftraggeber. Und
sie ist **sofort angewandt statt nur gebaut**: `pm/T-0028` (23.08.), `pm/T-0032` (19.08.),
`pm/T-0034` (17.08.), `team-dashboard/T-0001` (23.08.) tragen jetzt Termine.

**8 neue Tests im Board, 3 im Cockpit — Gesamtsuite 329** (vorher 318), Matrix **91 SWRs /
0 Lücken**, Katalog- und Architektur-Gate grün. **Gegenprobe geführt:** gegen den Altstand
scheitern drei der neuen Tests nachweislich.

---

**`team-dashboard` ist gegründet — das zweite Projekt-Team der Organisation (D006/TG-a, B045).**
Der Auftraggeber hat um 15:21 mit **TG-a** entschieden, also der Empfehlung des Teams gefolgt.
Vollzogen sind alle vier Schritte aus `pm/T-0031`:

1. **Repo `team-dashboard`** aus `process/templates/team-repo/`: Charter v1.0, `team.yaml`
   (Profil `wiederkehrend`, Rolle `DASH-RED`, drei SLAs), `steckbrief.yaml`, Decision-Log mit
   **D000 als Gründungsbeleg**, board-check-Workflow bereitgelegt, board-check grün. **Lokal
   ohne Remote — und bewusst ohne `.kein-remote`:** Datenklasse `intern` *erlaubt* einen
   Remote; er fehlt nur, weil GitHub-Repo, Secret und PAT-Erweiterung Handlungen des
   Auftraggebers sind. Ein `.kein-remote` hätte eine Regel behauptet, die nicht gilt.
2. **Registry-Eintrag** in `process/teams/registry.yaml`, Status `aktiv`, Gründungsbeleg
   `pm/T-0031` / `pm/D006`.
3. **Erstes Takt-Ticket `team-dashboard/T-0001`: „Widget-Vertrag entwerfen"**
   (`takt: je-session`, Frist 23.08. für den ersten Entwurf). Die im Kandidat-Text notierte
   Voraussetzung — *„Die Projekte haben eine Widget Kompatibilität"* — **existiert nicht**;
   sie zu schaffen ist die eigentliche erste Arbeit und die Vorbedingung für den Bau.
4. **Getrennter G0-DR `pm/T-0033` für Projekt P11 „Widget-Dashboard"** (Optionen G0a–G0c,
   Frist 23.08., Default G0a) — **nicht** in der Gründung mitentschieden, weil ein
   Projektauftrag eine eigene Klasse-A-Entscheidung ist. Drei Punkte stehen offen im Antrag:
   die Datenquelle existiert bereits (`aggregation.cockpit` — eine zweite wäre B033),
   „nicht scrollbar auf FHD" begrenzt bei 14 Projekten/Teams den Inhalt und ist eine
   Sprint-0-Entwurfsfrage, und „vom Handy aus dem Internet" bleibt außen vor (Runbook Kap. 10).

**Die Mail-Widget-Auflage steht dreimal im Klartext** — in `team.yaml`, im Charter und in der
Registry: `team-mail` ist `sensibel`, gerendert wird **nur zur Laufzeit hinter dem
PIN-Lesegate**, und der erste in ein Repo committete Digest-Inhalt macht `team-dashboard`
`sensibel` und kostet den GitHub-Remote. Ein Feldwert `intern` erzwingt das nicht — deshalb
ausgeschrieben, an jeder Stelle, an der jemand nachschaut.

---

**⚠ Befund in eigener Sache, mit Frist statt Fußnote: `pm/T-0034` (Frist 17.08., Priorität
hoch).** Der **team-mail-Wochendigest** ist seit der Teamgründung fällig — `takte: [7]` gilt,
`mail_digest.faellig(7)` meldet `True`, und in `team-mail/digest/` liegt bis heute **keine
einzige `-woche-`-Datei**. Gefunden wurde das in der 11:21-Session. Seither stand es als
Punkt 3 der Agenda, und die Sessions 11:45, 12:16, 14:05 und 14:50 haben jeweils „unverändert
offen" notiert. **Fünf Sessions, fünfmal derselbe Satz.** Das ist wörtlich das Muster aus
B043 — deshalb ist es ab jetzt ein Ticket mit Termin und nicht länger eine Agendazeile.
Lösen kann es nur der Host (kein IMAP/Ollama in dieser Sandbox, Guardrail 2); der kürzeste
Weg steht im Ticket: Server neu starten, Team-Reiter, „Jetzt zusammenfassen" — die
Klartextzeile aus SWR-090 sagt vorher „Woche", die Erfolgsmeldung nennt hinterher die Datei.

**Und noch ein Vorgang lief mitten hinein: der erste Wochendigest seit der Teamgründung steht
(B046).** Um **15:28** startete am Host ein Lauf über 7 Tage (165 Mails), fand **kein Ollama** und
schrieb Rohdaten mit dem Vermerk *„die naechste Session verdichtet"* — das ist der Fallback
SWR-062, und diese Session ist die nächste. `team-mail/digest/2026-08-16-woche-digest.md` ist
geschrieben, `mail_digest.faellig(7)` meldet jetzt **False**. Damit ist Verdacht 2 aus `T-0034`
ausgeräumt: **der Takt war korrekt** (7 Tage, kein zweiter B040) — es fehlte schlicht Ollama. Der
Digest ist als **von der Session verdichtet** gekennzeichnet, nicht als Ollama-Ergebnis; die
Vorlagenzeile zu übernehmen wäre eine Falschaussage im Dokument gewesen. **Nicht versendet** —
Mailversand ist Außenwirkung und läuft am Host. Vier Punkte darin brauchen deinen Blick:
Google-Sicherheitswarnungen, der **weiterhin unbeantwortete Vedaco-Phishing-Verdacht**, der
Enpal-Termin und eine Microsoft-365-Abo-Mail vom 10.08. **`pm/T-0034` bleibt offen** — dass die
Datei jetzt da ist, heißt nicht, dass der Autopilot funktioniert; sie kam von Hand.

Push: `PUSH-ANFORDERUNG.txt` aus der 14:50-Session war beim Sessionstart **noch unverarbeitet**
(letzter Wächter-Erfolg 14:30:22) — diese Session hängt eine weitere Zeile an (Repos: platform,
pm, p0, p9, process; `team-dashboard` ist neu und **lokal-only**, bis das GitHub-Repo besteht).
`pm/T-0010`/`T-0013`/`T-0026` bleiben unverändert `in_review` (kein `gh`/Netzzugriff in dieser
Sandbox). Alle Änderungen committet, `preflight.py` meldet STARTKLAR.

---

**Routine-Session 14:50:** Briefkasten hatte **einen neuen Brief** seit der 14:05-Session —
`pm/N-0027` (12:43), beantwortet; zweite Prüfung am Sessionende: leer. Inbox: **erstmals seit
Tagen wieder ein wartender Entscheid**, und zwar der von dieser Session vorgelegte (`pm/T-0031`),
gegen die Rohdaten geprüft. *(Nachtrag 15:35: Dieser Entscheid ist am 16.08. um 15:21 mit **TG-a** gefallen und in der 15:35-Session vollzogen — siehe oben.)*

**`pm/N-0027` („starte mit der initialiserung von team-dashboard aus dem projekt-pool") —
angefangen, aber bewusst nicht vollzogen.** Eine Team-Gründung ist **Klasse A** (Playbook
Kap. 16, `intake.md`): Das Team hat Schritt 1+2 des Intake geliefert — **Steckbrief formuliert**
(Auftrag, Profil `wiederkehrend`, Rollen, Datenklasse, Zugänge, Grenzen, SLA) und den
**Gründungs-DR `pm/T-0031`** in die Inbox gestellt (Optionen TG-a–TG-d, Frist 23.08., Default
TG-a). Repo aus Template, Registry-Eintrag und Betriebsstart folgen **nach** dem Entscheid. Der
Pool-Knopf „Team gründen" (`pm/T-0028`) wurde dafür **nicht** erst gebaut — die Gründung lief von
Hand über den regulären Intake-Weg; was dabei entstand, ist die Feldliste seines künftigen
Formulars. **Drei Befunde stehen im Antrag:**

1. **Das gewünschte Mail-Widget berührt Guardrail 2.** `team-mail` ist `sensibel` (private Mails,
   lokales Repo ohne GitHub-Remote). Machbar ist es genau so, wie der Team-Reiter es seit P7 tut —
   Rendern **zur Laufzeit** hinter dem bestehenden **PIN-Lesegate** — mit der harten Auflage,
   **nie** einen Digest-Inhalt oder Mail-Auszug in ein Repo zu committen. Wird das je gebraucht,
   ist `team-dashboard` ab dem Moment `sensibel` und verliert den GitHub-Remote. Das steht im
   Klartext im DR, weil ein Feldwert „intern" diese Regel nicht erzwingt.
2. **Der Kandidat-Text enthält zwei Dinge: ein Team und eine Produktspezifikation.** „Verwaltet,
   koordiniert, updatet" ist eine Daueraufgabe; das Dashboard selbst ist SW-Entwicklung auf der
   Mission-Control-Fläche, und die gehört dem ASPICE-Team. Empfehlung: **Bau als eigenes Projekt
   P11**, das neue Team ist fachlicher Auftraggeber, G0-Antrag getrennt — ein Projektauftrag soll
   nicht in einer Gründung mitlaufen. Option **TG-c** bietet den schlanken Weg ohne eigenes Team.
3. **„Vom Handy aus dem Internet" kollidiert mit Runbook Kap. 10** (nur Heim-LAN, nie
   Port-Forwarding). Weder still übergangen noch nebenbei aufgeweicht: Es gibt einen Weg, der die
   Leitplanke nicht bricht — ein **VPN** ins Heimnetz, kein offener Port —, aber das ist ein
   eigener Klasse-A-Entscheid und **nicht** Teil dieser Gründung.

**`pm/T-0025` ist ERLEDIGT (SWR-090) — genau das Ticket, an dem der Befund B043 hing.** Nach
sechs Sessions Liegenzeit als erste Arbeit nach dem Briefkasten aufgegriffen, wie die
14:05-Agenda es nach der Hochstufung angeordnet hatte. Der Sofort-Knopf im Team-Reiter sagt
jetzt **vorher**, womit er läuft (Takte · Modell · KI-Hinweis · Versand), und **hinterher**,
welche Digest-Dateien entstanden sind. Gebaut **ohne eine zweite Kopie der Takt-Regel**: neuer
Modus `--was-laeuft` im Werkzeug (Auskunft ohne Wirkung — kein IMAP, kein Ollama, keine Datei;
Takte aus **`jetzt_takte()`**), `teams.digest_vorschau()` fragt genau das über denselben
injizierbaren Runner wie der Lauf, `GET /api/team/digest-vorschau` hinter dem PIN-Lesegate. Die
geschriebenen Dateien werden aus der Ergebniszeile des Werkzeugs gelesen und **nicht** aus einem
Verzeichnis-Vergleich — der hätte beim zweiten Klick am selben Tag „nichts passiert" gemeldet
und wäre die Unsichtbarkeit aus `N-0002` in neuem Gewand. **8 neue Tests, Gesamtsuite 318**
(vorher 310), Matrix **90 SWRs / 0 Lücken**, Katalog- und Architektur-Gate grün. **Gegenprobe
geführt** (eine aus `cfg["takte"]` nachgebaute Variante scheitert am `--tage`-Override
nachweislich) und **am echten System gelaufen**: gegen die reale team-mail-Konfiguration meldet
die Vorschau „Woche · gemma3:27b · kein Zusatz · zusätzlich per Mail" — also genau den
Wochentakt, der im Brief `N-0002` nicht durchkam.

Push: `PUSH-ANFORDERUNG.txt` aus der 14:05-Session war beim Sessionstart bereits abgearbeitet
(Wächter-Erfolg 14:30:22) — diese Session schreibt am Ende eine neue Zeile für ihre eigenen
Commits (pm, platform, team-mail, p8, p0). `pm/T-0010`/`T-0013`/`T-0026` bleiben unverändert
`in_review` (kein `gh`/Netzzugriff in dieser Sandbox). team-mail-Digest-Befund unverändert offen
(`mail_digest.faellig(7)` weiterhin `True`, nur am Mission-Control-Host prüfbar — Session-Agenda
Punkt 3). `pm/T-0028` (Gründungs-Knopf im Pool) und `pm/T-0030` (Fristen/Uhrzeit-Takt) bleiben
`open`; `T-0030` ist jetzt der oberste offene Punkt. Alle Änderungen committet, `preflight.py`
meldet STARTKLAR, `PUSH-ANFORDERUNG.txt` fortgeschrieben.

---

**Routine-Session 14:05:** Briefkasten hatte **drei neue Briefe** seit der 12:16-Session.
`pm/N-0024` (12:05) lag beim ersten Check bereits vor und wurde sofort bearbeitet; **während**
die Session daran arbeitete, gingen zwei weitere ein — `pm/N-0025` (12:08) und `pm/N-0026`
(12:10) —, gefunden erst bei der Zweitprüfung vor Sessionende (Lesson B036 hat sich damit ein
drittes Mal bezahlt gemacht). Alle drei beantwortet, dritte Prüfung danach: wieder leer. Inbox
unverändert leer (37/37 `done`).

**`pm/N-0024` sofort geliefert als `pm/T-0029`** (SUP.9, zweite Korrektur an SWR-088, kein
neuer SWR): Selbst die in `pm/T-0027` auf 4000 Zeichen angehobene Grenze reichte für ein
reales „Quelle"-Feld (Zusatzspalte bei Technik-Kandidaten) nicht — zweiter Fehlversuch, eine
konkrete Zahl zu raten. Statt einer dritten Zahl: die eigentliche Ursache behoben.
`platform/backend/pool.py`: `FELD_MAX` 4000 → 200 000 — keine Inhaltsgrenze mehr, nur noch
eine technische Notbremse gegen einen versehentlichen Mega-Paste; hart verboten bleibt
weiterhin nur `|` (das einzige Zeichen, das die Markdown-Tabellenzeile wirklich sprengt, wie
schon in T-0027 festgehalten). HMI (`app.js`): „Nutzen"/„Voraussetzung"/„Quelle" laufen jetzt
ebenfalls über `<textarea>` statt einzeiliger Eingabe, weil alle drei durch dieselbe
Prüffunktion laufen — sonst wäre derselbe Befund an der nächsten Spalte fällig gewesen. 1
neuer Test, Gesamtsuite **310 Tests** (vorher 309), Matrix weiterhin **89 SWRs / 0 Lücken**,
Katalog- und Architektur-Gate geprüft und grün. Klasse C (rein technische Validierungsgrenze,
keine Geld-/Rechts-/Außenwirkung) — kein Decision-Log-Eintrag nötig, analog zu T-0027.

**`pm/N-0025` — BEFUND in eigener Sache: Ein offenes Ticket blieb über fünf Sessions liegen,
der Vorwurf trifft zu (B043, `pm/T-0030`).** Der Auftraggeber bemängelt, dass offene PM-Aufgaben
nicht terminiert werden und liegen bleiben, wiederkehrende Aufgaben keinen echten Zeittakt
(„jeden Tag um 14 Uhr") haben. Konkreter Beleg: `pm/T-0025` steht seit der 10:40-Session offen,
fünf Routine-Sessions haben es nicht aufgegriffen, obwohl die Agenda es seit der 10:23-Session
nennt — nur eben als Randnotiz ohne Priorität. Zwei strukturelle Lücken benannt: Backlog-Tickets
(CR/Problem) haben kein Fristfeld (nur Decision-Requests haben `frist`/`default`); „wiederkehrend"
heißt bisher nur „je Sessionlauf geprüft", nicht „zu einer festen Uhrzeit". **Nicht sofort
gebaut** — ein Fristfeld ohne geklärte Eskalationsregel und ein neuer Uhrzeit-Takt neben den
bestehenden zwei Taktlogiken (Session-Takt F14, team-mail-Takt) wären ein zu schnell gebautes
Werkzeug (B025/B038-Risiko). Als `pm/T-0030` für eine Design-Session eingeplant, Entwurf im
Ticket. **Sofort umgesetzt:** `pm/T-0025` Priorität mittel → hoch, jetzt oben auf der Agenda.

**`pm/N-0026` — einfache Statusfrage, direkt beantwortet:** Ja, P9 „Org-Cockpit" ist
abgeschlossen (G4a/D002, Baseline `p9-v1.0`), kein offenes Ticket in `p9`. Offen bleiben nur die
drei Betriebs-Stichproben aus `p9/T-0004`, die bewusst nicht vom Team abgehakt werden — kein
Blocker für den Abschlussstatus.

Push: `PUSH-ANFORDERUNG.txt` aus der 12:16-Session war beim Sessionstart bereits abgearbeitet
— diese Session schreibt am Ende eine neue Zeile für ihre eigenen Commits (platform, pm).
`pm/T-0010`/`T-0013`/`T-0026` bleiben unverändert `in_review` (kein `gh`/Netzzugriff in
dieser Sandbox). team-mail-Digest-Befund unverändert offen (`mail_digest.faellig(7)`
weiterhin `True`, nur am Mission-Control-Host prüfbar — siehe Session-Agenda Punkt 3).
`pm/T-0028` (Team-Gründung im Pool) bleibt bewusst `open`, für eine dafür vorgesehene
Session — kein Blocker für diese Session. Alle Änderungen committet, `preflight.py` meldet
STARTKLAR, `PUSH-ANFORDERUNG.txt` fortgeschrieben.

**Routine-Session 12:16:** Briefkasten hatte **zwei neue Briefe** seit der 11:45-Session —
`pm/N-0022` (09:59, committet 11:59) und `pm/N-0023` (10:05, committet 12:05), beide erst nach
Sessionende der Vorsession eingegangen, gefunden beim ersten Check dieser Session und
beantwortet (zweite Prüfung am Sessionende: wieder leer). Inbox unverändert leer (37/37 `done`).

**`pm/N-0023` sofort geliefert als `pm/T-0027`** (SUP.9, Korrektur an SWR-088, kein neuer SWR):
Die Validierung für Pool-Kandidaten war mit „1-200 Zeichen, keine Zeilenumbrüche" zu eng für den
eigentlichen Zweck des Feldes — bei Technik-Kandidaten trägt der Kandidat-Text die ganze Aufgabe
(kein zweites Beschreibungsfeld), bei Team-Kandidaten die Kurzbeschreibung; beides sollte
mehrsätzig sein dürfen, ausdrücklich auch bei KI-formulierten Vorschlägen (so der Brief).
`platform/backend/pool.py`: `FELD_MAX` 200 → 4000, neue Funktion `_text_bereinigen` zieht
Zeilenumbrüche zu Leerzeichen zusammen statt die Eingabe mit `PoolFehler(400, …)` abzulehnen —
hart verboten bleibt nur `|` (das einzige Zeichen, das die Markdown-Tabellenzeile wirklich
sprengt). HMI (`app.js`): Kurzbeschreibung (Team) und Kandidat-Text (Technik) laufen jetzt über
`<textarea>` statt einer einzeiligen Eingabe — reine Darstellung, Validierung bleibt serverseitig.
**Bewusst nicht angefasst:** `kandidat_starten` (Teil „Starten") prüft weiterhin hart auf `|`,
`"` und Zeilenumbruch, weil der Text dort in ein Ticket-YAML-Frontmatter eingebettet wird — ein
jetzt anlegbarer Kandidat mit `"` im Text lässt sich anlegen, aber erst nach Bereinigung starten
(Fehlermeldung sagt das); Bestandsverhalten aus `pm/T-0022`, nicht Teil dieses Befunds. 4
neue/geänderte Tests, Gesamtsuite **309 Tests** (vorher 305), Matrix weiterhin **89 SWRs / 0
Lücken** (Testzahl je SWR-088 gestiegen, keine neue Anforderung), Katalog- und Architektur-Gate
geprüft und grün.

**`pm/N-0022` — Team-Gründung im Pool beauftragt, aber bewusst nicht in dieser Session gebaut,
sondern als `pm/T-0028` (CR, `open`) für eine dafür vorgesehene Session eingeplant.** Der Brief
benennt selbst den Unterschied zu „Projekt starten" („bei team-steuer/team-trading hängt daran
mehr als ein Ordner"): `intake.md` verlangt für eine Team-Gründung einen vollen Steckbrief
(Auftrag, Profil `entwicklung`/`dienstleistung`/`wiederkehrend`, Rollen, **Datenklasse**,
Zugänge, Grenzen), Repo-Aufbau **aus Template** (`process/templates/team-repo/`) statt einem
Ordner-Skelett, und bei Datenklasse `sensibel` ausdrücklich **keinen GitHub-Remote** — Klasse A
mit Datenklassen-Wirkung (Playbook Kap. 15/16). Die Feldliste eines solchen Formulars in einer
Routine-Session ohne Rückfrage an dich zu entwerfen, ist genau das Risiko aus B025/B038: ein zu
schnell gebautes Werkzeug, das „sensibel" zwar als Option anbietet, den GitHub-Ausschluss
dahinter aber nicht wirklich erzwingt. `pm/T-0028` beschreibt den Umfang (Formular, Charter-Entwurf,
Gründungs-DR analog zu G0, Datenklasse explizit im Klartext) für die Umsetzung. **Zweiter Teil des
Briefs** („Löschen von Kandidaten bleibt Session auf Zuruf") ist eine Festlegung, keine Anfrage —
bestätigt, **keine Code-Änderung**.

Push: `PUSH-ANFORDERUNG.txt` aus der 11:45-Session war beim Sessionstart bereits abgearbeitet
(Wächter-Erfolg 12:00:22, Log `OK - alles geprueft und gepusht`) — diese Session schreibt am Ende
eine neue Zeile für ihre eigenen Commits (platform, pm, p0). `pm/T-0010`/`T-0013`/`T-0026` bleiben
unverändert `in_review` (kein `gh`/Netzzugriff in dieser Sandbox). team-mail-Digest-Befund
unverändert offen (`mail_digest.faellig(7)` weiterhin `True`, nur am Mission-Control-Host
prüfbar — siehe Session-Agenda Punkt 3). Alle Änderungen committet, `preflight.py` meldet
STARTKLAR, `PUSH-ANFORDERUNG.txt` fortgeschrieben.

**Routine-Session 11:45:** Briefkasten leer (zweimal geprüft, Sessionanfang und -ende), Inbox
unverändert leer (37/37 DRs `done`) — kein neuer Kandidat wurde real gestartet, siehe unten.
**`pm/T-0022` ist jetzt komplett: Teil 2 „Starten" geliefert** (Teil 1 „Anlegen" kam bereits in
der 11:21-Session). Nur Technik-Kandidaten — Team-Kandidaten brauchen die volle Team-Gründung aus
`intake.md` und sind laut Ticket bewusst außen vor. **Variante A gebaut** (weiterhin keine Antwort
auf die A/B-Rückfrage im Briefkasten, Default laut Ticket): Der neue Knopf im Pool-Reiter
entscheidet nichts — er legt `projects/p<N>` an (nächste freie Nummer über dieselbe Discovery wie
Board/Matrix/Preflight, `board.projekt_pfade`) und stellt einen G0-Decision-Request (T-0001, Frist
eine Woche, Default G0a) hinein, Ordner und Antrag in einem Commit im Sammel-Repo `projects`;
scheitert der Commit, bleibt nichts auf der Platte. Der gestartete Kandidat wird in einem zweiten
Commit aus dem Pool entfernt (Repo `pm`) — scheitert nur dieser zweite Commit, bleibt das bereits
sichtbare Projekt bestehen (eine Rücknahme würde einen echten G0-Antrag wieder verschwinden
lassen), die Antwort sagt das in Klartext statt es nur zu loggen (Lehre aus B038/`pm/T-0024`: ein
stiller Fehlschlag ist teurer als ein lauter). **Bewusst kein echter Kandidat aus dem realen Pool
gestartet** — das hätte einen echten, für dich sichtbaren G0-Antrag erzeugt, ohne dass konkret
danach gefragt wurde; geprüft ist die Funktion über 20 neue Unit-Tests mit isolierten
Git-Fixturen (`platform/tests/test_pool_starten.py`), keine echte Pool-Datei angefasst. SWR-089
auf der P9-Fläche (v1.6, direkte Fortsetzung von SWR-086–088, keine neue Baseline). **305 Tests
(vorher 285), Matrix 89 SWRs / 0 Lücken**, Katalog- und Architektur-Gate geprüft und grün. Push:
`PUSH-ANFORDERUNG.txt` aus der 11:21-Session war beim Sessionstart noch unverarbeitet (letzter
Wächter-Erfolg 11:00) — diese Session hängt eine weitere Zeile an; `pm/T-0010`/`T-0013`/`T-0026`
bleiben unverändert `in_review` (kein `gh`/Netzzugriff in dieser Sandbox). team-mail-Digest-Befund
aus der 11:21-Session unverändert offen (siehe Session-Agenda Punkt 3 — nur am Mission-Control-Host
prüfbar). Alle Änderungen committet, `preflight.py` meldet STARTKLAR, `PUSH-ANFORDERUNG.txt`
fortgeschrieben.

**Routine-Session 11:21:** Briefkasten leer (30/30 beantwortet), Inbox leer (37/37 DRs
entschieden, gegen Rohdaten geprüft). Der Auto-Push-Wächter lief um 11:00 wieder erfolgreich
(Nachfolge zu `pm/T-0024`) — 21 liegen gebliebene Commits und `p10-v1.0` sind auf GitHub;
`pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`, weil diese Sandbox keinen GitHub-Actions-Lauf
prüfen kann (kein `gh`, kein Netzzugriff). **Geliefert: `pm/T-0022` Teil 1 „Anlegen"** — neuer
Schreibpfad `platform/backend/pool.py` für den Projekt-Pool (Muster `tickets.py`/`inbox.py`:
PIN, Sofort-Commit, Rücknahme bei Fehlschlag), Formular für Team- und Technik-Kandidaten mit den
Feldern der jeweiligen Tabelle, laufende Nummer über beide Kategorien, Duplikat-Ablehnung.
SWR-088 auf der P9-Fläche (v1.5). **285 Tests (vorher 268), Matrix 88 SWRs / 0 Lücken**,
Katalog-/Architektur-Gate unverändert grün. Teil 2 „Starten" bewusst zurückgestellt (eigene
Session, Begründung + Stichprobe in `pm/T-0022` und der Session-Agenda). **Neuer Befund
team-mail:** ein Wochen-Digest ist laut `mail_digest.faellig(7)` fällig und wurde noch nie
erzeugt, obwohl `takte: [7]` seit Gründung gilt — aus dieser Sandbox nicht ausführbar (keine
IMAP/SMTP/Ollama-Zugangsdaten hier, Guardrail 2), Prüfung am Mission-Control-Host nötig (Details
in der Session-Agenda). Alle Änderungen committet, `preflight.py` meldet STARTKLAR,
`PUSH-ANFORDERUNG.txt` für den nächsten Wächter-Lauf geschrieben.

---

**Das Team ist im Regelbetrieb — kein aktives Projekt.** *(Stand 2026-08-16 10:12: **zehn** abgeschlossene Projekte — P10 „Aufgaben bearbeiten im HMI" wurde heute um 10:02 mit G4a/D002 abgenommen, Baseline `p10-v1.0`. **263 Tests, Matrix 87 SWRs / 0 Lücken, 0,00 € API.** Die Tabelle unten zeigt den historischen Stand bis P3.)* Bilanz: **4 abgeschlossene Projekte**, 1 released Produkt, 153 + 42 grüne Tests, Matrix 47 SWRs / 0 Lücken, 4 Konsistenz-Gates in abschluss.cmd (Tests, Matrix, Katalog, Architekturbild), **0,00 € API** über alles.

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

---

**⚠ BEFUND pm/T-0024 (Routine-Session 10:23, B038) — bitte zuerst lesen: Zwei Stunden lang ging nichts mehr nach GitHub, und aufgefallen ist es dir, nicht uns.** Dein Brief `pm/N-0021` fragte, warum beim pm ein paar Tasks „seit längerem in review" stehen. Nachgesehen — und der Grund lag nicht bei den Tickets. `pm/T-0010` und `pm/T-0013` warten beide darauf, dass ein **GitHub-Actions-Lauf** ihren Fix bestätigt. Genau der konnte seit **09:44** nicht mehr stattfinden: Der Auto-Push-Wächter brach dreimal in Folge ab (09:44, 09:59, 10:14), letzter erfolgreicher Push war **08:30**. Liegengeblieben waren **21 Commits** und die beiden Baseline-Tags **`p10-v1.0`** — die Abnahme des zehnten Projekts, die du um 10:02 per Knopf erteilt hast, existierte auf GitHub nicht. Die zwei Tickets warteten also nicht auf sich selbst, sondern auf ein Ereignis, das unmöglich geworden war.

**Die Ursache ist ein Umlaut, und das ist kein Scherz.** Der Preflight fragt vor dem Aufräumen von Git-Sperren nach, ob gerade ein Git-Prozess läuft — auf Windows über `tasklist`. Dessen Antwort kommt in der alten Konsolen-Codepage, Python las sie in einer anderen. Läuft **kein** git.exe — der Regelfall —, lautet die deutsche Antwort „… mit den angegebenen Kriterien **ausgeführt**."; das `ü` darin ist genau das Byte, an dem das Lesen zerbricht. Der Fehler fiel in einen vorsorglichen Auffang-Zweig, der im Zweifel „es läuft ein Git" annimmt. Die Abfrage meldete also **ausgerechnet dann „besetzt", wenn nichts los war** — und im Protokoll stand nur `NICHT entfernt (Git-Prozess aktiv)`, was sich wie eine korrekte Beobachtung liest. Ein zugehöriger Test wurde dadurch rot, `abschluss.cmd` bricht bei rotem Test ab, und damit stand die ganze Kette. Der zweite, gleichwertige Fehler steckte im Test selbst: Er prüft ein Wegwerf-Repo im Temp-Ordner, fragte dafür aber den **gesamten Rechner** nach Git-Prozessen ab — ein Commit aus dem HMI hätte ihn ebenso rot gemacht. Beides behoben, **4 neue Tests**, Gegenprobe gegen den alten Code (2 scheitern dort nachweislich), und der Abbruch von 10:14 exakt nachgestellt. **267 Tests, Matrix 87/0, 0,00 € API.** Preflight ist Prozess-Tooling — kein neuer SWR.

**Was uns daran mehr beschäftigt als der Bug:** Nicht die Automatik hat gemeldet, dass sie steht — **du hast dich über zwei Tickets gewundert.** Der Wächter schreibt seine Fehlschläge ausschließlich in `abschluss-auto.log`, und eine Logdatei liest ohne Anlass niemand. Nach außen sah alles normal aus: Sessions liefen, committeten, meldeten STARTKLAR. Als CR-Kandidat vermerkt: Warnmail nach dem n-ten Fehlversuch des Wächters — die Mail-Strecke gibt es seit SWR-033 bereits. **Bewusst nicht nebenbei gebaut**, weil eine Mail Außenwirkung hat und nicht in einen SUP.9-Fix gehört.

**⚠ Und dein dritter Brief hat einen zweiten Befund aufgedeckt, den der erste verdeckt hielt (`platform/N-0006` → `pm/T-0026`, B042).** Du meldetest einen roten CI-Lauf zu dem Commit, der den Codepage-Fix trägt. **Nicht der Commit ist schuld.** Nachgestellt in zwei Umgebungen, die den CI-Checkout nachbauen: mit `projects` **87 Anforderungen / 0 Lücken**, mit exakt der Repo-Liste aus `ci.yml` **82 / 5 Lücken → rot**. Die Unit-Tests sind in beiden Fällen grün. Gescheitert ist das **Matrix-Gate**: `ci.yml` checkt zwölf Repos aus, **`projects` kommt darin null mal vor** — seit dem Monorepo-Beschluss liegen Projekte aber als Ordner darin, und P10 hat dort fünf Anforderungen. Genau die fünf fehlen dem Runner. **Rot ist der Workflow seit der P10-Freigabe um 08:18 — gesehen hat es niemand, weil bis 10:30 kein Push durchkam.** Zwei Fehler desselben Vormittags, von denen der eine den anderen unsichtbar machte. Behoben (Checkout ergänzt); es ist dieselbe Lehre wie heute Vormittag bei `p9/T-0007`, nur war die letzte Kopie der Regel diesmal kein Python-Code, sondern eine YAML-Datei — die damalige Suche lief über den Quelltext und konnte Workflows gar nicht finden.

**Eine Handlung von dir, sonst wandert der Fehler nur:** Das Secret **`P0_READ_TOKEN`** muss **`DiOflOrds/projects`** einschließen. Fehlt es dort, scheitert künftig der Checkout-Schritt statt des Matrix-Schritts. Unter *github.com/settings/personal-access-tokens* den bestehenden PAT öffnen und `projects` zur Repo-Auswahl hinzufügen. (Nicht verwechseln mit `PLATFORM_READ_TOKEN` in `DiOflOrds/projects` — Gegenrichtung, liegt bereits vor.)

**Der Fix hat am echten System gewirkt:** Der Wächter-Lauf um **10:29 ist durchgelaufen** (`OK - alles geprueft und gepusht`, 10:30:17) — die 21 Commits und die Tags `p10-v1.0` sind draußen. Das ist der Nachweis am laufenden System, nicht im Test; genau die Prüffrage aus `pm/T-0023` („ist der nächste echte Arbeitsschritt danach noch möglich?").

**`pm/T-0010` und `pm/T-0013` bleiben `in_review`** — mit Vermerk, warum sie standen. Sie auf `done` zu setzen wäre die bequeme Antwort auf deinen Brief gewesen und genau der Fehler, den wir gestern als Lehre notiert haben: Ein Nachweis, der nicht geführt wurde, wird nicht dadurch geführt, dass jemand nachfragt. **Deine Stichprobe:** Nach dem nächsten Wächter-Lauf (alle 15 Min) ist `PUSH-ANFORDERUNG.txt` im Wurzelordner **verschwunden**, in `abschluss-auto.log` steht `OK - alles geprueft und gepusht`, und auf GitHub sind die Tags `p10-v1.0` da. Sind die board-check-Actions danach grün, schließen die beiden Tickets ohne weiteres Zutun.

**Dein zweiter Brief war ein echter Fehler, kein Wunsch (`team-mail/N-0002` → `team-mail/T-0003`, B040/B041).** Du wolltest beim „Jetzt zusammenfassen" dieselben Einstellungen wie gespeichert. Von deinen zwei Punkten war nur einer ein Fehler — dafür ein handfester: **Der Knopf lief fest auf einen Tag, obwohl bei dir `takte: [7]`, also wöchentlich, eingestellt ist.** Jeder Klick erzeugte damit einen Tages- statt des bestellten Wochen-Digests. Es gab keine Fehlermeldung, nichts stand rot — der einzige Hinweis war der Dateiname (`-tag-` statt `-woche-`). Behoben: Der Knopf läuft jetzt über **alle** gespeicherten Takte, mit Regressionstest und Gegenprobe gegen den alten Code. Kein neuer SWR — SWR-063 war nie auf einen Tag festgelegt, das war eine stille Annahme der ersten Umsetzung. **Der KI-Zusatztext hat dagegen immer gewirkt**, du konntest es nur nirgends sehen; genau das ist auch der Grund, warum der Takt-Fehler so lange lief. Beides bekommt deshalb eine Klartextzeile am Knopf (`pm/T-0025`). **Deine Stichprobe:** Server neu starten, klicken — es muss eine `-woche-digest.md` entstehen.

**Ein Vorfall in eigener Sache, der dich nichts gekostet hat, aber fast (B041):** An diesem Brief haben **zwei Routine-Sessions gleichzeitig** gearbeitet — die Überlappung, vor der die Agenda seit heute früh warnt. Sie sah anders aus als erwartet: nicht als blockierendes Git-Lock, sondern als fremde Änderung an einer Datei, die diese Session nur gelesen hatte. Die parallele Session hatte den **besseren** Befund (sie las deinen Satz wörtlich als „nimm die Konfiguration", diese Session hatte ein Auswahlmenü daraus gemacht) — und zog ihre Arbeit dann selbst zurück, weil sie den Konflikt bemerkte. Übrig geblieben wäre eine Antwort an dich, die auf ein Ticket verweist, das nicht mehr existiert, und ein richtiger Befund, der spurlos verschwindet. Gefunden wurde es nur, weil der Board-Check plötzlich **2 statt 3 Tickets** meldete. Der Befund ist neu geführt, geprüft und mit Herkunftsvermerk verbucht; drei neue Regeln stehen in der Agenda.

**`pm/T-0022` (Anlegen/Starten im Projekt-Pool) blieb in dieser Session liegen (B039)** — Reihenfolge, nicht Zeitmangel: Solange nichts nach außen geht, erzeugt jede Feature-Session Arbeit, die auf GitHub nicht existiert; genau das hat heute früh schon einmal eine komplette Session gekostet. Erst der Weg nach außen, dann neue Fläche. Der Punkt steht unverändert oben auf der Agenda. **Auf deine A/B-Rückfrage liegt weiterhin keine Antwort vor** — es bleibt bei der Ankündigung: ohne Antwort bauen wir **A**.

---

## Warten auf Auftraggeber

**✔ P10 IST ABGENOMMEN — G4a/D002 am 2026-08-16 um 10:02 von dir per Inbox-Knopf entschieden, Baseline `p10-v1.0` auf `projects` und `platform`.** Damit ist P10 das **zehnte abgeschlossene Projekt** und das erste, das vollständig als Ordner im Sammel-Repo `projects` gelaufen ist. Bemerkenswert am Ablauf: Deine Entscheidung fiel **14 Sekunden** nach dem Commit, mit dem der Sprint fertig wurde — Lieferung, Antrag, Knopfdruck und Abnahme lagen zum ersten Mal in einer einzigen Session. Verbucht sind `p10/T-0003` und `p10/T-0004`, der Abschlussbericht liegt in `projects/p10/management/p10-abschlussbericht.md`. **Deine sieben Stichproben aus `p10/T-0004` stehen weiterhin offen** — sie sind Betriebsnachweis und werden nicht vom Team abgehakt (Serverneustart vorher).

**Dein Brief `platform/N-0004` ist beantwortet — mit einer Rückfrage, die du in einem Wort beantworten kannst.** Du willst den „Anlegen/Starten"-Knopf im Projekt-Pool. Der war exakt bis heute 10:02 blockiert, weil er den geprüften Schreibpfad brauchte, den P10 gerade geliefert hat — er steht jetzt oben auf der Agenda (`pm/T-0022`). Vorher eine Klasse-A-Frage: **„Starten" ist eine Projektbeauftragung.** Variante **A** (Empfehlung): Der Knopf legt den Projektordner an und stellt dir einen G0-Entscheidungsantrag in die Inbox — zwei Klicks, dafür bleibt der Auftrag eine bewusste Entscheidung mit Begründung im Log. Variante **B**: Der Knopfdruck *ist* die Entscheidung, mit deinem Namen und Decision-Log-Zeile — nicht regelwidrig (deine Inbox-Buttons sind seit P3 genau das), nur endgültiger. **Antworte einfach „A" oder „B" im Team-Chat; ohne Antwort bauen wir A.**

*Historie (erledigt): `p10/T-0004` — G4-Abnahme von P10.* Sprint 1 ist gebaut: **Aufgaben lassen sich jetzt im HMI bearbeiten.** Deine beiden Briefe (pm/N-0013 „mehrfach labeln, als Bug/CR markieren", pm/N-0014 „ich würde gerne alle offenen tasks editieren können") sind damit umgesetzt. Titel, Typ, Priorität, Rolle, Sprint, Takt, Status, Reviewer, Frist und Fließtext ändern; beliebig viele frei gewählte Labels vergeben und im Board danach filtern. Jede Änderung wird sofort committet („Mensch via HMI"), `BOARD.md` zieht im selben Commit mit, und im Ticket steht eine Historienzeile — lesbar auch ohne Terminal, also auch am Handy. Nicht dabei, wie besprochen: Tickets anlegen oder löschen (Nummernvergabe), und erledigte Tickets ändern (nur Wiedereröffnung). **263 Tests, Matrix 87/0, 0,00 € API**, ~115 min gegen 120 min geschätzt. **Die Baseline `p10-v1.0` ist bewusst nicht gesetzt** — eine Abnahme ist Klasse A, das Team taggt nichts vorab.

**Der interessante Teil war nicht das Formular, sondern wo die Regeln leben.** Ein Editor im HMI ist ein *zweiter* Weg, Tickets zu schreiben — neben der Skript-Route, die die Sessions benutzen. Der bequeme Bau wäre gewesen, im Server „schnell" zu prüfen, ob eine Eingabe gültig ist. Damit hätte es zwei Regelwerke gegeben, die ab dem ersten Tag auseinanderlaufen — genau das Risiko, das im Sprint-0-Plan als R2 steht, und genau der Fehler, der heute Vormittag zweimal Befund war (dieselbe Pfadauflösung an vier Stellen). Deshalb liegt der Schreibpfad **in `board.py` selbst**; das Backend ist reine Fassade. Beim Hinschauen fiel auf, dass die Falle schon einmal zugeschnappt war: Die Zeitstempel-Formatierung aus deinem Uhrzeit-Wunsch (SWR-084) hätte für die Änderungshistorie ein zweites Mal entstehen müssen — `inbox` delegiert jetzt an `board.zeitpunkt`, eine Quelle für beides.

**Konflikte mit der Routine-Session (dein Punkt aus pm/T-0011) werden erkannt, nicht verhindert.** Vor jedem Schreiben prüft das HMI über einen Inhalts-Fingerabdruck, ob die Datei noch die ist, aus der dein Formular geladen wurde. Wenn nicht, wird **nicht** geschrieben, sondern in Klartext gemeldet und das Neuladen angeboten. Bewusst kein Dateisperren-Mechanismus: Auf einem Mount, auf dem sich Dateien nicht löschen lassen — genau das Problem von heute Vormittag —, wäre eine liegengebliebene Sperre schlimmer als der Konflikt, den sie verhindern soll. Nachgestellt ist der Fall in einem Test, in dem die Skript-Route zwischen Laden und Speichern tatsächlich dazwischenschreibt.

**Zwei Punkte im Antrag, denen du widersprechen kannst:** (1) **Labels stehen nicht im generierten `BOARD.md`**, nur im HMI — eine neue Board-Spalte ist eine Formatänderung, und genau die hat heute früh sämtliche `board-check`-Workflows rot gemacht; sie gehört gebündelt mit `pm/T-0013`. (2) **`frist` ist mit-editierbar**, obwohl der Auftrag sie nicht nannte — sonst zwänge jede Terminverschiebung zurück in die Skript-Route; jede Verschiebung steht sichtbar in Historie und Commit. Beides ist im DR benannt, damit es dir nicht später auffällt statt jetzt.

**Deine Stichproben (Server vorher neu starten), sieben Stück im Ticket:** Ticket bearbeiten und speichern · unerlaubten Status setzen → deutsche Ablehnung · zwei Labels vergeben und im Board danach filtern · `git -C projects log --oneline -3` → „Änderung via HMI" mit BOARD.md im selben Commit · Konflikt erzwingen (Ticket am Handy offen lassen, vom Rechner speichern, dann am Handy) · vom Handy ohne PIN speichern → Ablehnung, mit PIN → geht · erledigtes Ticket öffnen → nur „Wiedereröffnen", kein Formular.

**Ein Ablauffehler in eigener Sache, der dich betrifft (B036):** Dein Brief kam um 10:04 herein — mitten in der Session. Der Pflichtpunkt „Briefkasten zuerst" hatte kurz vorher sauber „keine offenen Briefe" gemeldet, und danach schaut bisher niemand mehr hin. Aufgefallen ist der Brief nur zufällig, weil beim Setzen der Baseline ein fremder Commit im `platform`-Log stand. Dasselbe galt für deine Entscheidung. Folgerung, ab sofort in der Agenda: **Briefkasten und Inbox werden vor dem Abschluss ein zweites Mal geprüft** — eine Session dauert länger, als der Blick an ihrem Anfang gültig ist. Praktisch hättest du nichts gemerkt (der Takt sind 30 Minuten), aber es war Glück und nicht Verfahren.

---

**⚠ BEFUND pm/T-0023 (Routine-Session 09:26, B031) — bitte zuerst lesen: Die Arbeit der letzten Session war fertig und stand nicht in Git.** Die 08:37-Session hat B028/B029/B030 vollständig geliefert, den Statusbericht geschrieben, die Agenda fortgeschrieben — und **nichts davon committet**. Ursache: In **allen 15 Repos** lag ein 0 Byte großer `.git/index.lock`. Git legt den vor jeder Index-Operation an und löscht ihn danach; auf dem Cowork-Mount deines Ordners schlägt genau dieses Löschen fehl (`unable to unlink … Operation not permitted`). Der Lock bleibt liegen — und **jeder weitere Commit im Repo bricht ab**. Ein harmloses `git status` wird so zur Sperre. Bitter daran: `preflight.py` hat das vollständig richtig erkannt und gemeldet, aber nur auf eine Handlung von dir am Host verwiesen. Die Session konnte lesen, dass sie blockiert ist, und hatte kein Mittel dagegen — 45 Minuten geprüfte Arbeit hingen an einer leeren Datei.

**Was diese Session getan hat.** Erstens: die liegengebliebene Arbeit **gegen die Werkzeuge verifiziert, nicht gegen ihre eigene Beschreibung** (223 Tests grün, Matrix 87 SWRs / 0 Lücken, Katalog und Architekturbild konsistent) und erst dann in fünf Commits nachverbucht — die Lehre aus B025 sagt, dass ein Dokument, das etwas behauptet, kein Beweis ist. Zweitens die Ursache im Werkzeug behoben: Auf diesem Mount ist `rename` erlaubt, nur `remove` nicht — und für Git ist ein Lock, der anders heißt, ebenso weg. `preflight.py` löscht jetzt erst, und wo das verboten ist, **räumt es das Artefakt nach `.git/verwaiste-locks/` weg**. Geparkt zählt bewusst **nicht** als Befund: Git ist entsperrt, die Session kann arbeiten. 7 Regressionstests, die `os.remove` abschalten und gegen den alten Code nachweislich scheitern. Preflight ist Prozess-Tooling (CR T-0024) — kein neuer SWR. **230 Tests, Matrix 87/0, 0,00 € API.**

**Der erste Fix war unvollständig — und das ist der interessantere Teil.** Der Commit direkt nach einem grünen Preflight-Lauf scheiterte wieder mit derselben Meldung. Git legt bei *jedem* Aufruf einen `index.lock` an, auch bei einem lesenden `git status`; Preflight ruft `git status` je Repo auf. Es räumte also am Anfang alles weg, erzeugte durch seine eigenen Prüfungen neue Sperren und meldete darüber STARTKLAR — ein Werkzeug, das aufräumt und beim Hinausgehen die Tür wieder zusperrt. Die Räumung läuft jetzt **zweimal** je Lauf (am Anfang und als Schlusslauf nach allen Prüfungen), dazu `--nur-locks` zum schnellen Entsperren vor einem einzelnen Schreibvorgang. Aufgefallen ist das nur, weil der Nachweis am echten System geführt wurde und nicht bei grünen Unit-Tests aufgehört hat — die Lehre steht in `pm/T-0023`.

**Eine Handlung von dir (keine Entscheidung):** Der Cowork-Session fehlt auf `Downloads\aspice-team-repos-final` das Recht, Dateien zu **löschen**. Der Fallback macht das Team arbeitsfähig, räumt die Ursache aber nicht aus der Welt — es sammeln sich weiter unlöschbare `.git\objects\**\tmp_obj_*` an (harmlos, aber sie wachsen). Sauber wird es erst mit erteiltem Lösch-Recht; bis dahin gelegentlich `.git\verwaiste-locks\` und die `tmp_obj_*` auf dem Host aufräumen. In Runbook Kap. 5 (Störung R7) vermerkt. **Deine Stichprobe:** `python platform\scripts\preflight.py --repos .` → STARTKLAR; danach schauen, ob `.git\verwaiste-locks\` existiert — wenn ja, hat der Fallback gearbeitet.

**P10 Sprint 1 wurde in der 09:26-Session bewusst nicht angefangen (B032)** — er war der Hauptpunkt der Agenda, die Zeit ging vollständig in den Lock-Befund. *Nachtrag 10:05: in der Folgesession geliefert (B033), siehe oben; der Lock-Fallback aus `pm/T-0023` hat dabei in allen 15 Repos gearbeitet — ohne ihn wäre auch diese Session blockiert gewesen.*

---

**Drei Briefe beantwortet und umgesetzt (Vorsession, B028/B029/B030 — jetzt verbucht) — 223 Tests, Matrix 87/0, 0,00 € API.**

- **`pm/N-0019` — Requirements sind nicht mehr auf ein Projekt beschränkt** (SWR-085, `pm/T-0019`): Der Reiter zeigt jetzt standardmäßig **alle 22 Dokumente aus 13 Projekten/Teams** und filtert nach Projekt/Team, Gruppe und Volltext, mit Zähler „n von m aus k". Die Ansicht war seit P1 gescopt (SWR-030) — bei zwei Projekten unauffällig, bei dreizehn ein Fehler: Sie sah vollständig aus und war es nie. Die Gruppen kommen aus derselben Einstufung wie Cockpit und Kopfbereich (SWR-082), die gescopte Einzelabfrage hält ein Regressionstest fest.
- **`pm/N-0020` — Projekt-Pool ist im HMI sichtbar, und der Grund für sein Fehlen ist unangenehm** (SWR-086, `pm/T-0020`): `pm/D005` sagte den Pool-Bereich „als CR T-0011" zu; `pm/T-0011` trägt seit demselben Tag den P10-Entscheidungsantrag. Die Nummer war vergeben, bevor das Ticket existierte — **kein Vorgang hat die Zusage getragen**, und es fiel niemandem auf, weil es nichts Offenes gab, das hätte auffallen können. Geliefert ist **Teil 1 „Anzeigen"**: eigener Reiter neben dem Cockpit mit deinen 5 Team- und 7 Technik-Kandidaten, direkt aus `pm/management/projekt-pool.md`. **Teil 2 „Anlegen/Starten" ist bewusst zurückgestellt** (`pm/T-0022`) — beides sind Schreibvorgänge, und der erste geprüfte Schreibpfad entsteht gerade in P10 Sprint 1; ihn hier vorab ein zweites Mal zu bauen wäre genau die Doppelung, die heute zweimal Befund war. Der Reiter sagt das im Kopf offen. Neue Regel: **eine Ticketnummer in einem Beschluss ist keine Beauftragung.**
- **`platform/N-0003` — jede Aufgabe trägt jetzt ihre eindeutige Kennung `<projekt>/T-xxxx`** (SWR-087, `pm/T-0021`): Ticketnummern sind nur je Repo eindeutig (`T-0002` gibt es in pm, p2, p3, p4, p9, p10); Inbox und Historie zeigten das Repo mit, Board, Ticket-Detail und Cockpit nicht. Gebildet wird die Kennung an **einer** Stelle im Server und von allen sechs Ansichten benutzt. **Nicht getan — und du kannst widersprechen:** Die Ticketdateien behalten ihre Nummern. Eine echte Umnummerierung würde jede Decision-Log-Zeile, jeden Brief, jeden Report und die Git-Historie falsch machen oder das Umschreiben von Vergangenem erzwingen (Kap. 16 schließt das aus); dazu hat heute Morgen schon eine Formatänderung am generierten BOARD.md alle board-check-Workflows rot gemacht. Willst du wirklich durchlaufende Nummern, legen wir das als Entscheidung mit Optionen vor, statt es nebenbei zu machen.

**Deine Stichproben (Server vorher neu starten):** Requirements-Reiter ohne Projektwahl öffnen → alles da, Filter auf `p10` greift · Reiter „Projekt-Pool" → beide Kategorien · Board von `pm` zeigt `pm/T-0019`, Board von `p10` zeigt `p10/T-0001`.

**P8 „Mail-Autopilot" ist ABGESCHLOSSEN (G4a/D002, 2026-08-16), Baseline `p8-v1.0`** (p8 + platform) — team-mail verdichtet per lokalem Ollama, Mehrfach-Takt, Sofort-Knopf, `--auto` in der Aufgabenplanung. **Acht Projekte abgeschlossen.** 171+42 Tests, Matrix 65/0, 0,00 € API.

**BUGFIX (N-0006/pm-T-0009, SUP.9):** Auto-Push scheiterte seit 15.08. 17:36 an einem cmd-Klammern-Fehler in abschluss.cmd (:repo_push) — **behoben**; Erfolgsnachweis: PUSH-ANFORDERUNG.txt verschwindet beim nächsten Wächter-Lauf. Voraussetzung: GitHub-Repos **p7 + p8** existieren (+ Secret, PAT). Lesson L-2026-08-16 verankert.

**P9 „Org-Cockpit" ist ABGESCHLOSSEN (G4a/D002, 2026-08-16), Baseline `p9-v1.0`** (p9 + platform). Cockpit gruppiert: Feste Teams (ASPICE + PM) / Projekt-Teams / aktiv / abgeschlossen (eingeklappt, automatisch über Baselines erkannt), jede Karte mit Beschreibung (13 Steckbriefe, SWR-069), Status-Pille und offenen Aufgaben; **projects-Sammelrepo wird entdeckt** (SWR-070) — P10 ist nur noch ein Ordner. **Neun Projekte abgeschlossen.** Vor der Stichprobe: Server per ⟳ neu starten; die drei Cockpit-Stichproben aus `p9/T-0004` stehen als Betriebs-Nachweis noch offen (werden nicht vom Team abgehakt).

**Betriebs-CRs T-0006/T-0007 ERLEDIGT (Routine-Session, PM-Beschluss B010):** Der Konfigurator bietet jetzt die **Ollama-Modellwahl** (Liste live vom lokalen Ollama, „automatisch" bleibt Default, aktives Modell wird angezeigt — SWR-071) und ein **KI-Hinweisfeld** (freier Zusatz-Auftrag an die KI, z. B. „achte auf Bewerbungen"; ergänzt den Prompt, ersetzt die feste Digest-Struktur nie — SWR-072). Umsetzung als p8/T-0009 + p8/T-0010 auf der P8-Fläche, **ohne neue Projekt-Baseline**. **181 Tests, Matrix 73/0, 0,00 € API.** Deine Stichprobe: Modell wählen, Hinweis eintragen, speichern, „Jetzt zusammenfassen" — und den Digest inhaltlich bewerten.

**Briefe N-0010/N-0011 beantwortet und erledigt (B013):** Mission Control **startet sich jetzt selbst neu**, wenn eine Session neuen Code auf die Platte legt (SWR-073, p7/T-0016) — abgesichert dreifach: nur mit Startskript (`mission-control[-lan].cmd`), nur bei Ruhe (kein Abbruch mitten in Entscheidung oder Digest-Lauf) und entprellt gegen Neustart-Flattern; die Seite lädt sich danach von allein nach. Zum Status-Wunsch: `in_progress` **existierte bereits** (open → in_analysis → in_progress → in_review → done, eigene Board-Spalte, erzwungene Übergänge) — der echte Befund war die Sichtbarkeit, deshalb neue Playbook-Regel (Kap. 5): `in_progress` wird beim Arbeitsbeginn gesetzt, nicht am Ende nachgezogen. **181 Tests, Matrix 73/0.** Deine Stichprobe: Server einmal manuell neu starten, damit die neue Fassung läuft.

**Brief N-0012 beantwortet und umgesetzt (B014):** Tickets tragen jetzt ein Feld `takt` — das Board hat eine **Takt-Spalte** (einmalige Aufgaben stehen ausdrücklich als „einmalig"), zählt „davon wiederkehrend: n", Board-Karte und Ticket-Detail markieren Daueraufgaben im Klartext, das Cockpit zeigt „Offen (n, davon m wiederkehrend)" (SWR-074, p9/T-0006). Damit ist sichtbar, dass Takt-Tickets absichtlich dauerhaft offen sind und nicht liegengeblieben. **185 Tests, Matrix 74/0.**

**Briefe N-0013/N-0014 zweigeteilt (B015):** Sofort erledigt — **erledigte Aufgaben, die älter als ein Tag sind, verschwinden aus dem Board** (Schalter in der Filterzeile holt sie zurück; BOARD.md bleibt vollständiges Archiv; SWR-075). Der Rest (Mehrfach-Labels, Typ selbst setzen, **offene Tickets editieren**) hängt am ersten Ticket-Schreibpfad neben der Skript-Route und liegt deshalb **als Klasse-A-Entscheidung in deiner Inbox: `pm/T-0011` „P10 Aufgaben bearbeiten im HMI"** — drei Zuschnitte, Frist 23.08., Default P10a; Umsetzung wäre der erste Vollzug des Monorepo-Beschlusses (Ordner in `projects`, kein neues GitHub-Repo). **187 Tests, Matrix 75/0.**

**P10 „Aufgaben bearbeiten im HMI" ist BEAUFTRAGT (D005/P10a, 2026-08-16 via Inbox).** Umfang: Ticket-Editor im HMI für offene Tickets, freie Mehrfach-Labels mit Team-/Projekt-Zuordnung und Board-Filter, Typ selbst setzen — inklusive Konflikterkennung gegen die parallel laufende Routine-Session. **Umsetzung als Ordner `projects/p10`** — erster Vollzug des Monorepo-Beschlusses D003, kein neues GitHub-Repo. Der Intake nach `intake.md` v3 ist der erste Arbeitspunkt der nächsten Routine-Session (B016).

**P10-INTAKE VOLLZOGEN (Routine-Session, B018) — `projects/p10` steht.** Erster Projektordner im Sammel-Repo (D003 in der Praxis, du legst kein Repo an): Projektauftrag mit Abnahmekriterien und ausdrücklicher Abgrenzung, **STK-020**, **SWR-077–081** (Editor mit `board.py`-Validierung · Sofort-Commit „Mensch via HMI" inkl. BOARD.md · freie Mehrfach-Labels mit Board-Filter · Konflikterkennung per Fingerprint gegen die 30-Minuten-Session · PIN-Gate + Änderungshistorie), Sprint-0-Plan mit Risiken, Decision-Log D000, board-check-Workflow für das Sammel-Repo. **Die SWRs stehen bewusst auf `draft` bis zu deiner G1-Freigabe.** → **In deiner Inbox: `p10/T-0002` (G1, Frist 23.08., Default G1a)** — darin zwei echte Rückfragen: „neues Projekt" als **Label** statt Ticket-Typ (weil ein Projekt über den Intake-Weg entsteht, nicht per Ticket-Typ), und Tickets im HMI **anlegen/löschen** haben wir außen vor gelassen (Nummernvergabe) — sag Bescheid, wenn du es drin haben willst.

**BEFUND p9/T-0007 (SUP.9) — gefunden und behoben, bevor er weh tat:** Das erste verschachtelte Projekt deckte auf, dass `preflight.py` (Board-Check-Runde, Briefkasten-Prüfung) und `trace_matrix.py` (SWR-Quellen) weiterhin nur Top-Level-Ordner sahen — `projects/p10` wäre **still an zwei Konsistenz-Gates vorbeigelaufen** (kaputte Tickets unbemerkt, Anforderungen nie im Lücken-Gate). Ursache: drei Kopien derselben Discovery-Logik, SWR-070 war nur in `aggregation.py` umgesetzt. Jetzt eine gemeinsame Auflösung (`board.projekt_pfade`), von Preflight und Matrix genutzt. **194 Tests, Matrix 81 SWRs / 0 Lücken, 0,00 € API.** Lesson im Playbook-Umlauf: Eine Anforderung „Werkzeuge sollen X unterstützen" ist erst erfüllt, wenn jede Kopie der Logik nachgezogen ist.

**Zwei Briefe während der Session beantwortet und erledigt (B020):** `pm/N-0017` — im Cockpit fehlte die Klartext-Markierung wiederkehrender Aufgaben (dort stand nur ein „↻" ohne Legende, auf dem Handy nicht einmal der Tooltip); jetzt dieselbe Pille wie im Board (pm/T-0014, Erfüllung von SWR-074, kein neuer SWR). `platform/N-0001` — der rote board-check ist **nicht** die Dublette von pm/T-0010: Projekt-Workflows checken `platform@main` von GitHub aus und erzeugen BOARD.md damit neu, `abschluss.cmd` pushte aber alphabetisch, also **p0–p9 vor platform** → altes Werkzeug gegen neues Board-Format (Takt-Spalte) → rot. `abschluss.cmd` pusht jetzt **platform/process zuerst** (pm/T-0013). Erfolgsnachweis: `pushe platform ...` steht als erste Zeile im nächsten Wächter-Lauf, danach grüne Actions — bis dahin bleibt T-0013 `in_review`. CR-Kandidat für später: Projekte checken platform auf einem **Tag** statt `main` aus, dann ist die Werkzeugversion explizit.

**Nichts weiter nötig (bestätigt 2026-08-16):** Das Secret **PLATFORM_READ_TOKEN** liegt im Repo `DiOflOrds/projects` bereits vor — der neue Board-Check für das Sammel-Repo läuft ohne weiteres Zutun. Lokal prüft der Preflight ohnehin mit.

**Briefe N-0015/N-0016:** Der Inbox-Reiter zeigt jetzt die **Zahl der auf dich wartenden Entscheidungen** und ist hervorgehoben (SWR-076, B017 — sofort umgesetzt). Der Kopfbereich soll nur noch aktive Projekte/Teams anklickbar zeigen (N-0015): eingeplant als `pm/T-0012` für die nächste Session — bewusst nicht im Schnellschuss, weil dort die Hash-Navigation und deine Deep-Links hängen; abgeschlossene Projekte bleiben unter „weitere" erreichbar. **188 Tests, Matrix 76/0.**

**`pm/T-0012` ERLEDIGT (Routine-Session, B021) — der Kopfbereich zeigt jetzt nur noch aktive Projekte/Teams, direkt anklickbar** (N-0015). Statt der Auswahlliste über alle entdeckten Repos stehen oben anklickbare Einträge in den Gruppen des Cockpits (Feste Teams · Projekt-Teams · Aktive Projekte), der aktuelle Eintrag hervorgehoben; die zehn abgeschlossenen Projekte liegen hinter **„weitere (10)"** und klappen von allein auf, wenn ein Deep-Link auf eines von ihnen zeigt — Boards, Berichte und Entscheidungslogs von p0–p9 bleiben erreichbar. Kern ist eine **gemeinsame serverseitige Einstufung** (`aggregation.einstufung`), die Cockpit und der neue Endpunkt `/api/navigation` teilen: Kopf und Cockpit können nicht mehr auseinanderlaufen — bewusst so gebaut nach der Lesson vom Vormittag (jede Kopie derselben Logik ist ein künftiger Befund). Deep-Links (`#/board/p3`) unverändert, SWR-082 auf der P9-Fläche (v1.3). **199 Tests, Matrix 82/0, 0,00 € API.** Deine Stichprobe: Server neu starten, oben klicken, einen Deep-Link auf ein abgeschlossenes Projekt öffnen — auch auf dem Handy.

Sonst: Pilotreview team-mail 29.08., BB-5 PAT ab 5.9.; `pm/T-0010` (board-check-Flake) bleibt `in_review`, bis ein GitHub-Actions-Lauf nach dem Fix grün ist.

## Betriebs-Backlog

**BB-5** PAT-Erneuerung ab 2026-09-05 (Runbook Kap. 4/7) — sonst leer. CR-Kandidaten: **Warnmail, wenn der Auto-Push-Wächter mehrfach hintereinander scheitert** (aus B038 — heute zwei Stunden unbemerkter Stillstand, Mail-Strecke aus SWR-033 vorhanden; nicht nebenbei gebaut, weil Mailversand Außenwirkung ist), Live-API-Chat mit Budgetfreigabe, „Briefkasten zuerst" ins Playbook, JS-Tests (P3-R1), Produkt-Architekturbilder (P3-R2), Schätz-Kalibrierung (P2-R1).

## Offene Fragen

Keine — F1–F17 vollständig entschieden; Decision Logs: p0 D000–D027, p1 D000–D009, p2 D000–D004, p3 D000–D004, p4 D000–D003.

## Referenzen

Repos: github.com/DiOflOrds/{process,platform,p0,produkt-datakonv,p1,p2,p3,p4,p5} · Baselines: **genesis-v1.0**, datakonv v1.0.0/req-v1.1, **p1-v1.0**, **p2-v1.0**, **p3-v1.0** · **Abschlussberichte:** `p0/management/p0-abschlussbericht.md`, `p1/…/p1-abschlussbericht.md`, `p2/…/p2-abschlussbericht.md`, `p3/…/p3-abschlussbericht.md` · Runbook + Betriebs-Backlog: `process/cm/runbook.md` · Intake: `process/process/intake.md`

**P10 IST FREIGEGEBEN — G1a/D001 am 2026-08-16 08:18 (via Inbox), verbucht (B026/B027).** Damit ist der Befund aus `pm/T-0017` auch praktisch bestätigt: Der Antrag war nach dem Fix sichtbar und entscheidbar. **Deinem Wunsch entsprechend tragen Entscheidungen ab jetzt Datum *und* Uhrzeit** (SWR-084, `pm/T-0018`, P2-Fläche v1.1) — in der Decision-Log-Zeile und im Ticket-Vermerk, beide aus einem Zeitwert, damit sie nicht über einen Minutenwechsel auseinanderlaufen; das HMI zeigt es ohne eigene Änderung mit. Für die P10-Freigabe wurde die Uhrzeit **nachgetragen: 08:18** — nicht geschätzt, sondern der Zeitstempel des Commits `cfab77c`, mit Herkunftsvermerk im Log und im Ticket; der Entscheidungsinhalt blieb unangetastet. Nicht geändert: `frist`/`erstellt`/`geändert` bleiben reine Datumsfelder (Fristen gelten tagesgenau, `board.py` validiert dort ein Datumsmuster). **Eine Abweichung, der du widersprechen kannst (B027):** Der Intake hatte zugesagt, SWR-077–081 gingen mit G1 auf `reviewed`. Das habe ich **nicht** getan — die Matrix hätte sie mangels Tests als „manuelle Abnahme dokumentiert" ausgewiesen und das Lücken-Gate wäre grün geblieben, obwohl nichts gebaut ist (nachgestellt: 84 SWRs / 0 Lücken trotz leerer Umsetzung). Stattdessen wechselt jede Anforderung einzeln auf `reviewed`, wenn Sprint 1 sie mit Nachweis liefert. **214 Tests, Matrix 84/0, 0,00 € API.** Nächster Schritt: P10 Sprint 1 (ADR-007, Schreibendpunkt, Editor, Labels, PIN-Gate).

**⚠ BEFUND pm/T-0017 (Routine-Session, B024) — bitte zuerst lesen: Eine Entscheidung, die dir nie vorgelegt wurde.** Beim Pflichtpunkt „Inbox prüfen" lieferte die Inbox eine **leere Liste** — obwohl Agenda und dieser Statusbericht seit heute Vormittag sagen, der G1-Antrag `p10/T-0002` warte dort auf dich. Ursache: `aggregation.projekte()` fand `p10` korrekt, aber **vier** Stellen bauten den Pfad danach selbst als `root/<name>` zusammen; für ein Projekt im Sammel-Repo ergibt das `./p10` statt `./projects/p10` — Ordner existiert nicht, **null Tickets, keine Fehlermeldung**. Betroffen: Inbox (SWR-027), Inbox-Zähler (SWR-076), Übersicht (SWR-026), Entscheidungshistorie (SWR-042) — und, am schwersten, die **Frist-Warnmail (SWR-033/034)**. Heißt konkret: Am 23.08. wäre der Default **G1a** gelaufen und P10 Sprint 1 hätte begonnen, ohne dass du den Antrag je gesehen oder auch nur eine Warnmail bekommen hättest. Genau das schließt Playbook Kap. 16 aus. Verschärfend: Dass hier „liegt in deiner Inbox" stand, hat die Lücke zugedeckt. **Behoben** — alle vier Stellen nutzen jetzt `aggregation.projekt_pfad`, dazu **5 Regressionstests, die gegen den alten Code nachweislich scheitern**; kein neuer SWR (SWR-070 war richtig, nur unvollständig umgesetzt). Es ist derselbe Fehler wie in p9/T-0007 vom Vormittag, nur eine Ebene tiefer — die Lesson war richtig und wurde zu eng angewendet; sie ist jetzt aufs ganze Repo verschärft (B025). **210 Tests, Matrix 83/0, 0,00 € API.** **Die Frist von `p10/T-0002` bleibt unverändert 23.08.** — sie zu verschieben wäre ein Eingriff in einen Klasse-A-Vorgang; wenn dich die verlorenen Tage stören, genügt ein Wort im Briefkasten. **Deine Stichprobe: Server neu starten, Inbox öffnen — steht der G1-Antrag jetzt da?**

**Brief platform/N-0002 beantwortet und behoben (B023):** Der `ConnectionResetError`-Traceback (WinError 10054) in deinem Server-Log war **kein Fehler** — ein Gerät in deinem LAN (sehr wahrscheinlich das Handy) kappt die offen gehaltene Verbindung, wenn du den Bildschirm sperrst oder den Tab schließt. Trotzdem behoben, weil ein Log, in dem Normalvorgänge wie Abstürze aussehen, den nächsten *echten* Traceback unsichtbar macht: Ab jetzt steht dort eine Klartextzeile statt fünfzehn Zeilen Stack. Gefangen werden **nur** die drei Abbruch-Arten, echte Fehler behalten ihren vollen Traceback (zwei Tests sichern genau das ab). Nebenbefund mitgeprüft: Der Ruhe-Zähler des Selbst-Neustarts (SWR-073) wird auch im Abbruchfall freigegeben — sonst hätte ein einziger Handy-Abbruch den Server dauerhaft als „beschäftigt" markiert. Nachweis: Symptom nachgestellt, **vorher 2 Tracebacks, nachher 0**, Folge-Anfrage weiter `200`. `pm/T-0016`, kein neuer SWR.

**Brief N-0018 sofort erledigt (B022):** Der **Team-Chat zeigt die neuesten Nachrichten zuerst** (SWR-083, P4-Fläche v1.1, pm/T-0015). Gedreht wird nur die Anzeige — die API liefert weiterhin chronologisch (SWR-050 unverändert), umgekehrt wird eine Kopie der Liste, damit andere Leser derselben Daten unberührt bleiben. **Das Schreibfeld ist mit nach oben gewandert**: nicht verlangt, aber zwingend, weil es sonst hinter dem gesamten Verlauf läge und man zum Schreiben erst durch alles scrollen müsste — im Brief ausdrücklich benannt, damit du widersprechen kannst. **199 Tests, Matrix 83/0, 0,00 € API.** Deine Stichprobe: Server neu starten, Team-Chat von `pm` öffnen — N-0018 oben, Schreibfeld direkt unter der Kopfkarte, auf dem Handy genauso.
