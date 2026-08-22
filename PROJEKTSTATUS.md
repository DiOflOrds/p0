# Projektstatus — Fortschreibung über Sessions

---

## Sprint 37 (2026-08-22, Cowork **mit Shell**) — der Befund war unser eigener Plan

Der Auto-Abschluss des Auftraggebers brach seit Stunden bei Schritt **[1/6]** mit Exit 1 ab:
kein Push, keine Teststrecke, kein CI. Sprint 36 hatte den Grund als *„in diesem Lauf nicht
identifiziert"* berichtet. Er stand wörtlich im Protokoll.

    [org] BEFUND: 12 Planzeile(n) nennen eine andere Sprintnummer als ihr Ticket

**Sprint 36 hat seine Tickets vorbildlich auf 37 nachgezogen — und seine eigene Plantabelle
stehen lassen.** Damit war `plan_drift` von der anderen Seite ausgelöst: nicht der Plan lief
dem Ticket davon, sondern das Ticket dem Plan. `pl.md` Lehre 8 zum **dritten Mal in vier
Sprints**, und die Ursache war eine Vorsichtsmaßnahme gegen genau denselben Fehler.

> **Die teuerste Handlung dieses Tages war eine Tabelle.**

### Repariert wurde das Muster, nicht nur der Befund

Die 32 nicht geschlossenen Tickets stehen auf `geplant_sprint: 38` **und** die
Fälligkeitsspalte der Plantabelle ist im **selben Schritt** mitgezogen. Gemessen mit
**laufendem** Sprint 37 und Tickets auf **38**:

| Prüfung | Wert |
|---|---|
| `plan_drift` · `sprint_vergangen` · `status_drift` · `plan_nachlauf` · `nicht_geplant` | **0 · 0 · 0 · 0 · 0** |

**Das ist die erste Sprintübergabe dieses Hauses, die grün ist, egal ob der alte Sprint noch
läuft oder schon geschlossen ist** (`L-2026-08-22e`, `pl.md` Lehre 16).

### Der Ertrag: vier Tickets, drei Anforderungen, 27 Zusicherungen

| Ticket | Was geschah | Wirkung |
|---|---|---|
| `platform/T-0066` → **in_review** | **`SWR-214`.** Der leere Ollama-Takt wird im **Preflight** gemeldet statt 87 Läufe lang im Protokoll eines Dienstes. Die maßgebliche Auflösung ist **gemessen**: nur `besetzungen.yaml` steht im Pfad, der ein Ticket verwirft. | Offload-Engpass benannt |
| `platform/T-0055` Teil A → **in_review** | **`SWR-215`.** Der Herzschlag des Wächters bekommt einen **Leser** — vier Zustände, nicht zwei. | nächster Ausfall < 15 Min sichtbar |
| `pm/T-0085` → **in_review** | **`pm/B060` + `SWR-216`.** Kennung ist Beschriftung, nicht Identität — bewacht statt umnummeriert. | räumt `pm/T-0082` |
| `team-termine/T-0002` → **in_review** | CM-Plan P16 v1.0 — **10 Work Products, 0 Lücken**. | letzte WP-Lücke geschlossen |

### ⚠⚠ Ollama-Offload: 0 — und der Grund ist zum ersten Mal gezählt

| Größe | Wert |
|---|---|
| Instanzen mit `motor: ollama` | **2** (`PROB@platform`, `MAIL-RED@team-mail`) |
| offene Tickets mit einer davon | **0 von 34** |
| Aufgaben-Typen mit Ollama-Kette, die je ein Ticket trugen | **2 von 8** |
| Tickets im Gesamtbestand mit `aufgaben_typ` | **4 von 383 (1,0 %)** |

> **Selbst wenn Ollama aus dieser Sandbox erreichbar wäre, hätte es nichts zu tun. Sechs von
> acht Aufgaben-Typen mit Ollama-Kette haben in 383 Tickets nie eines getragen — das ist
> keine Auslastungsfrage, sondern eine Absichtserklärung.**

Dieser Lauf hat deshalb den **Engpass gebaut** statt die Delegation zu behaupten. Was fehlt,
ist eine **Besetzungsentscheidung** (Klasse B des PM) — ausdrücklich nicht hier
mitentschieden, übergeben an `pm/T-0079` mit der Zahl in der Hand.

### ⚠ Vier Befunde, die keine Planung gefunden hat

1. **Ein Brief kam ZWISCHEN den Sprints an.** `platform/N-0010`, committet **14:13:59** —
   12 Min nach dem Ende von 36, 9 Min vor dem Beginn von 37, beim Start bereits beantwortet.
   Der Briefkasten war zu Recht „0 offen"; dass die **Post gewachsen** ist, sah nur
   `test_post_im_lauf` (70/75 → 71/76). **Dritter Lauf in Folge.**
2. **Ein falsches Grün im eigenen Bau.** Der erste Entwurf stellte eine Befund-Tabelle über
   die Plantabelle; `plan_tabelle()` liest die **erste**. `plan_drift` meldete **0**, weil
   **keine** Planzeile geparst wurde — widerlegt nur von `nicht_geplant: 39`.
   > **Eine Prüfung, die nichts findet, weil sie nichts liest, sieht genauso aus wie eine,
   > die nichts zu finden hatte.**
3. **Eine Mutationsprobe hat den eigenen Test widerlegt.** Die Probe „jeder `p*`-Ordner ist
   eine Kennung" blieb **grün**: der Test prüfte die **Ausgabe**, nicht die **Regel**.
   Geschärft, dann 4 von 4 rot.
4. **Die Nachverbuchung des Hosts läuft der Session in die Commits.** Dreimal war der Diff
   schon verbucht, während dieser Lauf am `index.lock` wartete — die Ticket-ID im Commit
   ging jedes Mal verloren. Behandelt mit einem leeren Commit **neben** dem Diff; eine
   Umgehung, keine Lösung (gehört zu `platform/T-0071`/`T-0072`).

### Zahlen — gemessen, nicht geschätzt

| Größe | Wert |
|---|---|
| Offene Aufgaben | **39 → 39** (4 auf `in_review`, keines `done`) |
| Teststrecke | **111 von 112 Modulen, 1567 Zusicherungen, 0 rot** (blockweise; die Sandbox deckelt einen Aufruf bei ~178 s) |
| Rot **im** Lauf | **1**, gefunden **und** geschlossen (`test_post_im_lauf`) |
| `trace_matrix` | **216 SWRs, 0 Lücken** (213 → 216) |
| `organigramm.py --check` | **grün** (21 Dateien) |
| Briefkasten | Start **0 offen / 70** (oberste Ebene) · Ende **0 offen / 71** (beide Ebenen) |
| Work Products | **56 → 66** über 8 Einheiten, **0 fehlend, 0 undeklariert** |
| Workflows | **8** über 5 Einheiten, **0 unabgedeckte Takte** |
| Wächter | **lebt** — Herzschlag 14:27:21, PID 23284 |
| Ollama-Offload | **0 delegiert, Ersparnis 0** |

⚠ **Nicht gemessen und deshalb nicht behauptet:** `test_js_teststrecke` und ein
**vollständiger** `preflight` laufen in dieser Sandbox über die Zeitgrenze. Gemessen ist
diesmal **wo** die Zeit hingeht: `uebergangshistorie` **45 s**, `sprint.plan` 6 s,
18× `git status` 9 s, `parkplatz_stand` 0,3 s.

⚠ **Ein Nebenbefund ohne Ticket, hier benannt statt verschwiegen:** der Lock-Parkplatz ist
auf **12 716** Artefakte gewachsen (`platform` 2 753, `pm` 2 560) und wächst weiter, weil
der Mount kein `unlink` erlaubt. `preflight` sagt seit Wochen *„Parkplatz gelegentlich auf
dem Host leeren"* — getan hat es niemand.

### ⚠⚠ Die Stichprobe ist noch im Lauf gefahren — und hat die Erwartung widerlegt

Zweimal, das zweite Mal mit untätiger Session. **Die Org-Prüfungen sind grün** (`Plan-Drift
0`, `Offen auf vergangenem Sprint 0`, `Plannachlauf 0`, `Statusübergänge im laufenden
Sprint 0`) — **und der Abschluss bricht weiter bei `[1/6]` ab, jetzt mit 7 Befunden statt
einem.**

Die 7 sind `index.lock`-Artefakte, und der eigentliche Fund ist, dass drei Beobachter
verschieden antworten: die **Sandbox** sagt „existiert nicht", **`git` in derselben
Sandbox** sagt „existiert" (`unable to unlink … Operation not permitted`), der **Host**
sagt „existiert, nicht entfernt — Git-Prozess aktiv", obwohl seit zehn Minuten keiner lief.

> **Eine Sperre zu räumen beweist nicht, dass der Weg frei ist. Es beweist nur, dass diese
> Sperre weg ist — und das ist genau der Unterschied, den eine Stichprobe misst und ein
> Haken behauptet.**

Aufgenommen als **`platform/T-0073`** (prio hoch, Sprint 38), im selben Zug mit seiner
Planzeile. ⚠ Der Lock-Parkplatz wuchs in diesem Lauf von 12 630 auf **12 841** (+211).

**Für den Menschen bleibt damit offen:** es wird weiter nicht gepusht. Der Rückstand steht
namentlich in `PUSH-ANFORDERUNG.txt`, der Grund ist ab jetzt benannt statt unbekannt.

---

## Sprint 36 (2026-08-22, Cowork **mit Shell**) — vierzehn Sperren gefallen, und keine durch neuen Code

Die Sandbox läuft wieder. Zum ersten Mal seit fünf Sitzungen hatte ein Cowork-Lauf `git`,
`python`, Tests und das Sprintregister — **Sprint 36 ist eröffnet** (`s36-2026-08-22-1300`),
nachdem er dreimal an einem offenen Sprint 35 gescheitert war.

### Der Ertrag: zwei Nachweise lagen fertig im Haus, und ein Plan war ein Template geblieben

| Ticket | Was geschah | Wirkung |
|---|---|---|
| `platform/T-0060` → **done** | ⚠⚠ Der Ollama-Nachweis war **seit dem 21.08. 20:59 geführt**: `Gateway: status=ok provider=ollama`, `gemma3:27b`, **2 Artefakte**, 221,2 s — und lag **16 Stunden ungelesen** im Register. | entsperrt **4** Tickets |
| `team-termine/T-0001` → **in_review** | `docs/projektplan.md` von der Platzhalter-Fassung auf **v1.0 vollständig** (8 Kapitel, Ziele Z1–Z5, 6 Phasen, Risiken R1–R7 mit Eigentümer). | entsperrt **10** Tickets |
| `pm/T-0086` → **done** | ⚠⚠ `pm/D030` = **C** stand seit **00:23** im Decision-Log und war **13 Stunden unverbucht**. Der DR zählte in `wartet_auf_mensch` mit, während der Auftraggeber längst geantwortet hatte. | `wartet_auf_mensch` **1 → 0** |
| `platform/T-0068` → **in_review** | Vorabfragen **gezählt**: **1** Fundstelle im ganzen Bestand, **0 von 75** Belegen fälschlich durchgelassen. Dazu die eigentliche Lücke: die Host-Reparatur baute **drei neue Zweige ohne jede Zusicherung**. | 2 Zusicherungen + Gegenprobe |
| `team-dashboard/T-0007` → **neu** | Aus Brief `p0/N-0002`. | siehe unten |

> **Der Engpass dieses Hauses war nicht die Arbeit, sondern das Lesen dessen, was schon
> dastand.**

### ⚠⚠ Drei Befunde über uns selbst — alle von Zusicherungen gefunden, keiner von einem Menschen

1. **Die entschiedene, unverbuchte Klasse-A-Frage** (`pm/D030`) — gefunden von
   `test_dr_verbuchung`, einer Zusicherung, die genau dafür gebaut und **vier Sprints
   nicht gefahren** wurde.
2. **Ein Brief kam im Lauf an und wäre unbemerkt geblieben.** `p0/N-0002` (12:51, vom
   Auftraggeber). Der Lauf hatte „0 offen / 69 Briefe" gemessen; gefunden hat den 70. Brief
   `test_post_im_lauf`. ⚠ Er lag in **`p0`** — genau der Ebene, vor der PL-Lehre 6 warnt.
3. **⚠ Ein unzulässiger Status-Übergang stammt aus DIESEM Lauf.** `platform/T-0068` ging
   `open -> in_review` ohne `in_progress` (Commit `04da965`). **Ursache: `board.py` lief
   in derselben Befehlszeile wie `git commit`, aber mit `;` — die Validierung meldete den
   Fehler, und der Commit lief trotzdem.** Die Prüfung hat funktioniert; ihren Exit-Code
   hat niemand gelesen (`L-2026-08-22d`).

### Der Brief des Auftraggebers — beantwortet, dreigeteilt

> *„das ist viel zu groß und hat noch alte inhalte mit darstellungsfehlern, das muss in
> einen normalen kleinen widget reinpassen."*

Der Screenshot wurde **angesehen**, nicht nur zitiert. Drei getrennte Ursachen:
(1) alle drei Zeiträume werden gleichzeitig gerendert, (2) **überlappende Spalten**,
(3) Bestandsdaten statt jüngstem Stand. ⚠ **Punkt 2 stand nicht im Brief** — ohne das Bild
wäre er nicht gefunden worden. Aufgenommen als `team-dashboard/T-0007`, Prio hoch.

### Regel der vierten Berührung — fünf Tickets, fünf Entscheidungen statt fünf Termine

| Ticket | Entscheidung |
|---|---|
| `platform/T-0055` | **schneiden** — ⚠⚠ `waechter.py` ist längst **gebaut**; offen ist nur die DoD. Und der Wächter ist **selbst seit 14 h tot** (letzter Herzschlag 21.08. 23:25), während die Dienste laufen, die er bewacht. Sein eingefrorener Statusbericht behauptet weiter „kein laufender Sprint". |
| `pm/T-0080` | **schneiden** — Teil A: eine Aufgabe, eine Spurenquelle (Ticket + `git log`). |
| `pm/T-0082` | **schneiden** — erst die doppelte Kennung P13 klären (`pm/T-0085`). |
| `team-dashboard/T-0004` | **schneiden** — **Kachel-Vertrag zuerst**: gemeinsame Ursache von `T-0004`, `T-0006` und `T-0007`. |
| `team-mail/T-0006` | **BAUEN** — als einziges nicht geschnitten. Auflage: kein Versandweg im Diff. |

### Zahlen — gemessen, nicht geschätzt

| Größe | Wert |
|---|---|
| Offene Aufgaben | **38 → 37** |
| `wartet_auf_mensch` | **1 → 0** |
| Briefkasten | Start **0 offen / 69** · Ende **0 offen / 70** |
| Teststrecke | **109 Module, 1553 Zusicherungen** (modulweise — die Sandbox deckelt einen Aufruf bei ~178 s) |
| Rot am Ende | **1** während des Sprints, selbst verursacht (Befund 3) — nach `--beende` grün, weil die Zusicherung nur den **laufenden** Sprint prüft. ⚠ **Das ist keine Reparatur:** der Verstoß steht dauerhaft in der Liste der fortgeschriebenen Übergänge (`T-0068: open -> in_review`, Commit `04da965`). |
| `trace_matrix` | **213 SWRs, 0 Lücken** |
| `organigramm.py --check` | **grün** (21 Dateien) |
| Ollama-Offload | **0 delegiert, Ersparnis 0** |

⚠ **Der Ollama-Nachweis liegt vor — delegiert wurde trotzdem nichts, und der Grund ist der
Ort:** Ollama ist aus dieser Sandbox nicht erreichbar (`curl 127.0.0.1:11434` bleibt leer);
der Takt läuft auf `DESKTOP-8OOO6JS`. Die Bedingung der Session-Anweisung ist erfüllt, die
Ausführung gehört auf den Host.

⚠ **Nicht gemessen und deshalb nicht behauptet:** `test_js_teststrecke` läuft in dieser
Sandbox in die Zeitgrenze; `preflight` ist aus demselben Grund nicht vollständig
durchgelaufen. Der Schnelltakt des Hosts meldet zuletzt **`PREFLIGHT: 1 Befund(e)`** —
**dieser eine Befund ist in diesem Lauf nicht identifiziert worden** und bleibt offen.


---

## Host-Lauf vom 22.08.2026 (Auftraggeber-Session) — die sechs roten Zusicherungen behandelt

Die Sandbox ist weiterhin tot (fünfter identischer Startfehler auch in dieser Session);
der Host-Takt lief die Nacht durch und das CM-Review hat seinen ersten Ertrag geliefert:
**sechs rote Zusicherungen**, die vier Sprints lang unter „1551 Tests" verborgen lagen,
stehen seit 21:55 in jedem `abschluss-logs\review-*.md`. Alle sechs in diesem Lauf
behandelt:

1. **`test_berichtskennzahlen`** (Bericht 34/0, gemessen 38/1): neuer Schritt **[0b/6]
   Kennzahlen-Selbstheilung** in `abschluss.cmd` — misst NUR bei rotem Test neu und
   verbucht `pm`; kein Commit-Takt aus Zeitstempeln.
2. **`test_goldset` Herkunft** (`/etc/passwd` wurde durchgewinkt): echter
   Windows-Defekt — seit Python 3.13 sagt `os.path.isabs("/etc/passwd")` unter Windows
   **False**. `goldset._maengel_herkunft_form` prüft jetzt zusätzlich führenden
   Schrägstrich, Laufwerksbuchstaben und `..` in Backslash-Schreibweise.
3. **`test_goldset` Abdeckung** (`prob hat 0` von 20): **20 belegte prob-Fälle** ins
   Goldset angehängt (12 problem-klassifikation, 5 ursachenanalyse, 2 ticket-routing,
   1 trend-report) — alle aus echten Vorgängen des Bestands, jede `herkunft` mit
   wörtlicher Belegstelle, je Aufgaben-Typ ein `soll_scheitern_auf`. ⚠ Vom Team
   ungeprüft — QM/promt-team mögen sie gegenlesen und schärfen.
4.-6. **Die drei Lehren-Zusicherungen** (acht Namen `dj`–`dq`): alle acht INTERIM als
   `**Beobachtung:**` gebucht (der zweite von der Sperrklinke selbst benannte Ausgang),
   `test_kein_bestand_wird_still_als_beobachtung_geparkt` mit Begründung nachgezogen,
   `OHNE_VERTRETER_BASIS` **unverändert**. Zwischenstand und Auftrag je Lehre stehen in
   `platform/T-0070` — die Einzelentscheidung (DoD 1/2) bleibt beim `coach`, Sprint 36.

Dazu: das CM-Review las die `PREFLIGHT:`-Zeile bisher aus dem GANZEN Log und erwischte
eine Testausgabe — jetzt liest es nur das Fenster zwischen `[1/6]` und `[2/6]`.

⚠ **In der Inbox wartet `pm/T-0086` (Klasse A, Frist 28.08.)** auf den Auftraggeber:
Sandbox reparieren, Takt auf den Host ziehen, oder beides.

⚠ Nicht gelaufen und deshalb ohne Zahl: die Teststrecke selbst (keine Shell). Die
Verifikation übernimmt der nächste Auto-Abschluss-Lauf; sein `review-*.md` ist die
Stichprobe — erwartet: Preflight STARTKLAR, Tests grün, Push durch.

---

## Lauf vom 21.08.2026, spätabends (vierter Cowork-Lauf ohne Shell) — die Teststrecke ist ROT, und das wusste seit Stunden nur der Host

**Kein Sprint 36** (kein `sprint_register.py`). ⚠ **Sprint 35 ist seit 20:21 im Register
beendet** — `reparatur-sprint35.cmd` hat den offenen Eintrag geschlossen, den drei Läufe
als Blocker gemeldet haben. Der Weg für Sprint 36 ist frei; er beginnt mit `--beginne`.

> **⚠⚠ Drei Läufe in Folge haben „keine Shell → keine Zahl" berichtet, während der Host
> im selben Ordner die volle Teststrecke fuhr und ihr Ergebnis in `abschluss-logs/`
> ablegte. Es ist derselbe Fehler, den Sprint 35 am Ollama-Protokoll gefunden hat —
> eine Ebene höher, und diesmal an uns selbst.**

### Die Teststrecke, zum ersten Mal seit vier Sprints vollständig

| Größe | Wert | Quelle |
|---|---|---|
| Tests gelaufen | **1551** in 210,4 s | `abschluss-logs/abschluss-20260821-211400.log` |
| **Rot** | **6** | ebd. |

⚠⚠ Sprint 35 hat **„1551 Tests"** als Verifikationszeile geführt **und im selben Bericht
eingeräumt, dass 1136 davon nie gelaufen sind.** Die Zahl der *gesammelten* Zusicherungen
ist vier Sprints lang als Zahl der *grünen* gewandert.

**Die sechs auf drei Ursachen, alle terminiert (Sprint 36):**

| Ticket | Rolle | Befund |
|---|---|---|
| `platform/T-0068` | dev, hoch | `goldset` prüft mit `os.path.isabs`. Auf dem Rechner des Auftraggebers ist `/etc/passwd` damit **kein** absoluter Pfad — **die Schranke gegen Belege außerhalb des Bestands steht dort offen.** Der Code ist krank, der Test war vier Sprints grün, weil er nur in der Sandbox lief. |
| `platform/T-0069` | prob, mittel | Zwei Zusicherungen sind genau dann grün, wenn auf dem **ganzen Rechner** kein zweiter Git-Prozess läuft. Sie messen die Auslastung der Maschine. |
| `platform/T-0070` | coach, hoch | **Acht** Lehren `L-2026-08-21dj…dq` ohne Vertreter — ⚠ **sechs davon aus Sprint 35 selbst**, der die Prüfung nur nicht gefahren hat. |

⚠⚠ **Der Folgelauf des Hosts um 21:55 hat zwei dieser Zahlen schon wieder verändert, und
beide Richtungen sind lehrreich:** die zwei `git_schreibweg`-Zusicherungen sind **ohne
jede Codeänderung grün** (das ist der Beweis für `T-0069`), und **eine neue ist rot —
verursacht von diesem Lauf** (`test_berichtskennzahlen`: `tickets_offen 34→38`,
`wartet_auf_mensch 0→1`). Summe 6 → 5.

> **Der Kennzahlenblock ist unangetastet geblieben und ist genau deshalb falsch: er
> veraltet durch das TICKET, nicht durch das Bearbeiten der Plandatei.** Nicht von Hand
> nachgetragen — `kennzahlen.py --schreibe` ist der Weg und braucht eine Shell.
> **Erster Schritt des nächsten Laufs mit Shell.**

⚠ Das ist die **dritte** Zusicherung in zwei Sprints, deren Grün von der *Umgebung* des
Läufers abhängt: Zeitzone → Betriebssystem → Prozessliste. Jedes Mal gefunden, weil jemand
die Strecke woanders laufen ließ — **nie von uns.**

### ⚠⚠ Zwei eigene Regeln sind an ihrer eigenen Wirkung widerlegt

1. **„Ohne `git` ist die Ticketdatei tabu"** (`L-2026-08-21dq`) war **am Tag ihrer
   Formulierung** überholt: `abschluss.cmd` Schritt **[0/6]** verbucht seither jede
   Arbeitskopie vor dem Preflight (gemessen: **0 von 18** Repos unverbucht um 21:15).
   Die Regel hat **zwei Läufe lang** die fällige Entscheidungsanfrage verhindert.
   ⚠⚠ Sie steht in `NOTBETRIEB-OHNE-SHELL.md` **neun Zeilen über** der Tabelle, die ihr
   den Grund nimmt — ein Lauf, eine Datei, ein Autor. Berichtigt.
2. **„Der Rest des Hauses ist frei"** ist die teurere Hälfte: acht Lehren ohne Vertreter
   machen drei Zusicherungen rot — ⚠ **sechs davon aus Sprint 35**, einem Lauf **mit**
   Shell; die Läufe ohne Shell haben den Befund vergrößert, nicht erzeugt. **Dieser Lauf
   hat deshalb bewusst keine neue Lehre angelegt**; der Nachtrag steht **in** `dq`.

⚠⚠ **Und beide Berichtigungen waren beim ersten Schreiben selbst zu bequem — das
unabhängige Gegenlesen hat in ZWEI Durchgängen zehn Befunde an diesem Bericht gefunden,
keinen davon der Autor. Fünfter Lauf in Folge.** Die wichtigsten: *„alle acht Lehren aus
Läufen ohne Shell"* → **sechs stammen aus Sprint 35**, einem Lauf **mit** Shell ·
*„seit 20:00 STARTKLAR"* → 20:30 brach ab · und im **zweiten** Durchgang der schwerste:
*„der Tick um 21:40 brach ab, der Host hat es eine Minute später geheilt"* → **falscher
Lauf und falsche Entwarnung**; die Abbrüche stehen bei **21:55, 22:10 und 22:25**. Alle
im Lauf korrigiert, keiner geglättet; die Liste steht in `pm/docs/historie.md`.

> **⚠⚠ Der Autor hat einen Bericht über das Nichtzählen geschrieben, dabei nicht gezählt
> — und beim Berichtigen des Nichtzählens wieder nicht gezählt. Die bessere Geschichte
> („alle acht") hätte die eigentliche Ursache verdeckt: nicht der Ausfall der Shell,
> sondern ein Sprint MIT Shell, der 1551 Tests als Verifikation führte und 1136 davon
> nicht ausführte.**

> **⚠⚠ Und der Preis steht daneben: der Lauf, der den Ollama-Nachweis LEGEN wollte, hat
> den Ollama-Takt drei Takte lang blockiert — mit genau den Ticketdateien, die den
> Nachweis tragen sollen. Jede Korrektur erzeugt eine neue unverbuchte Fassung; der
> Verbucher läuft im 15-Minuten-Takt hinterher. Die Regel lautet ab jetzt: eine
> Ticketdatei ohne `git` wird EINMAL FERTIG geschrieben.**

### ⚠⚠ Ollama: ab 20:00 überwiegend STARTKLAR — und trotzdem nichts zu tun. Die fünfte Antwort.

In fünf von sechs Läufen ab 20:00 bricht der Tick **nicht mehr ab** (20:30 ist die
Ausnahme, 1 Befund). Er endet mit: *„Der Bestand hat für diese Besetzung nichts — ein
weiterer Lauf ändert das nicht."*

> **Genau ZWEI Besetzungen des Hauses tragen `motor: ollama` — `PROB@platform` und
> `MAIL-RED@team-mail` —, und kein offenes Ticket hat je eine dieser Rollen getragen.
> Vier Sprints Diagnose an einer Maschine, der nie jemand Arbeit hingelegt hat.**

**Behandelt statt berichtet:** `platform/T-0069` ist als `rolle: prob` /
`aufgaben_typ: problem-klassifikation` angelegt (Kette `[ollama, session, claude]`,
`tier: standard`, **nicht gate-relevant**). Damit trägt zum ersten Mal ein offenes Ticket
die Rolle, für die diese Besetzung existiert.

⚠⚠ **Ein gelegter Nachweis, kein geführter — und der erste Versuch ist schon
fehlgeschlagen — dreimal.** Die Läufe um **21:55, 22:10 und 22:25** brachen an den noch
unverbuchten Ticketdateien ab. `pm/T-0071` hat weiterhin **null** Ticks mit `status: ok` +
Artefakt, Token-Ersparnis dieses Laufs **0**. Ob der Nachweis je geführt wird, steht im
`ollama-schnelltakt.log` und nicht hier.

⚠ **Im Betrieb bestätigt (22:10, 22:25):** alle 18 Repos `sauber`, `board-check: OK` für
alle 19 Einheiten, und `[org] 1 Ticket(s) warten auf den Menschen: pm/T-0086`. Die vier
Tickets sind formal gültig und die Entscheidungsanfrage ist angekommen — **die einzige
Verifikation, die dieser Lauf ohne Shell führen konnte, und sie ist geführt.**

### Für den Auftraggeber — eine Entscheidung liegt vor

**`pm/T-0086`** (Klasse A, Frist **2026-08-28**, Default **C**): Sandbox reparieren (A),
Takt ganz auf den Host ziehen (B) oder beides (C). Empfehlung **C**.
Kurzfassung von A: **Claude Desktop komplett beenden und neu starten, freien Platz auf
`C:` prüfen und schaffen, alte Cowork-Sitzungen in der App löschen.** Bleibt es, ist es
eine Störung der App und gehört an Anthropic gemeldet — nicht ans Projekt.

⚠ Diese Frage war in **zwei** Läufen als fällig erkannt und beide Male nicht gestellt —
mit der Begründung aus Punkt 1, die schon nicht mehr galt.

### Zahlen dieses Laufs

Briefkasten **0 offen** (69 Briefdateien, beide Ebenen) · offene Aufgaben **34 → 38** ·
auf den Menschen wartend **0 → 1** · Plandrift/Statusdrift/ohne Sprint/unverbuchte DRs je
**0** · unverbuchte Arbeitskopien **0 von 18** · Parkplatz `verwaiste-locks` **12461**.

⚠ **Ein Widerspruch bleibt stehen:** Abschlusslauf 21:14 meldet **4 Preflight-Befunde**,
Schnelltakt 21:15 **STARTKLAR**. Sie messen nicht dasselbe (`abschluss.cmd` fährt
`p1`/Produkte mit). **Welche der beiden die Organisation meint, ist ungeklärt** und liegt
als Vorabfrage 3 in `platform/T-0069`.

⚠⚠ **Keine Zeile Plattformcode geändert.** `T-0068` wäre eine Zeile gewesen — ohne
Teststrecke wäre jede Reparatur eine Behauptung.

---

## Host-Lauf vom 21.08.2026 (Auftraggeber-Session) — Takt repariert, Wächter gebaut

**Kein Sprint** (die Sandbox-Shell war zum dritten Lauf in Folge tot — vier identische
Startfehler), aber der Lauf hatte, was den Vorläufern fehlte: **die Dateien des Hosts.**
Vier Reparaturen, alle unten nachlesbar:

1. **Befund A ausgeführt (Schritt 0):** die zehn Tickets mit `geplant_sprint: 35` stehen
   jetzt auf **36**, je mit Notiz im Ticket; Planzeilen in `sprint-aktuell.md` nachgezogen.
   **Befund B dazu:** `team-termine/T-0011`/`T-0012` von `open`+`blocked_by` auf `blocked`.
2. **Auto-Abschluss repariert:** `abschluss.cmd` hat wieder einen Schritt **[0/6]
   Nachverbuchung** — der Host committet liegengebliebene Arbeitskopien VOR dem Preflight
   (die Notizen in `PUSH-ANFORDERUNG.txt` sagen wörtlich, dass abschluss.cmd das tut; der
   rekonstruierten Fassung vom 17.08. fehlte genau dieser Schritt — Ursache von 500+
   roten Wächterläufen in Folge). `abschluss-auto.cmd` kippt die Anforderung nicht mehr
   komplett ins Log (~390 Zeilen × 500 Läufe), nur noch die Zeilenzahl.
3. **`reparatur-sprint35.cmd`** (einmalig, idempotent): schließt Sprint 35 im Register
   (`s35-2026-08-21-1450`), schreibt den Kennzahlenblock (`test_berichtskennzahlen`),
   ruft `abschluss.cmd`. Danach ist der Weg für Sprint 36 frei.
4. **Wächter gebaut** (Brief `platform/N-0008`, Ticket `platform/T-0055`):
   `waechter.py` + `waechter.cmd` + `waechter-einrichten.cmd` — startet und überwacht
   Mission Control (Neustart inkl. Code 42), Auto-Abschluss und Ollama-Schnelltakt
   (Soll-Takt aus der Aufgabenplanung, Beleg je Dienst benannt), meldet den
   Ollama-Dienst, schließt abgebrochene Sprints nach der SWR-136-Messung
   (Schreibspur, zwei Beobachtungen). Status: `waechter-status.json` + `waechter.log`.
   ⚠ Betriebsmittel des Auftraggebers — die DoD von `T-0055` (Zählung, Zusicherungs-Paar,
   Review) bleibt offen und beim Team.
5. **Erster Reparaturlauf gefahren und ausgewertet:** `reparatur-sprint35.cmd` lief —
   Sprint 35 im Register **beendet**, Kennzahlen geschrieben, Nachverbuchung committete
   `pm`, Preflight kam durch bis auf **einen** Befund: die Planzeile `platform/T-0065`
   sagte „geplant", das Ticket ist `done`. Während des laufenden Sprints war das geduldet
   (pm/D006), nach `--beende` wurde es blockierend. **Planzeile nachgezogen** — der
   nächste Lauf sollte durchgehen.
6. **Abschluss belegt und von cm gegengelesen** (Wunsch des Auftraggebers vom 21.08.):
   Jeder Abschlusslauf schreibt sein vollständiges Protokoll nach
   `abschluss-logs\abschluss-<zeit>.log`; danach liest die Rolle **cm** es maschinell
   gegen (`abschluss-review.py` → `abschluss-logs\review-<zeit>.md`, erste Zeile
   maschinenlesbar „ERGEBNIS: OK/BEFUNDE"). Prüfpunkte: Schrittfolge, Preflight, Tests,
   Push je Repo, CI, Schlussmarke, Exit-Code; „nicht prüfbar" zählt als Befund, nie als
   in Ordnung. Der Wächter zeigt das jüngste Review-Ergebnis mit an. Aufbewahrung:
   jeweils die 200 jüngsten Protokolle/Reviews.

7. **Sandbox-Ausfall eingeordnet und dokumentiert:** vierter Cowork-Lauf in Folge ohne
   Shell (`useradd`/`ENOSPC` — Speicher der App-Sandbox voll oder eingekeilt). Das ist
   eine Störung der Cowork-App auf dem Rechner, **kein** Projektfehler. Diagnose,
   Selbsthilfe (App-Neustart, Platz auf `C:`) und die Regeln für Sessions ohne Shell
   stehen jetzt in **`NOTBETRIEB-OHNE-SHELL.md`** (Wurzelordner).

⚠ **Nicht gelaufen und deshalb ohne Zahl:** Tests, Preflight, Matrix (keine Shell).
Die Verifikation übernimmt der nächste `abschluss.cmd`-Lauf (Schritt [2/6]) auf dem Host;
ein unabhängiges Gegenlesen dieser Reparatur fand 2 Härtungspunkte + 5 Kleinigkeiten,
alle eingearbeitet.

---

## Folgelauf vom 21.08.2026 — **wieder kein Sprint**, dafür eine Falle, die wir vorher gesehen haben

**Die Shell war zum zweiten Lauf in Folge nicht da.** Vier identische Startfehler. Ohne
sie: kein `git`, kein `board.py`, kein `preflight`, keine Tests, kein Ollama-Tick, kein
Sprintregister. Sprint 35 steht weiterhin **offen** — nach SWR-136 hätte ein Sprint 36
ohnehin nicht beginnen dürfen. **Also wieder nichts gebaut, nichts geschlossen, nichts
terminiert.**

Dieser Lauf konnte nur **lesen und rechnen**. Das hat gereicht, um zwei Dinge zu finden,
die keine unserer Prüfungen heute meldet — und eines davon hätte deinen Takt beim
nächsten Sprintstart erneut lahmgelegt.

### ⚠⚠ Neun Verschiebungen haben nur im Bericht stattgefunden

Der Abschluss von Sprint 35 sagt, neun Aufgaben seien nach Sprint 36 verschoben, „Grund
je im Ticket". **In keinem einzigen dieser Tickets steht das.** Alle neun stehen
unverändert auf Sprint 35, dazu eine zehnte, die beim Reviewer liegt.

| | |
|---|---|
| Betroffen | `platform/T-0055`, `T-0060`, `T-0064`, `pm/T-0080`, `T-0082`, `team-dashboard/T-0004`, `T-0006`, `team-mail/T-0006`, `T-0007`, `team-termine/T-0001` |
| Heute | **still** — die Prüfung vergleicht gegen den *laufenden* Sprint, und das ist noch 35 |
| Beim nächsten Sprintstart | **alle zehn werden gemeldet**, Takt bricht ab |

> **Das wäre das dritte Mal in Folge, dass unser eigener Sprint-Abschluss deinen Takt
> sperrt. Neu ist nur eines, und es ist das Wertvolle an diesem Lauf: wir sehen es
> diesmal, BEVOR es passiert — weil wir die Regel gelesen haben, statt das Ergebnis
> abzuwarten.**

**Eingetragen als Schritt 0** in `sprint-aktuell.md`, **vor** dem Schließen von Sprint 35.
Nicht angehängt — davorgestellt, denn die Reihenfolge ist der ganze Punkt.

### ⚠ Und ein zweiter, kleinerer: neun von elf aufgeräumt

Sprint 35 hat bei deinem Projekt `team-termine` neun Aufgaben von einem Widerspruch
befreit („offen" und gleichzeitig „wartet auf") — **zwei blieben liegen**. Nachgesehen,
warum es niemand gemeldet hat: unsere Prüfung kennt nur die eine Richtung des Fehlers.

> **Eine Regel, die von Hand auf neun Fälle angewandt und nie als Prüfung gebaut wird,
> ist beim zehnten wieder weg.**

### ⚠⚠ Warum wir beides NICHT repariert haben

Beides wären wenige Zeilen. Wir haben es gelassen, und der Grund ist nachgelesen und
nicht gefühlt: Unser Preflight betrachtet **jede geänderte, nicht committete Ticketdatei
selbst als Befund** — genau daraus bestehen zwei der drei Blockaden, die deinen Takt
gerade aufhalten.

> **Ohne `git` verwandelt jede Ticket-Änderung Arbeit in einen neuen Blocker. Zehn
> Tickets richtigzustellen hieße, zehn Befunde anzulegen, um zehn Befunde zu vermeiden.**

Damit hat die Lehre vom Vorlauf („bei Werkzeugausfall das tun, was das Werkzeug ohnehin
nicht löst") zum ersten Mal eine **nachlesbare Grenze**: es gibt eine Liste im Code, die
sagt, welche Dateien ein Lauf ohne Shell nicht anfassen darf — und alles andere darf er.
Genau das ist hier geschrieben worden: Plan, Chronik, Rollenkarte, Agenda, dieser Bericht.

### ⚠ Und das Gegenlesen hat vier Fehler in genau dieser Arbeit gefunden

Fünfter Lauf in Folge, und wieder keinen davon der Autor:

| Befund | Korrektur |
|---|---|
| „zehn Befunde" | Es ist **ein** Befund, der zehn Aufgaben namentlich nennt. Für deinen Takt gleichwertig, für jede Zählung nicht. |
| „sobald `--beginne` läuft" | Es braucht **zwei** Schritte: `--beende` und dann `--beginne`. Vorher verweigert das Register ohnehin. |
| „diese Dateien sind unbedenklich, weil sie keine Verifikationsquelle sind" | Für zwei davon stimmt das Ergebnis, aber nicht der Grund: sie liegen in der Arbeitswurzel, und die gehört zu keinem Repo. **Die richtige Antwort aus dem falschen Grund ist keine Messung.** |
| „frei heißt folgenlos" | `sprint-aktuell.md` wird sehr wohl gelesen — von drei Prüfungen und einem Test. Wir haben deshalb Plantabelle und Kennzahlenblock nicht angefasst. |

> **Ein Befund über den Prüfer selbst: er meldete unsere neue Lehren-Nummer als „schon
> vergeben" — gelesen hatte er die Dateien, die derselbe Lauf gerade geschrieben hatte.
> Eine Prüfung gegen die Arbeitskopie kann „vergeben" nicht von „soeben von dir vergeben"
> unterscheiden.**

### Für dich (E. John)

| Was | Warum |
|---|---|
| ⚠⚠ **`abschluss.cmd` ausführen** | Unverändert der wichtigste Punkt — **fünf Tage plus acht Sprints plus zwei Läufe ohne Shell**. Wir pushen nie selbst. **Stichprobe:** danach steht in `abschluss-auto.log` `OK - alles geprueft und gepusht` und `PUSH-ANFORDERUNG.txt` ist verschwunden. |
| ✅ **Nichts wartet auf eine Antwort von dir** | Briefkasten **0 offen** (69 Briefe, zweimal geprüft — beide Ebenen). Keine offene Entscheidung. |
| ⚠ **Dein Takt bleibt bis dahin blockiert** | Unverändert die drei Befunde aus Sprint 35; zwei davon löst nur `abschluss.cmd` auf deinem Rechner. Der dritte ist im Vorlauf behoben. |
| ⚠ **Die Sperr-Reste löschen, wenn du magst** | Stand zuletzt **12351 Dateien**. ⚠ **Diesmal nicht nachgemessen** — dafür bräuchten wir die Shell. Wir schreiben die alte Zahl deshalb nicht als aktuelle hin. |
| ⚠ **Die alten Punkte** | Mail-**Versand**daten (`team-mail/N-0003`) — dein ältester offener Punkt, seit Sprint 21. Dazu deine Zählung der Kacheln im Reiter „Dashboard". |

### Zahlen — und was wir bewusst NICHT behaupten

**Gemessen:** Briefkasten **0 offen** (69 Briefe). Offene Aufgaben **34** = 20 offen,
13 wartend, 1 im Review. Tickets, die noch auf Sprint 35 zeigen: **10**. Ollama-Offload
**0 delegiert, Token-Ersparnis 0** (`pm/T-0071` hat weiterhin keinen erfolgreichen Tick
mit Artefakt — und der Tick kann hier ohne Shell gar nicht laufen).

⚠ **Eine Zahl des Vorlaufs stimmt so nicht, und wir überschreiben sie nicht still:** dort
stand „34 = 22 offen + 12 wartend". Die **Summe** ist beide Male 34, die Aufteilung nicht;
unsere 13 Wartenden sind namentlich belegbar.

⚠⚠ **Nicht gelaufen und deshalb ohne Zahl:** Tests, Anforderungs-Matrix, Organigramm,
Board-Prüfung, Preflight. **Eine Zahl aus dem letzten Lauf hier zu wiederholen, wäre eine
Behauptung über heute.**

---

## Lauf vom 21.08.2026, ~16:4x — **kein Sprint 36**, dafür eine Messung, die du brauchst

**Diese Session hatte keine Shell.** Fünf identische Startfehler, vom ersten bis zum letzten
Versuch. Ohne Shell gibt es kein `git`, kein `board.py`, kein `preflight`, keine Tests,
keinen Ollama-Tick und kein `sprint_register.py --beende`. Sprint 35 steht im Register
weiterhin **offen** — nach SWR-136 hätte `beginne()` einen Sprint 36 ohnehin verweigert.

> **Ein Sprint, dessen Verifikation nicht laufen kann, ist kein Sprint. Wir haben deshalb
> nichts gebaut, nichts geschlossen und nichts terminiert — statt Arbeit zu melden, die
> niemand nachmessen konnte.**

### ⚠⚠ Dein Takt ist wieder blockiert — und zum zweiten Mal in Folge durch uns

`ollama-schnelltakt.log`, letzter Lauf **21.08. um 16:01:20**:
`PREFLIGHT: 3 Befund(e)` → `Tick abgebrochen: Preflight hat Befunde`.

**Alle drei stammen aus Sprint 35 selbst:**

| # | Befund | Wer kann es lösen |
|---|---|---|
| 1 | `p9/requirements/software/software-requirements.md` nicht committet | **`abschluss.cmd`** (Host) |
| 2 | `pm/tickets/T-0085.md` nicht committet | **`abschluss.cmd`** (Host) |
| 3 | Planzeile `pm/T-0085` sagte Sprint 35, das Ticket sagt Sprint 36 | ✅ in diesem Lauf korrigiert |

> **Sprint 35 hat den Takt entsperrt und ihn im selben Abschluss wieder gesperrt. Das ist
> dieselbe Bauart wie die 138 Abbrüche davor: die Sperre trägt wieder den Namen der
> Sorgfalt — nur diesmal wussten wir es beim Schreiben.**

⚠ **Punkt 3 hätte `abschluss.cmd` NICHT gelöst.** Ein Commit der falschen Zeile hätte den
Befund mitgenommen. Das war das einzige der drei Dinge, das ohne Shell überhaupt behebbar
war — und es ist behoben (`pm/management/sprint-aktuell.md`, die Datei war ohnehin schon
unverbucht und geht mit `abschluss.cmd` mit).

⚠ **Ehrliche Grenze:** wir konnten diese Korrektur **nicht nachmessen**. Dass der nächste
Takt `STARTKLAR` meldet, ist eine **Erwartung, keine Messung**.

### Für dich

| Was | Warum |
|---|---|
| ⚠⚠ **`abschluss.cmd` ausführen** | Unverändert der wichtigste Punkt — **fünf Tage plus acht Sprints** — und er ist jetzt zusätzlich das, was deinen Takt entsperrt. **Stichprobe:** danach `PREFLIGHT: STARTKLAR` in `ollama-schnelltakt.log`, `OK - alles geprueft und gepusht` in `abschluss-auto.log`, und `PUSH-ANFORDERUNG.txt` ist verschwunden. |
| ⚠ **Sprint 35 im Register schließen** | Braucht die Shell (`sprint_register.py --beende`, Kennung `s35-2026-08-21-1450`). Solange er offen ist, startet kein Sprint 36. Bewusst **nicht** mit einer erfundenen Endezeit nachgetragen (L-2026-08-21da). |
| ✅ **Nichts wartet auf eine Entscheidung** | Briefkasten **0 offen** über alle Repos (gemessen: 69 Briefe, kein `status: offen`), `0 Tickets warten auf den Menschen` laut Preflight-Protokoll. |
| ⚠ **Die alten Punkte** | Mail-**Versand**daten (`team-mail/N-0003`), die SPAM-Zahl fürs Post-Widget, deine Zählung der Kacheln im Reiter „Dashboard", die Zugangsdaten für `team-termine`. Unverändert. |
| ⚠ **Die Sperr-Reste** | **12461 Dateien** (Stand 16:01, aus dem Protokoll). Wir können sie nicht löschen, du schon. |

**Zahlen (alle gemessen, keine geschätzt):** offene Aufgaben **34** (22 `open` + 12
`blocked`), Briefkasten **0 offen**, Preflight **3 Befunde / 10 fortgeschrieben**,
Ollama-Offload **0 delegiert / Token-Ersparnis 0** — `pm/T-0071` hat weiterhin keinen Tick
mit `status ok` + Artefakt. Tests, Trace-Matrix und Organigramm sind in diesem Lauf
**nicht gelaufen** und werden deshalb auch nicht als Zahl behauptet.

---

## Sprint 35 (2026-08-21) — dein Ollama-Takt läuft seit einem Tag, 87 Mal, und wir haben ihn selbst blockiert

**Der wichtigste Satz zuerst, und er ist unangenehm:** Wir haben dir drei Sprints lang
erklärt, warum der Ollama-Nachweis nicht zu führen ist — und dabei jedes Mal den falschen
Rechner gemessen.

### ⚠⚠ Bitte zuerst lesen: der Takt läuft auf deinem Rechner, und sein Protokoll lag die ganze Zeit da

`ollama-schnelltakt.cmd` läuft bei dir alle 15 Minuten. Seit dem 20.08. um 17:15 sind das
**87 Läufe, 138 Abbrüche und null Erfolge** — nachzulesen in `ollama-schnelltakt.log`, die
im selben Ordner liegt wie alles andere und heute um 14:46 zuletzt beschrieben wurde.

Sprint 34 hat gemeldet, der Nachweis sei „aus dieser Sandbox nicht führbar", und das sauber
belegt: `localhost:11434` antwortet nicht, `host.docker.internal` ist gesperrt. **Beides
stimmt. Beides misst die Maschine, auf der der Takt gar nicht läuft.**

> **Drei Sprints lang haben wir die Erreichbarkeit eines Rechners diskutiert, auf dem der
> Takt nicht stattfindet — während sein echtes Protokoll unangetastet danebenlag und
> 87 Mal dasselbe sagte.**

**Und der Grund der 138 Abbrüche ist unsere eigene Buchführung.** Jeder einzelne bricht mit
derselben Zeile ab: *„Preflight hat Befunde"*. Es sind zwei Befunde, und **beide hat
Sprint 34 selbst erzeugt** — vier Zeilen in seinem eigenen Sprintplan trugen noch die alte
Sprintnummer, und die neun Aufgaben, die er bei der Gründung von `team-termine` angelegt
hat, hatten keinen Termin.

> **Unser eigener Sprint-Abschluss hat den Nachweis blockiert, den derselbe Sprint als
> „nicht führbar" gemeldet hat. Die Sperre trug den Namen der Sorgfalt.**

**Beides ist geräumt und nachgemessen (0 und 0).** Damit kann der Takt bei dir zum ersten
Mal seit dem 20.08. um 22:05 überhaupt wieder bis zum Gateway kommen.

**Deine Stichprobe:** Nach dem nächsten Schnelltakt-Lauf steht in `ollama-schnelltakt.log`
**`PREFLIGHT: STARTKLAR`** statt „Preflight hat Befunde". Danach steht dort entweder eine
`Gateway:`-Zeile — dann ist der Nachweis geführt — oder `Kein bearbeitbares Ticket
(Besetzung)`. Falls Zweiteres: das haben wir vorausgesehen und als `platform/T-0066`
aufgeschrieben, samt Messung (die beiden Rollen, die überhaupt auf Ollama laufen dürfen,
haben zusammen **null** offene Aufgaben).

⚠ **Das Ticket bleibt trotzdem offen.** Ein Nachweis, der nicht geführt wurde, wird nicht
dadurch geführt, dass wir die Ursache verstanden haben.

### Was sonst gebaut wurde

**Deine Post wird jetzt richtig gezählt.** Bisher zählte unsere Kennzahl nur **neue**
Briefe. Wenn du in einen vorhandenen Brief hineingeschrieben hast — was du regelmäßig tust
— meldete sie **0**. Gezählt über den ganzen Bestand: **69 Erstbriefe gegen 74 Beiträge.
52 Prozent aller Post in diesem Haus sind Beiträge, und die Kennzahl sah davon nichts.**

⚠ Der interessantere Teil: die naheliegende Reparatur allein hätte nichts geändert. Unser
Leser schnitt Zeitstempel auf das Datum ab — dein Beitrag von **12:26** wurde als
Mitternacht gelesen und lag damit vor dem Sprintstart. **Der Zerleger hat die Uhrzeit
weggeschnitten, die er selbst schreibt.** Eine Kennzahl, die nur ihre Leseseite repariert,
hätte weiter 0 gemeldet — und dabei grün ausgesehen.

**Und unsere Fehlerprotokolle sagen jetzt, was gescheitert ist.** Alle elf Fehlereinträge
unserer Laufprotokolle trugen ein **leeres** Provider-Feld. Genau daher kommen die drei
falschen Ollama-Diagnosen: Ein Eintrag, der nicht sagt, *was* gescheitert ist, unterscheidet
nicht zwischen „nichts wurde versucht" und „Ollama hat mit 404 geantwortet" — und der erste
Fall lädt zum Warten ein statt zum Nachsehen.

### ⚠⚠ Was wir über uns selbst aufschreiben müssen

**Das unabhängige Gegenlesen hat SIEBZEHN Befunde in unserer bereits fertig gemeldeten
Arbeit gefunden. Keinen davon wir selbst. Vierter Sprint in Folge.**

Die drei schwersten waren echte Fehler: ein Feld erbte den Wert seines Vorgängers (das
Protokoll behauptete, `claude` habe ein Modell benutzt, das es nie angefasst hat); eine
Fehlermeldung wurde von einem übersprungenen Eintrag überschrieben; und ein Brief mit
datumslosem Zeitstempel fiel durch **alle drei** Zahlen unserer neuen Kennzahl — weder
gezählt noch als „unbekannt" geführt, sondern spurlos weg.

Dazu **fünf** Zusicherungen, die auch bei kaputtem Code grün geblieben wären, und **vier
falsche Zahlen** in bereits geschriebenen Anforderungen. Alle korrigiert, keine
stillschweigend.

> **Vier Sprints in Folge füllt das Reparieren eigener Arbeit den Lauf. Das ist keine
> Pechsträhne mehr, sondern eine Eigenschaft unseres Bauens — und sie gehört als solche
> behandelt, nicht als Ausrede für Verschiebungen.**

⚠ **Ein Fehler, den nicht einmal das Gegenlesen fand, sondern das Werkzeug:** Wir haben die
Katalogzeile einer neuen Anforderung **ohne Zeilenumbruch an die Zeile davor angehängt**.
Sie war vorhanden — und für jedes Werkzeug unsichtbar. Gefunden hat es das Lücken-Gate.

### ⚠ Ehrliche Grenze dieses Laufs

**Die Teststrecke ist nicht vollständig gelaufen, und das ist eine Aussage.** Block 1 lief
(415 Tests, 414 grün). Danach ist unsere Ausführungsumgebung ausgefallen — kein
Speicherplatz — und nicht wiedergekommen. **Die Zahl 1551 sagt, wie viele Zusicherungen es
gibt, nicht dass sie grün sind.**

**Deshalb ist der Sprint-Abschluss nur teilweise verbucht.** Der Code und die
Anforderungen sind committet; die Abschluss-Dokumente (dieser Bericht, der Sprintplan, die
Chroniken, die Lehren, die Trace-Matrix) liegen auf der Platte und brauchen einen
Verbuchungslauf. In `PUSH-ANFORDERUNG.txt` steht namentlich, was fehlt.

### Für dich

| Was | Warum |
|---|---|
| ⚠⚠ **`abschluss.cmd` ausführen** | **Fünf Tage plus ACHT komplette Sprints.** Wir pushen nie selbst. **Stichprobe:** danach steht in `abschluss-auto.log` `OK - alles geprueft und gepusht` und `PUSH-ANFORDERUNG.txt` ist verschwunden. |
| ✅ **Der Ollama-Takt ist entsperrt** | Zum ersten Mal seit dem 20.08. 22:05. **Stichprobe:** `PREFLIGHT: STARTKLAR` in `ollama-schnelltakt.log`. |
| ⚠ **Die Sperr-Reste löschen, wenn du magst** | **12351 Dateien** (Stand 14:46). Wir können sie nicht löschen, du schon. |
| ⚠ **Die alten Punkte** | Mail-**Versand**daten (`team-mail/N-0003`) — dein **ältester** offener Punkt. Die SPAM-Zahl fürs Post-Widget (ein Wort genügt). Deine Zählung der Kacheln im Reiter „Dashboard". Die Zugangsdaten für `team-termine`. |
| ✅ **Nichts wartet auf eine Entscheidung** | Inbox leer, Briefkasten 0 offen — am **Ende** gemessen. |

---

## Sprint 34 (2026-08-21) — dein Projekt steht, und wir haben 91 gelöschte Lehren zurückgeholt

**Sechs Aufgaben geschlossen, sechs verschoben, ein Projekt gegründet.** Der Ertrag steckt
aber in zwei Funden, die niemand geplant hatte.

### ⚠⚠ Bitte zuerst lesen: 91 unserer Lehren waren gelöscht — und unsere Prüfung meldete Fortschritt

Am 21.08. hat der Abschluss-Commit von Sprint 32 zwei Lehrbücher **überschrieben statt
angehängt**: `knowledge/cm/lessons.md` fiel von 1931 auf 26 Zeilen, `knowledge/pl` von 831
auf 26. **91 Lehr-Abschnitte gelöscht, 2 hinzugefügt.** Der Commit trägt im Betreff die
Worte *„Lehren cq-cv verankert"*.

**Neunzig davon hatten heute nirgends im Haus mehr einen Kopf** — sie existierten nur noch
in der Git-Historie.

> **Ein Bestand kann verschwinden, während sein Wächter Erfolg meldet.** Unsere Prüfung
> sah die Menge schrumpfen und meldete: *„Diese Lehren haben einen Vertreter bekommen —
> bitte die Basis nachziehen."* Sie konnte „Fortschritt" nicht von „Gegenstand weg"
> unterscheiden und nannte beides beim Namen des angenehmeren Falls.

**Und unsere Erklärung aus dem letzten Sprint war ebenfalls falsch.** Dort hatten wir
geschlossen, die Lehren hätten *„nie in einem Lehrbuch gelebt"*. Sie haben dort gelebt,
bis ein Commit sie überschrieb. **Zwei Sprints hintereinander trug dieselbe Lücke eine
falsche Erklärung — weil wir beide Male den Bestand gezählt haben und nie die Geschichte
der Datei.**

**Alles wiederhergestellt** (aus dem Commit davor, die zwei späteren Lehren **angehängt**).
Der Beweis ist eine Zahl, die niemand gewählt hat: unsere Kennzahl liefert wieder **exakt
die 91** IDs von Sprint 31, in beide Richtungen identisch. Die Liste hatte die ganze Zeit
recht.

> **⚠ Gerettet hat sie die Zurückhaltung des letzten Sprints.** Dort steht wörtlich: *„die
> Basis auf den heutigen Stand zu setzen hätte die Zusicherung in einer Minute grün gemacht
> — und den Befund gelöscht."* Genau das hätte 90 Lehren endgültig gekostet.

**Deine Stichprobe:** `git -C process log --oneline -3 knowledge/` — der oberste Commit
stellt sie wieder her. Neu gebaut ist eine Prüfung, die **Namen nennt** statt eine
Differenz zu melden.

### ✅ Dein Projekt `team-termine` steht — und liegt bewusst nicht dort, wo geplant war

Gegründet als **P16** nach deiner Entscheidung `pm/D016` = B: Projektauftrag mit
**Abgrenzung** (kein zweiter Postfachzugang, kein Einladungsversand an Dritte, keine
weiteren Konten, kein Ändern fremder Termine, keine Kalenderinhalte in Git), Sprint-0-Plan
mit sechs Risiken, 12 Aufgaben, 2 Workflows, Entscheidungslog.

⚠ **Die Bestätigungsstufe vor jedem Schreibvorgang ist Schritt 1 des Plans** — sie wird
als Anforderung formuliert, **bevor** ein Schreibweg entsteht. Sie war Teil deiner
Entscheidung und ist keine Zutat, die man am Ende ergänzt.

**⚠⚠ Und beim Gründen ist etwas aufgefallen, das dich unmittelbar betrifft.** Unser
Gründungswerkzeug nahm die Angabe „Datenklasse: sensibel" entgegen, **prüfte** sie — und
legte das Projekt trotzdem unter `projects/` an, also in ein Repo **mit** GitHub-Remote,
das wir bei jedem Lauf pushen. Die Angabe landete als **Kommentarzeile** im Steckbrief.

> **Eine Datenklasse, die nur beschriftet und nicht platziert, ist keine Schranke, sondern
> eine Aufschrift — und sie stand in einem Kommentar, also an der einzigen Stelle, die kein
> Werkzeug von uns liest.**

Der Kalender deiner Familie wäre bei der nächsten Ausführung von `abschluss.cmd`
mitgegangen. **Behoben:** `team-termine` liegt jetzt als eigenes Repo **ohne Remote**
(`.kein-remote`), genau wie `team-mail`. **Nächster Schritt bei dir: die Zugangsdaten.**
Sie blockieren das Widget und die Planung **nicht**.

⚠ Nebenbefund am echten Bestand: **`p13` war seit seiner Freigabe ohne Mannschaft** — sein
Steckbrief trug keinen Status, und unser Resolver überspringt statuslose Einheiten
stillschweigend. Repariert; `p13` hat jetzt seine 10 Rollen.

### ✅ Dein Post-Widget ist gebaut — und eine Kachel deiner Vorlage können wir nicht füllen

Deine Antwort um **12:26** (*„1. 180 Zeichen ok. 2. Aufklappen 3. die eine Reaktion
verlangen"*) kam **mitten in diesem Lauf** und hat das Ticket entsperrt, das seit Sprint 32
darauf wartete. Gebaut ist es im selben Sprint: 2×2-Raster, echte Zahlen, 180 Zeichen als
**benannte Konstante** (damit deine Festlegung eine Festlegung bleibt).

**⚠⚠ Für `SPAM` führt dein Digest keine Rubrik.** Wir haben dort **keine 0**
hingeschrieben.

> **Eine 0 hieße „kein Spam". Niemand sieht einer 0 an, dass sie erfunden ist.**

Die Kachel steht da, sagt „keine Daten", nennt den Grund **und die Ticketnummer**
(`team-mail/T-0007`). **Sag einmal Bescheid, wenn du die Zahl willst** — dann bekommt der
Digest die Rubrik.

⚠ **Noch nicht fertig: das Aufklappen.** Es ist der erste Punkt überhaupt, an dem die
Oberfläche das PIN-Lesegate benutzt, und ein Gate, das im Frontend falsch bedient wird, ist
schlimmer als keines. Abgetrennt als `team-dashboard/T-0006`, Sprint 35. Wir sagen das
lieber, als es dir beim Antippen auffallen zu lassen.

**Deine Stichprobe:** Server neu starten → Dashboard → beim Wochendigest steht unter
„Rechnung" eine **0** (das ist ein Ergebnis), unter „SPAM" **„keine Daten"** mit Grund
(das ist keins).

### ⚠ Eine Abnahme von dir war vier Tage lang ohne Gegenstand

Du hast am **17.08. um 21:57** die Baseline `p12-v1.0` abgenommen (`p12/T-0010`, Option A).
**Der Tag wurde nie gesetzt.**

> **Vier Tage lang war ein Projekt abgenommen, ohne dass es einen abgenommenen Stand gab.
> Der Steckbrief sagte „abgeschlossen", die Entscheidung stand im Log — und der Gegenstand,
> auf den sich beide beriefen, existierte nicht.**

Nachgetragen — ⚠ auf den **Stand von damals** und **nicht auf heute**: ein Tag auf heute
würde behaupten, du hättest den heutigen Stand abgenommen. Neu gebaut ist die Prüfung, die
das künftig meldet; sie zählt heute **13 abgenommene Baselines und 13 Tags**.

⚠ Nebenbei: **die Frage im Brief war anders gestellt, als die Lage ist.** Du hattest
gefragt, warum „seit dem 07.08." keine Baseline gezogen wurde. Die letzten sind vom
**16.08.**; der 07.08. gehört einer anderen Baseline-Linie. Und beide Ursachen, die wir
vermutet hatten (Ollama, der stehende Push), waren **falsch**.

### ⚠⚠ Das Gegenlesen hat sieben Fehler in unserer fertig gemeldeten Arbeit gefunden

Dritter Sprint in Folge, und keinen davon haben wir selbst gefunden. Alle sieben sind im
selben Lauf behoben. Zwei davon sind es wert, hier zu stehen:

**Eine Anforderung verlangte drei Dinge und sicherte zwei.** Der ungeprüfte Halbsatz war
genau der, dessen Fehlen `p13` sein Core Team gekostet hatte. Der Prüfer entfernte ihn aus
dem Code — **139 Tests, kein einziger rot**.

> **Ein Halbsatz in einer Anforderung, den keine Zusicherung vertritt, ist eine
> Absichtserklärung.**

**Und derselbe Bau, der eine Doppelung benennt, hat eine neue angelegt** — zwei Listen mit
verschiedenem Inhalt und einem Kommentar daneben, der ihre Gleichheit *behauptet*.

> **Ein Kommentar behauptet. Eine Zusicherung stellt her.**

### ⚠ Zwei eigene Fehler dieses Laufs, benannt statt geglättet

**Erstens:** wir haben denselben Schreib-statt-Anhängen-Fehler gemacht, den wir eine Stunde
vorher als Lehre aufgeschrieben hatten — ein Ticket verlor seinen Kopf. Wiederhergestellt.

**Zweitens, und das ist der interessantere Teil:** unsere erste Erklärung dafür war, unser
Werkzeug habe den Schaden gar nicht sehen können. Nachgemessen: **es hat ihn gesehen und
den Dateinamen genannt.** Der Aufruf lief mit weggeworfener Ausgabe.

> **Eine Prüfung, deren Ausgabe man wegwirft, ist teurer als keine — sie erzeugt den
> Eindruck, geprüft zu haben.**

**Drittens:** unsere Kennzahl „Briefe im Lauf" meldet **0**, obwohl deine Nachricht um
12:26 eingegangen ist. Sie liest nur, wann ein Brief **angelegt** wurde — du hast in einen
**vorhandenen** geschrieben. Die Zahl steht im Bericht **falsch und danebengestellt
richtig**; sie stillschweigend zu korrigieren hätte den Befund gelöscht
(`platform/T-0065`).

### ⚠ Dein Ollama-Takt: die Diagnose ist wieder eine andere — diesmal zu Ende gemessen

Sprint 33 sagte „seit der Reparatur kein Versuch". Jetzt gemessen: **wir können Ollama aus
unserer Umgebung gar nicht erreichen** — `localhost:11434` antwortet nicht,
`host.docker.internal` ist von der Netz-Allowlist gesperrt. Der Nachweis braucht **deinen**
Rechner. Vier Aufgaben hängen daran; beim nächsten Anlauf **entscheiden** wir, statt ein
viertes Mal zu terminieren.

**Zahlen:** Anforderungen **211 / 0 Lücken**, Tests **1529** in **107** Dateien — in Blöcken
gefahren, **1496 grün**, ⚠ **zwei Module ungeprüft** (sie überschreiten einzeln das Zeitlimit
unserer Umgebung; ihr Gegenstand ist ersatzweise direkt nachgewiesen), JS **114**,
Organigramm grün (**21** Dateien), Workflows **8 / 0** unabgedeckt, Work Products **56 / 0**,
Briefkasten **0 offen** (am Ende gemessen), offene Aufgaben **33** (davon 12 aus dem neuen
Projekt), auf dich wartend **0**, **0,00 € API**.


## Das Wichtigste (Stand Sprint 33, 2026-08-21)

1. **✅ DREI TICKETS GESCHLOSSEN (`SWR-204`, `SWR-205`, `SWR-206`), ACHT VERSCHOBEN —
   mit einem Grund, der keine Floskel ist.** Vier Tickets neu angelegt, zwei davon aus
   Messungen an eigenen Fehlern.
2. **⚠⚠ ZUM ZWEITEN MAL IN FOLGE IST DER ERTRAG DAS UNABHÄNGIGE GEGENLESEN — UND DIESMAL
   HAT ES EINE ANFORDERUNG UMGEDREHT.** Drei Tickets waren gebaut, zugesichert und auf
   `in_review`. Das Review fand **drei ernste Fehler**; keinen davon der Autor, keinen
   eine der eigenen Zusicherungen. Der schwerste ist ein **Zeitzonenfehler**: Briefe
   tragen **UTC**, das Sprintregister **Wanduhrzeit**, und der Vergleich warf den Offset
   weg statt ihn umzurechnen.
   > **⚠⚠ Zwei Stunden Versatz — länger als ein ganzer Sprint. Die Kennzahl, die den
   > Satz „keiner eingegangen" verhindern sollte, hätte ihn maschinell erzeugt.**
   Und sie hatte bereits Schaden angerichtet: der Bau hatte damit sein **eigenes
   Ursprungsticket „korrigiert"** — die Behauptung stand in `SWR-206`, im Ticket und in
   einer eingefrorenen Regressionsschranke. `platform/T-0057` hatte die ganze Zeit recht.
   > **Eine Zeitzone ist keine Formatfrage, sondern eine Maßeinheit. Und eine falsche
   > Messung, die eine KORREKTUR behauptet, ist teurer als gar keine.**
3. **⚠⚠ BEIDE ZÄHLUNGEN HABEN IHR EIGENES TICKET UMGESTELLT — ZUM SECHSTEN UND SIEBTEN
   MAL IN DIESEM HAUS.** `T-0058` fragte nach einem **vierten Ticket-Zustand** für drei
   Fälle; gezählt sind **8** Verweise in **5** Tickets — und **kein einziger**
   `blocked_by` des Hauses zeigte auf ein **offenes** Ticket, obwohl `SWR-193` genau das
   verlangt.
   > **Der Befund ist nicht „uns fehlt ein Zustand", sondern: EINE SPERRE WIRD NIE
   > ZURÜCKGENOMMEN, WEIL NICHTS DANACH FRAGT. Vier der acht waren Altpapier.**
   Der vierte Zustand ist **verworfen** — gemessener Preis: 9 Quelldateien, 153
   Zustands-Literale, für eine Lage, die in 386 Tickets **einmal** vorkam. Gebaut ist die
   fehlende **Prüfung**: null neue Wörter, Wirkung 4 Befunde → 0.
   `T-0054` nahm 3 Namen und 6 Literale an; es sind **5** und **7** — und einer der
   Fundstellen war ein **echter** Schaden: `offene_blocker` fragte `!= "done"`, ein
   **verworfener** Blocker hätte das abhängige Ticket für immer gesperrt.
4. **⚠⚠ DER AUFTRAGGEBER HAT WÄHREND DES LAUFS ENTSCHIEDEN — ZUM VIERTEN MAL AN EINEM
   TAG, NACH 47 MINUTEN BEI SIEBEN TAGEN FRIST.** `pm/D029` = **C**: die vier Aufgaben an
   `pm/T-0077` zeigen ab jetzt auf die **offene** `platform/T-0060`.
   > **Damit war die namentliche Ausnahmeliste nach VIER STUNDEN leer. Eine
   > Ausnahmeliste, die man leer bekommt, war die richtige Bauform — ein vierter
   > Ticket-Zustand wäre für immer geblieben.**
   ⚠ **Und er hatte inhaltlich recht:** unsere Ollama-Diagnose war fünf Sprints alt. Alle
   11 Fehlschläge liegen **vor** der Reparatur vom 20.08. 20:45, seither gab es **keinen
   einzigen Versuch**, und der eine erfolgreiche Lauf trug `gemma3:27b`.
   > **Eine Fehlerliste ohne Zeitachse ist keine Diagnose, sondern ein Archiv, das sich
   > wie ein Befund liest.** `platform/T-0060`.
5. **⚠ EINE EIGENE ZUSAGE HATTE KEINEN LESER.** Die Gründung des Projekts `team-termine`
   (`pm/D016` = B) stand als *„nächster Schritt: `pm/T-0083`"* im Schlussabsatz eines
   **geschlossenen** Tickets — mit Nummer, aber ohne Ticket. Gefunden hat es die
   Sprint-Planung beim Abgleich der Zusagen gegen den Bestand.
   > **Eine Zusage in einem geschlossenen Ticket ist keine Aufgabe. Eine genannte Nummer
   > deckt die Lücke besonders gut zu — sie sieht aus wie ein Verweis auf etwas
   > Vorhandenes.**
6. **⚠ NICHT REPARIERT UND BENANNT (Kap. 16): 84 VON 119 LEHREN STEHEN IN KEINEM
   LEHRBUCH.** Die Kennzahl „Lehren: 121" zählt **Zitate im ganzen Haus**, die Prüfung
   „ohne Vertreter" zählt **Köpfe im Lehrbuch** — zwei Zahlen unter einem Namen, und die
   rote Zusicherung meldete den Unterschied als *„gewonnene Vertreter"*.
   > **Eine Lehre, die nur im Abschlussbericht steht, ist eine Erinnerung an einen
   > Sprint. Erst im Lehrbuch ist sie eine Regel für den nächsten.** `platform/T-0061`.
   ⚠ Die Basis auf den heutigen Stand zu setzen hätte die Prüfung in einer Minute grün
   gemacht **und den Befund gelöscht**. Sie bleibt rot.
7. **Zahlen:** **206** SWRs / **0** Lücken (v1.91), **1480** Tests / **101** Dateien,
   Organigramm grün (20 Dateien), Briefkasten **0 offen** (am **Ende** gemessen),
   `briefe_im_lauf` **0**, offene Tickets **20**, auf den Menschen wartend **0**,
   tote Sperren **0** bei **leerer** Ausnahmeliste. **Ollama-Offload: nichts delegiert,
   Token-Ersparnis 0 — gemessen.**

---

## Das Wichtigste (Stand Sprint 32, 2026-08-21)

1. **✅ ZWEI TICKETS GESCHLOSSEN WIE GEPLANT (`SWR-201`, `SWR-202`), EIN DRITTES AUS EINER
   MESSUNG WÄHREND DES LAUFS (`SWR-203`).** Aus dem Plan **nichts verschoben**. **13**
   Tickets neu angelegt — **elf davon aus Briefen und Entscheidungen des Auftraggebers**,
   die während des Laufs eintrafen.
2. **⚠⚠ DER ERTRAG DIESES LAUFS IST DAS UNABHÄNGIGE REVIEW, NICHT DER BAU.** `SWR-201`
   war in der ersten Fassung **kaputt** — und alle sechs eigenen Zusicherungen waren grün.
   Vier Befunde der Schwere *hoch*:
   > **⚠⚠ Die Ausnahme war an „ein Sprint läuft" gebunden statt an „diese Planzeile
   > gehört zu ihm". Während gearbeitet wird, läuft aber immer einer — eine Bedingung,
   > die während der ganzen Arbeitszeit wahr ist, ist keine Bedingung, sondern ein
   > offenes Tor mit einer Aufschrift.**
   Dazu: ein **Schlupfloch über `rejected`** (ein unbequemes Ticket verwerfen hätte die
   Meldung beseitigt), eine **Verdrahtung ohne Zusicherung** (das Review entfernte Aufruf
   und Payload-Schlüssel — alle sechs blieben grün), und die Anforderung stand auf
   `reviewed`, **bevor** das Review lief. `L-2026-08-21cq`, `ct`.
3. **⚠⚠ ZUM FÜNFTEN MAL „ERST ZÄHLEN, DANN BAUEN" — UND ZUM FÜNFTEN MAL HAT DIE ZAHL DIE
   FRAGE VERÄNDERT.** `T-0053` fragte, welche von **zwei** Zählweisen für „offene Tickets"
   bleibt (9 gegen 12). Gezählt sind **drei** Erzeuger, und **zwei folgten der Festlegung
   bereits**.
   > **Ausgerechnet die beiden, die sich den NAMEN `tickets_offen` teilten, waren die, die
   > sich widersprachen. Es gab nie zwei berechtigte Größen unter einem Namen, sondern
   > EINE Größe mit einem abweichenden Erzeuger — dem jüngsten.**
   `SWR-202`; `SWR-113` hat nach **zwanzig Sprints** endlich einen Vertreter.
   `L-2026-08-21cr`.
4. **⚠⚠ DIE SPERRKLINKE AUS SPRINT 30 IST BEIM ERSTEN GEBRAUCH GEBROCHEN WORDEN.** Als der
   Auftraggeber drei Anfragen beantwortete, vergab die Inbox `D014`–`D016` in `pm` — IDs,
   die `p0` seit dem 06.08. trägt. **Die mehrdeutige Menge wuchs an einem Tag von 14 auf
   17.** `SWR-197` hatte geschrieben, seine Sperrklinke sei „an der Vergabe" gebaut;
   gemessen las `_naechste_d_id` weiterhin **ein** Log.
   > **Eine Prüfung, die neben der Vergabe steht und sie nicht anfasst, ist kein Riegel,
   > sondern ein Zeuge — und bei einem append-only Log ist „gemeldet" wertlos.**
   `SWR-203`, `L-2026-08-21cu`. Der Altbestand ist ehrlich fortgeschrieben, **aber nur
   zusammen mit der Reparatur**.
5. **⚠⚠ ACHT BRIEFE KAMEN WÄHREND DES LAUFS — UND DER HAKEN „BRIEFKASTEN ERFÜLLT" STAND
   SCHON.** Beim Start: 0 offen, korrekt gemessen. Beim Abschluss: 8, alle zwischen 06:32
   und 08:07 eingegangen. Alle beantwortet und qualifiziert.
   > **„Briefkasten zuerst" ist eine Reihenfolge und keine Zusicherung. Was am Anfang
   > gemessen und am Ende berichtet wird, ist eine Momentaufnahme in der Aufmachung einer
   > Garantie.**
   ⚠ **Und dieselbe zu enge Discovery ein zweites Mal im selben Lauf:** die Ticketsichtung
   las nur `*/tickets/` — **`p13/T-0001` und damit eine Projekt-Freigabe des Auftraggebers
   ist der Planung entgangen.** `L-2026-08-21cs`, `platform/T-0057`.
6. **⚠⚠ DER AUFTRAGGEBER HAT ALLE DREI OFFENEN ENTSCHEIDUNGEN IM LAUF BEANTWORTET —
   ZWEI DAVON MINUTEN NACH ANLAGE.** `pm/D014` = **A** (`T-0077`, nach **vier Sprints**
   in einer Empfehlungsliste: **sieben Minuten**, bei sieben Tagen Frist), `p13/D000` =
   **G0a** (Projektauftrag p13 freigegeben), `pm/D015` = **B** und `pm/D016` = **B**
   (38 Minuten nach Anlage).
   > **⚠⚠ Fragen ist billiger als Ausweichen, und den Preis des Ausweichens zahlt nicht
   > der, der fragt.** Dritte Messung derselben Sorte.
   ⚠ Bei `D015` hat er die angebotene Option **präzisiert** („Nur dimitri.john83@gmail.com,
   kein zweites") — enger als angeboten. **Verbucht wie er es geschrieben hat, nicht wie
   wir es gemeint hatten.**
7. **⚠⚠ EINE LAGE OHNE ZULÄSSIGEN ZUSTAND, ZUM DRITTEN MAL IN DREI SPRINTS.** `D014` = A
   hat den Wartegrund von `pm/T-0071`, `promt-team/T-0003` und `T-0012` **bestätigt** statt
   beseitigt. `blocked` verlangt einen offenen Verweis, ein Termin wäre eine Zusage ohne
   Arbeitsvorrat, `done` wäre Option C — die nicht gewählt wurde.
   > **Unsere Zustände beschreiben, WER handeln muss, und haben keinen Ausdruck für
   > „niemand muss, und das ist entschieden".** `platform/T-0058`, prio hoch.
8. **⚠ UND EIN EIGENER FEHLER, DEN DIESER BERICHT ZWEI ABSÄTZE FRÜHER BESCHREIBT:** wir
   haben viermal `open -> done` **committet**, weil `in_progress` erst am Ende gesetzt und
   zusammen mit `done` verbucht wurde. **Die Prüfung liest Commits, nicht Arbeitsspeicher.**
   Die Liste der fortgeschriebenen Übergänge wächst **4 → 8**; die Hälfte gehört diesem
   Lauf. `L-2026-08-21cv`.
9. **VERIFIKATION (10:12):** **`PREFLIGHT: STARTKLAR`** (8 fortgeschrieben), Matrix
   **203 SWRs / 0 Lücken**, **1452 Tests** über **99** Dateien, `organigramm.py --check`
   grün (20 Dateien), Briefkasten **0 offen — am ENDE gemessen**, Workflows **6 / 0
   unabgedeckt**, Work-Product-Lücken **0** (56 WPs), Lehren **121 / 91 ohne Vertreter**
   (unverändert — alle **sechs** neuen haben einen), auf den Menschen wartend **0**,
   Parkplatz **11714** (Stand 10:07).
   ⚠ **Nicht gefahren und deshalb benannt (`SWR-189`):** `test_js_teststrecke`
   überschreitet in dieser Sandbox das Zeitlimit. Es wurde **kein JavaScript geändert** —
   aber „nicht betroffen" ist eine Behauptung, kein Messergebnis. Die übrigen **98**
   Module sind einzeln gelaufen.
10. **⚠ OLLAMA-OFFLOAD: NICHTS DELEGIERT, TOKEN-ERSPARNIS 0 — GEMESSEN.** `pm/T-0071` hat
    unverändert **keinen** Tick mit `status: ok` + Artefakt; die Run-Registry zeigt
    ausschließlich `status: fehler` (`model 'llama3.1:8b' not found`). Mit `D014` = A ist
    entschieden, dass sich daran nichts ändert.

**Deine Stichprobe:** `python platform\scripts\preflight.py --repos .` → `STARTKLAR`.
⚠ **Der Push-Rückstand ist auf fünf Tage und sechs Sprints gewachsen** — `abschluss.cmd`
ist der wichtigste offene Punkt.

---

## Das Wichtigste (Stand Sprint 31, 2026-08-21)

1. **✅ DREI TICKETS GESCHLOSSEN, NICHTS VERSCHOBEN — BEIDE NULLTEN TERMINIERUNGEN AUS
   SPRINT 30 UND DIE VIERTE BERÜHRUNG.** `platform/T-0051` (**SWR-198**),
   `platform/T-0050` (**SWR-199**), `platform/T-0049` (**SWR-200** — gebaut **und**
   geschnitten). Zwei neue Tickets, **beide aus Messungen dieses Laufs**: `T-0052`,
   `T-0053`.
2. **⚠⚠ DREIMAL AN EINEM TAG LAG DER FEHLER NICHT IN EINER PRÜFUNG, SONDERN ZWISCHEN
   ZWEIEN — DAS IST DER ROTE FADEN DES LAUFS.** Für ein **gesperrtes** Ticket gab es
   keinen zulässigen Terminwert: alter Sprint → Befund, leer → Befund, Zukunft → still,
   aber eine Zusage über fremdes Handeln.
   > **Eine Lage, in der die bequeme Handlung die einzige ist, die grün macht, ist genau
   > die Bauart, gegen die `SWR-166` gebaut wurde.**
   ⚠⚠ Und die Ausnahme **existierte bereits** — an einem **Typ** (`decision-request`)
   statt an einem **Zustand**, weil `blocked` erst seit `SWR-193` existiert, **einen
   Sprint alt**.
   > **Ein Stellvertreter, der lange mit der Sache zusammenfiel, wird zum Loch in dem
   > Moment, in dem die Sache einen eigenen Namen bekommt.**
   `SWR-198`, `L-2026-08-21cm`. **Am echten Bestand gemessen: `unterminierte_tickets`
   3 → 0**; der Schnelltakt meldet seitdem `[org] 0 Tickets ohne Sprint`. ⚠ Die Ausnahme
   hängt am `blocked_by`-**Verweis** und nicht am Wort — *„gesperrt" ohne Verweis ist eine
   Behauptung*, und eine Ausnahme, die auf ein Statuswort hört, wäre ein Schlupfloch für
   jedes unbequeme Ticket.
3. **⚠⚠ ZUM VIERTEN MAL „ERST ZÄHLEN, DANN BAUEN" — UND ZUM VIERTEN MAL HAT DIE ZAHL DIE
   FRAGE VERÄNDERT.** `SWR-194` nannte seine Grundmenge die *„ehrliche Untermenge"*.
   Gemessen: **24 %** der 38 „Erkannten" haben einen Vertreter, **15 %** der 73
   „Übersehenen".
   > **Die Menge war nie eine Auswahl von Lehren, die einen Vertreter BRAUCHEN. Sie war
   > eine Auswahl von Lehren, die jemand mit Doppelpunkt geschrieben hat.**
   ⚠ Die zweite Messung hat die **Bauform** bestimmt: zwischen „Muster erweitern"
   (111 von 112) und „Filter weglassen" (112) liegen **null** Lehren — beide ergeben 91.
   **Von zwei gleichwertigen Bauformen ist die mit einem Begriff weniger die richtige.**
   `SWR-199`, `L-2026-08-21cn`. Kein einziger Dauerbefund: der Bestand ist **benannt**,
   rot wird nur Neues — ab jetzt in **jeder** Schreibweise. Der Ausstieg heißt
   `**Beobachtung:**` und ist eine **Handlung** statt eines Nebeneffekts der
   Zeichensetzung.
4. **⚠⚠ DIE VIERTE BERÜHRUNG HAT IHRE EIGENE VERMUTUNG WIDERLEGT.** Drei Sprints lang
   galt: *„es gibt einen zweiten SCHREIBWEG ins Entscheidungslog."* Gemessen über 17 Logs
   und 158 Zeilen: **es gibt keine zweite Funktion.**
   > **Der zweite Schreibweg ist die HAND — und er ist nicht die Ausnahme, sondern die
   > MEHRHEIT: 103 von 158 Zeilen (65 %).**
   ⚠ Geschnitten ist die Nummernvergabe, und der Grund ist gemessen: der Schaden wird seit
   `SWR-195` (Sprint 29) und `SWR-197` (Sprint 30) bereits gefangen — von Tickets, die
   **nach** dieser Frage entstanden sind. **Die Frage hat ihre eigene Antwort überlebt.**
   Neue Regel: bei jeder Terminierung eines weitergereichten Tickets wird nicht nur der
   **Grund** der Verschiebung geprüft, sondern die **Gültigkeit der Frage**.
   `SWR-200`, `L-2026-08-21co`.
5. **⚠⚠ EINE ZUSICHERUNG AUS SPRINT 30 HAT DIESE SESSION AUFGEHALTEN — UND GENAU DAFÜR
   WAR SIE GEBAUT.** `test_termin_zange_blocked.py` sicherte den **Mangel** und trug den
   Auftrag *„wird mit T-0051 UMGEDREHT und nicht gelöscht"* in ihrem eigenen Text. Nach
   dem Bau von `SWR-198` wurde sie rot.
   > **Eine Zusicherung, die einen Mangel BENENNT statt ihn zu verschweigen, meldet seine
   > Behebung von allein. Wäre der Mangel nur in Prosa vermerkt gewesen, hätte die Datei
   > nach dem Fix schweigend weiter den alten Zustand beschrieben.**
   ⚠ Und sie hat dabei einen **zweiten, echten Fehler** gefunden, den keine neue
   Zusicherung dieses Laufs gesehen hätte: `board.parse_liste` brach an einer **echten
   Liste** mit `AttributeError` — es kannte nur Text aus dem Frontmatter. **Eine
   Zerlegefunktion, die an ihrem eigenen Ergebnis scheitert, ist nicht idempotent.**
   `L-2026-08-21cp`.
6. **⚠⚠ DER SCHNELLTAKT LÄUFT — UND DIESE SESSION HAT IHN SELBST BLOCKIERT.** Um **06:15**
   meldete der Preflight zweimal `STARTKLAR`. Ab **06:30** bis **07:01**: dreimal
   `1 Befund`, **6 Ticks abgebrochen** — und der Befund war jedes Mal die Statusdrift, die
   **diese Session** erzeugt hat, indem sie ihre drei Tickets schloss.
   > **⚠⚠ Der Plan wird laut `pm/D006` am Sprint-ABSCHLUSS fortgeschrieben. Also ist der
   > Bestand während JEDES Sprints widersprüchlich — per Konstruktion —, und genau in
   > diesem Fenster kann der Schnelltakt nie laufen. Das ist kein Ausrutscher, das ist die
   > Dauer eines Sprints.**
   ⚠ Das **stellt richtig**, was die Agenda seit Sprint 30 behauptet: `pm/T-0077` ist
   **nicht** die einzige Sperre vor dem Ollama-Offload. Beide bisherigen Diagnosen waren
   für ihren Messzeitpunkt richtig — gemessen wurde jeweils am **Ende** einer Session, wenn
   der Plan schon stand. **Eine Ursache, die nur am Ende eines Laufs gemessen wird, kann
   einen Zustand nicht sehen, der nur WÄHREND des Laufs besteht.** `platform/T-0052`,
   prio hoch, aufgeschrieben und terminiert statt schnell repariert.
7. **⚠ ZWEI WERKZEUGE ZÄHLEN „OFFENE TICKETS" VERSCHIEDEN — UND ES WAR SCHON ENTSCHIEDEN.**
   `sprint.kennzahlen` sagt **12** (Status weder `done` noch `rejected`, `SWR-113`),
   `kennzahlen.py` sagt **9** (`status == "open"`). Die Differenz sind **genau die 3
   gesperrten** Tickets. `SWR-113` ist in Sprint 7 zu **genau dieser Frage** gebaut worden
   — *„eine unwiderlegbare Kennzahl ist keine"*.
   > **Die Festlegung stand in einem Docstring und in keiner Zusicherung. Das ist wörtlich
   > `SWR-125`: eine Entscheidung, die keine Prüfung mitgeändert hat, ist eine
   > Absichtserklärung.**
   Beide Zahlen stehen **mit ihrer Definition** im Bericht; keine wird still gewählt.
   `platform/T-0053`.
8. **⚠ DER OLLAMA-OFFLOAD IST WEITERHIN NICHT DELEGIERT.** `pm/T-0071` hat unverändert
   **keinen** Tick mit `status: ok` + Artefakt — der Nachweis **fehlt** und wird hier
   benannt, damit er nicht später als erledigt gilt, weil ihm niemand widersprochen hat.
   **Kein Ticket delegiert; Token-Ersparnis 0 — gemessen, nicht geschätzt.**
9. **VERIFIKATION:** **1429 Tests** über **95** Testdateien (zwei unabhängige Messungen,
   deckungsgleich), Matrix **200 SWRs / 0 Lücken**, `organigramm.py --check` grün
   (19 Dateien), **`PREFLIGHT: STARTKLAR`** (4 fortgeschrieben), Briefkasten **0 offen /
   0 eingegangen**, Workflows **6 / 0 unabgedeckte Takte**, Work-Product-Lücken **0**
   (56 WPs), Lehren **115 / 91 ohne Vertreter** (= die benannte Basis, alle vier neuen
   Lehren haben einen), unzulässige Statusübergänge im laufenden Sprint **0**, Parkplatz
   **11540** (Stand 07:20).

**Deine Stichprobe:** `python platform\scripts\preflight.py --repos .` → `STARTKLAR`;
`ollama-schnelltakt.log` muss ab dem nächsten Lauf wieder `PREFLIGHT: STARTKLAR` zeigen
statt `Tick abgebrochen` — das ist der Nachweis für Punkt 6 am laufenden System.

---

## Das Wichtigste (Stand Sprint 30, 2026-08-21)

1. **✅ ZWEI TICKETS GESCHLOSSEN, NICHTS VERSCHOBEN — BEIDE WAREN NULLTE TERMINIERUNGEN
   AUS SPRINT 29 UND SIND IM FOLGELAUF GEBAUT WORDEN, WIE ANGEKÜNDIGT.**
   `platform/T-0047` (**SWR-197**), `platform/T-0048` (**SWR-196**). Zwei neue Tickets aus
   **Messungen**: `T-0049`, `T-0050`. Offene Tickets **8 → 10**.
2. **⚠⚠ DIE VORHERSAGE AUS SPRINT 29 IST EINGETRETEN UND IST JETZT EINE MESSUNG.** Um
   **04:15** — dem ersten Schnelltakt-Lauf nach dem Commit von `SWR-191` um 04:10 — steht
   `PREFLIGHT: STARTKLAR` im Log statt `Preflight hat Befunde`. Davor **65** Abbrüche.
   > **⚠⚠ UND DAHINTER STAND EIN ZWEITER BLOCKER, DEN DER ERSTE VERDECKT HAT — das ist
   > der eigentliche Befund dieses Laufs.** 2 von 2 Ticks endeten trotzdem ohne Ergebnis.
   > `waehle_ticket` gab `kandidaten[0]` zurück; die Besetzungsprüfung lief **danach**.
   > **Eine Prüfung nach der Auswahl ist kein Filter, sondern ein Veto gegen genau einen
   > Kandidaten — die Zweitplatzierten werden nie angesehen.** `SWR-196`,
   > `L-2026-08-21cj`. Wirkung am echten Bestand gemessen, nicht versprochen.
3. **⚠⚠ DIE ALTE MELDUNG WAR WAHR UND ZU ENG, UND DAS IST DER ZWILLING DES FALSCHEN
   BEFUNDS AUS SPRINT 29.** *„… T-0001 bleibt unangetastet"* las sich wie ein Zufall;
   gemessen ist ein Zustand: **0 von 8** offenen Tickets tragen eine ollama-besetzte Rolle
   (cm 2, pl 4, coach 1, dev 1 gegen `PROB@platform`, `MAIL-RED@team-mail`).
   > **Die enge Aussage lädt zum Wiederkommen in 15 Minuten ein — und der Takt hat das
   > 90-mal getan. Sie trainiert dasselbe Wegsehen wie ein falscher Befund, nur mit
   > besserem Gewissen.** `L-2026-08-21cl`.
   ⚠ Der Zustand war seit dem 20.08. gemessen — die Zahl stand im **Docstring einer
   Funktion**, nicht in der Meldung, die der Betrieb 90-mal gedruckt hat.
4. **✅ ZUM DRITTEN MAL „ERST ZÄHLEN, DANN BAUEN" — UND ZUM DRITTEN MAL HAT DIE ZAHL DIE
   FRAGE VERÄNDERT.** `T-0047` Vorabfrage 1: von **1023** praefixlosen Zitaten stehen
   **743 (73 %)** im besitzenden Repo, **65 (6 %)** nennen eine nur einmal vergebene ID,
   **214 (21 %)** sind echt mehrdeutig. `T-0036` hatte recht — die 1003 waren keine 1003
   Probleme.
   > **⚠⚠ Und alle 214 nennen eine von VIERZEHN IDs (`D000`–`D013`). Ab `D014` ist jede ID
   > organisationsweit einmal vergeben. Der Mangel ist ein PRÄFIX DES NUMMERNRAUMS und
   > keine Eigenschaft des Korpus** — also ist die Sperrklinke an der **Vergabe** gebaut.
   `SWR-197`, `L-2026-08-21ck`.
5. **⚠⚠ DAS ARGUMENT GEGEN DEN URSPRÜNGLICH GEPLANTEN ZUSCHNITT IST AN DIESER SESSION
   SELBST GEMESSEN.** Während des Baus stiegen die Zahlen von 1023/214 auf **1030/216** —
   allein dadurch, dass Ticket und Anforderung **über** das Problem schreiben.
   > **Eine Prüfung auf die Zitatzahl hätte jeden Bericht bestraft, der den Befund
   > erklärt: ein Dauerbefund, den das Erklären selbst füttert.**
6. **⚠⚠ DER UNANGENEHMSTE BEFUND BETRIFFT DIE EIGENE PRÜFUNG AUS SPRINT 29.** `SWR-194`
   hätte **drei** Lehren dieses Laufs übersehen — sie standen als `**Regel.**` statt
   `**Regel:**`; die Zählung blieb bei 34/29, als gäbe es sie nicht.
   > **Der Fehler ist nicht das Durchrutschen, sondern dass die Prüfung dabei GRÜN
   > geblieben ist. Eine Sperrklinke, die man mit einem anders gesetzten Doppelpunkt
   > umgeht, ist keine.**
   Gemessen: **34** von **111** Lehren tragen `**Regel:**`, **110** tragen irgendeine
   Regel-Schreibweise — **76 übersehen**. ⚠⚠ Die als *„gefunden und nicht erfunden"*
   begründete Konvention **unterscheidet nichts**: die 34 sind eine Schreibweise.
   `platform/T-0050`. ⚠ Die drei Lehren sind nachgezogen und haben Vertreter
   (`ohne_vertreter` wieder **29**); **die Lücke bleibt und ist terminiert, nicht
   geschlossen** — die naheliegende Reparatur erzeugte ~100 Dauerbefunde und wäre
   `SWR-166` ein viertes Mal.
7. **⚠⚠ EIN VIERTER BEFUND, BEIM AUFRÄUMEN GEFUNDEN: FÜR EIN GESPERRTES TICKET GIBT ES
   KEINEN ZULÄSSIGEN TERMINWERT.** Drei gesperrte Tickets wurden als *„offen auf
   vergangenem Sprint"* gemeldet; nach dem Leeren des Termins meldet sie
   `unterminierte_tickets` als *„Ticket ohne Sprint"*.
   > **Zwei Prüfungen bilden eine Zange. Still ist nur eine Terminzusage über fremdes
   > Handeln — also die falsche Handlung.**
   ⚠ Beide Prüfungen sind einzeln richtig; der Fehler liegt **zwischen** ihnen: die
   Ausnahme steht an einem **Typ** (`decision-request`), wo sie einen **Zustand** meint —
   `blocked` gibt es erst seit `SWR-193`, **einen Sprint lang**. ⚠ **Das stellt Sprint 29
   richtig: dort ist nichts liegengeblieben, es gab nichts Besseres.** `platform/T-0051`,
   prio hoch.
8. **⚠ KEIN OLLAMA-OFFLOAD — ABER DER GRUND IST EIN NEUER.** `pm/T-0071` hat unverändert
   keinen Tick mit `status: ok` + Artefakt. Neu ist, **woran es liegt**: nicht mehr am
   Preflight, sondern am leeren Arbeitsvorrat. **Kein Ticket delegiert; Token-Ersparnis
   0 — gemessen, nicht geschätzt.**
9. **1404 Python-Tests** über **93** Testdateien (**gemessen**; Gegenrechnung: 1367 + 37 der drei neuen Dateien = 1404, deckungsgleich), Matrix **197 SWRs / 0 Lücken**,
   Briefkasten **0 offen / 0 eingegangen**, offene Tickets **10**, auf den Menschen
   wartend **1** (`pm/T-0077`, Frist 28.08.), Workflows **6 / 0 unabgedeckte Takte**,
   Work-Product-Lücken **0**, Parkplatz **11325** (Stand 05:06, `SWR-174`).

---

## ⚠ Der Schnelltakt läuft — und hat nichts zu tun

Sprint 29 stand hier mit einer **Vorhersage**. Sie ist eingetreten. Was jetzt im Log steht:

```
Kein bearbeitbares Ticket (Besetzung): 2 offene(s) Ticket(s) geprüft, keines trägt eine
Rolle mit motor 'ollama' in Einheit 'platform' — Rollen im Bestand: CM; mit motor 'ollama'
besetzt in dieser Einheit: PROB@platform. Der Bestand hat für diese Besetzung nichts —
ein weiterer Lauf ändert das nicht.
```

⚠⚠ **Das ist kein Fortschritt in der Sache, sondern in der Auskunft.** Gearbeitet wird
weiterhin nichts. Der Unterschied: vorher sah es nach Pech aus, jetzt steht der Zustand da
— und die Handlung, die ihn abstellt, ist eine Entscheidung und kein weiterer Lauf.
**`pm/T-0077` ist damit die einzige verbliebene Sperre; alles Technische davor ist
repariert.**

---

<details><summary>Archiv: Sprint 29 und früher</summary>


## ⚠ Der Preflight meldet in diesem Lauf KEINEN falschen Befund mehr

Sprint 28 stand hier mit *„der Preflight meldet ZWEI FALSCHE BEFUNDE"*. Das ist erledigt:
`SWR-191` vergleicht den **Baum** mit HEAD statt den **Index** mit HEAD.

**Stichprobe:** in `platform` oder `pm` sagt `git status` weiterhin `MM` für Dateien, die
committet sind (solange ein `index.lock` liegt) — der **Preflight** sagt es nicht mehr.
Und wenn eine Sperre liegt, steht dort jetzt eine **eigene** Zeile mit eigenem Wortlaut,
die **keinen Befund zählt**.

⚠ **Was das für deinen Schnelltakt heißt:** der Abbruch aus diesem Grund sollte aufhören.
**Das ist eine Vorhersage und keine Messung** — eine Cowork-Session kann deinen Takt nicht
auslösen. Bricht er weiter ab, ist es etwas anderes, und dann bitte melden.

---

## ⚠⚠ WICHTIG FÜR DEN NÄCHSTEN BLICK: der Preflight meldet ZWEI FALSCHE BEFUNDE

Der Abschluss-Preflight dieses Laufs sagt:

```
[platform] BEFUND: 3 Datei(en) … sind nicht committet
[pm]       BEFUND: 1 Datei(en) … sind nicht committet
```

**Das stimmt nicht, und es ist nachgemessen.** Über **alle 17 Repos** gilt:
`git diff HEAD` gegen einen **frischen** Index → **0 abweichende Dateien**. HEAD und
Arbeitskopie sind überall byte-identisch.

> **⚠⚠ Die Prüfung vergleicht den INDEX mit HEAD statt den BAUM mit HEAD. Ein
> stehengebliebenes `index.lock` (0 Byte, auf diesem Mount **nicht löschbar**) friert den
> Index auf dem Stand vor dem Commit ein — und die Prüfung meldet Arbeit als offen, die
> committet ist.** Erfasst als **`platform/T-0046`**.

**Was das für dich heißt:** dein Schnelltakt bricht bei jedem Lauf ab, solange das so
steht — der Preflight ist sein Tor. Das hört auf, sobald `abschluss.cmd` **auf dem Host**
läuft, wo die Sperre löschbar ist.

**Stichprobe, ob es wirklich falsch ist** (in `platform` oder `pm`):

```
git diff HEAD --name-only     →  leere Ausgabe = alles committet
git status                    →  zeigt „MM" = der veraltete Index, nicht die Wahrheit
```

⚠ **Und das ist der eigentliche Preis des Parkplatzes:** `SWR-164` führt ihn seit Sprint 24
als *„ausdrücklich KEIN Befund"*. Er ist in diesem Lauf von **10533 auf 11001** gewachsen
(**+468 an einem Abend**) und hat zum ersten Mal **Arbeit blockiert** statt nur Platz zu
belegen.

## Was der Auftraggeber tun kann

1. **`pm/T-0077` beantworten** — A/B/C, Frist 28.08., Default A. Die Frage, die drei
   Tickets seit vier Sprints aufhält. Schweigen kostet nichts, **hat aber einen im Antrag
   benannten Preis**.
2. **`abschluss.cmd` ausführen** — Rückstand: fünf Tage **plus der gesamte
   Projektmodell-Rework** plus Sprint 28. **Stichprobe:** danach steht in
   `abschluss-auto.log` `OK - alles geprueft und gepusht`, und `PUSH-ANFORDERUNG.txt` ist
   verschwunden.
3. **Mission-Control-Server neu starten** — neue Routen und zwei neue Reiter aus dem Rework.
4. **`.git/verwaiste-locks` löschen** — **10904** Dateien (02:16). ⚠ Neu: erstmals nicht
   folgenlos.
5. **Alte Punkte:** `team-mail/N-0003` (Mail-Zugangsdaten), Kachelzählung im Reiter
   „Dashboard", `ollama list`.

---

## Das Wichtigste (Stand Sprint 27, 2026-08-20)

1. **⚠⚠ EINE ANFORDERUNG WAR GRÜN, IN VIER GEGENPROBEN BELEGT — UND IHRE WIRKUNG WAR
   NULL.** `SWR-169` (Sprint 26) holt das Ollama-Modell aus dem Besetzungsregister. Alle
   vier Gegenproben prüften die **Auflösungsfunktion**, keine ihren **Aufrufer**. Im
   Betrieb bekommt sie Rolle und Einheit nie richtig.
   > **Gefunden hat es kein Preflight und kein Test, sondern der Schnelltakt des
   > Auftraggebers, der um 21:30 in Sprint 26 hineingefeuert hat. Ohne diesen Zufall hätte
   > Sprint 26 „SWR-169 gebaut" berichtet und wäre durchgekommen.**

   `platform/T-0033` (`prio: kritisch`), **`SWR-171`/`SWR-172`**.
2. **⚠⚠ UND DER BEFUND IST GRÖSSER ALS DER MODELLNAME.** Gezogen wurden `CM@platform`
   (`motor: cowork`) und `DEV@team-mail` — **letzteres existiert im Besetzungsregister
   überhaupt nicht.**
   > **Der Tick hat Arbeit an eine Instanz gegeben, die niemand besetzt. Der leere
   > Modellname war die FOLGE, nicht die Ursache — und eine Prüfung auf den Modellnamen
   > wäre still geworden, sobald irgendjemand irgendein Modell einträgt.**

   `SWR-171` prüft die **Besetzung**, vor Gateway-Aufruf, Branch und Statuswechsel;
   Rückgabe 0 mit dem Grund im Ergebniswort (die Bauform aus `SWR-167`).
3. **⚠ ERST GEZÄHLT, DANN GEBAUT — UND DIE ZAHL HAT DIE BAUART ENTSCHIEDEN: 0 VON 14.**
   Kein offenes Ticket trägt eine Rolle mit ollama-Besetzung.
   > **Die wörtliche Umsetzung von `pm/D010` wäre damit keine Lösung, sondern eine
   > Abschaltung.** Der Schalter (`--rolle`, `SWR-172`) ist **gebaut und nicht umgelegt**;
   > eine Zusicherung prüft, dass `ollama-schnelltakt.cmd` ihn nicht trägt.

   Vorgelegt als `platform/T-0035` (A/B/C, Frist 27.08., Default A) — es ist seine Automatik.
4. **✅ DER WIRKNACHWEIS KAM AUS DEM BETRIEB.** Um **22:00** hat der Schnelltakt erneut
   gefeuert. Log: `Tick OHNE ERGEBNIS (Besetzung): …`. Nachgemessen: **kein** neuer
   Run-Registry-Eintrag (letzter 21:46), `platform` und `team-mail` sauber auf `main`,
   `T-0001` unverändert `open`.
   > **⚠⚠ Derselbe Lauf hat unsere MUTATION ausgeführt** — die absichtlich verfälschte
   > Gegenprobenfassung stand um 22:00 auf der Platte, im Log des Auftraggebers steht
   > `IMMER ABBRUCH`. **Folgenlos, und es steht hier, weil es sonst niemand erführe.**
   > Eine Mutationsprobe an Code, den eine fremde Automatik alle 15 Minuten startet, ist
   > ein Eingriff in den Betrieb und keine Laborhandlung.
5. **⚠⚠ DIE GEGENPROBE ZUR GEGENPROBE HAT SICH SELBST GETÄUSCHT.** Erster
   Mutationsdurchgang: **grün** bei ausgeschalteter Prüfung. Ursache: die Mutation stand
   zum Testzeitpunkt nicht auf der Platte, ein alter `__pycache__` lag daneben. Zweiter,
   verifizierter Durchgang: 2 rot; „bricht immer ab": 1 rot (das Paar); Rücknahme: 20/20.
   > **Grün ist zweideutig — „die Prüfung greift nicht" oder „die Mutation ist nicht
   > angekommen". Es hätte als „Gegenprobe bestanden" im Bericht gestanden.**
   `L-2026-08-20cm`.
6. **✅ `platform/T-0027` BEI DER VIERTEN BERÜHRUNG: GEBAUT *UND* GESCHNITTEN.**
   **`SWR-173`** — `platform/scripts/kennzahlen.py` misst sieben Kennzahlen aus ihren
   Quellen (Sammlung statt Summe von Testläufen; ein **Ladefehler** zählt als eigener
   Befund, weil eine nicht importierbare Testdatei sonst als „weniger Tests" durchginge).
   **`SWR-174`** — eine Zusicherung hält den Bericht dagegen, **vor** dem Push; eine
   **fehlende** Zahl gilt als Abweichung, sonst wäre ein Bericht ohne Zahlen der grünste.
   ⚠ Der Parkplatz ist **mit Begründung im Test** von der Gleichheit ausgenommen und muss
   einen **Zeitpunkt** tragen. Erwartungswert vor dem Bau notiert: 0 Abweichungen.
   Gemessen: 0.
   ⚠ **Geschnitten:** die Rubrik **„gelernt ohne Vertreter"** ist `platform/T-0034`
   geworden — vorgegeben vom eigenen Text des Tickets. `L-2026-08-20cp`, Runbook Kap. 15.
7. **⚠⚠ EINE GEGEN FEHLSCHLÄGE GESCHÄRFTE BEDINGUNG WAR DURCH EINEN ERFOLG VON VOR
   VIERZEHN TAGEN SCHON ERFÜLLT.** `promt-team/T-0008` verlangte *„ein Tick mit
   `status: ok` und Artefakt"* und schrieb **„Stand: 0 von 3"**. In
   `p0/management/runs/run-registry.jsonl` steht seit dem 2026-08-06:
   `cm | ok | provider: ollama | artefakte: ['process/']`.
   > **Die Bedingung liest über den BESTAND, gemessen wurde ein EREIGNIS. Zweimal
   > hintereinander war die Grundmenge das, worauf niemand gesehen hat — `SWR-128` zum
   > dritten Mal.** Neue Bedingung mit benannter Grundmenge **und Stichtag**.
8. **⚠ DER EIGENE FEHLER DIESES LAUFS.** Der Abschluss von `T-0033` schrieb `status: done`
   direkt auf `open`; `board.py` hat abgelehnt — **neben** dem Commit (`;` statt `&&`)
   statt davor. Repariert über `open → in_progress → in_review → done`, je ein Commit; der
   Fehlcommit war lokal, ungepusht und ist zurückgenommen.
   > **Eine Prüfung, die neben dem Schreibvorgang läuft statt vor ihm, ist eine Meinung.**
   `L-2026-08-20cn`/`co`, Runbook Kap. 16 und 17.
9. **1280 Python-Tests** in der Sammlung (**gemessen**, **79** Testdateien), Matrix
   **176 SWRs / 0 Lücken**, Briefkasten **0 offen, 0 eingegangen**, entschiedene
   unverbuchte DRs **0**, auf den Menschen wartend **0**, Parkplatz **10533**
   (Stand 23:02 — die Zahl trägt ab jetzt ihren Zeitpunkt, `SWR-174`).

## Was der Auftraggeber tun kann

1. **`platform/T-0035` beantworten** — A/B/C, Frist 27.08., Default A. Sein Schnelltakt
   hat 0 von 14 Aufgaben. Schweigen kostet nichts.
2. **Eine Aufgabe für `PROB@platform` oder `MAIL-RED@team-mail` anlegen**, wenn der Takt
   wirklich arbeiten soll. Ohne eine solche gibt es nichts zu tun — das ist der Grund für
   den Leerlauf und keine Panne.
3. **`abschluss.cmd` ausführen** — Rückstand vier Tage plus **drei** Läufe.
   **Stichprobe:** danach steht in `abschluss-auto.log` `OK - alles geprueft und gepusht`
   und `PUSH-ANFORDERUNG.txt` ist verschwunden.
4. **`ollama list`** — unverändert von hier aus nicht messbar, solange aber nicht dringend.
5. **`p9/T-0008`** (Frist 27.08., Default A), **`team-mail/N-0003`** (Mail-Zugangsdaten).

---


---

## ⚠⚠ NACHTRAG: der Auftraggeber hat WÄHREND des Laufs BEIDE offenen Fragen beantwortet

| Frage | gestellt | beantwortet | Antwortzeit |
|---|---|---|---|
| `platform/T-0035` (Schnelltakt) | 22:18, **in diesem Lauf** | 22:21, **A** | **3 Minuten** |
| `p9/T-0008` (Wo leben die Anforderungen?) | Sprint 26, Frist 27.08. | 22:25, **A** + Anweisung | **7 Minuten** |

> **Zum zweiten Mal in zwei Sprints kostet das Fragen weniger als das Ausweichen. `T-0035`
> war die Frage, die diesen Sprint daran gehindert hat, die Automatik selbst umzustellen —
> sie war in drei Minuten beantwortet.**

**`platform/T-0035` = A:** alles bleibt. Der Takt läuft weiter und meldet ehrlich, dass es
für seine Besetzungen nichts zu tun gibt. **Keine Folgearbeit** — A ist der Zustand, den
dieser Lauf hergestellt hat. Kein Nachfolgeticket.

**`p9/T-0008` = A *plus* Anweisung:** *„Nennen P9 in Org-Cockpit um."* Der Antrag hatte A
und C als **Alternativen** angeboten; die Antwort nimmt A und den Kern von C.
> **Das ist keine Unentschlossenheit, sondern die genauere Auskunft: die Anforderungen
> bleiben liegen, wo sie liegen, und der Name sagt ab jetzt, was dort liegt. Identität und
> Beschriftung sind zwei Dinge — der Antrag hat sie als Alternativen behandelt.**

Ausgeführt als **`SWR-175`**: `steckbrief.yaml` trägt ein Feld `name`, Rangfolge
Team-Registry > Steckbrief > Ordnername. Im Organigramm steht **Org-Cockpit**; die
Discovery-Kennung, der Ordner und jeder Querverweis `p9/...` bleiben **`p9`**.

⚠ **Was damit NICHT erledigt ist:** *keine Prüfung dieses Hauses fragt, ob der Name über
einem Ordner noch stimmt.* Ein Anzeigename macht diesen einen Fall lesbar und lässt die
Prüfung fehlen (`platform/T-0034`).

### ⚠ Und das Verbuchen selbst hat einen Befund geliefert: `platform/T-0036`

Der Entscheidungsmarker lautet **`D000`** — und `D000` gibt es in diesem Haus **17-mal**.
Die IDs werden **je Repo** vergeben (`inbox._naechste_d_id` liest das Log des jeweiligen
Repos), zitiert werden sie in den Berichten **global**: „D004", „D005", „D000".
⚠ Härter: `pm/.../decision-log.md` führt **`D005` dreimal und `D006` zweimal** — eine
Kollision in **einer** Datei, die `max+1` nicht erzeugt haben kann. Es gibt einen zweiten,
handgeschriebenen Schreibweg ins Entscheidungslog, und der hat keine Nummernvergabe.
> **Das ist `L-2026-08-20ce` an neuer Stelle: eine Angabe, die ihren Ort verloren hat.**
**Benannt, nicht gebaut** — eine Umstellung von Entscheidungs-IDs berührt jede Zitatstelle
in jedem Bericht dieses Hauses.


### ⚠⚠ Nachtrag 2: der Preflight hat einen echten Drift gemeldet und das FALSCHE Paar genannt

Bei der Schlussverifikation stand `1 Befund`: *„Plan sagt Sprint 27, Ticket sagt Sprint 28"*
für `promt-team/T-0008`. Die Planzeile sagt **28**, das Ticket sagt **28**.

Die Zeile, die den Befund auslöste, war eine **andere**: `p9/T-0008`. Sie gehört einem
**geschlossenen** Ticket und steht deshalb nicht in der Menge der offenen; die Auflösung
fiel auf die nackte `T-0008` zurück, und die war unter den **offenen** Tickets eindeutig —
`promt-team/T-0008`, anderes Repo, anderer Sprint.

> **⚠⚠ Die Eindeutigkeit ist über die OFFENEN Tickets geprüft, die Zeile gehörte einem
> GESCHLOSSENEN. Eine ID wird nicht dadurch eindeutig, dass die Restmenge klein ist.**

⚠ Das Schwestermodul `statusdrift` löst über **alle** Tickets auf und ist nie in diese
Falle gelaufen — dieselbe Frage, zwei Grundmengen, eine davon falsch gewählt.

> **Damit ist es der DRITTE Befund dieses Sprints aus derselben Familie (`SWR-128`, *grün,
> weil niemand fragt, worüber*): die Gegenprobe ohne Aufrufer, die Bedingung, die den
> Bestand liest und an einem Ereignis gemessen wurde — und jetzt die Grundmenge einer
> Nachschlagetabelle.**

⚠ Und der Fund selbst ist kein Zufall: die Zeile entstand, **weil dieser Lauf `p9/T-0008`
geschlossen hat**. *Eine Prüfung kann dadurch falsch werden, dass ein Ticket erledigt
wird.*

Behoben als **`SWR-176`** — nennt eine Planzeile ein Repo, gilt nur die qualifizierte
Form. Vier Zusicherungen, darunter das Paar (die eigene Zeile wird weiterhin geprüft) und
der Notnagel (eine Zeile **ohne** Repo löst weiterhin über die nackte ID auf).

# Anhang: Sprint 26


## Das Wichtigste (Stand Sprint 26, 2026-08-20)

1. **⚠⚠ DER ERSTE TICK, DER JEMALS DURCHGELAUFEN IST — UND ER HAT NICHTS GETAN.** `SWR-166`
   hat den Preflight entsperrt; seither sind **3 von 26** Tick-Versuchen durchgekommen
   (20:00 `platform`, 20:15 `platform`, 20:15 `team-mail`), alle drei mit `status=fehler`
   und `artefakte=[]`.
   > **Sprint 25 hatte ausdrücklich aufgeschrieben, dass er genau das NICHT gemessen hat —
   > „damit es nicht später als erledigt gilt, weil ihm niemand widersprochen hat". Dies
   > ist die Messung, und die Antwort ist nein.**

   `platform/T-0031`, `platform/T-0032`, `SWR-167`–`SWR-170`.
2. **⚠⚠ DIE URSACHE STAND SEIT VIERZEHN TAGEN ALS LEHRE IM BESTAND — DREIMAL ABGELEGT UND
   MIT ERWARTUNGSWERT.** `404: model 'llama3.1:8b' not found`. **`L-003` vom 2026-08-06**
   (`p0/T-0011`/F13) nennt den Guardrails-Default, nennt `gemma3:27b` als das installierte
   Modell und nennt die Gegenmaßnahme wörtlich: *„Modell-Defaults gegen das Geräteregister
   prüfen; Abweichungen als Registry-/Guardrails-CR nachziehen."* Abgelegt in
   `T-0036-prompt.md`, `p0/management/sprint-1/retro.md` und `p0/tickets/T-0016.md` — dort
   mit **„Erwartungswert: Wiederholungsquote dieser Fehlerbilder in Sprint 2 = 0"**.

   | | |
   |---|---|
   | Erwartete Wiederholungsquote | **0** |
   | Gemessene Quote in Sprint 26 | **3 von 3** |

   > **Es fehlte NICHT die Sorgfalt beim Aufschreiben. Die Lehre ist vorbildlich
   > formuliert, dreifach abgelegt und mit einer Zahl versehen — und hat vierzehn Tage lang
   > exakt null Wirkung gehabt, weil der Satz, der ihren Vollzug trug, nie ein Ticket und
   > nie eine Prüfung geworden ist.**

   Elfter Beleg für `platform/T-0027`, neue Rubrik **„gelernt ohne Vertreter"**.
   `L-2026-08-20ci`.
3. **⚠⚠ DREI BEFUNDE IN EINER FUNKTION, UND DER DRITTE HAT DEN PREFLIGHT BLIND GEMACHT.**
   (a) `print("Tick abgeschlossen…")` stand **unbedingt** vor `return 0`. (b) Der Branchname
   ist bei jedem Tick derselbe; beim zweiten Tick von `T-0001` zog `checkout <branch>` HEAD
   **zwei Commits zurück** — `main` und Branch divergiert (Merge-Basis `a370306`, main +2,
   Branch +1). (c) Die Rückkehr auf `main` stand mit `fehler_ok=True` da und ist
   stillschweigend misslungen.
   > **⚠⚠ Folge: `main` behielt `T-0001: in_progress`, der Arbeitsbaum stand auf dem Branch
   > mit `open` — und `SWR-155`, das „liegengebliebene Arbeit" melden soll, liest den
   > ARBEITSBAUM und meldete 0. Eine Prüfung, die den Arbeitsbaum liest, prüft den Branch,
   > auf dem sie zufällig steht.**

   Repariert (`e532681`, inkl. des nur auf dem Branch liegenden Run-Registry-Eintrags),
   gebaut (`SWR-167/168`, `checkout -B` + nachgeprüfter Rückweg, kein `return` im
   `finally`). `L-2026-08-20cj`.
4. **✅ DER AUFTRAGGEBER HAT NACH FÜNF MINUTEN GEANTWORTET.** `p12/T-0012` ist am 20.08. um
   **20:34** mit **A** entschieden (`D004`) — Sprint 26 begann um 20:29. Verbucht,
   geschlossen, **nichts gebaut, nichts zurückgebaut**, kein Nachfolgeticket.
   > **Fünf Sprints als Aufgabe terminiert, einmal gefragt, fünf Minuten Antwortzeit.**

   ⚠ Bemerkt hat die Antwort **kein Preflight** (der lief vorher), sondern
   `test_dr_verbuchung` über den **echten Bestand**, mitten im Lauf. `L-2026-08-20cl`.
5. **⚠ EINE BEDINGUNG, DIE EIN FEHLSCHLAG ERFÜLLT, IST KEINE BEDINGUNG.** `pm/T-0071`,
   `promt-team/T-0003`, `promt-team/T-0008` warteten auf *„mindestens einen durchgelaufenen
   Tick"* — wörtlich erfüllt, inhaltlich nicht. Überall nachgeschärft auf **`status: ok`
   und mindestens ein Artefakt** (Stand **0 von 3**).
   ⚠ Nebenbefund: es gibt **drei** Run-Registries. Der Tick schreibt in die des Ziel-Repos,
   `promt-team/T-0008` liest nur die von `p0` — **die Bedingung zeigt auf ein Register, in
   das die Ticks nicht schreiben** (B033 mit einem Datenbestand als vergessener Kopie).
   Benannt, nicht gebaut. `L-2026-08-20ck`.
6. **⚠⚠ Zum FÜNFTEN Lauf in Folge hat ein Werkzeug den frischen Entwurf verworfen — DREIMAL
   in diesem Lauf.** Der dritte war der **Preflight gegen den Sprintplan**: die Planzeile zu
   `p9/T-0008` sagte „erledigt", weil der *Brief* beantwortet war — der *DR* ist es nicht.
   *Ein beantworteter Brief ist keine getroffene Entscheidung.* Die anderen zwei waren Tests
   gegen ihren eigenen Verfasser: `test_kein_return_im_finally` suchte nach
   dem **Wort** „return" und wurde von dem Kommentar rot gemacht, der das Verbot erklärt;
   `test_am_echten_bestand…` erwartete `MAIL-RED@mail`, **gebildet** statt **gelesen** —
   die Instanz heißt `MAIL-RED@team-mail`.
7. **⚠ ZWEI BRIEFE KAMEN WÄHREND DES LAUFS — und einer hat etwas gefunden, das keine
   Prüfung findet.** `p9/N-0001` (*„kann dieses projekt geschlossen werden? warum gibts das
   noch?"*): gemessen **7/7 Tickets `done`**, **0** offener Vorrat — und **78 Commits in 7
   Tagen**. Der Grund: `p9/requirements/software/software-requirements.md` trägt **81 SWRs**,
   davon 19 aus `platform`, 17 aus `pm`; von den **letzten 25** stammen **neun** aus
   `platform`, darunter alle vier dieses Laufs.
   > **Die Anforderungen der Plattform liegen im Requirements-Ordner eines ABGESCHLOSSENEN
   > Projekts. Das hat nie jemand entschieden — es ist gewachsen, weil die nächste
   > Anforderung immer dort hingeschrieben wurde, wo die letzte stand. Keine Prüfung dieses
   > Hauses fragt, ob der Name über einem Ordner noch stimmt.**

   Als DR `p9/T-0008` vorgelegt (A/B/C, Frist 27.08., Default A) statt selbst entschieden:
   ein Umzug von 81 Anforderungen ändert die Grundlage der Matrix.
   `promt-team/N-0002` (*„beim prompt team bewegen sich die aufgaben nicht mehr"*): 8/10
   `done`, die zwei offenen warten auf Läufe **mit Ergebnis**.
8. **1236 Python-Tests** in der Sammlung (**gemessen**, **76** Testdateien), Matrix
   **170 SWRs / 0 Lücken**, Briefkasten **0 offen beim Start, 2 eingegangen, 2 beantwortet**,
   entschiedene unverbuchte DRs **0**,
   Parkplatz **10043**.
   ✅ Neue Preflight-Zeile (`SWR-170`): **2 von 2** ollama-Besetzungen weichen ab — erwartet
   waren 2, **vor** dem Bauen aufgeschrieben.

## Was der Auftraggeber tun kann

1. **`ollama list` auf dem eigenen Rechner** — ist `gemma3:27b` installiert? Von hier aus
   nicht messbar (`L-2026-08-20ce`), deshalb nicht behauptet. Ab jetzt fragt der Tick nach
   dem Namen aus dem Besetzungsregister; ein falscher Wert ist dort sichtbar und in einem
   Zug korrigierbar.
2. **`abschluss.cmd` ausführen** — Rückstand jetzt vier Tage plus zwei Läufe.
   **Stichprobe:** danach steht in `abschluss-auto.log` `OK - alles geprueft und gepusht`
   und `PUSH-ANFORDERUNG.txt` ist verschwunden.
3. **Nächsten Schnelltakt-Lauf ansehen**: „Tick abgebrochen" darf nicht mehr stehen;
   **„Tick OHNE ERGEBNIS"** ist die neue ehrliche Meldung, falls doch nichts entsteht.
4. ⚠ **Eine offene Entscheidung** — `p9/T-0008` (deine eigene Frage), Klasse C, Frist
   **27.08.**, Default **A = alles bleibt**. Schweigen kostet nichts.
5. Unverändert offen: Mail-Zugangsdaten (`team-mail/N-0003`), Kachel-Zählung im Reiter
   „Dashboard", `.git/verwaiste-locks` (**10043**, nicht eilig).

## ⚠⚠ NACHTRAG — der Schnelltakt hat um 21:30 selbst die Gegenprobe gefahren

Was oben als „nicht messbar" offengelassen war, ist während des Laufs passiert.

| | |
|---|---|
| `SWR-167` | ✅ **„Tick OHNE ERGEBNIS (status=fehler, artefakte=0)"** statt „Tick abgeschlossen". |
| `SWR-168` | ✅ Beide Repos nach dem Tick auf `main`, sauber. |
| `SWR-170` | ✅ Zeile steht in der Preflight-Ausgabe des Ticks. |
| `SWR-169` | ⚠⚠ **Greift nicht** — weiter `llama3.1:8b`. |

`pm/D010` entschied den Takt **je Besetzung** (*platform/PROB*); `ollama-schnelltakt.cmd`
übergibt nur die **Einheit**. Gezogen wurden `CM@platform` und `DEV@team-mail` — für die
steht im Register kein Modell, also greift der Guardrails-Rückfall.

> **⚠⚠ Die Anforderung ist grün, die Wirkung ist null. Alle vier Gegenproben prüften die
> Auflösungsfunktion, keine ihren Aufrufer — eine Gegenprobe, die die Funktion prüft und
> nicht ihren Aufrufer, misst die Hälfte, die man selbst geschrieben hat. Ohne den
> zufälligen Lauf um 21:30 hätte dieser Bericht „SWR-169 gebaut" behauptet.**

`platform/T-0033`, `prio: kritisch`, erster Punkt von Sprint 27.

## ⚠ Was dieser Lauf ausdrücklich NICHT gemessen hat

Ob ein Tick **nach** `SWR-169` ein brauchbares Artefakt liefert. Dazu muss einer laufen,
und dazu muss `gemma3:27b` auf dem Rechner des Auftraggebers installiert sein — von hier
aus nicht messbar. Der Satz steht hier aus demselben Grund wie in Sprint 25: damit er nicht
später als erledigt gilt, weil ihm niemand widersprochen hat.

⚠ Zweitens: `main` und `feature/t-0001-…` in `platform` sind **repariert, nicht
aufgelöst** — der Branch steht als Beleg da. Löschen wäre Glätten, Mergen hieße einen
Commit aus einem Fehllauf in die Historie holen. `SWR-168` sorgt dafür, dass kein neuer
dazukommt.

---

# Anhang: Stand Sprint 25

## Das Wichtigste (Stand Sprint 25, 2026-08-20)

1. **⚠⚠ DREI TAGE OHNE PUSH, UND ES STAND DIE GANZE ZEIT IN ZWEI LOGDATEIEN.** Letzter
   erfolgreicher Wächterlauf: **2026-08-17 11:32:30**. Seither **83 Läufe, 83 Abbrüche**.
   Der **Ollama-Schnelltakt**, den der Auftraggeber selbst eingerichtet hat, lief **6-mal**
   und brach **alle 12** Ticks ab (`Tick abgebrochen: Preflight hat Befunde`).
   > **Beide brechen ab, weil `preflight` Exit 1 liefert, solange irgendein Befund
   > dasteht — und vier Befunde sind Statusübergänge aus ABGESCHLOSSENEN Sprints, die
   > niemand mehr reparieren kann. Ein Wächter, der auf eine Tatsache blockiert, die
   > niemand mehr ändern kann, ist kein Wächter mehr, sondern ein Schalter, den jemand
   > umgelegt und niemand bemerkt hat.**

   ⚠ Gefunden hat es **kein Startcheck**, sondern die dritte Nachfrage des Auftraggebers.
   `SWR-166`, `platform/T-0029`, `L-2026-08-20cg`.
2. **⚠⚠ DIE REGEL DAGEGEN STEHT SEIT SPRINT 9 IM SELBEN MODUL UND WIRD DORT ZWEIMAL
   ANGEWANDT** — auf den Altbestand vor dem Stichtag und auf die Uhrenprobe, beide Male
   wörtlich mit der Begründung, ein Dauerbefund trainiere das Wegsehen. An der dritten
   Stelle nicht.
   > **Das ist B033 — nur ist die vergessene Kopie diesmal keine Codestelle, sondern eine
   > BEGRÜNDUNG.**

   ⚠ Der Stichtag ist **nicht** verschoben (`ALTBESTAND_ERWARTET` bleibt **56**), es
   entsteht **kein** Register von Einzelfällen, und die vier Fälle stehen weiterhin
   **namentlich und mit Commit** in jeder Ausgabe. Geändert hat sich nur, wen sie stoppen.
   ⚠ Das Waffenpaar steht daneben: ein Übergang aus dem **laufenden** Sprint blockiert
   weiter, und die Gegenprobe dazu ist **gefahren** (Mutation → rot).
3. **⚠⚠ DER AUFTRAGGEBER HATTE RECHT, UND DER GEGENBEWEIS LAG IN UNSEREM EIGENEN COMMIT.**
   Zu `team-mail/N-0004` (*„sowohl OLAMA wie IMAP ist eingerichtet und funktioniert"*):
   Commit **`70d5aa1`** vom 20.08. 16:01:05 trägt

   | Datei | Inhalt |
   |---|---|
   | `digest/2026-08-20-tag-digest.md` | 26 Mails, „Automatisch verdichtet (lokales Ollama)" |
   | `eingang/2026-08-20-rohdaten.md` | 231 Zeilen IMAP-Rohdaten |
   | `tickets/T-0001.md` | *„Gesetzte `MAIL_IMAP_*`-Variablen: **0** — erneut GEMESSEN, nicht angenommen"* |

   Eine Sekunde später ging derselbe Satz in den Sprintplan (`c964a56`).
   > **Die Zahl stimmte. Gemessen wurde in der Cowork-SANDBOX, wo sie nicht anders
   > ausfallen kann. Eine Umgebungsmessung gilt für die Maschine, auf der sie lief — und
   > in der Angabe stand nur die Zahl, nie der Ort. Das Wort „gemessen" hat drei Sprints
   > lang genau das getan, wogegen es eingeführt wurde: die Prüfung beendet.**

   `L-2026-08-20ce`. `team-mail/T-0001` und `promt-team/T-0003` sagen nicht mehr „wartet
   auf Umgebung".
4. **✅ `p12/T-0011` BEI DER FÜNFTEN BERÜHRUNG GELIEFERT — und der Grund war nie
   Kapazität.** In der Aufgabe steckte eine **Entscheidung**, die niemandem vorgelegt
   worden ist. Fällig war etwas Kleineres: `RohtextAnsichtTest` maß, **wie viele**
   Rohtext-Ansichten es gibt, nicht **welche** — ein Tausch (eine umgestellt, anderswo eine
   neue) wäre grün geblieben. Gebaut; der Rest ist als `p12/T-0012` **gefragt** statt ein
   sechstes Mal terminiert. `L-2026-08-20ch`.
5. **⚠⚠ ZUM VIERTEN LAUF IN FOLGE HAT EIN WERKZEUG DEN FRISCHEN ENTWURF VERWORFEN — UND
   ZWEIMAL IN EINEM LAUF.** `board.py` wies `p12/T-0012` ab und widerlegte damit dessen
   eigenen Satz, es gehe *nicht* in die Inbox (`inbox.py` legt **jeden** offenen DR vor).
   `test_konsole` fand `scripts/organigramm.py` aus dem Orga-Rework als Einstiegspunkt
   **ohne `konsole.sichere_ausgabe()`**. Und der **Preflight** widerlegte denselben DR ein
   zweites Mal: ohne `frist` ist er ein unterminiertes Ticket — *eine Frage ohne Frist ist
   keine schonende Frage, sondern eine, deren Ausgang niemand aufgeschrieben hat.*
   **Dreimal in einem Lauf.** `L-2026-08-20cf`.
6. **⚠ Die Arbeit der Vorsession stand nicht in Git** — 60 Dateien Orga-Rework
   (`pm/T-0070/T-0072`, `platform/T-0028`). Gegen die Werkzeuge verifiziert
   (`organigramm --check` grün, 8/8 Tests), dann in 16 Repos nachverbucht (B025).
7. **1219 Python-Tests** (über die Sammlung **gemessen**, **74** Testdateien) + **42**
   `produkt-datakonv`, **111 JS-Tests grün**, Matrix **166 SWRs / 0 Lücken**, Briefkasten
   **0 offen**.
   ✅ **`PREFLIGHT: STARTKLAR (5 fortgeschrieben)`** — zum ersten Mal seit dem 17.08.
   ⚠ Die 5 sind die vier Statusübergänge und die Pause: **gemeldet, nicht geglättet**.
   Dieser Lauf hat **keinen neuen** hinzugefügt.

## Was der Auftraggeber tun kann

1. **`abschluss.cmd` ausführen** — es liegt ein Rückstand von drei Tagen plus diesem Lauf
   an. **Stichprobe:** danach steht in `abschluss-auto.log` `OK - alles geprueft und
   gepusht` und `PUSH-ANFORDERUNG.txt` ist verschwunden.
2. **Nächsten Schnelltakt-Lauf ansehen** (alle 15 Min): in `ollama-schnelltakt.log` darf
   `Tick abgebrochen` nicht mehr stehen.
3. **Eine Frage in der Inbox** (`p12/T-0012`, Klasse C, **Frist 27.08.**): sollen
   Aufgaben-Texte wie Briefe gerendert werden (Überschriften, Tabellen) oder wie heute als
   Rohtext? ⚠ Default **A = heutiger Zustand**; Schweigen kostet nichts und baut nichts
   zurück.
4. Unverändert offen: Mail-Zugangsdaten (`team-mail/N-0003`), die Kachel-Zählung im Reiter
   „Dashboard", `.git/verwaiste-locks` (**9754** Dateien, nicht eilig).

## ⚠ Was dieser Lauf ausdrücklich NICHT gemessen hat

Ob ein Tick nach dem Entsperren inhaltlich etwas Sinnvolles tut. **Es ist nie einer
gelaufen.** Der Satz steht hier, damit er nicht später als erledigt gilt, weil ihm niemand
widersprochen hat (`pm/T-0071`, Schritt 3).

---

# Anhang: Stand Sprint 24

## Das Wichtigste (Stand Sprint 24, 2026-08-20)

1. **✅ DREIMAL DIE REGEL DER VIERTEN BERÜHRUNG ANGEWANDT, DREIMAL GEBAUT.**
   `projects/p11/T-0015`, `platform/T-0021` und `platform/T-0022` standen alle bei der
   **vierten** Berührung und trugen zusammen **zehn** Verschiebungen. Keines ist ein
   viertes Mal terminiert worden.
   > **Der Grund war jedes Mal „Kapazität" und jedes Mal wahr. Er wird nicht falsch, wenn
   > man ihn viermal aufschreibt — er hört nur auf, eine Aussage zu sein.**

   ⚠ Eine **vierte** Aufgabe steht ebenfalls dort und ist es **nicht** geworden
   (`projects/p12/T-0011`). Das ist im Plan **benannt und nicht begründet**.
2. **✅ DER RÜCKBAU IST DURCH — UND SEINE TEUERSTE STELLE WAR DIE, AN DER NICHTS ZU TUN
   WAR.** `p11/T-0015`: `GET /api/dashboard`, `aggregation.dashboard` und `KACHEL_FELDER`
   entfernt, **SWR-135 auf die Layout-Hälfte zurückgeschnitten** (v1.61, mit
   Historienzeile).
   > **⚠⚠ Der erste Entwurf des Wächters prüfte nur, was FEHLT. `_zustand` und
   > `zustaende_von` stehen in derselben Datei, tragen dieselben Konstanten und sehen aus
   > wie Dashboard-Code — sie tragen seit SWR-146 den `zustaende`-Block des COCKPITS. Eine
   > Prüfung, die nur Abwesenheit misst, ist nach einem Kahlschlag ebenfalls grün.**

   Der Wächter ist deshalb ein **Paar** mit echter Auswertung. `L-2026-08-20by`.
   ⚠ Die Frontend-Hälfte ist **gezählt** (4 Bausteine, **11** von 111 JS-Zusicherungen) und
   **nicht** mitgenommen — `projects/p11/T-0016`.
3. **⚠⚠ DIE MESSUNG ZU `platform/T-0021` HAT DEN TITEL DES TICKETS WIDERLEGT — SWR-163.**
   Die `tmp_obj`-Reste, nach denen es benannt ist, sind **Müll und keine Sperre** (Commit
   mit fünf `unlink`-Warnungen und **Exit 0**). Die Sperre, die tötet, ist `index.lock`,
   und sie wird vom **gelingenden** Aufruf hinterlassen:

   | Aufruf | Exit | Sperre bleibt liegen |
   |---|---|---|
   | `git status --porcelain` | **0** | **JA** |
   | `git add`, `git commit`, `git log`, `git diff` | 0 | nein |

   > **Git beendet einen SCHREIBENDEN Indexvorgang durch Umbenennen — das geht durch. Einen
   > bloß LESENDEN Refresh beendet es durch LÖSCHEN — und das ist hier verboten.**

   ⚠ **Frage 2 des Tickets war damit falsch gestellt**, und der Rückfall aus **SWR-134**
   sah drei Sprints lang wie die Lösung aus: er repariert den Aufruf, der **gescheitert**
   ist. `L-2026-08-20bx`.
   ⚠ Die Zusicherung aus `platform/T-0015` DoD 2 ist **nicht aufgeweicht**: verboten bleibt
   das Räumen **vor** einem Aufruf; der Test dazu ist **geschärft**, nicht gelöscht
   (`L-2026-08-20bz` — dieselbe Bewegung zum **dritten** Mal in diesem Haus).
4. **✅ SWR-164: eine Größe, die niemand gemessen hat.** Der Parkplatz `verwaiste-locks`
   wächst unbegrenzt, weil die erste Räumstufe auf diesem Mount **immer** scheitert:
   **1975** (Sprint 21) → **2099** (heute) in `pm`, **9506** über alle Repos am Ende dieses Laufs.
   ⚠ Die Zahl ist eine **Momentaufnahme**: sie wächst mit jedem Commit (allein dieser Lauf
   rund +170). Die Zusicherung daneben prüft deshalb eine **Größenordnung** und keine feste
   Zahl — der Fehler aus SWR-157.
   ⚠ Ausdrücklich **kein Befund** — reparierbar ist es von hier aus nicht; eine ungemessene
   Größe ist von einer, die nicht wächst, nicht zu unterscheiden.
5. **⚠⚠ DER GRÖSSTE BEFUND DIESES LAUFS IST WIEDER EINER ÜBER SICH SELBST — UND ZUM
   ZWEITEN LAUF IN FOLGE HAT IHN EINE ÄLTERE ZUSICHERUNG GEMACHT.** `SWR-165` verlangt
   wörtlich, der Rumpfmarker stehe an **einer** Stelle; ihr erster Entwurf legte eine
   **zweite** Konstante an.
   > **Rot gemacht hat das nicht der Autor, sondern ein Zähltest aus Sprint 17, der nichts
   > tut, als zu zählen, in wie vielen Dateien ein Literal vorkommt.**

   Sprint 23: SWR-134 gegen die Uhrenprobe. Sprint 24: SWR-131 gegen den eigenen Marker.
   **Beide Male sah der Entwurf für seinen Autor richtig aus.** `L-2026-08-20cd`.
6. **✅ `platform/T-0022` ist nach drei Verschiebungen GANZ geschlossen — SWR-165.** Die
   drei Schreibvorgänge von `inbox.entscheide` sind gezählt, und die Zählung hat die Frage
   **umgestellt**: nicht die Reihenfolge ist offen, sondern welche Lücke die schlimmere
   ist — die zwischen dem **ersten** und dem **zweiten**.
   > **Eine Entscheidung, die protokolliert ist und im Ticket unsichtbar bleibt, ist
   > schlimmer als eine, die gar nicht ankam: die eine merkt der Mensch, die andere nicht.**

   ⚠ Gebaut ist eine **Prüfung** und **kein Umbau** — die Frage, was bei einem Teilausfall
   gilt, ist niemandem gestellt worden. Gemessen: 93 Logzeilen, **46** von der Inbox,
   **0** ohne Marker; die **47** handgeschriebenen werden ausdrücklich nicht verlangt.
7. **✅ Eine Entscheidung, die eine fünfte Terminierung ersetzt hat.** `promt-team/T-0010`,
   **Klasse C** (PL): (a) *je Sprint eine Rolle aufrufen* und (b) *Übungsläufe* verworfen —
   beide erzeugen einen Lauf **um der Messung willen**.
   > **Ein Goldset folgt dem Betrieb. Es geht nicht voran und es wird nicht nachgeholt.**

   `promt-team/T-0008` ist **umgeschnitten** statt geschnitten (mit Prüfung, weil eine
   Regel ohne Vertreter keine drei Sprints hält) und **entsperrt**. `L-2026-08-20cb`.
8. **⚠ ACHTER geschätzter Wert — unter einer Überschrift, die „gezählt, nicht übersehen"
   heißt.** **9** stand da, **11** sind gemessen. ⚠ Und der Fall widerlegt einen
   naheliegenden Zuschnitt von `platform/T-0027`: die dort genannten fünf Rubriken hätten
   ihn **nicht** gefunden, eine Schablone auch nicht — die Zahl stand in Fließtext.
   `L-2026-08-20cc`.
9. **1201 Python-Tests** (über die Sammlung **gemessen**, **72** Testdateien), **111
   JS-Tests grün**, Matrix **165 SWRs / 0 Lücken**, Briefkasten **0 offen**, entschiedene
   unverbuchte DRs **0**, Pflichtartefakte **0** fehlend, Decision-Log gegen Ticketmarker
   **0**.
   ⚠ **Nicht startklar:** der Altbefund über **vier** Statusübergänge (drei aus 13/15,
   einer aus Sprint 23) steht unverändert. ✅ **Dieser Lauf hat keinen neuen hinzugefügt.**
10. **Fünf Tickets geschlossen** (`p11/T-0015`, `p11/T-0003`, `platform/T-0021`,
    `platform/T-0022`, `promt-team/T-0010`), **eines neu** (`p11/T-0016`), **eines
    entsperrt und umgeschnitten** (`promt-team/T-0008`), **drei Anforderungen** (SWR-163,
    164, 165), **eine geändert** (SWR-135 → Layout-Hälfte), **eine Entscheidung**
    (Klasse C), **sieben Lessons** (`bx` `by` `cc` cm · `bz` `cd` test · `ca` `cb` pl).
    ⚠ **Nichts liegt beim Menschen** — dieser Lauf hat nichts vorzulegen.

### ✅ Ein Widerspruch in der eigenen Schlussmessung — und er ist aufgelöst

Die Schlussverifikation lieferte **zwei** Zahlen für dieselbe Sache: die Sammlung meldete
**1201** Tests, die Summe der gefahrenen Blöcke **1208**.

Die Ursache war eine **veraltete Stapelliste**: die Blöcke waren nach Dateiindex
geschnitten, und dieser Lauf hat *währenddessen* zwei Testdateien angelegt — eine Datei lief
dadurch in zwei Blöcken.

> **Gefunden hat das nicht die Sorgfalt, sondern der Widerspruch zwischen zwei unabhängigen
> Messungen derselben Größe. Eine allein wäre unwidersprochen geblieben.**

⚠ Nachgerechnet über neu geschnittene, überschneidungsfreie Blöcke:
**387 + 288 + 384 + 122 + 20 = 1201**, deckungsgleich mit der Sammlung. Alle Blöcke grün
bis auf den einen bekannten Altbefund.

⚠ Das ist im selben Zug ein **Argument für den Zuschnitt von `platform/T-0027`**: eine
Prüfung, die die Berichtszahl gegen **eine** Quelle hält, hätte hier nichts gemerkt — beide
Zahlen waren korrekt erhoben, nur über verschiedene Mengen.

---

## Das Wichtigste (Stand Sprint 23, 2026-08-20)


1. **✅ `platform/T-0020` IST GEBAUT — nach vier Verschiebungen, bei der fünften
   Berührung.** **SWR-158**: `trace_matrix` liest die **Zieldatei**, bevor es sie ersetzt,
   vergleicht an **IDs**, kennt **kein Flag** und schreibt bei einer verschwundenen ID
   **nichts**.
   > **Der Vorgang von Sprint 17 (143 → 24, „Matrix geschrieben", Exit 0) lebte und starb
   > in einer Arbeitskopie. Eine Warnung NACH dem Schreiben hätte ihn gemeldet und
   > trotzdem angerichtet — deshalb ist die tragende Zusicherung nicht der Exit-Code,
   > sondern: die alte Fassung steht danach byteweise unverändert da.**

   ⚠ Frage 3 des Tickets (der Abschlussbericht ohne eigene Prüfung) ist **abgetrennt** als
   `platform/T-0027` — *ein Ticket, das nach seiner Erledigung noch eine offene Frage
   trägt, ist zwei Tickets in einem, und das zweite verschwindet mit dem ersten.*
2. **✅ DIE NEGATIVE PAUSE IST GEMESSEN — UND DAS TICKET VERDÄCHTIGTE DIE FALSCHE ZEILE.**
   `platform/T-0026` → **SWR-159**. Registerzeit gegen die Commit-Zeit des Commits, der
   sie brachte, über **alle 31** Ereignisse:

   | | |
   |---|---|
   | sechs reguläre `ende` | **+0,6 bis +1,1 Min** |
   | `ende` Sprint 17 (dokumentierter Nachtrag) | +21,3 Min |
   | **`ende` Sprint 16** | **−37,4 Min** |
   | `start`-Ereignisse (früh geschrieben, spät committet) | +0,9 bis +81,3 Min |

   > **⚠⚠ Commit `911e57a` vom 16:32:36 trägt die Zeile `"ende": "2026-08-17 17:10"`.
   > Kein Prozess kann 38 Minuten vor seiner eigenen Uhr liegen. Nicht der START von
   > Sprint 17 ist der falsche Wert, sondern das ENDE von Sprint 16.**

   ⚠ Zwei der drei Hypothesen fallen ohne weitere Messung: ein Nachtrag liefert einen
   **positiven** Abstand, ein Zonenversatz ein Vielfaches von 15 Minuten, eine
   Sommerzeitumstellung genau 60 — **37,4 ist keines von beidem**.
   ⚠ **Welche** Uhr richtig ging, wird **nicht behauptet**: die einzigen zwei Zeugen sind
   die streitenden Uhren; ein dritter wurde gesucht und existiert nicht.
   ⚠ Die im Ticket vorgeschlagene Abhilfe (**Register mit Offset**) ist **verworfen** —
   beide Commits tragen `+02:00`, sie hätte den Fall nicht gefunden. `L-2026-08-20br`.
3. **⚠⚠ DER GRÖSSTE BEFUND DIESES LAUFS KAM AUS EINEM EIGENEN FEHLER.** Dieser Lauf hat
   `projects/p11/T-0009` von `in_progress` direkt auf `done` gebucht. Die Frage *„warum
   ist dabei nichts rot geworden?"* ergab: **`uebergang_historie` hat das Sammel-Repo
   `projects` (p10, p11, p12) seit Sprint 9 NIE angesehen — 66 Statuswechsel ungeprüft**,
   darin **vier** Altfälle und der eigene.
   > **Zwei unabhängige Ursachen, beide für sich plausibel: `pruefe_alle` übersprang jedes
   > Projekt ohne eigenes `.git` — WÄHREND DER KOMMENTAR DANEBEN SAGTE, DASS DANN DAS
   > SAMMEL-REPO ZÄHLT — und `status_wechsel` filterte `git log -- tickets/` relativ zur
   > Repo-Wurzel.**

   Repariert als **SWR-162**, `ALTBESTAND_ERWARTET` **52 → 56** (nicht der Stichtag
   verschoben). ⚠ Der eigene Verstoß ist **nicht geglättet** und ab jetzt der **vierte**
   stehende Befund. `L-2026-08-20bs`, `L-2026-08-20bw`.
4. **✅ Zwei Tickets bei der VIERTEN Berührung, zwei verschiedene Ausgänge.**
   `projects/p11/T-0013` → **gebaut** (**SWR-160**: Widget-Inhalt hinter dem PIN-Lesegate,
   Kachel bleibt sichtbar, Vertrag **v2.7**). `promt-team/T-0008` → **`blocked`**, weil
   gemessen **0 Läufe für zehn Rollen** vorliegen, unverändert seit Sprint 18.
   > **Ein Ticket viermal auf „Kapazität" zu terminieren, während es auf eine Tatsache
   > wartet, die kein Lauf herstellt, indem er das Ticket anfasst, heißt den Grund viermal
   > falsch aufzuschreiben.** `L-2026-08-20bv`.
5. **⚠ Der Ertrag von SWR-160 ist eine Unterscheidung, die vorher niemand aufgeschrieben
   hatte.** *Die **Anzahl** offener Punkte ist eine Kennzahl; ihr **Wortlaut** sind
   Betreffzeilen, Absender und Links.* Zahl und Wortlaut kommen aus **derselben** Auswahl —
   zwei Auswahlregeln über eine Rubrik wären B033 gewesen. ⚠ Und die Sperre ist **kein
   vierter Zustand** geworden: *„keine Daten" und „nicht für dich" in ein Vokabular zu
   werfen* wäre die kürzeste Änderung und die falsche. `L-2026-08-20bu`.
6. **✅ Zum DRITTEN Mal in zwei Läufen hat die Zählung vor der Reparatur den Ertrag
   geliefert — und zum dritten Mal fiel sie kleiner aus als die Vermutung.**
   `platform/T-0022` Fragen 2+3 → **SWR-161**: von **sechs** Pflichtartefakten fehlte über
   17 Repos genau **eines**, vier fehlten **nirgends**.
   > **Und die Antwort auf Frage 3 ist gemessen, nicht abgewogen: der selbstheilende Weg
   > aus SWR-152 hat GENAU das Repo geheilt, in das jemand hineingelaufen ist. Den Mangel,
   > in den noch niemand gelaufen ist, findet nur eine Prüfung, die alle Repos durchgeht.**

   ⚠ Die Prüfung sieht nur, was die Discovery sieht: `produkt-datakonv` hat ebenfalls kein
   Entscheidungslog und steht in **keiner** der 17 — benannt, nicht mitgeheilt.
7. **⚠ Eine Zusicherung aus Sprint 16 hat den eigenen Entwurf verworfen.** Die Uhrenprobe
   rief zuerst `git` **im Sprintzähler** auf und wurde rot an
   `test_die_messung_ruft_KEIN_git_auf` (SWR-134).
   > **Eine Prüfung, die Uneinigkeit zwischen zwei Läufen erkennen soll und dabei selbst
   > sperrt, ist ihr eigener Schadensfall. Gefunden hat das nicht der Entwurf, sondern
   > eine Regel, die sieben Sprints früher jemand in einen Test gegossen hat.**

   ⚠ Die Zusicherung wurde **nicht aufgeweicht**: Material (`uebergang_historie`), Regel
   (`sprint_register`) und Naht (`preflight`) sind getrennt. `L-2026-08-20bt`.
8. **⚠ ZWEI Zahlen dieses Laufs waren geschätzt statt gemessen.** (a) Der Kommentar der
   eigenen Reparatur behauptete „rund 2 s"; gemessen sind es **10 s → 36 s**. (b) Die
   Commit-Nachricht zu den Lessons nennt **fünf**; es sind **sechs**. Beide vor dem Leser
   korrigiert, **keine** durch eine Prüfung gefunden — **sechster** und **siebter** Beleg
   für `platform/T-0027`, im selben Lauf, in dem es entstand.
9. **1185 Python-Tests** (über die Sammlung **gemessen**, **70** Testdateien), **111
   JS-Tests grün**, Matrix **162 SWRs / 0 Lücken**, Briefkasten **0 offen**, entschiedene
   unverbuchte DRs **0**, Plan-Drift **0**, Statusdrift **0**, Pflichtartefakte **0**
   fehlend.
   ⚠ **Nicht startklar**, und zum ersten Mal seit vielen Läufen mit einem Befund **mehr**:
   drei aus den Sprints 13/15 (unverändert) **plus einer aus diesem Lauf**.
10. **Vier Tickets geschlossen** (`platform/T-0020`, `platform/T-0026`, `p11/T-0013`,
    Klammer `p11/T-0009`), **zwei neu** (`platform/T-0027`, `promt-team/T-0010`), **eines
    blockiert** (`promt-team/T-0008`), **fünf Anforderungen** (SWR-158 … SWR-162),
    Widget-Vertrag **v2.7**, **sechs Lessons** (`br` `bs` cm · `bt` `bu` test · `bv` `bw`
    pl). ⚠ **Nichts liegt beim Menschen** — dieser Lauf hat nichts vorzulegen.

---

## Das Wichtigste (Stand Sprint 22, 2026-08-20)

1. **✅ DER BRIEF, DEN SPRINT 21 NUR BEANTWORTEN KONNTE, IST GEBAUT.** `team-mail/N-0004`
   rügte, dass **60,2 Stunden Ausfall bei 60 Minuten Takt** unbemerkt blieben. **SWR-156**
   (`platform/T-0025`): der Preflight nennt die Pause seit dem letzten Sprintende in
   Minuten **und** in Vielfachen des Takts — **immer**, auch wenn sie unauffällig ist
   (SWR-114/117/155). Heute: *56 Min = 0,93x Takt.*
2. **⚠ Die Schwelle ist NICHT an den Bestand gefittet.** Gemessen sind sieben Pausen:
   −0,35 · 0,0 · 0,1 · 0,23 · 0,7 · 0,93 · **60,2** Takte. Zwischen der größten
   unauffälligen und der einen auffälligen liegen zwei Zehnerpotenzen — **jede** Zahl
   dazwischen trennt gleich gut.
   > **Die Messung sagt, wo die Grenze NICHT liegen darf, und lässt offen, wo sie liegt.
   > Wenn die Daten die Wahl nicht treffen, trifft sie der vorhandene Regelbestand und
   > nicht die Meinung des Laufs.**

   Gewählt ist `STILLE_TAKTE = 2` — dieselbe Zahl, mit der die Kachel seit SWR-102 Stille
   meldet. `L-2026-08-20bo`.
3. **⚠⚠ ZWEI KONSTANTEN FÜHRTEN ZWEI WERTE FÜR DENSELBEN SACHVERHALT.**
   `session.TAKT_MINUTEN` = **30**, `sprint_register.TAKT_MIN_STANDARD` und jedes
   `takt_min` im Register = **60**. Die Kachel meldete Stille nach **einer** statt nach
   **zwei** Stunden, seit dem 17.08.
   > **B033 in seiner leisesten Gestalt: nicht zwei Anzeigen, die sich widersprechen,
   > sondern zwei Konstanten, die einander nie begegnen. Nichts wird rot, niemand
   > vergleicht sie, und beide sehen für sich plausibel aus.**

   ⚠ Eine **dritte** Kopie steckte im Test (`minutes=95` als „zwei Takte") — grün, solange
   der Irrtum galt. `L-2026-08-20bm`.
4. **⚠⚠ EINE VON SIEBEN PAUSEN IM REGISTER IST NEGATIV.** Sprint 17 nennt einen Start
   (16:49) **vor** dem Ende von Sprint 16 (17:10). Die Ereignisreihenfolge in der
   append-only-Datei ist einwandfrei.
   > **Wenn die Reihenfolge stimmt und die Uhrzeiten sich widersprechen, dann stammen die
   > Uhrzeiten nicht aus derselben Uhr.**

   ⚠ **Nicht auf 0 geklemmt** — der negative Wert ist der einzige Beleg dafür, dass es das
   Problem gibt. Ursache **nicht geraten** (drei mögliche, ein Vorkommen in 22 Sprints):
   `platform/T-0026`. `L-2026-08-20bn`.
5. **✅ Die drei Tage rote Zusicherung ist repariert, das Datum NICHT hochgezählt**
   (**SWR-157**, `platform/T-0024`). Der Ertrag ist die **Zählung davor**: über **66**
   Testdateien, mit dem **Syntaxbaum** und nicht mit einer Textsuche, gibt es **genau
   eine** Fundstelle dieser Bauart — während die richtige Gegenbauart (Schranke statt
   Gleichheit) an **zwei** Stellen längst existierte.
   > **Der Fehler war nicht Unwissen, sondern eine Gelegenheit — die Zahl stand gerade da
   > und war richtig.** `L-2026-08-20bp`.
   ⚠ Nebenbefund: die tragende Annahme der Auswahl (*„`digest_liste` liefert neueste
   zuerst"*) stand als **Kommentar** da und war von keiner Zusicherung gedeckt.
   `L-2026-08-20bq`.
6. **⚠ DIE DREI FRAGEN VON `platform/T-0020` SIND BEANTWORTET — ZWEI DAVON UMGEKEHRT ZUR
   VERMUTUNG IM TICKET.** Gemessen über alle **95 Commits** der Trace-Matrix: in **94
   Übergängen** ist **nie** eine Anforderungs-ID verschwunden (21 → 157, ausschließlich
   wachsend).
   > **⚠⚠ Der Vorfall, der das Ticket auslöste (143 → 24, Exit 0), steht NICHT in der
   > Historie: `40a460fd` trägt 143, der nächste Commit trägt 144. Er ist im selben Lauf
   > entstanden und im selben Lauf repariert worden — er hat die Arbeitskopie ruiniert
   > und die Commits nie erreicht.**

   Damit: Vergleich über **IDs** (0 Fehlalarme über die ganze Historie), **keine**
   Ausnahme und **kein** Flag (die drei legitimen Fälle sind nie eingetreten — *eine
   Ausnahme, die es noch nie gab, ist keine Ausnahme, sondern eine Vermutung über die
   Zukunft*), Vergleich **je Zieldatei**, damit `--produkt` nicht an der eigenen Ausnahme
   scheitert.
7. **⚠ ZUM ZWEITEN MAL IN ZWEI LÄUFEN DERSELBE BLINDE FLECK.** Sprint 21: ein
   ausgefallener Lauf hinterlässt keine Spur. Sprint 22: der Matrix-Vorfall hinterließ
   ebenfalls keine.
   > **Unsere Prüfungen lesen Commits, und Commits sind das, was übrig bleibt, wenn ein
   > Lauf gut ging. Was einen Lauf zerstört oder gar nicht erst stattfinden lässt, steht
   > dort nicht drin.**
8. **✅ Die zwei Klammern hat diesmal der PM nachgezogen** (`p11/T-0003`, `p11/T-0009`) —
   nach zwei Läufen, in denen der Preflight es tun musste.
9. **⚠ Eine Zahl in diesem Bericht wäre ZUM VIERTEN MAL fortgeschrieben worden.** Der
   Entwurf trug **1128** Python-Tests aus Sprint 21; gemessen sind es **1147** (66 statt
   65 Dateien). Korrigiert **vor** dem Commit, wieder durch Nachzählen und wieder ohne
   Prüfung — **fünfter Beleg für Frage 3 von `platform/T-0020`**, die damit der einzige
   noch offene Teil dieses Tickets ist.
10. **1147 Python-Tests** (über die Sammlung **gemessen**, 66 Testdateien), Matrix
    **157 SWRs / 0 Lücken**, Briefkasten **0 offen** (58/58), entschiedene unverbuchte DRs
    **0**, Plan-Drift **0**, Statusdrift **0**.
    ⚠ **Nicht startklar**, aber **ein** roter Test statt zweier: der Altbefund aus den
    Sprints 13/15 (**unverändert, keiner aus diesem Lauf**). `test_widget_post` ist grün.
11. **Zwei Tickets geschlossen** (`platform/T-0024`, `platform/T-0025`), **eines neu**
    (`platform/T-0026`), **zwei Anforderungen** (SWR-156/157), **fünf Lessons**
    (`bm` cm · `bn` cm · `bo` pl · `bp` test · `bq` test), **ein Brief eingelöst**
    (`team-mail/N-0004`). ⚠ **Nichts liegt beim Menschen** — dieser Lauf hat nichts
    vorzulegen.

---


## Das Wichtigste (Stand Sprint 21, 2026-08-20)

1. **⚠⚠ DER BEFUND DIESES LAUFS IST EINE MESSUNG ÜBER UNS SELBST.** Der Auftraggeber hat
   in `pm/N-0043` verlangt, dass eine Aufgabe beim Start auf `in_progress` geht. **Die
   Regel gibt es seit Sprint 1** — `board.UEBERGAENGE` erzwingt
   `open → in_progress → in_review → done`, ein Sprung darüber hinweg ist seit SWR-118 ein
   Prüfbefund. Die bequeme Antwort wäre „haben wir schon" gewesen und **belegbar richtig**.
   Gemessen über die committete Historie, **320 Ticketdateien**:

   | | |
   |---|---|
   | geschlossene Aufgaben, die **nie** `in_progress` waren | **159** |
   | Median-Aufenthalt bei den übrigen 141 | **22 Sekunden** |
   | unter 10 Minuten | 134 von 141 |
   | Maximum über den gesamten Bestand | 30 Minuten |

   > **Der Status wurde gesetzt, weil die Prüfung ihn verlangt, und nicht, weil er
   > jemandem etwas sagt. Die Übergangsprüfung kennt die REIHENFOLGE der Zustände und
   > nicht ihre DAUER — der Mensch, der auf die Anzeige sieht, prüft genau umgekehrt.**

   `L-2026-08-20bh`.
2. **⚠ Und daraus folgte die Reihenfolge der Arbeit, nicht aus Bequemlichkeit.** Punkt 4
   desselben Briefes („am Sprintende steht ein anderer Status drin") war **bereits
   erfüllt** — nicht durch Disziplin, sondern weil der geprüfte Zustand praktisch nicht
   vorkam.
   > **Eine Prüfung, die auf einem Bestand grün ist, in dem der geprüfte Zustand gar nicht
   > vorkommt, prüft nichts.** (`L-2026-08-17ai`, dritter Beleg)
3. **✅ Drei Anforderungen geschlossen, alle drei aus DIESEM Brief, am selben Tag.**
   **SWR-153** (Sprintnummer an der Kachel „Letzte Session" — aus dem **Register** über den
   **Commit**, nie aus der Überschrift), **SWR-154** (der Plan in **Kapiteln mit Nummer im
   Titel**, Zuordnung im Server, `aktuell`/`nächster` **auch leer**), **SWR-155** (der
   Preflight meldet Aufgaben, die angefangen und liegengeblieben sind — **melden, nicht
   aufräumen**).
4. **✅ Die neue Arbeitsregel ist in der Historie belegbar:** `platform/T-0023` und
   `pm/T-0069` gingen **vor der ersten inhaltlichen Zeile** auf `in_progress`, jeweils mit
   eigenem Commit.
5. **⚠⚠ `platform/T-0021` Frage 1 ist beantwortet — und die drei Sprints alte Vermutung
   war FALSCH.** `objects/**/tmp_obj_*` ist **kein** Sperrproblem (Warnung, Exit 0). Die
   Sperre ist `.git/index.lock`, und die Ursache ist eine andere als gedacht:
   > **Umbenennen ist auf diesem Mount erlaubt, Löschen nicht. Git beendet einen
   > SCHREIBENDEN Indexvorgang mit einem Rename — der geht durch. Einen bloß LESENDEN
   > Refresh (`git status`) beendet es mit einem Unlink — der scheitert und lässt die
   > Sperre stehen, an der der nächste Aufruf mit Exit 128 stirbt.**

   ⚠ Damit ist auch erklärt, warum der **Preflight** das Problem nicht lösen kann: **er
   ist selbst ein lesender Aufruf** und hinterlässt die Sperre für den, dem er den Weg
   frei machen sollte. `L-2026-08-20bi`.
6. **⚠⚠ Eine Zusicherung stand DREI TAGE rot, und niemand hat es gesehen.**
   `test_widget_post.BestandTest` hält den **echten** Bestand gegen ein festgeschriebenes
   Datum. Am 17.08. um **22:22** ist ein neuer Digest entstanden — **vier Minuten nach dem
   Abschlussbericht von Sprint 20 (22:18)**.
   > **Zum zweiten Mal in vier Tagen trifft etwas nach dem Abschlussbericht ein und wird
   > zum Altbestand des nächsten Laufs. Beim ersten Mal war es eine Klasse-A-Entscheidung
   > des Auftraggebers, diesmal eine Textdatei.**

   ⚠ **Nicht geglättet** — das Datum wird nicht hochgezählt, das verschöbe den Befund nur
   bis zum nächsten Digest. Neu als `platform/T-0024`. `L-2026-08-20bj`.
7. **⚠ Eine Zahl in diesem Bericht war ZUM DRITTEN MAL fortgeschrieben statt gemessen.**
   Der Entwurf nannte **1155** Python-Tests; gemessen sind es **1128**. Korrigiert **vor**
   dem Commit — aber wieder durch **Nachzählen** und nicht durch eine Prüfung. Dritter Fall
   nach Sprint 18 und 19, und damit der dritte Beleg für **Frage 3 von `platform/T-0020`**.
8. **⚠ Zum zweiten Mal in Folge hat der Preflight dieselben zwei Klammern nachgezogen**
   (`p11/T-0003`, `p11/T-0009` standen wieder auf Sprint 20).
   > **„Eine Klammer folgt ihren Teilen" ist eine mechanische Regel — und mechanische
   > Regeln gehören an eine Prüfung, nicht an eine Erinnerung.**
9. **1128 Python-Tests** (über die Sammlung **gemessen**, 65 Testdateien), **111 JS-Tests
   grün** (von 104), Matrix **155 SWRs / 0 Lücken**, Briefkasten **0 offen** (zweimal
   geprüft), entschiedene unverbuchte DRs **0**, Plan-Drift **0**, Statusdrift **0**.
   ⚠ **Nicht startklar** und **zwei** rote Tests: der Altbefund aus den Sprints 13/15
   (**unverändert, keiner aus diesem Lauf**) und der eben gefundene `platform/T-0024`.
10. **⚠⚠ NACHTRAG (11:50, nach dem Abschluss): der Auftraggeber hat einen zweiten Brief
    geschrieben, und er hat recht.** `team-mail/N-0004` (11:35, **19 Minuten nach dem
    Abschlussbericht von 11:16**): die Routine hat **60,2 Stunden** ausgesetzt bei einem
    Takt von **60 Minuten** — das **Sechzigfache** — und Sprint 21 hat es nicht gemeldet.
    > **`nicht_beendete()` prüft Läufe OHNE `ende`, also solche, die mittendrin abbrachen
    > — eine Prüfung auf eine SPUR. Ein Lauf, der ausfällt, hinterlässt keine Spur, und
    > alle unsere Prüfungen sehen nur Spuren.**

    ⚠ Derselbe Lauf ist an der Stelle **vorbeigelaufen**: SWR-153 hat der Kachel „Letzte
    Session" an genau diesem Tag den Zeitpunkt und die Sprintnummer gegeben. **Die Angabe
    existierte, die Frage nicht.** `L-2026-08-20bk`, neu als `platform/T-0025`.
    ⚠ **Drittes Mal in vier Tagen**, dass etwas nach dem Abschlussbericht eintrifft —
    diesmal ein Brief, der genau diesem Bericht vorwirft, etwas übersehen zu haben.
11. **⚠ Die Nachprüfung des eigenen Abschlusses hat ZWEI Fehler in ihm gefunden.**
    (a) `platform/T-0021` wurde ohne Begründung von Sprint 20 auf 22 gezogen, während der
    Bericht zweimal „Grund im Ticket" behauptete — *ein Ticket, in dem in diesem Sprint
    etwas Gutes passiert ist, sieht bearbeitet aus* (`L-2026-08-20bl`). (b) Drei
    Testzahlen in SWR-153/154/155 waren **geschätzt statt gezählt** (10/17/10 statt
    **12/20/9**) — derselbe Fehlertyp wie Punkt 7, **im selben Lauf und eine Etage
    tiefer**. Beides korrigiert. ⚠ **Vierter Beleg für Frage 3 von `platform/T-0020`**.
12. **Zwei Tickets geschlossen** (`platform/T-0023`, `pm/T-0069`), **zwei neu**
    (`platform/T-0024`, `platform/T-0025`), **drei Anforderungen** (SWR-153/154/155),
    **fünf Lessons** (`bh` pl · `bi` cm · `bj` test · `bk` pl · `bl` cm), **zwei Briefe
    beantwortet** (`pm/N-0043` Klasse B via B058, `team-mail/N-0004` als Nachtrag).
    ⚠ **Nichts liegt beim Menschen** — außer dem Ausfall selbst, den nur er verhindern
    kann.

---

## Das Wichtigste (Stand Sprint 20, 2026-08-17)

1. **⚠⚠ Eine KLASSE-A-ENTSCHEIDUNG DES AUFTRAGGEBERS LIESS SICH NICHT VERBUCHEN.** Er hat
   `promt-team/T-0009` über die Inbox mit **A** entschieden; der Schreibweg starb mit
   `[Errno 2] No such file or directory` — `promt-team` hat nie ein
   `management/decisions/decision-log.md` bekommen. `open(..., "a")` legt eine **Datei** an,
   aber kein **Verzeichnis**; das Verzeichnis legt `pool.gruende` bei der **Gründung** an.
   > **Der Schreibweg setzte eine Datei voraus, die ein ANDERER Weg anlegt. Solange jedes
   > Repo durch diesen anderen Weg entstanden ist, ist die Annahme unsichtbar richtig — und
   > sie wird an dem Repo sichtbar, das anders entstand. Das war ausgerechnet das, in dem
   > eine Klasse-A-Entscheidung fällig war.**

   Betroffen: **zwei** Repos (`promt-team`, `platform`), gemessen. Repariert als **SWR-152**
   (`platform/T-0022`).
2. **⚠⚠ Kein bestehender Test hätte es finden können — und das ist der eigentliche Befund.**
   Jede Testfixture legt ihre Verzeichnisse **selbst** an, also auch das, das in Produktion
   fehlte. Das ist wörtlich die seit Sprint 16 offene Erkennungsfrage `L-2026-08-17ai`
   (*welche unserer über tausend Zusicherungen prüfen etwas, das die Testdatei selbst
   eingerichtet hat?*) — **zum ersten Mal an einem echten Schaden belegt** statt als Sorge
   formuliert. Die neue Teststrecke beginnt deshalb mit einer **Gegenprobe**, die den echten
   Zustand herstellt und zeigt, dass `open(..., "a")` dort wirft. `L-2026-08-17bg`.
3. **⚠ Angelegt statt abgewiesen — mit benannter Kehrseite.** Ein sauberer 400er wäre
   ehrlicher gewesen als der Errno und hätte den Menschen mit einer getroffenen Entscheidung
   stehen lassen, die er nicht verbuchen kann.
   > **Eine getroffene Entscheidung, die am Ablageort scheitert, ist verloren, sobald das
   > Fenster zu ist.**

   ⚠ Ein selbstheilender Weg macht den Mangel **unsichtbar**. Ob das Anlegen in den
   Schreibweg gehört oder als Befund in den Preflight, ist **offene Frage 3** in
   `platform/T-0022` — nicht stillschweigend beantwortet. ⚠ Die schärfste Zusicherung ist,
   dass ein **bestehendes** Log **byteweise unberührt** bleibt: das Log ist append-only, und
   ein Weg, der unter Umständen überschreibt, löscht genau die Entscheidungen, die jemand
   später sucht.
4. **✅ `promt-team/T-0009` verbucht (D000, Option A)** — Ollama lokal, 0 €.
   `promt-team/T-0003` ist **entblockt**.
5. **⚠ Und `T-0003` wartet auf eine UMGEBUNG, nicht auf den Menschen — gemessen:**
   `which ollama` leer, `localhost:11434` ohne Antwort.
   > **Eine Aufgabe, die fälschlich „wartet auf den Menschen" sagt, verschiebt die Schuld an
   > ihrem Liegenbleiben.**

   Der Wartegrund steht als **Feld und Messung im Ticket** und nicht als Satz im Plan — genau
   der Fehler aus Sprint 17 (`L-2026-08-17ag`), diesmal vorher angewandt.
6. **⚠⚠ Ein Bestandstest hat eine ZWEITE Entscheidung gefunden, von der niemand wusste.**
   Der Auftraggeber hat um **21:57** auch `p12/T-0010` mit **A** entschieden — erfolgreich.
   Der Abschlussbericht von Sprint 19 (21:45) meldete „entschiedene unverbuchte DRs: **0**",
   und das war **zu diesem Zeitpunkt richtig**.
   > **Eine Entscheidung, die nach dem Abschlussbericht eintrifft, ist für diesen Bericht
   > unsichtbar und für den nächsten Lauf ein Altbestand. Der Bestandstest ist die einzige
   > Stelle, die beides verbindet.**
7. **✅ G4 für `p12-v1.0` ERTEILT (D003) — die Klammer `p12/T-0003` ist geschlossen.** P12 ist
   an seiner Baseline abgenommen. ⚠ Der **benannte Folgepunkt** ist mit G4 **ausdrücklich
   offengehalten** (`p12/T-0011`), und die **zwei Vorbehalte** gelten weiter (Statikprüfungen
   sind aus dem Bestand abgeleitet; die JS-Strecke ist `B-node-optional`).
   > **Ein erteiltes Gate sagt „das Beauftragte ist geliefert und geprüft". Es sagt nicht
   > „hier ist nichts mehr offen" — und der Unterschied verschwindet, sobald nur der Haken
   > übrig bleibt.**
8. **⚠ Drei Befunde hat der PREFLIGHT an diesem Lauf gefunden**, nicht der Verfasser des
   Plans: eine Plan-Drift, eine Statusdrift und **zwei Klammern auf einem vergangenen
   Sprint**. Alle drei behoben.
   > **Eine Klammer, die auf einem vergangenen Sprint stehen bleibt, sieht aus wie etwas
   > Liegengebliebenes und ist etwas Wartendes. Der Unterschied steht im Feld, nicht im Kopf
   > des Lesers.**
9. **⚠ Eine Zusicherung dieses Laufs war falsch rot** — sie suchte dateiweit nach
   `_naechste_d_id(log_pfad)` und fand die **Definition** statt des Aufrufs.
   > **Eine Textsuche kann eine Definition nicht von ihrem Aufruf unterscheiden — und die
   > Definition steht nun einmal vor dem Aufruf.**

   **Sechster Fehlalarm derselben Familie in drei Tagen** (nach fünf über Kommentare).
   Gemessen wird jetzt im **Rumpf der Funktion**. ⚠ Die Familie wächst, und **keine Regel hat
   sie bisher verhindert** — das steht so da, weil es die Lage ist.
10. **1087 Python-Tests** — **gemessen** über die Sammlung und nicht fortgeschrieben, die
    Lehre von `L-2026-08-17bf` diesmal angewandt —, **104 JS-Tests grün**, Matrix **152 SWRs
    / 0 Lücken**, Briefkasten **0 offen**, entschiedene unverbuchte DRs **0**, Plan-Drift 0,
    Statusdrift 0. ⚠ **Nicht startklar**: der Altbefund über drei Statusübergänge aus den
    Sprints 13 und 15 ist unverändert, **keiner aus diesem Lauf**.
11. **Zwei Klasse-A-DRs geschlossen** (`promt-team/T-0009`, `p12/T-0010`), **eine Klammer**
    (`p12/T-0003` — Baseline abgenommen), **zwei neu** (`platform/T-0022` **offen mit drei
    Fragen**, `p12/T-0011`), **eine Anforderung** (SWR-152), **eine Lesson** (`bg`).
    ⚠ **Nichts liegt mehr beim Menschen.**

---

## Das Wichtigste (Stand Sprint 19, 2026-08-17)

1. **✅ `projects/p12/T-0006` gebaut — die Zusammenführung ist eingelöst, und der Nachweis
   ist eine ZAHL.** `ALTBESTAND_TLINKS_AUFRUFE` von **4 auf 0**: `tlinks` ist nicht „nicht
   mehr aufgerufen", sondern **entfallen** (0 Aufrufe **und** 0 Definitionen — eine tote
   Funktion, die auf 0 gezählt wird, steht trotzdem da). **SWR-097 bis SWR-101** wechseln
   zum ersten Mal auf `reviewed`, **einzeln, jede mit ihrem Nachweis** (B027).
2. **⚠⚠ Der Befund dieses Laufs: ein neuer Zweig war TOTER CODE, und der Zähltest war dabei
   grün.** Der Code-Zaun-Zweig aus ADR-P12-001 Entscheidung 3 war gebaut und wurde **nie
   erreicht**: Absatz- und Listenpfad sammeln Folgezeilen, bis ein bekanntes Muster kommt,
   und ```` ``` ```` stand in dieser Abbruchregel nicht.
   > **Ein neuer Block-Zweig ist erst dann erreichbar, wenn die Fortsetzungsregel des
   > vorherigen Blocks ihn kennt. Beide Stellen sind für sich genommen richtig.**

   ⚠ Der Zähltest liest den Quelltext und **sah den Zweig stehen**; gefunden hat es der
   Verhaltenstest. ⚠ Und dessen **erste Fassung war ebenfalls grün** — sie hatte den Zaun am
   Textanfang, wo keine Fortsetzungsregel greift. *Ein Beispiel, das die Stelle nicht trifft,
   ist grün und sagt nichts.* `L-2026-08-17az`.
3. **✅ Drei eingefrorene Zusicherungen aus Sprint 18 sind rot geworden — genau die drei und
   keine vierte — und UMGEDREHT statt gelöscht.**
   > **Ein eingefrorener Befund ohne die Zusage, ihn beim Bauen umzudrehen, ist eine Warnung
   > mit Zeitstempel. Die Zahl der rot gewordenen Zusicherungen ist selbst eine Messung:
   > wären es vier oder zwei gewesen, wäre entweder mehr passiert als geplant oder weniger
   > als versprochen.**

   `L-2026-08-17ba`. Das beantwortet **Frage 2 von `platform/T-0020`** an einem Fall statt an
   einer Überlegung.
4. **⚠ Die Prüfstrecke hätte fast einen zweiten Ladeweg bekommen.** Der Inline-Pass fragt
   seit der Umstellung `Regeln` nach dem Ticketziel; der Nachweis-Harnisch lud `regeln.js`
   nicht und wurde rot. Der bequeme Weg wäre ein **Ersatz-`Regeln` im Test** gewesen — *eine
   zweite Antwort auf genau die Frage, gegen die SWR-150 gebaut ist.* Geladen wird jetzt die
   echte Datei in der Reihenfolge von `index.html`, und der Ladeweg liegt **einmal** in
   `_app_laden.cjs`.
5. **✅ `projects/p11/T-0011` bei der VIERTEN Berührung gebaut (SWR-151)** — nach
   `L-2026-08-17x`: gebaut, nicht zerlegt, weil das Ticket seit Sprint 17 im eigenen Text
   sagt, dass es **keine Naht** hat. Damit ist die **Klammer `p11/T-0008`** geschlossen, ein
   Ticket mit **vier** Verschiebungen und einer ausdrücklichen Zusage an den Auftraggeber aus
   Sprint 11.
6. **⚠⚠ Die bestimmende Frage von `T-0011` war DoD 2, nicht die Technik.** Sie verlangt
   wörtlich, den Unterschied zu SWR-133 zu **begründen und nicht zu behaupten** — *zwei
   benachbarte Ansichten, eine speichert und eine nicht.*
   > **Falten ist ein Griff beim Lesen. Eine Auswahl ist eine Aussage. Der Einwand aus
   > SWR-133 (*„sonst fehlt eine Gruppe und niemand weiß, warum"*) verbietet die Persistenz
   > nicht — er verlangt die ERKLÄRUNG.**

   Sie steht im **Kopf** der Ansicht: Zahl, **Namen**, Weg zurück. ⚠ Und die andere Hälfte
   der Begründung ist eine **Messung**: eine Zusicherung hält fest, dass der Faltzustand
   weiterhin flüchtig ist — wäre er beiläufig persistent geworden, wäre die Begründung
   gegenstandslos, **ohne dass jemand sie zurückgenommen hat**. `L-2026-08-17bc`.
7. **⚠ Gespeichert wird das ABGEWÄHLTE.**
   > **Eine gespeicherte Auswahl altert gegen einen wachsenden Bestand: sie sagt „zeig
   > diese", und was danach dazukommt, fällt lautlos aus der Ansicht.**

   Ein Team, das ein `widget.yaml` neu hinlegt, hätte sonst für jeden, der einmal
   konfiguriert hat, **nichts** getan. `L-2026-08-17bb`. ⚠ **Kein Schreibweg zum Server**
   (ADR-003): die Vorliebe **eines** Menschen an **einem** Gerät ist keine Aussage über die
   Organisation — geprüft wird die **Abwesenheit** der Route, genau das, was ein
   Verhaltenstest nicht kann.
8. **✅ `projects/p11/T-0014` entschieden (Option B) — die Messung hat zwei Optionen an ihrer
   VORAUSSETZUNG erledigt.** Das Ticket verlangte *„erst messen, dann entscheiden"*; der
   einzige benannte künftige Leser war `p11/T-0011`. Nach dessen Bau steht fest: es liest
   `/api/widgets`. Option A hätte einen **falschen** Satz in einen Docstring geschrieben,
   Option C war an genau diesen Bedarf konditioniert. `L-2026-08-17be`.
   ⚠ Die **Ausführung** ist `p11/T-0015` und **keine Verschiebung**: ein Entscheidungsticket
   ist mit der Entscheidung fertig. ⚠ `_zustand` bleibt — **SWR-146 hängt daran**, und das
   steht in der DoD des Folgetickets, nicht in einem Kommentar.
9. **⚠⚠ Ein Werkzeugbefund, den dieser Lauf AM EIGENEN LEIB gemessen hat**
   (`platform/T-0021`, neu): auf diesem Mount hinterlässt **jeder Commit**
   `.git/objects/**/tmp_obj_*`, an denen der **nächste** Git-Aufruf scheitert — dreimal in
   Folge gemessen.
   > **Ein Vorlauf, der einmal am Anfang räumt, schützt gegen den Zustand von gestern und
   > nicht gegen den, den dieser Lauf gerade selbst erzeugt.**

   ⚠ Die zweite Gefahr ist die unangenehmere: `setze_status` nimmt den Wechsel korrekt
   zurück — *und ein korrekt zurückgenommener Wechsel ist von einem nie versuchten nicht zu
   unterscheiden.* Erste DoD ist eine **Messung** und keine Reparatur: `warning:` bei
   Exit ≠ 0 lässt offen, ob es eine Sperre oder Müll ist. `L-2026-08-17bd`.
10. **⚠⚠ Und eine Zahl in diesem Bericht war ZUM ZWEITEN MAL fortgeschrieben statt gemessen.**
    Der erste Entwurf nannte **1077** Python-Tests; gemessen sind **1079** (61 Dateien, über
    die Sammlung gezählt).
    > **Sprint 18 hat genau diesen Fehler als eigenen Abschnitt aufgeschrieben. Sprint 19 hat
    > ihn an derselben Stelle wiederholt — mit der Warnung vor Augen.**

    ⚠ Aufgefallen wieder **beim Nachzählen** und nicht durch eine Prüfung: der Abschlussbericht
    hat für seine eigenen Kennzahlen keine. Das ist **Frage 3 von `platform/T-0020`**, und die
    Wiederholung binnen eines Sprints ist der Beleg, dass Aufschreiben allein nicht wirkt.
    `L-2026-08-17bf`.
11. **1079 Python-Tests, davon 1 rot** (der Altbefund über drei unzulässige Übergänge aus den
    Sprints 13 und 15 — **keiner aus diesem Lauf**), **104 JS-Tests grün** (von 78), Matrix
    **151 SWRs / 0 Lücken**, Briefkasten **0 offen**, entschiedene unverbuchte DRs **0**.
    ⚠ **Nicht startklar**, und das bleibt die richtige Meldung. Nichts geglättet.
12. **Drei Sachtickets geschlossen** (`p12/T-0006`, `p11/T-0011`, `p11/T-0014`), **eine
    Klammer** (`p11/T-0008`), **drei neu** (`p12/T-0010` als **G4-Inbox-DR Klasse A**,
    `p11/T-0015`, `platform/T-0021`), **sechs Anforderungen** (SWR-097–101 abgenommen,
    SWR-151 neu), **sieben Lessons** sofort verankert. Zwei Tickets auf Sprint 20 verschoben,
    jedes mit **Grund im Ticket**.

---

## Das Wichtigste (Stand Sprint 18, 2026-08-17)

1. **✅ Das seit Sprint 17 dringlichste Sachticket der Organisation ist gebaut**, nicht zum
   zweiten Mal verschoben: `promt-team/T-0007` (**SWR-149**) liefert **51 belegte
   Goldset-Fälle** — CM 23, DEV 28 — und die gemessene Baseline. Damit ist die Klammer
   `promt-team/T-0002` nach **fünf** Berührungen geschlossen und das Eval-Gate
   (`promt-team/T-0003`) hat nur noch **eine** offene Eingabe.
2. **⚠⚠ Der Befund dieses Tickets war einer an seiner eigenen DoD.** Sie verlangt wörtlich
   *„real heißt: aus dem Bestand belegt, nicht ausgedacht"* — und dieser Satz stand seit
   Sprint 15 **nur im Ticket**.
   > **Keine Prüfung liest einen Satz. Ein Lauf hätte 51 plausibel formulierte Fälle
   > schreiben und die DoD als erfüllt melden können — und nichts hätte widersprochen.**

   Gebaut ist `herkunft` als **Pflichtfeld mit Belegstelle** (`pfad::suchtext`), gegen den
   Bestand aufgelöst. ⚠ Die **Stelle** ist die eigentliche Prüfung: *eine Datei existiert
   auch für einen erfundenen Fall.* Verankert als `L-2026-08-17au`.
3. **⚠⚠ Eine Messung, die die DoD NICHT verlangt hat, hat die eigene Arbeit dieses Laufs
   widerlegt.** Die **Trennschärfe**: von 46 textbasierten Prüfungen des ersten Entwurfs
   gingen **41** auch in **fremden** Artefakten des Sets auf.
   > **Eine Prüfung, deren Suchtext überall steht, geht auf, ohne etwas zu unterscheiden.
   > Ein Goldset aus solchen Prüfungen ist kein Maßstab, sondern ein Maß für die
   > Beliebigkeit seiner Suchtexte — und es war grün, belegt und mangelfrei.**

   Geschärft auf **2 von 40**, **vor dem ersten Commit**. ⚠ Die Zahl wird **berichtet und
   nicht erzwungen**: eine Prüfung über eine **Konvention** soll überall aufgehen, und ein
   Gate dort verböte richtige Fälle (SWR-131). `L-2026-08-17av`.
4. **⚠⚠ Der Bericht sagt VOR seiner Tabelle, dass seine 100 % KEIN gutes Zeugnis sind.** Die
   Prüfausdrücke sind aus den Artefakten **abgeleitet**; dass sie dort aufgehen, ist zum Teil
   **Bauart und nicht Befund**. Eine Zahl mit ihrem Vorbehalt **dahinter** wird ohne ihn
   gelesen. Was fehlt, ist **benannt statt geschätzt**: die Erfolgsquote eines **frischen**
   Laufs je Rolle — Provider nötig, kostet Geld, **Klasse A** (`promt-team/T-0009`).
5. **✅ `projects/p11/T-0012` bei der ZWEITEN Verschiebung gebaut** (**SWR-150**). ⚠ Der
   Befund war nicht der fehlende Link, sondern der **zweite Bauplatz**: **neun** Stellen in
   `app.js` setzten die Route selbst zusammen, und in **sieben** davon war die Beschriftung
   `x.ref` — die Kennung **vom Server**.
   > **Ein Link, dessen Aufschrift der Server liefert und dessen Ziel die Ansicht
   > zusammenbaut, ist zwei Aussagen über dasselbe Ticket. Solange beide gleich sind, merkt
   > es niemand.**

   Und sie sind nicht theoretisch verschieden: **68 Ticketnummern gibt es in mehr als einem
   Projekt**, `T-0002` allein in **17** — gemessen, nicht befürchtet. Eine nackte Nummer
   ergibt jetzt **keinen** Link: *ein Link auf das falsche Projekt ist schlimmer als kein
   Link, weil er ein fremdes Ticket öffnet und dabei richtig aussieht.* `L-2026-08-17aw`.
6. **✅ `projects/p12/T-0009` liefert ADR-P12-001** — die Regel gegen den zweiten Renderpfad
   als **Zähltest** statt als Vorsatz; Altbestand `tlinks`-Aufrufe **eingefroren bei 4**.
   `SWR-097`–`SWR-100` haben damit zum ersten Mal **Prüfungen**. Klammer `p12/T-0005`
   geschlossen.
   > **Ein Altbestand, der als Warnung dasteht, wächst. Einer, der als Zahl dasteht, kann
   > nur sinken.** (`L-2026-08-17ax`)

   ⚠ Zwei Zusicherungen halten bewusst den **heutigen** Zustand fest und werden rot, sobald
   `p12/T-0006` baut — **das ist ihr Zweck**: sie sagen dem Lauf, der es tut, dass er den
   Altbestand mitzunehmen hat, statt dieselbe Erkennung zweimal stehen zu lassen.
7. **⚠ Dieser Lauf hat zuerst eine fremde Buchung nachgetragen.** Sprint 17 war fertig und
   committet (18:50), hatte aber aus Rücksicht auf eine parallele Session **kein `ende`**
   gebucht. `beginne()` hätte ihn automatisch als **`abgebrochen: true`** geschlossen — eine
   **falsche Angabe** über einen Sprint mit vier geschlossenen Tickets.
   > **Das Register kennt „läuft" und „abgebrochen". Für „fertig, aber aus Rücksicht nicht
   > gebucht" hat es kein Wort — und der automatische Weg wählt dann das falsche.**

   Geschlossen mit `beende()` ohne Abbruchmarke, mit der **Messung** in der Notiz
   (Schreibspur unbewegt, alle 17 Repos clean). `L-2026-08-17ay`.
8. **⚠ Eine Zusicherung dieses Laufs ist an ihrem eigenen Kommentar rot geworden** — der
   Präfix-Zähltest fand das **Beispiel in der Erklärung darüber**. *Eine Textsuche kann eine
   Erklärung nicht von ihrem Gegenstand unterscheiden.* **Fünfter Fehlalarm derselben Art in
   zwei Tagen.** Gemessen wird jetzt der Code **ohne** Kommentare.
9. **⚠ Die Board-Validierung hat den ersten Wurf des neuen Inbox-DR zu Recht abgelehnt**
   (`frist` kein Datum, `default` kein Token aus `optionen`). Ein Vertrag, der seine eigenen
   Vorlagen prüft, ist billiger als einer, der sie beschreibt.
10. **1061 Python-Tests, davon 1 rot** (der Altbefund über drei unzulässige Übergänge aus
    den Sprints 13 und 15 — **keiner aus diesem Lauf**), **78 JS-Tests grün** (von 73),
    Matrix **150 SWRs / 0 Lücken**, Briefkasten **0 offen**. ⚠ **Nicht startklar**, und das
    bleibt die richtige Meldung. Nichts geglättet.

---

## Das Wichtigste (Stand Sprint 17, 2026-08-17)

1. **✅ Zwei Tickets bei der VIERTEN Berührung gebaut statt zum vierten Mal verschoben.**
   `pm/T-0065` (**SWR-144**, Terminierungsknopf) und `pm/T-0063` (**SWR-147**,
   Team-Gründung vorlegen). Beide sagten in ihrem eigenen Text, dass sie **keine Naht**
   haben und eine erfundene Zerlegung schlimmer wäre als der Bau — also war die Antwort
   eine Entscheidung. Damit sind auch die Klammern `pm/T-0054` und `pm/T-0028`
   geschlossen; letztere trägt **acht** wortgleiche Verschiebungen in ihrer Historie.
2. **⚠⚠ Dieser Lauf hat einen Werkzeugfehler AUSGELÖST, nicht gelesen** (`platform/T-0019`,
   **SWR-145**). `trace_matrix.py` **ohne** `--alle-projekte` hat die kanonische Matrix mit
   **24 von 145** Anforderungen überschrieben — 121 Zeilen entfernt, „Matrix geschrieben"
   gemeldet, **Exit 0**.
   > **Ein Werkzeug, dessen unvollständiger Modus an den Ort des vollständigen schreibt,
   > macht aus einem Tippfehler einen Totalbefund.**

   ⚠ Keine der beiden Voreinstellungen ist allein falsch — `--alle-projekte` ist aus, weil
   ein Flag *hinzuschaltet*, und das Ziel ist die kanonische Datei, weil der Normalfall ohne
   Argumente laufen soll. Erst ihre **Kombination** erzeugt den Schaden, und genau deshalb
   hat es keine bestehende Prüfung gefunden. Es ist die Bauart von **SWR-143** eine Etage
   höher: die Richtigkeit hing am Wissen des Aufrufers. Repariert im selben Lauf — der
   Beleg ist die **Gleichheit** beider Aufrufe (145/0).
3. **✅ `platform/T-0016` geschlossen: der benannte Altbestand ist von 3 auf 0**
   (**SWR-146**, Widget-Vertrag **v2.5**). Der Cockpit-Payload trägt den Zustand je Feld als
   **Schwesterschlüssel** — dieselbe Bauform, unter der SWR-117 den Org-Kopfblock einführen
   durfte; eine Umhüllung nach dem Muster des Dashboards hätte **jeden** Leser geändert, um
   eine Angabe zu liefern, die drei Felder betrifft.
   ⚠⚠ Die Menge der Zustände folgt dem **Vertrag** (`pflicht: false`) und **nicht** der
   heutigen Ansicht: nach der Ansicht wären es drei gewesen, und der vierte hätte beim
   ersten Leser gefehlt, der ihn anzeigt — eine Lücke, die nur im `null`-Fall sichtbar wäre.
4. **✅ SWR-147: Team-Gründung ist VORLEGEN, und der Code kann nicht mehr.** Klasse A bleibt
   beim Menschen; kein Repo, kein Remote, kein Registry-Eintrag. ⚠ Das ist **am
   Dateisystem** zugesichert und nicht im Docstring behauptet.
   ⚠ Die Substanz ist DoD 3 und eine Regel über das **Lesen**: SWR-127 gibt seine Auflagen
   als Rückgabewert zurück, damit sie nicht übersehen werden *können* — hier werden sie
   verbraucht. Ohne diese Stelle wäre SWR-127 die **dritte** Prüfung dieses Projekts, deren
   Ergebnis niemand liest (nach SWR-122 und SWR-125).
5. **⚠⚠ Der Auftraggeber hat uns MITTEN IM LAUF bei einer falschen Behauptung erwischt**
   (`team-mail/N-0003`, 17:54): *„team-mail/T-0001 -> IMAP ist schon längst eingerichtet."*
   Er hat recht — `team-mail/T-0002` steht auf **`done`**, und trotzdem stand im Sprintplan
   seit mehreren Sprints „wartet-auf-Mensch — fällig ab IMAP-Einrichtung".
   > **Eine Aufgabe, die fälschlich „wartet auf den Menschen" sagt, verschiebt die Schuld
   > an ihrem Liegenbleiben — das ist schlimmer als eine, die einfach offen dasteht.**

   Der Grund stand als **Satz im Plan** und nicht als Feld; `blocked_by` war korrekt und
   längst erfüllt, und keine Prüfung liest den Plansatz. Das ist wörtlich `L-2026-08-17ag`,
   an einer anderen Stelle desselben Tages angewandt und hier nicht.
6. **⚠⚠ Sprint 17 ist NICHT beendet — bewusst.** Ab etwa 18:10 arbeitet eine **zweite
   Session** in denselben Repos (`team-mail/T-0004`, Widget-Vertrag **v2.6** / SWR-148).
   `beende()` hätte den laufenden Sprint unter ihr geschlossen und ihre Commits in einen
   abgeschlossenen Sprint fallen lassen.
   > **Ein Sprint, der beendet wird, während noch jemand darin arbeitet, ist kein
   > abgeschlossener Sprint, sondern eine falsche Buchung mit Zeitstempel.**

   ⚠ Die Kehrseite ist benannt: bleibt auch die andere Session stehen, trägt Sprint 17 am
   Ende kein `ende` und `nicht_beendete()` meldet ihn. Ein gemeldeter offener Sprint ist ein
   Befund; ein falsch geschlossener ist eine Lüge in der Buchhaltung.
7. **⚠ Der Sprint wurde nicht eröffnet, sondern ÜBERNOMMEN.** Die Registerzeile stand um
   16:49 in der Datei und war **nicht committet**; seit dem Ende von Sprint 16 hatte kein
   Repo einen Commit. Gewählt ist der **idempotente Wiedereintritt** (SWR-136), nicht eine
   Übernahme mit neuer Nummer — die hätte eine Sprintnummer für einen Lauf ohne Ergebnis
   verbraucht. Verankert als `L-2026-08-17ap`.
8. **⚠ Fünf Zusicherungen haben in diesem Lauf ihre eigenen Verfasser korrigiert**, vier
   davon beim **ersten** Lauf:
   (a) Der Rollback-Test schob `.git` weg und maß **404 statt 503** — die Rücknahme wurde
   nie erreicht. *Ein Fehler, den man dem System durch Wegnahme seiner Voraussetzungen
   beibringt, ist ein anderer Fehler als der, den man messen wollte.*
   (b) Eine Zusicherung verlangte `BOARD.md` im Commit; `geplant_sprint` ist **keine**
   Board-Spalte, das Board ändert sich nicht.
   (c) `cockpitFeldText` fiel bei unbekanntem Zustand auf `"undefined"` durch — *wörtlich*
   der Fehler, den der Kommentar drei Funktionen weiter oben in derselben Datei beschreibt.
   (d) Ein Test namens *„die Version wird gelesen und nicht eingetragen"* trug die Version
   selbst als Literal. (e) Ein Zähltest prüfte auf eine **Zeilennummer**.
   > **Eine Warnung, die im Nachbarcode steht, verhindert den Fehler nicht — die
   > Zusicherung, die sie messbar macht, tut es.**
9. **⚠⚠ Und eine Zusicherung DIESES Laufs war binnen 30 Minuten falsch.**
   `test_vertragsversion_ist_25` schrieb die Vertragsversion fest; die parallele Session hat
   sie zu Recht auf v2.6 gehoben. Es ist derselbe Fehler, den dieser Lauf **eine Stunde
   vorher** als `L-2026-08-17an` aufgeschrieben hat — vom selben Lauf wiederholt, der die
   Lesson formuliert hat.
   > **Eine Lesson zu schreiben ist nicht dasselbe, wie sie anzuwenden. Der Abstand
   > zwischen beidem betrug hier sechzig Minuten.**
10. **✅ Der Widget-Vertrag ist erstmals NICHT vom Wächter nachgezogen worden**, sondern im
    selben Lauf wie der Payload — die erste Ausnahme von `L-2026-08-17y`. Der Grund ist kein
    Vorsatz, sondern die **Reihenfolge**: DoD 1 von `platform/T-0016` stand einen ganzen
    Sprint vor dem Code. Als vorsichtige Regel verankert (`L-2026-08-17ao`), nicht als
    Zusage.
11. **1016 Python-Tests, davon 1 rot** (der Altbefund über drei unzulässige Statusübergänge
    aus den Sprints 13 und 15 — **keiner aus diesem Lauf**), **65 JS-Tests grün** (von 51),
    Matrix **147 SWRs / 0 Lücken** — ⚠ die Zahlen sind **unsere Messung**; beim Abschluss steht der Bestand bei **73 JS-Tests** und **148 SWRs / 0 Lücken**, weil der parallele Lauf SWR-148 und acht JS-Tests beigesteuert hat. Zwei richtige Zahlen zu verschiedenen Zeitpunkten, keine Korrektur —, Briefkasten 0 offen → **1 neuer mitten im Lauf** →
    beantwortet → wieder 0, entschiedene unverbuchte DRs **0**, Plan-Drift 0, Statusdrift 0,
    Tickets ohne Sprint 0, Kalenderfristen 0.
    ⚠ **Nicht startklar**, und das bleibt die richtige Meldung. Kein Stichtag verschoben,
    keine Historie umgeschrieben, kein Test angepasst, um grün zu werden.
12. **⚠⚠ Und dieser Lauf hat DIESE DATEI beschädigt und repariert.** Beim Fortschreiben
    wurde alles **vor** der Marke „Frühere Stände" ersetzt — damit war der komplette
    **Sprint-16-Block (92 Zeilen) gelöscht**, von einem Lauf, der im selben Atemzug
    schrieb, er habe nichts umgeschrieben.
    > **Die Datei verspricht in ihrer eigenen Überschrift, dass nichts umgeschrieben wird.
    > Der Schreibvorgang, der sie fortschreibt, war die einzige Stelle, an der dieses
    > Versprechen gebrochen werden konnte — und er hat es gebrochen.**

    Wiederhergestellt, weil derselbe Lauf den Block zu Beginn gelesen hatte. ⚠ Gefunden hat
    es **kein** Test: diese Datei liegt im Wurzelverzeichnis und damit in **keinem** Repo —
    kein `git diff`, keine Historie, keine Rücknahme. Das gilt ebenso für
    `PUSH-ANFORDERUNG.txt` und die `SESSION-BEFUND-*.md`. Als Befund aufgenommen
    (`L-2026-08-17at`), nicht als Pech verbucht.
13. **Vier Sachtickets geschlossen** (`pm/T-0065`, `platform/T-0019`, `platform/T-0016`,
    `pm/T-0063`), **zwei Klammern** (`pm/T-0054`, `pm/T-0028`), **zwei neu**
    (`platform/T-0019` im selben Lauf gebaut und geschlossen, `platform/T-0020` mit
    benannter Naht und drei offenen Fragen), **vier neue Anforderungen** (SWR-144 bis
    SWR-147), **acht Lessons** sofort verankert. Sieben Tickets auf Sprint 18 verschoben,
    jedes mit **Grund im Ticket**.

---

## Frühere Stände (unverändert, nichts umgeschrieben)

## Das Wichtigste (Stand Sprint 16, 2026-08-17)

1. **✅ `platform/T-0017` gebaut (SWR-139) — und die Vorkehrung ist im selben Lauf
   ZWEIMAL an einem echten Fall eingetreten.** `setze_status` schreibt **und** bucht;
   scheitert die Buchung, werden Ticketdatei **und** `BOARD.md` byteweise zurückgesetzt und
   der Fehler geworfen. Bei `p12/T-0008` scheiterte eine Buchung, der Wechsel wurde
   zurückgenommen, und der Folgeschritt wurde korrekt abgewiesen.
   > **Eine Vorkehrung, die im Lauf ihrer Entstehung greift, ist der einzige Beleg, den es
   > für sie gibt.**
2. **⚠⚠ SWR-143 (`platform/T-0018`): ein Fehler von SWR-134, gemessen IN PRODUKTION während
   des Laufs — und einen ganzen Sprint lang GRÜN GETESTET.** `git_schreiben.entsperre`
   legte `os.path.dirname(__file__)` in den Pfad; das ist `backend/`, `preflight` liegt in
   `scripts/`. Der Import scheiterte, die Funktion gab `0` zurück, die Räumung lief **gar
   nicht** — außer der Aufrufer brachte den Pfad mit (`board`, `preflight`, **und die
   Testdatei**).
   > **Die Reparatur wirkte überall dort, wo der Aufrufer sie mitgebracht hat — also genau
   > dort nicht, wo SWR-134 sie hinbringen wollte.**

   Gefunden hat es kein Test, sondern drei gescheiterte Commits mit `geraeumt: 0`. ⚠ Die
   Erkennungsfrage — *welche unserer 936 Zusicherungen prüfen etwas, das die Testdatei
   selbst eingerichtet hat?* — bleibt **unbeantwortet** und steht so in `L-2026-08-17ai`.
3. **✅ Die Baseline aus `promt-team/N-0001` ist gemessen (SWR-140/141) — und sie ist
   leer.** 7 Läufe, **0** mit Token-Feld, **6 von 7** ohne `aufgaben_typ` und damit nicht
   zuordenbar; der **eine** auswertbare Lauf lief über **Ollama**.
   > **Ein Mittel über die Läufe, die zufällig gemeldet haben, ist kein Mittel über die
   > Läufe. Ohne seinen Nenner gedruckt ist es von einer vollständigen Messung nicht zu
   > unterscheiden.**

   Jedes Aggregat trägt deshalb `n_gemessen` **und** `n_gesamt`; ohne eine einzige Messung
   ist es `nicht_geliefert` und **nicht** `0`. Das ist `kosten_eur: 0.0` aus SWR-137 eine
   Etage höher — dort im Feld, hier im Aggregat.
4. **✅ Token-Messung an der Quelle ohne Schätzung (SWR-141).** Ollama meldet **eine** Zahl
   (`prompt_eval_count` für den ganzen Prompt), der Vertrag verlangt **zwei**. Gelöst mit
   einem zweiten Aufruf **ohne Erzeugung** (`num_predict: 0`) und einer Subtraktion:
   > **Zwei Messungen und eine Subtraktion sind keine Aufteilung.**

   ⚠⚠ Fehlt **eine** der beiden Messungen, bleiben **beide** Felder `None` — eine halbe
   Messung als ganze auszugeben wäre im Report von einer vollständigen nicht zu
   unterscheiden.
5. **✅ Goldset-Format (SWR-142, `promt-team/T-0006`).** `fehlschlag_erkannt_an` ist eine
   **strukturierte** Prüfung aus geschlossener Menge; ein Fall ohne sie wird **abgelehnt**
   und nicht vorbelegt — ein Vorgabewert machte jede ungeschriebene Prüfung stillschweigend
   zu einer bestandenen. `soll_scheitern_auf` wird **je Aufgaben-Typ** geprüft, nicht je
   Fall: ein Feld ohne Prüfung ist ein Wunsch (SWR-125 angewandt statt zitiert).
6. **✅ `p12/T-0005` bei der VIERTEN Berührung zerlegt, Teil a gebaut** (`T-0008`,
   SWR-099-Nachweis): der **echte** Renderer aus `app.js` gegen **57** Briefe, zeichenweise
   bilanziert. **Kein Nutzzeichen geht verloren.** ⚠ Die Naht stand **nicht** im Ticket und
   wurde beim Schneiden hergeleitet — drei DoD-Punkte sind Entwurfsfragen, einer ist eine
   Messung, und *die Messung ist die Voraussetzung des Entwurfs, nicht sein Anhang*.
7. **⚠⚠ Der erste rote Lauf dieses Nachweises war ein Fehler der MESSUNG.** Er meldete an
   sieben Briefen fehlende Ziffern — die Marken der Nummernlisten, die das `<ol>` erzeugt.
   > **Was als „Markup" gilt, ist eine Entscheidung der Messung, und eine unsaubere macht
   > ein richtiges System rot.**

   Ein solcher Dauerbefund wäre schlimmer als kein Nachweis. Korrigiert wurde die **Ebene**
   (Zeilenstruktur statt Zeichenklasse), beide Richtungen eigens zugesichert.
8. **✅ Die repo-übergreifende Blockade aus Sprint 15 ist aufgelöst.**
   `team-dashboard/T-0001` hat als Vertragseigentümer entschieden (Klasse C): **Weg A**,
   der Cockpit-Payload trägt den Zustand je Feld, Vertrag v2.5.
   > **Ein Ticket gegen B033 zu lösen, indem man einen neuen B033-Fall anlegt, ist keine
   > Lösung, sondern eine Verschiebung mit besserer Presse.**
9. **⚠ Drei bestehende Zusicherungen wurden von SWR-139 rot — und sie waren NICHT der Fall
   aus SWR-136.** Ihre Regel („nicht vorsorglich räumen") war **richtig** und nur zu weit
   gezogen. Verschärft statt gelöscht: gemessen wird die **Reihenfolge** (vor dem ersten
   Git-Aufruf wird nicht geräumt) und die **Wiederholung** (genau eine). Der Unterschied
   zwischen beiden Fällen steht als Tabelle in `L-2026-08-17aj`.
10. **⚠ Zwei Zusicherungen wurden von ihrem eigenen Gegenstand rot.** (a) Der Zähltest
    „kein Vorgabewert auf dem Weg" war eine **Textsuche** und fand sich im Kommentar, der
    genau diesen Fehler erklärt — *eine Textsuche kann eine Warnung nicht von ihrem
    Gegenstand unterscheiden*. (b) Der JS-Nachweis war **rot, während jede einzelne
    Zusicherung grün dastand**: der Startlauf von `app.js` warf asynchron nach Testende.
11. **⚠⚠ Beinahe-Vorfall beim Bauen von SWR-139:** der erste Entwurf schrieb eine **zweite**
    `status_in_head` unter demselben Namen. Python meldet das nicht; die spätere Definition
    gewinnt lautlos, und sie konnte drei Dinge nicht, die die erste kann.
    > **Eine zweite Antwort auf dieselbe Frage muss nicht widersprechen, um zu schaden —
    > es genügt, dass sie weniger weiß als die erste.**

    Gefunden hat es `test_board.VerschachteltesRepoUebergangTest`. Die Reparatur ist ein
    **Zähltest über den Syntaxbaum**, nicht der Vorsatz, künftig genauer hinzusehen.
12. **936 Python-Tests, davon 1 rot** (der Altbefund über drei unzulässige Statusübergänge
    aus den Sprints 13 und 15 — **keiner aus diesem Lauf**), **51 JS-Tests grün** (von 45),
    Matrix **143 SWRs / 0 Lücken**, Briefkasten zweimal geprüft und beide Male **0 offen**,
    entschiedene unverbuchte DRs **0**, Plan-Drift 0, Statusdrift 0.
    ⚠ **Nicht startklar**, und das bleibt die richtige Meldung. Kein Stichtag verschoben,
    keine Historie umgeschrieben, kein Test angepasst.
13. **Sechs Sachtickets geschlossen** (`platform/T-0017`, `platform/T-0018`,
    `promt-team/T-0005`, `promt-team/T-0006`, `promt-team/T-0001` als Klammer,
    `projects/p12/T-0008`), **drei neu** (`platform/T-0018`, `p12/T-0008`, `p12/T-0009`),
    **eine Zerlegung**, **fünf neue Anforderungen** (SWR-139 bis SWR-143). Vier Tickets auf
    Sprint 17 verschoben, jedes mit **Grund im Ticket** und mit benannter oder ausdrücklich
    **fehlender** Naht.

## Das Wichtigste (Stand Sprint 15, 2026-08-17)

1. **✅ `platform/T-0013` gebaut — SWR-136, das dringlichste offene Ticket der
   Organisation.** Das Sprintregister kennt ein **Ende**: eine Zeile ohne `ende` ist ein
   laufender Sprint, `beginne()` verweigert die Eröffnung, solange einer läuft, und die
   Meldung **nennt** ihn (B038). Zweimal verschoben und **beide Male von seinem eigenen
   Schadensfall überholt** — das Ticket gegen Nebenläufigkeit war zweimal deren Opfer.
2. **⚠ Die Zeitgrenze der ersten DoD ist vor dem Bauen gemessen und verworfen.** 12
   Abstände: Median 57 Min, **Minimum 15**, **7 von 12 unter dem Takt**. Sie hätte die
   Mehrheit der regulären Folgeläufe abgewiesen.
   > **Eine Uhr sieht bei 15 Minuten Abstand denselben Wert wie bei einem Absturz nach 15
   > Minuten. Nur die Schreibspur unterscheidet die beiden.**

   Gebaut wurde die Abbrucherkennung an **Schreibspuren**: Beobachtung anhängen, der nächste
   Lauf vergleicht — bewegt = arbeitet (abweisen), unbewegt = abgebrochen (Übernahme, `ende`
   **mit** `abgebrochen: true`, DoD 6). Wartezeit **ein** Takt, nicht unendlich.
3. **⚠ Zwei Abweichungen von der DoD, beide IM TICKET begründet** (`L-2026-08-17ag`
   angewandt): (a) die Registerdatei bleibt **append-only**, ihre Zeilen sind ab jetzt
   **Ereignisse** — ein Umschreiben verliert Daten genau bei zwei Schreibern, also im Fall,
   für den das Modul existiert; (b) `schreibspur()` ruft **kein `git`** auf, sondern liest
   `.git/HEAD` von der Platte, weil nach SWR-134 schon ein **lesendes** `git status` eine
   unlöschbare `index.lock` hinterlässt. *Eine Prüfung gegen Nebenläufigkeit, die selbst
   Sperren erzeugt, wäre ihr eigener Schadensfall.* Gehalten von einem Zähltest über den
   **Syntaxbaum**.
4. **⚠⚠ Drei bestehende Zusicherungen hatten das Fehlverhalten ZUGESICHERT.**
   `test_beginne_zaehlt_hoch` verlangte `beginne("a") → 1`, `beginne("b") → 2` **ohne**
   `beende` dazwischen — wörtlich den Schaden aus `platform/T-0013`.
   > **Eine Prüfung, die den Fehler zusichert, ist schlimmer als keine: sie verteidigt ihn
   > gegen jede Änderung.** Sechste Gestalt der Familie SWR-122/125/128/131/136.

   Nicht gelöscht, sondern um das `beende()` ergänzt — ihre *Absicht* war der Zähler.
5. **✅ `promt-team/T-0001` nach der FÜNFTEN Berührung zerlegt, Teil a gebaut** (`T-0004`,
   SWR-137): Feldvertrag der Lauftelemetrie, drei Zustände je Feld, **Blocker statt
   Schätzung**, am **einen** Schreibweg. ⚠ Liefert **keine Zahl** — er macht die Baseline
   **als leer erkennbar** (0 von 7 Läufen mit Token, 6 von 7 ohne `aufgaben_typ`) statt sie
   mit einer siebenfachen `0.0` zu beantworten, die wie ein Ergebnis aussieht.
6. **⚠⚠ Ein eigener roter Test hat den Hauptbefund von SWR-137 gefunden: Schlüssel sind
   keine Messungen.** Die erste Fassung wandte die Drei-Zustände-Regel auf alle
   Pflichtfelder an — ein leerer `aufgaben_typ` war damit „echte Null", und die Lücke, um
   deren Sichtbarkeit es geht, wäre durchgewinkt worden.
   > **Eine Regel über Messwerte auf einen Schlüssel anzuwenden ist eine
   > Kategorienverwechslung, und sie macht die Lücke unsichtbar, die sie zeigen soll.**

   Die schärfste Zusicherung prüft **beide Fälle in einem Eintrag**: getrennte Tests waren
   jeder für sich grün zu bekommen, indem man die Regel in die eine oder andere Richtung
   verschiebt.
7. **✅ `pm/T-0052` nach der FÜNFTEN Berührung geschlossen** (SWR-138): „Für dich" hat zwei
   Abschnitte. Die Beobachtung des Auftraggebers war präzise, die Ursache lag eine Etage
   tiefer als seine Frage — **die Inbox lehnt Handlungstickets nicht ab, sie kennt sie
   nicht. Es fehlte kein Filter, sondern der Kanal.** Die Handlungen sind die **Teilmenge**
   von `wartet_auf_mensch` ohne die DRs (kein zweiter Erhebungsweg, B033), der scharfe Fall
   (DR **mit** `verantwortlich: mensch`) ist eigens zugesichert.
8. **⚠ Die für `pm/T-0052` benannte Naht war beim Schneiden hinfällig.** Der Abschnitt
   „Entscheidungen" existiert seit SWR-042; eine Zerlegung hätte einen **leeren** Teil
   erzeugt. **Eine benannte Naht kann verfallen** — deshalb ganz geschlossen, und das steht
   im Ticket statt in einer stillen Ganzschließung.
9. **✅ `pm/T-0061` gemessen und entschieden (Klasse C) — die Messung widerlegt die Prämisse
   des eigenen Tickets.** Über **966** Ticket-Blobs der ganzen Historie: **167** trugen
   `frist` **und** `geplant_sprint`, **81** Kombinationen in **6** Repos. Die Prüfung hatte
   einen großen Anwendungsbereich und hat ihn in **Sprint 11** verloren — sie hatte ihn
   nicht „nie". Entscheidung: **stehen lassen**, vier Gründe, der stärkste Einwand (SWR-122)
   trifft nicht zu, weil `app.js` die Liste liest. ⚠ Ob sie je **angeschlagen** hat, bleibt
   offen und wird als offen benannt: es zu rekonstruieren hieße, die damalige Sprintnummer
   zu erfinden (B027/B038).
10. **✅ `pm/T-0066` Klammer geschlossen** — DoD 3 beantwortet: **kein** neuer CR, weil
    SWR-135 (Dashboard) der Nachfolger der widerlegten Ursache ist. *Wir haben das Richtige
    gebaut und die falsche Ursache behandelt — und die richtige ist im nächsten Lauf
    behandelt worden.*
11. **⚠⚠ ZWEI selbstverschuldete Vorfälle desselben Typs in diesem Lauf, einer davon
    committet.** Ein Statuswechsel besteht aus zwei Vorgängen (Datei schreiben, buchen).
    Scheitert der zweite an einer Git-Sperre, ist der Zustand geschrieben und **nicht**
    gebucht; der nächste überschreibt ihn. `platform/T-0013`: **vor** dem Commit bemerkt,
    Reihenfolge wiederhergestellt (nichts war gebucht). `pm/T-0052`: **committet** —
    `in_progress → done`, **dritter** unzulässiger Übergang seit dem Stichtag.
    > **Beim ersten Mal ging es gut aus, weil jemand hingesehen hat — nicht, weil eine
    > Vorkehrung gegriffen hätte.** Und der Unterschied zwischen beiden Fällen war die
    > Aufmerksamkeit eines Augenblicks.

    Nicht geglättet: kein Stichtag verschoben, keine Historie umgeschrieben, kein Test
    angepasst. Neu als `platform/T-0017`, Lesson `L-2026-08-17ah`. ⚠ Die Reparatur heißt
    *ein Zustandswechsel ist ein Vorgang* und **nicht** „besser aufpassen".
12. **⚠ Nebenbefund an SWR-134, im selben Lauf gemessen:** der Rückfall von
    `git_schreiben` greift bei **selbstverursachten** Sperren nicht. `verbuche()` ruft `add`,
    dann `commit`; das eigene `add` hinterlässt die `index.lock`, an der das `commit`
    scheitert, und die Wiederholung läuft in dieselbe Folge (drei Commits dieses Laufs mit
    `FEHLER | geraeumt: 19`).
    > **Der Rückfall ist gegen die Sperre eines fremden Laufs gebaut. Gegen die eigene hilft
    > er nicht, weil er sie zwischen seinen beiden Hälften selbst erzeugt.**

    Als Punkt 6 in `platform/T-0017`; die Räumung gehört **zwischen** `add` und `commit`.
13. **⚠⚠ Beim Terminieren gemessen: `blocked_by` kann einen repo-übergreifenden Blocker
    nicht ausdrücken.** Der Versuch, `platform/T-0016` gegen `team-dashboard/T-0001` zu
    sperren, wurde abgewiesen (*„verweist auf unbekanntes Ticket"*). 17 Repos, und `ref()`
    (SWR-087) existiert genau deshalb — für Blocker gilt es nicht.
    > **Ein Abhängigkeitsfeld, das nur innerhalb eines Repos zeigen kann, kann die häufigste
    > Abhängigkeit dieser Organisation nicht ausdrücken: die zwischen zwei Teams.**

    Das Ticket bleibt `open`, die Blockade steht **in Prosa** — für jede Prüfung unsichtbar,
    benannt statt geglättet, mit Erkennungsfrage im Ticket.
14. **Drei Zerlegungen nach der fünften Berührung, alle an der IM TICKET benannten Naht:**
    `promt-team/T-0001` (→ T-0004 erledigt / T-0005), `promt-team/T-0002` (→ T-0006 /
    T-0007, mit `blocked_by`, weil *ohne Format 20 Fälle 20 Einzelmeinungen sind*),
    `projects/p11/T-0009` (→ T-0012 / T-0013, Naht = *eine Zugriffsentscheidung ist kein
    Layout*).
15. **879 Python-Tests, davon 1 rot** (der Übergangsbefund, selbstverschuldet, benannt),
    **45 JS-Tests grün** (+5), Matrix **138 SWRs / 0 Lücken**, Briefkasten zweimal geprüft
    und beide Male 0 offen, entschiedene unverbuchte DRs **0**, Plan-Drift 0, Statusdrift 0.
    ⚠ **Nicht startklar**, und das ist die richtige Meldung: drei unzulässige Übergänge seit
    dem Stichtag.
16. **⚠ Eine Kennzahl aus dem Sprint-14-Bericht lässt sich nicht reproduzieren.** Dort stand
    *„826 Python-Tests (2 rot)"*; gemessen ist heute **ein** roter Test, der **drei**
    Verstöße listet. Entweder war damals ein zweiter Test rot, oder **Verstöße** wurden als
    **Tests** gezählt — ohne den damaligen Stand nicht entscheidbar, deshalb steht beides da.
    > **„2 rot" und „2 Befunde" sind zwei Aussagen, und eine Kennzahl, die zwischen ihnen
    > rutscht, ist keine Messung mehr.**
17. **Fünf Sachtickets geschlossen** (`platform/T-0013`, `promt-team/T-0004`, `pm/T-0052`,
    `pm/T-0061`, `pm/T-0066`), **sieben neu** (`promt-team/T-0004`–`T-0007`,
    `p11/T-0012`/`T-0013`, `platform/T-0017`), **drei Zerlegungen**. Erstmals seit Sprint 13
    **ein** Lauf ohne Nebenlauf.

---

## Das Wichtigste (Stand Sprint 14, 2026-08-17)

1. **✅ Der Auftraggeber hat die Messung geliefert, die dem Team fehlte** — zwei Aufnahmen
   seines 4K-Bildschirms zu `pm/T-0068`. Gemessen: **3 Projektkacheln** ohne Scrollen sichtbar,
   links und rechts je rund **ein Fünftel der Breite leer**, Kacheln einzeln untereinander in
   der 62rem-Spalte.
2. **⚠⚠ Die Messung widerlegt die Annahme, auf der `pm/T-0066` beruhte.** Das Team hielt die
   **Menge** der Kacheln für die Ursache des Scrollens und baute deshalb das Falten
   (`pm/T-0067`, SWR-133). Die Ursache ist das **Layout**.
   > **Wir haben das Richtige gebaut und die falsche Ursache behandelt.** Beides gleichzeitig
   > wahr. Zweiter Nebenbefund: die Sprint-Plan-Tabelle steht mit ~25 Zeilen **über** den
   > Gruppen — am Cockpit zu falten macht den Weg dorthin nicht kürzer.

   ⚠ Die Frage war zu eng gestellt (*„wie viele Kacheln"*) und hat eine Ursache zurückgegeben.
   Das ist ein Fehler der Fragestellung, nicht der Antwort.
3. **✅ `projects/p11/T-0008` nach der VIERTEN Berührung zerlegt**, Naht lag seit Sprint 12
   wörtlich im Ticket: `p11/T-0010` (Endpunkt, lesend, **erledigt**) und `p11/T-0011`
   (Konfiguration, schreibend, Sprint 15).
4. **✅ Gebaut: SWR-135** — Reiter „Dashboard", `/api/dashboard`. Der Endpunkt liest
   **ausschließlich** `aggregation.cockpit_alle`; der Test ersetzt diese **einzige** erlaubte
   Quelle durch eine Attrappe und verlangt, dass **nichts** übrig bleibt. Ein Test, der nur
   prüft „es kommen Kacheln", hätte einen zweiten Erhebungsweg nicht bemerkt (Risiko R1,
   SWR-092).
5. **✅ Die drei Vertragszustände werden erstmals AUSGEWERTET.** `cockpit` liefert seit
   SWR-108 den Unterschied zwischen `team: null` und `briefe_offen: 0` — **gelesen hat ihn
   nie jemand**, jede Ansicht entschied selbst, was ein leeres Feld bedeutet. Ab jetzt je Feld
   `{wert, zustand}`, und `nicht_geliefert` ist **auch auf dem Schirm** sichtbar anders als
   eine `0`. ⚠ Wäre es gleich formatiert, wäre die Unterscheidung im Code richtig und für den
   Leser wertlos.
6. **⚠ Ein Feld ohne bekannten Zustand gilt als `nicht_geliefert`.** Der erste Entwurf fiel
   bis `String(wert)` durch und hätte die Zeichenkette **„undefined"** angezeigt — eine
   Anzeige, die aussieht wie ein Inhalt und keiner ist. Gefunden, weil die **Gegenprobe zum
   eigenen Test fehlte**: er war so geschrieben, dass er beides durchgelassen hätte.
7. **✅ Zwei Festlegungen aus Sprint 9 nach fünf Sprints eingelöst** — DR `p11/T-0006`
   (LAY-a, 08:11) und `ADR-P11-002`: das Dashboard verlässt den Korridor, **die Ausnahme
   sitzt an der Ansicht** (`main.breit`), `main { max-width:62rem }` bleibt ausnahmslos.
   ⚠ Und sie wird bei **jedem** regulären Zeichnen abgeräumt — sonst blieb `breit` nach einem
   Dashboard-Besuch hängen und die Ausnahme wäre faktisch global, obwohl LAY-b ausdrücklich
   verworfen war. Der Aufräumer steht in `zeige()`, nicht in der Dashboard-Funktion: dort
   müsste ihn jede künftige Ansicht kennen.
   ⚠ **Fünfte Gestalt der SWR-131-Familie:** eine Entscheidung, die vorlag und nicht wirkte —
   diesmal nicht, weil niemand sie las, sondern weil ihr Ticket viermal verschoben wurde.
8. **⚠ Nebenbefund von SWR-135, gefunden von einer Prüfung für etwas anderes:** die
   Drei-Zustände-Regel steht in `cockpitKarte` **dreimal inline**. Alle drei sind **sachlich
   richtig** — das ist der Befund. Vier Formulierungen bestehen damit heute. Aufgenommen als
   `platform/T-0016`, **bei 3 eingefroren** und ausdrücklich **nicht** mitmigriert:
   `/api/cockpit` führt kein `zustand`-Feld, eine zweite Herleitung in JavaScript wäre ein
   *neuer* B033-Fall, und die Aufnahme in den Payload berührt den Widget-Vertrag (B066,
   Eigentümer `team-dashboard`, Versions-Bump).
9. **⚠⚠ ZWEI Läufe hielten Sprint 14 gleichzeitig — und BEIDE haben geschrieben.** Am 11:05
   hatte der zweite Lauf noch verzichtet. Hier ist der Fall eingetreten, vor dem
   `platform/T-0013` warnt.
10. **⚠⚠ Die Kollision ist eingetreten — bei der SWR-Nummer, nicht bei der Ticket-ID.** Beide
    Läufe nannten ihre Anforderung **`SWR-134`**. Entdeckt wurde es **nicht von einer
    Prüfung**, sondern beim Lesen des fremden Commits.
    > **Eine Kollisionsregel schützt die Kennungen, die sie nennt — und keine anderen.**

    Die Regel vom 2026-08-16 gilt für **Ticket-IDs**; für `SWR-xxx`, `D0xx`, `N-xxxx`, `L-…`,
    `ADR-…` gab es sie nicht. Aufgelöst: der **committete** SWR-134 gewinnt, das Dashboard
    wurde auf **SWR-135** umgenummert. Verankert als `L-2026-08-17ae`.
11. **⚠ Und die Prüfung wäre auch mit Regel wirkungslos gewesen.** Der Nebenlauf hat die 134
    *unmittelbar vor* dem Commit gegen HEAD geprüft — gegen einen bewegten HEAD ist das ein
    Wettlauf. Die Reparatur heißt `platform/T-0013` (Register mit **Ende**), nicht
    „gründlicher prüfen". **Es ging gut aus, weil beide Läufe verschiedene Dateien anfassten —
    Glück, keine Vorkehrung.**
12. **✅ Der Nebenlauf hat `platform/T-0015` gebaut (SWR-134) — und dessen Ursachenaussage
    widerlegt.** Der `rename`-Rückfall existierte seit `pm/T-0023`; der Befund war die
    **Reichweite**: von acht Commit-Stellen benutzte genau **eine** die Räumung.
    *Eine Reparatur, die nur ihr eigener Fundort benutzt, ist eine Reparatur des Fundorts.*
13. **✅ Sprint 13 ist auf dem Remote angekommen** — der Auftraggeber hat gepusht.
14. **826 Python-Tests (2 rot), 40 JS-Tests grün** (+11), Matrix **135 SWRs / 0 Lücken**,
    Briefkasten zweimal geprüft und beide Male 0 offen, entschiedene unverbuchte DRs **0**,
    Plan-Drift 0, Statusdrift 0.
    ⚠ **Weiterhin nicht startklar:** die zwei Statusverstöße aus Sprint 13 stehen unverändert.
    **Dieser Lauf hat keinen neuen erzeugt** — `L-2026-08-17ad` hat gehalten.
15. **Drei Tickets geschlossen** (`pm/T-0068`, `p11/T-0010`, Zerlegung `p11/T-0008`), **drei
    neu** (`p11/T-0010`, `p11/T-0011`, `platform/T-0016`). `p11/T-0011` ist durch `T-0010`
    entsperrt. ⚠ `promt-team/T-0001` und `pm/T-0052` sind bei der **fünften** Verschiebung —
    Kandidat 1 und 2 für Sprint 15.

---

## Das Wichtigste (Stand Sprint 13, 2026-08-17)

1. **⚠⚠ Der Startcheck dieses Laufs hat einen Fehler von Sprint 12 gegenüber dem
   Auftraggeber gefunden: wir haben ihn um eine Antwort gebeten, die er zwölf Minuten zuvor
   gegeben hatte.** `projects/p12/T-0007` wurde **11:48:25** über die Inbox mit
   `B-node-optional` entschieden und committet (`c3aa788`). Danach schrieb derselbe Sprint 12
   drei Berichte — Sprintplan 11:50, Agenda ~12:00, Projektstatus 12:03 —, die alle sagen,
   die Frage liege beim Menschen, Frist 24.08. Der Preflight bestätigte es (`1 Ticket wartet
   auf den Menschen`) und meldete trotzdem **STARTKLAR**.
2. **⚠⚠ Und es ging eine E-Mail hinaus.** `dr_benachrichtigung.unbenachrichtigte` filterte
   nur auf `status` und den Versand-Marker, **nicht** auf „entschieden" — während
   `warnfaellige()` eine Funktion darunter es tat. Der Vermerk
   `**Benachrichtigt:** 2026-08-17 per E-Mail (SWR-033)` steht unter der Entscheidungszeile
   und wird **nur bei `ok=True`** geschrieben (`mailer.sende` liefert ohne `SMTP_HOST`
   `False`). Es ist die einzige Stelle dieses Befunds mit **Außenwirkung**, und sie war die
   schwächste.
3. **⚠ Ursache: vier Formulierungen eines Wortes.** `inbox` las „entschieden" am
   Rumpfmarker (SWR-039), `board`/`aggregation`/`preflight` am `status`,
   `aggregation.cockpit` trug eine dritte Kopie, `dr_benachrichtigung` eine vierte.
   `inbox.entscheide` fasst `status` nie an — nach ADR-003 richtig so.
   > **Eine Entscheidung im Fließtext ist für jede Prüfung unsichtbar.**

   ⚠ Der Docstring von `aggregation.wartet_auf_mensch` sagt seit SWR-120 wörtlich *„Ein
   entschiedener DR wartet auf niemanden"* — der Satz war **richtig und unwirksam**.
4. **⚠⚠ Nicht alle vier lagen falsch — sie waren verschieden.** Der Cockpit-DR-Block hat
   `p12/T-0007` nach 11:48 korrekt **nicht mehr** geführt, während der Preflight ihn zählte.
   *Der Preis von B033 ist nicht eine falsche Anzeige, sondern zwei richtige, die sich
   widersprechen.*
5. **Gebaut: SWR-131** (`platform/T-0014`). `board.dr_entschieden` ist der eine
   Auflösungspunkt (Rumpfmarker **oder** finaler Status — Anfang und Ende **eines**
   Vorgangs); alle vier Leser delegieren; **neuer Preflight-Befund**
   `dr_entschieden_nicht_verbucht`. ⚠ Die erste Hälfte allein wäre **schlimmer als der
   Fehler**: das Ticket verschwände aus jeder Anzeige und stünde weiter offen — SWR-122 eine
   Etage tiefer. 19 Zusicherungen, 5 Gegenproben, darunter ein Test, der die
   **Marker-Definitionen im Quelltext zählt**.
6. **⚠⚠ Ein bestehender Test hat das Fehlverhalten ZUGESICHERT.**
   `test_entschiedene_drs_ohne_warnung` prüfte korrekt, dass SWR-034 keine Frist-Warnung
   schickt, und verlangte in derselben Zeile `["gesendet"]` — die Neu-Mail an einen
   entschiedenen DR.
   > **Eine Prüfung, die den Fehler zusichert, ist schlimmer als keine: sie verteidigt ihn
   > gegen jede Änderung.** Fünfte Gestalt der Familie (SWR-122/125/128/131).
7. **⚠ Der erste Anlauf von SWR-131 übersah zwei der vier Leser.** Gefunden erst durch ein
   `grep`. `platform/T-0014` wurde deshalb **im selben Lauf wiedereröffnet** (KPI
   Wiederöffnungsquote) statt still nachgebessert.
8. **✅ Zwei Zusagen aus Sprint 12 eingelöst** — `pm/T-0064` (SWR-132) und `pm/T-0067`
   (SWR-133). Die Agenda von Sprint 12 schrieb *„Beides kommt im nächsten Lauf"*.
9. **SWR-132: die Liste kommt aus DEMSELBEN Objekt, das `offen_gesamt` zählt.** Der
   Ticket-Entwurf nannte `aggregation`; gemessen ist `sprint.offene_tickets` die bessere
   Quelle, weil die Zahl schon von dort kommt — Zahl und Liste **können nicht
   auseinanderlaufen**. Das ist SWR-131 im selben Lauf angewandt statt nur beschrieben.
   ⚠ `rolle` und `verantwortlich` bleiben **getrennt** (der Befund hinter SWR-116); die
   Rollen-Sicht ist eine **Gruppierung derselben Liste**, keine zweite Ansicht (B033).
10. **⚠ SWR-133: `pm/T-0066` wurde zerlegt, weil die halbe DoD nicht erfüllbar war.** DoD 4
    („wie viele Kacheln bei 1920×1080") ist eine Frage an einen gerenderten Browser; ADR-008
    hat bewusst keinen, ein Headless-Browser wäre **Klasse A**. Gebaut wurde die Wirkung
    (`pm/T-0067`), die Messung liegt als `pm/T-0068` beim Menschen.
    > **Wir haben gebaut, was er wollte, und wissen nicht, um wie viel es besser wurde.**
    Das steht im Bericht statt als Zahl behauptet zu werden.
11. **⚠⚠ Dieser Lauf hat selbst ZWEI unzulässige Statusübergänge committet — und sie
    stehen gelassen.** `platform/T-0014` ging in der Datei `done → in_progress → in_review →
    done`, in den **Commits** aber `done → in_review`: der Zwischenstand bekam keinen eigenen
    Commit, weil die Wiederöffnung sich wie Buchhaltung anfühlte und nicht wie ein
    Zustandswechsel. **Kein Verschieben des Stichtags, kein Umschreiben der Historie, keine
    Anpassung des Tests.** ⚠⚠ **Und derselbe Fall ein zweites Mal: `pm/T-0064` (`open → in_review`)** — er lag beim
    Schreiben der Lesson zum ersten Fall **schon in der Historie** und wurde erst vom
    Abschluss-Preflight gefunden. *Eine Regel aufzuschreiben ist nicht dasselbe wie den
    Bestand danach zu prüfen.* Verankert als `L-2026-08-17ad`.
    > *Der Lauf, der die Prüfung gegen „Zustand nur in Prosa" gebaut hat, hat im selben
    > Ticket den Zustand in der Historie verloren.*
12. **⚠ Die Taktmessung widerlegt die DoD von `platform/T-0013` — vor dem Bauen.** 12
    Abstände: **Median 57 Min, Minimum 15, Maximum 124, 7 von 12 unter 60.** Die geplante
    Zeitgrenze („weniger als ein Takt") hätte **die Mehrheit der regulären Folgeläufe
    abgewiesen**. Das Ticket hat selbst verlangt, den Takt zu messen; die DoD ist korrigiert
    (Kriterium `ende`, Abbrucherkennung über Schreibspuren statt Uhr). Erste Verschiebung mit
    gemessenem Grund.
13. **⚠ Drei vierte Verschiebungen — und die fällige Zerlegung ist NICHT gemacht worden.**
    `pm/T-0052`, `projects/p11/T-0008`, `promt-team/T-0001`. Die Regel `L-2026-08-17x`
    verlangt bei vier die Zerlegung; die Nähte liegen seit Sprint 12 benannt bereit. ⚠
    `p11/T-0008` ist damit **zweiter Lauf in Folge nach ausdrücklicher Zusage**.
14. **⚠ `os.rename` gelingt, wo `os.remove` scheitert.** Vier Commits dieses Laufs wurden von
    verwaisten `.git/*.lock` abgewiesen; auf diesem Mount ist `unlink` verboten,
    **Umbenennen** erlaubt. SWR-123 räumt per `unlink` und greift hier nicht. Aufgenommen als
    `platform/T-0015` — und **als Schuld geführt**: die Regel steht in `L-2026-08-17ac` und
    noch nicht im Code (SWR-125-Lage, benannt statt als erledigt gemeldet).
15. **Vier Sachtickets geschlossen** (`projects/p12/T-0007`, `platform/T-0014`, `pm/T-0064`,
    `pm/T-0067`) plus sechs Takt-Pflichten. **Vier neue Tickets**: `platform/T-0014`,
    `platform/T-0015`, `pm/T-0067`, `pm/T-0068`. `pm/T-0065` ist durch `T-0064` **entsperrt**.
16. **786 Python-Tests grün, 1 rot** (Punkt 11, selbstverschuldet und benannt), **29 JS-Tests
    grün** (+13), Matrix **133 SWRs / 0 Lücken**, entschiedene unverbuchte DRs **0** (war 1),
    unzulässige Übergänge seit Stichtag **2**, Altbestand 52 (unverändert).
    ⚠ **Der Lauf ist damit nicht startklar, und das ist die richtige Meldung.**
17. **Briefkasten: beim Start und beim Abschluss geprüft, beide Male 0 offen.** Die Regel aus
    Sprint 11/12 hat gegriffen. ⚠ Die Erkennungsfrage daraus war der Schlüssel zum ganzen
    Lauf: dieselbe Aussage („bei 60-Minuten-Takt ist ein Eingang mitten im Lauf der
    Regelfall") gilt für **Entscheidungen** wie für Briefe — Sprint 12 hatte sie nur für
    Briefe angewandt.

---

## Das Wichtigste (Stand Sprint 12, 2026-08-17)

1. **⚠⚠ Der beschlossene HMI-Sprint konnte seine eigene Abnahme nicht erfüllen.** Die DoD
   von `pm/T-0058` und `pm/T-0060` verlangt wörtlich *„JS-Test; scheitert nachweislich
   gegen den Vorstand"*. Gemessen: **741 Python-Tests, 0 JS-Tests** bei **1.524 Zeilen
   `app.js`**, während SWR-098/099/100 Nachweise an JavaScript verlangen.
   > **Eine Prüfung, die es nicht gibt, ist von einer grünen nicht zu unterscheiden.**
   Fünf Sprints lang war „Tests grün" wahr — für die Tests, **die es gab**. Dritte Gestalt
   derselben Familie in drei Sprints: SWR-122 (Prüfung ohne Leser), SWR-125 (Regel ohne
   Prüfung), jetzt **Fläche ohne Prüfung**.
2. **Gebaut: ADR-008 + SWR-128** (`projects/p12/T-0004`). Renderentscheidungen wandern nach
   `backend/static/regeln.js` (kein DOM, kein Netz), geprüft mit Nodes **eingebautem**
   Runner — **kein npm, kein package.json, keine Abhängigkeit**. ADR-002 („no build") wird
   damit nicht widerrufen, sondern **eingelöst**: sein eigener Satz lautete *„bei
   wachsendem Frontend-Scope neu bewerten"*. 13 Python-Zusicherungen.
3. **⚠ Die Werkzeugfrage ist NICHT vom Team entschieden.** „Darf Node Voraussetzung
   werden?" ist ein **neues externes Werkzeug** → **Klasse A** → DR
   **`projects/p12/T-0007`** (A/B/C, Default `B-node-optional`, Frist 2026-08-24). Die
   bequeme Gegenerzählung („ist gratis, also Klasse C") war verfügbar und wurde nicht
   genommen — genau dafür existiert die Regel.
4. **⚠ `übersprungen` ist nicht `ok`.** `js_tests.lauf()` kennt **drei** Zustände. Wer nur
   zwei kennt, verbucht das Nichtlaufen als Erfolg — und genau so blieb „null JS-Tests"
   fünf Sprints unsichtbar. `rot` zählt als Befund, `übersprungen` nicht: ein Werkzeug ohne
   Entscheidung darf den Lauf des Menschen nicht blockieren. Die Meldung nennt `node`
   **und** den offenen DR, damit sie einen Handlungsweg trägt statt eine Sackgasse.
5. **⚠ Die ADR-Regel wurde im selben Lauf mit einer Prüfung versehen** — die Lehre aus
   Sprint 11 („eine Regel, die im selben Lauf am Nachbarfall nicht angewandt wird, ist noch
   keine Praxis"). `regeln.js` darf im **Code** kein `document.`/`fetch(` enthalten,
   `app.js` muss die vier Regeln aus `Regeln` lesen. ⚠ Nebenbefund: der erste Entwurf
   dieser Prüfung wurde **an einer Kommentarzeile** rot — sie bestrafte die Begründung,
   warum die Datei das DOM *nicht* anfasst. Kommentare werden jetzt entfernt, mit
   Gegenprobe gegen zu viel Nachsicht.
6. **✅ `pm/T-0060` (SWR-129): der Brief ist im HMI ein Verlauf.** Beiträge mit Absender und
   Zeit, nach Urheber getrennt, **Antwortfeld je Brief**, und der durch eine Nachfrage
   wieder geöffnete Brief trägt ein eigenes Schild — ohne das sähe er aus wie ein nie
   beantworteter. ⚠ Der Urheber wird aus der **Nutzerregistry** aufgelöst, nicht aus einem
   Vergleich mit `brief.von`: der Mensch darf einen anderen registrierten Nutzer wählen —
   Registry ist ein Fakt, Namensvergleich wäre eine Annahme (B038). Die Gegenprobe wird
   gegen die naive Regel rot.
7. **✅ `pm/T-0058` (SWR-130): Anzeige ohne Reload — auch im Fehlerfall.** Der 900-ms-Timer
   ist ersetzt; gezeigt wird, was `GET /api/briefkasten` liefert (kein zweiter
   Inhaltszustand, B033). Im 503-Fall wird **ebenfalls** nachgeladen und der Brief trägt
   „gespeichert, noch nicht verbucht" — die Datei liegt vor git auf der Platte (SWR-121),
   und eine Liste, die sie verschweigt, behauptet das Gegenteil. Ohne Kennung in der
   Meldung wird **keine erfunden** (B038): das ist dann ein echter Fehler.
8. **✅ Klammer `pm/T-0039` geschlossen** — beide Teile erledigt (`T-0059`/SWR-126 Sprint
   11, `T-0060`/SWR-129 Sprint 12). Vier Verschiebungen, eine Zerlegung, jetzt vollständig.
9. **⚠ `pm/T-0054` nach ZWEI Verschiebungen zerlegt statt nach vier.** Sprint 11 leitete
   die Regel bei vier ab und hinterließ die Erkennungsfrage *„auf welche anderen offenen
   Fälle trifft dieser Satz gerade zu?"* (`L-2026-08-17x`). Antwort dieses Laufs:
   `pm/T-0054`, dessen Naht wörtlich im Ticket steht. Neu: `pm/T-0064` (Liste, Sprint 13),
   `pm/T-0065` (Knopf, Sprint 14).
10. **⚠⚠ Eine Zusage an den Auftraggeber ist nicht eingelöst.** Sprint 11 schrieb ihm, der
    Dashboard-Endpunkt und die Detailseiten kämen *„im Oberflächen-Lauf als Nächstes"*.
    Der Oberflächen-Lauf war dieser. `p11/T-0008` ist **dritte Verschiebung**. Der Befund
    steht im Ticket, im Sprintplan und in der Agenda — nicht in einer Fußnote.
11. **⚠ Drei dritte Verschiebungen** (`pm/T-0052`, `p11/T-0008`, `promt-team/T-0001`). Bei
    allen dreien ist die **Zerlegungsnaht jetzt benannt**, statt sie beim vierten Mal zu
    suchen. Das ist der operative Unterschied zu Sprint 11.
12. **⚠ Zwei Routine-Läufe schrieben heute 10:25–11:21 gleichzeitig in dieselben Repos.**
    Der zweite hat es gemessen und **nichts geschrieben** (Befundbericht 11:05).
    `sprint_register.beginne()` ist idempotent je *Kennung* und kennt keinen Fall für
    **zwei verschiedene** Läufe. *Ein Register ohne Endezeitpunkt kann Überlappung nicht
    sehen.* Aufgenommen als **`platform/T-0013`** (Sprint 13) — mit der Auflage, die
    Taktabstände **vor** dem Bauen zu messen: 07:10 / 09:14 / 10:04 / 11:27 sind **nicht**
    gleichmäßig 60 Min, der Takt ist bisher eine Annahme.
13. **⚠ Ein Schreibversuch hat in diesem Lauf eine Datei zerstört.** Ein Patch-Skript
    öffnete `preflight.py` mit ungültigem `newline`-Wert; Python kürzte die Datei auf
    **0 Bytes** und warf danach die Ausnahme. Folgenlos, weil auf einer Arbeitskopie
    gearbeitet wurde (und das war **Glück aus einer anderen Entscheidung** — Tests auf
    einer Kopie sind ~50× schneller, Befund vom 11:05 — nicht Vorsicht an dieser Stelle).
    **Dieselbe Klasse wie `abschluss.cmd` in Sprint 1**, dem einzigen offenen Punkt beim
    Auftraggeber. Verankert als `L-2026-08-17y`: Temp-Datei schreiben, dann `os.replace`.
14. **Vier Sachtickets geschlossen** (`p12/T-0004`, `pm/T-0060`, `pm/T-0058`, `pm/T-0039`),
    alle über den legalen Weg mit je drei Commits, plus sechs Takt-Pflichten. **Vier neue
    Tickets**: `p12/T-0007` (DR), `platform/T-0013`, `pm/T-0064`, `pm/T-0065`.
15. **754 Python-Tests grün** (+13), **16 JS-Tests grün** (+16, von **null**), Matrix
    **130 SWRs / 0 Lücken**, Preflight **STARTKLAR** — nach allen Änderungen des Laufs
    gemessen. unterminiert 0, Kalenderfristen 0, Plan-Drift 0, überfällig 0, Statusdrift 0,
    Statusübergänge seit Stichtag 0, Altbestand 52 (unverändert).
16. **⚠ Briefkasten: beim Start leer, beim Abschluss nicht.** `pm/N-0042` traf **12:00**
    ein, mitten im Sprintabschluss, und wurde noch in diesem Lauf beantwortet (Klasse B).
    **Zweiter Sprint in Folge**, in dem der Startstand am Laufende nicht mehr galt — die
    Regel aus Sprint 11 („zweimal prüfen") hat gegriffen, und die Wiederholung zeigt, dass
    es kein Sonderfall ist: bei 60-Minuten-Takt ist ein Brief mitten im Lauf der
    **Regelfall**. ⚠ Nebenbefund am eigenen Ablauf: der Abschluss-Preflight lief **nach**
    dem Schreiben der Berichte, die deshalb nachträglich ergänzt werden mussten.
17. **⚠ Der neue Brief enthielt einen Widerspruch zum Brief desselben Morgens** —
    `pm/N-0038` verlangt, **alle** offenen Aufgaben zu sehen (zum Priorisieren),
    `pm/N-0042` weniger Scrollen. Aufgelöst als *falten statt weglassen* und dem
    Auftraggeber **im Antwortbrief offengelegt**, statt als stillschweigende Auslegung
    angewandt zu werden. Die Rollen-Sicht wurde in `pm/T-0064` **hineingezogen** statt
    danebengestellt (B033); neu ist nur `pm/T-0066` (Kompaktheit).

---


## Das Wichtigste (Stand Sprint 11, 2026-08-17)

1. **⚠⚠ Der Auftraggeber hat Kalenderfristen zum zweiten Mal gerügt — die Ursache war die
   eigene Prüfstrecke.** `unterminierte_tickets` (SWR-091 → SWR-114 → SWR-117) meldet jedes
   offene Ticket **ohne `frist`**. Die Gegenentscheidung steht seit **SWR-106**
   (Anforderungen v1.12): *„Terminierung auf Sprints statt auf Kalenderdaten"* — derselbe
   Satz im Kopf von `sprint_register.py`. **Die Entscheidung hat keine Prüfung
   mitgeändert.** Gebaut: **SWR-125** (`platform/T-0012`), 19 Tests.
2. **⚠ Und die Prüfung musste dafür nicht einmal blockieren.** Der erste Entwurf von Brief
   und Ticket behauptete „sonst wird der Startcheck rot"; nachgemessen am HEAD von Sprint 10
   fehlt dort `befunde += 1`. Es genügte, dass **„unterminiert 0" berichtet wird** — in
   `PROJEKTSTATUS-UPDATE.md`, `sprint-aktuell.md` und `session-agenda.md`.
   **Eine Kennzahl steuert, sobald sie berichtet wird.** Die Zeile zählt ab jetzt.
3. **⚠ Eine ungeprüfte Behauptung über den eigenen Code, in dem Ticket, das eine ungeprüfte
   Zahl aufarbeitet.** Gefunden nur, weil derselbe Lauf die Stelle anfassen musste.
   Korrigiert an allen drei Orten, der Originalsatz steht im Brief daneben.
   Erkennungsfrage in `L-2026-08-17w`: *habe ich in den Code gesehen, oder aus dem Namen
   geschlossen?*
4. **Die Schätzung des Auftraggebers war genauer als jede eigene Zahl.** Er schrieb „über
   240 Durchläufe". Gemessen über alle 14 offenen Nicht-DR-Tickets, Abstand zwischen
   geplantem Sprint und Sprint der Frist bei 24 Sprints/Tag: **+168 bis +408, Median +240.**
   **Alle 14 auf grün** — die vier unbemerkten Verschiebungen von `pm/T-0039` (Befund aus
   Sprint 10) liefen die ganze Zeit unter einer grünen Frist.
5. **✅ `pm/T-0059` als erste Sacharbeit erledigt, wie Sprint 10 zugesagt hatte** —
   **SWR-126**, der Brief ist ein Verlauf. Die Zerlegungsregel ist **am Bestand gemessen**:
   41 Briefe, **52** `## Antwort`-Überschriften (alle mit ISO-Datum) und **11** weitere
   `##`-Überschriften, die Abschnitte *innerhalb* einer Antwort sind. Ein naives „jede `##`
   ist ein Beitrag" hätte **11 Briefe falsch zerlegt**.
6. **52 > 41 ist selbst ein Befund:** Briefe mit **mehreren** Teambeiträgen existieren
   längst, von Hand angelegt (`pm/N-0015`). **Der Wunsch des Auftraggebers beschrieb keine
   neue Idee, sondern eine bestehende Praxis ohne Werkzeug.**
7. **⚠ `pm/T-0028` nach vier Verschiebungen zerlegt statt ein fünftes Mal geschoben.**
   Gemessen: `geplant_sprint` 7→8→9→10→11 — **derselbe Zählerstand, an dem Sprint 10 bei
   `pm/T-0039` die Zerlegungsregel abgeleitet hat**, während `pm/T-0028` in *derselben
   Plantabelle desselben Laufs* mit dem Vermerk „Rest = Umfang (3 Flächen)" ein viertes Mal
   verschoben wurde. **Umfang ist nach D006 der Zerlegungsgrund selbst.** Erster Teil
   gebaut: **SWR-127** (`pm/T-0062`), 15 Tests.
8. **⚠ Dieselbe Nichtanwendung an zwei weiteren Stellen desselben Vorlaufs.** Die Klammer
   `pm/T-0039` blieb auf Sprint 11, während ihr letzter Teil auf 12 liegt — gegen die Regel,
   die Sprint 10 *„wer zerlegt, zieht die Klammer nach"* selbst formuliert hat.
   `projects/p12/T-0003` trug wörtlich den Vermerk *„beim Anfassen zerlegen, nicht
   schieben"* und wurde angefasst und geschoben. Beide korrigiert, `p12/T-0003` zerlegt.
   **Eine Regel, die im selben Lauf am Nachbarfall nicht angewandt wird, ist noch keine
   Praxis** (`L-2026-08-17x`).
9. **⚠⚠ Der schwerste Planbefund: B025 ist für die HMI kein Grund, sondern ein
   Ausschluss.** Fünf offene Aufgaben liegen auf der HMI-Fläche (`pm/T-0052`, `T-0054`,
   `T-0058`, `T-0060`, Rest von `T-0028`). Die Arbeit jedes Laufs entsteht aus den Briefen
   des Auftraggebers, und die treffen zuerst das Backend. **Solange jeder Lauf Backend baut,
   bekommt die HMI nie einen Lauf.** Aufgelöst nicht durch einen sechsten Satz, sondern
   durch einen Beschluss (Klasse B): **Sprint 12 ist ein HMI-Sprint.**
10. **⚠ Fünf Alttests fielen — und alle fünf hatten recht.** Zwei durch SWR-125, drei in
    `test_org_cockpit`/`test_org_kopfblock`. Der lehrreichste:
    `test_decision_request_ist_kein_treffer` nannte im Docstring `frist` + `default` als
    Steuerung und legte den DR **ohne frist** an — er belegte eine **Nachsicht** und nannte
    sie eine **Steuerung**. **In allen fünf Fällen wurde die Provokation ersetzt, nie die
    Erwartung.** Dritter bis siebter Fall dieser Sorte in zwei Sprints.
11. **Ein Nebenbefund an der alten Regel:** sie nahm **jeden** `decision-request` aus, auch
    einen ganz ohne Termin. Im Bestand tragen **3 von 46** DRs keine `frist` — die Prüfung
    konnte sie nicht sehen. Die neue Regel meldet sie.
12. **`kalenderfristen` steht nicht nur im Preflight, sondern auch im Cockpit-Kopfblock.**
    Der Auftraggeber sieht ins Cockpit, nicht in den Startcheck; eine Prüfung, deren
    Ergebnis nur dort erscheint, wo der Betroffene nicht hinsieht, ist die halbe
    Wiederholung von SWR-122. Dritter Schlüssel — Vertrags**erweiterung**, keine Änderung.
13. **Drei Sachtickets geschlossen** (`platform/T-0012`, `pm/T-0059`, `pm/T-0062`), alle
    über den legalen Weg mit je drei Commits, plus sechs Takt-Pflichten. **Sechs neue
    Tickets**: `pm/T-0061` (Nebenbefund), `pm/T-0062`/`T-0063` und `p12/T-0004`–`T-0006`
    (Zerlegungen).
14. **⚠ `pm/T-0061` ist der ehrliche Rest:** `board.sprint_widerspruch` (SWR-106) hält
    `frist` gegen `geplant_sprint` und war der **Preis** für die Doppelführung beider
    Felder. Seine Begründung beruft sich wörtlich auf den Auftraggeber — der sie mit
    `pm/N-0041` **am selben Tag** widerrufen hat. Nach der Migration: **0 offene Tickets mit
    beiden Feldern**, die Prüfung hat keinen möglichen Fall mehr. Nicht gelöscht (das wäre
    eine zweite Änderung derselben Fläche, B025), sondern terminiert.
15. **741 Tests grün** (+52), Matrix **127 SWRs / 0 Lücken**, Preflight **STARTKLAR** — nach
    allen Änderungen des Laufs gemessen. unterminiert 0, **Kalenderfristen 0**, Plan-Drift 0,
    überfällig 0, Statusdrift 0, Statusübergänge seit Stichtag 0, Altbestand 52
    (unverändert). **Ein Brief eingegangen und beantwortet, keiner offen.**
16. **⚠ Zwei weitere Briefe kamen **während** des Laufs herein und wurden noch in ihm
    beantwortet** (`promt-team/N-0001`, `team-dashboard/N-0002`). Der Startcheck am
    Laufbeginn kannte sie nicht — sie trafen um 08:39 und 08:43 ein und wurden erst vom
    **Abschluss**-Preflight gemeldet. **Ein Briefkasten-Stand vom Laufbeginn ist am
    Laufende keine Aussage mehr.** Beide sind beantwortet, keiner offen.
17. **⚠ Und der erste dieser Briefe traf denselben Befund ein zweites Mal.** Der
    Auftraggeber fragt, welche KI-Rollen über Ollama statt Claude laufen können. **Die
    Zuordnung existiert seit Sprint 3** — 9 Aufgaben-Typen in `process/roles/registry.yaml`
    tragen `chain: [ollama, …]` mit dem Kommentar *„ollama ab Sprint 6"*. Gemessen:
    `run-registry.jsonl` enthält **7 Läufe insgesamt**, davon **1** auf Ollama; Telemetrie
    und Goldset je Rolle existieren nicht. **Dritter Fall desselben Musters in einem Lauf:
    beschlossen, nicht geprüft, wirkungslos.** Keine Empfehlung gegeben — Kap. 14 bindet
    Routing-Änderungen an Daten, und die Rollenbeschreibung des Auftraggebers sagt selbst
    *„ohne Baseline kein Optimierungslauf"*. Als Soll/Ist-Prüfung in `promt-team/T-0001`
    aufgenommen.
18. **⚠ Der Abschluss-Testlauf hat einen Vertrag nachgefordert, den dieser Lauf vergessen
    hatte.** `test_vertrag_feldliste` meldete zwei Payload-Schlüssel
    (`kalenderfristen_gesamt`/`_refs`), die der Widget-Vertrag nicht kannte. **Zweimal in
    Folge derselbe Ablauf** — der Vermerk in v2.3 lautet wörtlich „das ist nicht der
    Sorgfalt zu verdanken". **Wer Code ändert, sieht den Vertrag nicht: er liegt in einem
    anderen Repo.** Vertrag auf **v2.4**, Lesson `L-2026-08-17y`. Die Prüfung ist damit die
    **Lösung** und nicht der Notausgang — sie ist die einzige Stelle, die die beiden Repos
    zusammenhält, und darf nicht als Redundanz gelesen werden.

---

## Sprint 11 (2026-08-17) im Detail

### ⚠⚠ Eine Regel, die fünf Sprints lang von einer Prüfung überstimmt wurde

| | |
|---|---|
| Beschluss | SWR-106, Anforderungen **v1.12**: „Terminierung auf Sprints statt auf Kalenderdaten" |
| zweiter Ort desselben Satzes | Modulkopf `platform/scripts/sprint_register.py` |
| Prüfung, die das Gegenteil belohnt | `aggregation.unterminierte_tickets` — meldet Tickets **ohne `frist`** |
| bei der Entscheidung angefasst? | **nein** |
| Zustand fünf Sprints später | **14 von 14** offenen Teamaufgaben mit Kalenderdatum |
| erste Rüge | Brief, der zu SWR-106 führte |
| zweite Rüge | `pm/N-0041`, 2026-08-17 07:41 |

Der Mechanismus ist banal und deshalb gefährlich: Der Startcheck fragt *„welche Tickets
haben keinen Termin?"* und liest „Termin" als **Datum**. Jeder Lauf sah „Ticket ohne
Frist", trug eine Frist ein und hielt die berichtete Null.

> **Eine Entscheidung, die keine Prüfung mitgeändert hat, ist eine Absichtserklärung.**

Spiegelbild zu **SWR-122** aus Sprint 10 — dort wurde eine Prüfung berechnet und von
niemandem **gelesen**, hier eine Regel beschlossen und von keiner Prüfung **vertreten**.

### ⚠ Der Fehler im eigenen Entwurf, und warum er den Befund verschärft

Behauptet: *„sonst wird der Startcheck rot."* Gemessen am HEAD von Sprint 10: die Zeile wird
**gedruckt** (`print`), `befunde += 1` fehlt. Der Check blieb grün.

Damit fällt die einfache Erklärung („ein Gate hat uns gezwungen") weg. Übrig bleibt die
schwierigere: **es hat gereicht, dass die Zahl im Bericht an den Auftraggeber steht.**

> **Eine Kennzahl steuert, sobald sie berichtet wird — auch wenn sie nichts blockiert.**

Die Frage „blockiert sie?" ist damit die falsche Frage an eine neue Kennzahl. Die richtige:
*wer liest sie, und was tut er, damit sie gut aussieht?*

### Was SWR-125 tut

1. **Umgedreht, nicht ergänzt** (B033 — sonst zwei Terminbegriffe): terminiert heißt
   `geplant_sprint`. Ein Ticket **nur mit `frist`** ist unterminiert.
2. **Neuer Befund `kalenderfristen`** — die Rückkehr wird **gemeldet**, nicht bloß nicht
   mehr gefordert. Genau dieses Nichtmelden ist die Ursache des Befundes.
3. **Das Datum bleibt, wo ein Mensch wartet** (`decision-request`): seine Antwortzeit läuft
   in Tagen. Dieselbe Grenze zog `sprint_vergangen` (SWR-112) schon in der Gegenrichtung —
   jetzt an **beiden** Enden gleich. **Ein DR ohne `frist` ist ab jetzt unterminiert**
   (3 von 46 im Bestand).
4. **Die Abgrenzung steht genau einmal** (`_ist_unterminiert`) und wird von Kachelzahl
   (SWR-091) **und** Org-Summe (SWR-114/117) gelesen. Zwei Stellen mit derselben Regel waren
   der Grund, dass SWR-106 wirkungslos blieb.

### ✅ SWR-126 — und was die Messung über die eigene Praxis verraten hat

| Messung am Briefbestand (2026-08-17) | |
|---|---|
| Briefe | **41** |
| `## Antwort…`-Überschriften | **52** — alle mit ISO-Datum |
| davon Briefe mit **mehr als einer** Team-Antwort | mehrere, **von Hand** (`pm/N-0015` „## Vollzug") |
| andere `##`-Überschriften (Abschnitte *in* einer Antwort) | **11** |
| davon mit ISO-Datum in Klammern | **1** — und die **ist** ein Beitrag |

Daraus die Regel: Beitragskopf ist, was mit `Antwort` beginnt **oder** eine Klammer mit
ISO-Datum trägt. Ein naives „jede `##` ist ein Beitrag" hätte **11 Briefe falsch zerlegt**;
die Gegenprobe über alle 41 echten Briefe wird gegen das naive Verfahren rot.

⚠ **`52 > 41` ist der eigentliche Nebenbefund:** die Praxis „im selben Brief weiterreden"
gab es längst — ihr fehlte nur das Werkzeug. Ein CR, der eine **bestehende** Praxis
beschreibt, ist etwas anderes als eine neue Idee, und viermal verschoben wurde er trotzdem.

**`spalte_antwort` ist ab jetzt eine Sicht auf `beitraege`**, kein zweiter Parser (B033) —
B054 ist der Beleg, was zwei Leser derselben Datei kosten: dort blieb bei zehn von dreißig
Briefen die Antwort unsichtbar.

**Die Statusrücksetzung ist der Punkt, an dem der CR kippt.** `offene()` trägt die
Preflight-Zeile und die Cockpit-Kachel; ein Beitrag an einem `beantwortet`-en Brief wäre von
**keiner** Session gesehen worden. Sie ist **unbedingt** und nicht an einer Absenderprüfung
aufgehängt: `COMMIT_IDENTITAET` legt diesen Pfad auf den Menschen fest, ein Absenderfeld
ließe sich fälschen.

### ⚠ Drei Nichtanwendungen einer Regel aus dem Vorlauf, in einem Lauf gefunden

| Fall | Regel aus Sprint 10 | was Sprint 10 tat |
|---|---|---|
| `pm/T-0028` | „viermal um eins verschoben → zerlegen" | vierte Verschiebung, Grund „Umfang" |
| `pm/T-0039` (Klammer) | „Klammer auf den Termin des letzten Teils nachziehen" | auf 11 gelassen, letzter Teil auf 12 |
| `projects/p12/T-0003` | *„beim Anfassen zerlegen, nicht schieben"* (im Ticket) | angefasst und geschoben |

**Fünfter Sprint in Folge, in dem die Verifikation einen Fehler des Vorlaufs findet.** Der
Fehler ist damit keine Nachlässigkeit einer Session, sondern eine Eigenschaft des
Arbeitsschritts „Regel aufschreiben und weiterarbeiten". Erkennungsfrage aus
`L-2026-08-17x`: *auf welche anderen offenen Fälle trifft dieser Satz gerade zu?*

### ⚠⚠ B025 als Ausschluss — der Planbefund und sein Beschluss

| | |
|---|---|
| offene Aufgaben auf der HMI-Fläche | **5** (`pm/T-0052`, `T-0054`, `T-0058`, `T-0060`, Rest `T-0028`) |
| Verschiebungsgrund bei allen | B025 („nicht zwei Bauflächen in einem Lauf") |
| Herkunft der Arbeit jedes Laufs | Briefe des Auftraggebers |
| Fläche, die diese Briefe zuerst treffen | **Backend** (Ursache, Reparatur) |
| Folge | die HMI ist strukturell immer „die zweite Fläche" |

**Ein Grund, dessen Bedingung durch die eigene Arbeitsweise nie eintritt, ist kein Grund,
sondern ein Ausschluss.** Beschluss (Klasse B, PM — Playbook Kap. 16 „Priorisierung"):
**Sprint 12 ist ein HMI-Sprint**, die Backend-Flächen bleiben unberührt, sofern kein Brief
sie erzwingt.

### Verifikation (nach allen Änderungen gemessen)

| | |
|---|---|
| Preflight | **STARTKLAR** |
| Tests | **741 grün** (+52) |
| Matrix | **127 SWRs / 0 Lücken** |
| unterminiert | **0** |
| **Kalenderfristen an Teamaufgaben** | **0** (vorher 14) |
| Plan-Drift / überfällig / Statusdrift | **0 / 0 / 0** |
| Statusübergänge seit Stichtag | **0** (Altbestand 52, unverändert) |
| Briefkasten | 1 eingegangen, 1 beantwortet, **0 offen** |

---

## Das Wichtigste (Stand Sprint 10, 2026-08-17)

1. **⚠⚠ `PREFLIGHT: STARTKLAR` über sechs Befunden.** Der Startcheck meldete grün, während
   `plan_drift` (SWR-109) **3** und `sprint_vergangen` (SWR-112) **3** ergaben. Beide
   Kennzahlen werden von `sprint.plan()` berechnet, in den Payload gelegt — und von
   **niemandem gelesen**. Sie standen **einen Schlüssel neben** `status_drift`, das der
   Preflight liest. Gebaut: **SWR-122** (`platform/T-0011`), 13 Tests.
2. **⚠ Die Begründung, die SWR-115 in den Preflight gebracht hat, gilt für beide Nachbarn
   wörtlich** — *„sichtbar vor dem Push und vor dem Bericht an den Auftraggeber, statt
   einen Sprint später"* — und wurde bei beiden nicht angewandt. `plan_drift` war vier
   Sprints lang wirkungslos vorhanden, `sprint_vergangen` drei.
3. **⚠⚠ Der Abschlussbericht von Sprint 9 hat deshalb an drei Stellen eine falsche Zahl
   gemeldet.** „unterminiert 0, überfällig 0, **Plan-Drift 0**, Statusdrift 0" stand in
   `PROJEKTSTATUS-UPDATE.md`, `sprint-aktuell.md` **und** `session-agenda.md`. Gemessen am
   Bestand, den derselbe Lauf committet hat: **3** und **1**.
4. **⚠ Wie die Null falsch wurde, ist der eigentliche Befund.** Sie war richtig, **als sie
   gemessen wurde**. Danach hat derselbe Lauf die Plantabelle umgeschrieben (`pm/T-0028`
   und `pm/T-0039` von „Sprint 9" auf „Sprint 10"), ohne die Ticketfelder nachzuziehen —
   und damit den Drift **erzeugt**, den die Zahl daneben bestritt.
   **Eine Messung, die vor der Änderung liegt, die sie abdecken soll, ist keine Messung
   des Ergebnisses, sondern des Ausgangszustands.** Schwesterbefund zu SWR-118 aus
   Sprint 9: dort hing das Ergebnis an der Reihenfolge der Session, hier die Gültigkeit
   einer berichteten Zahl.
5. **⚠ `pm/T-0039` ist viermal um genau eins verschoben worden** — `geplant_sprint`
   6→7→8→9, **kein einziges Mal mit einem neuen Grund**; der Abschnitt „Warum nicht in
   dieser Session gebaut" steht wörtlich seit der Erstanlage.
6. **⚠ Aufgefallen ist es beim fünften Mal — und nur, weil es diesmal *schlampiger*
   gemacht wurde.** Statt das Feld zu erhöhen, wurde nur die Plantabelle geändert, und
   genau das erzeugte den `plan_drift`. **Ein sauber ausgeführter Verzug wäre unsichtbar
   geblieben.**
7. **⚠ Fünfter Sprint in Folge, in dem ein Verschiebungsgrund an der Messung scheitert.**
   `pm/T-0028`: die Feldliste ist **Klasse C** (Team darf entscheiden), es gab **keinen**
   DR dazu, und die Felder stehen **bereits in der eigenen DoD**. Entschieden und
   ausgeschrieben — der nächste Lauf baut statt zu überlegen.
8. **✅ `pm/T-0055` Teil 2 gebaut (SWR-123)** — der Bug des Auftraggebers ist zu Ende
   repariert: die verwaiste `index.lock` wird über den **vorhandenen** Mechanismus
   (`preflight.finde_lock_artefakte`/`entferne_artefakte`) geräumt und der Commit **einmal**
   wiederholt. Kein zweiter Räumweg (B033), keine Schleife. 8 Tests.
9. **⚠⚠ Der Bau hat drei Tests aus Sprint 9 umgeworfen — und sie hatten recht.** Sie
   erzeugten ihren Fehlerfall über genau die Sperre, die SWR-123 wegräumt.
   **Ein Test, der seinen Fehlerfall über einen Mechanismus erzeugt, den das System später
   repariert, prüft ab diesem Tag nicht mehr, was in seinem Namen steht.** Er wurde hier
   rot, weil die Erwartung „wirft einen Fehler" lautete — **bei einer anderen Erwartung
   wäre er still grün geworden.**
10. **⚠ `pm/T-0057`: zwei von drei genannten Ursachen halten der Messung nicht stand.**
    Die Beschreibung **wird** geprüft (`_text_bereinigen`, `|`-Ablehnung, `FELD_MAX`), und
    die Zeilenumbrüche gingen nicht „beim Einfügen" verloren, sondern werden
    **absichtlich** zusammengezogen — eingebaut auf Brief `pm/N-0023`, der genau darum bat.
    Gefehlt hat weder Prüfung noch Grenze, sondern ein **Zielort**. Gebaut: **SWR-124**.
11. **⚠ `FELD_MAX` wurde in drei Tickets angehoben — 200 → 4.000 → 200.000.** Zweimal
    lautete die Frage „welche Zahl ist richtig?", und beide Male war die richtige Antwort
    **keine Zahl, sondern ein anderer Ort für den Text.** `ZELLE_MAX = 400` ist gemessen
    (längste Bestandszellen: 229 und 153; Auslösefall: 9.000).
12. **⚠ Und dabei fielen zwei weitere Alttests, die denselben Fehler machten** — sie
    prüften den **Aufbewahrungsort** statt der Zusage „wird angenommen und nicht gekürzt".
    **Zweimal in einem Lauf stand in einem Test etwas anderes als in seinem Namen.** Beide
    Male wurde die Provokation bzw. die Prüfgröße ersetzt, **nie die Erwartung**.
13. **✅ `pm/T-0053` beantwortet, ohne eine Zeile Code.** Die 21× `open -> in_review`
    zerfallen nach Datum in **drei Ereignisse**: 7 vor Existenz der Prüfung (p0, ein
    Commit), 13 aus **einer** Sitzung binnen 56 Minuten (p1), 1 Einzelfall neun Tage
    später. In `pm`, `platform`, `p2`–`p9`, `projects`, `team-dashboard`: **kein einziger**.
    **Eine Zahl von Befunden zählt Artefakte, keine Entscheidungen.** `UEBERGAENGE` bleibt.
14. **⚠ Eine Regel aus der Zerlegung:** `p11/T-0003` wurde als überfällig gemeldet, obwohl
    es seit Sprint 9 nur noch eine **Klammer** über drei Teiltickets ist — es trug die
    Nummer aus der Zeit **vor** der Zerlegung. **Wer zerlegt, zieht die Klammer auf den
    Termin des letzten Teils nach.**
15. **⚠ Eine ID-Kollision vermieden, die die bestehende Regel nicht abdeckte.** Die
    Lessons-Kennung `L-2026-08-17r` war bereits in `process/knowledge/cm/lessons.md`
    vergeben; die Buchstabenreihe läuft über **zwei** Dateien. Die Kollisionsregel vom
    2026-08-16 war für **Ticket**-IDs geschrieben — derselbe Fehler steht bei jeder
    Kennung, die an mehr als einer Stelle vergeben wird.
16. **Vier Sachtickets geschlossen** (`platform/T-0011`, `pm/T-0053`, `pm/T-0055`,
    `pm/T-0057`), alle über den legalen Weg mit je drei Commits, plus sechs
    Takt-Pflichten. **Drei neue Tickets** aus Zerlegungen (`pm/T-0058`, `pm/T-0059`,
    `pm/T-0060`), eines aus dem Startcheck (`platform/T-0011`).
17. **✅⚠ Und die neue Prüfung hat im selben Lauf ihren Erbauer erwischt.** Beim
    Abschluss-Preflight meldete sie **fünf** Plan-Drifts — wörtlich derselbe Fehler, den
    dieser Sprint an Sprint 9 gefunden hat, begangen von dem Lauf, der ihn erhoben hat.
    **Vierter Sprint in Folge, in dem eine Verifikation einen Fehler des eigenen Laufs
    findet.** Der Fehler ist damit keine Nachlässigkeit einer Session, sondern eine
    Eigenschaft des Arbeitsschritts „Plantabelle fortschreiben".
18. **689 Tests grün** (+30), Matrix **124 SWRs / 0 Lücken**, Preflight **STARTKLAR** —
    und diesmal **nach** allen Änderungen des Laufs gemessen, nicht davor. Plan-Drift 0,
    überfällig 0, Statusdrift 0, unterminiert 0, Statusübergänge seit Stichtag 0,
    Altbestand 52 (unverändert). **Kein Brief eingegangen, kein Brief offen, die Inbox ist
    leer.**

---

## Sprint 10 (2026-08-17) im Detail

### ⚠⚠ Zwei Kennzahlen, die berechnet und nie gelesen wurden

| Prüfung | Seit | Im Preflight? | Folge |
|---|---|---|---|
| `nicht_geplant` (SWR-106) | Sprint 4 | nein | — |
| `plan_drift` (SWR-109) | Sprint 6 | **nein → ab jetzt ja** | Sprint 9 meldete „0" bei 3 |
| `sprint_vergangen` (SWR-112) | Sprint 7 | **nein → ab jetzt ja** | `pm/T-0039` 4× unbemerkt verschoben |
| `status_drift` (SWR-115) | Sprint 8 | ja | greift seit Sprint 9 |

**SWR-122** legt beide in dieselbe Meldezeile wie `status_drift`, aus **einem** Aufruf von
`sprint.plan()` je Lauf (`sprintsicht` mit Cache). Drei Aufrufe zu drei Zeitpunkten könnten
drei verschiedene Antworten geben, und niemand würde es merken — die Bauart aus B033.
Beide Zeilen erscheinen **auch bei 0** (SWR-114-Begründung), nennen **Referenzen** statt
einer nackten Zahl (B038), und **zählen als Befund**: eine Zeile, die nichts blockiert,
hätte den Bericht von Sprint 9 nicht verhindert.

### ⚠ Der Verschiebungsgrund, fünfter Sprint in Folge

| Sprint | Ticket | Warum der Grund leer war |
|---|---|---|
| 6 | `platform/T-0008` | Der Grund ließ sich prüfen, ohne die Arbeit zu tun. |
| 7 | `pm/T-0036` | Der Grund galt nicht mehr. |
| 8 | `pm/T-0038` | Der Grund zeigte auf ein Ticket, **das es nicht mehr gab**. |
| 9 | `pm/T-0047` | Der Grund war die erste Aufgabe des Tickets selbst. |
| **10** | **`pm/T-0028`** | **Der Grund nannte ein Risiko, das die eigene DoD bereits ausräumt.** |

`pm/T-0028` schob „Risiko einer Fehlannahme ohne Rückfrage" vor. Gemessen: die Feldliste
eines Formulars ist **Klasse C** (Klasse A ist die *Gründung*, und die bereitet der Knopf
laut Ticket nur vor); es gibt **keinen DR** dazu; die Felder **stehen bereits** im
Abschnitt „Umfang für die Umsetzung" desselben Tickets; und der Fall ist seit Sprint 9
einmal von Hand durchgespielt (`promt-team`).

### ⚠ SWR-123 — die Ursache statt der Meldung

Sprint 9 hat die **Meldung** geradegezogen (SWR-121: „Deine Nachricht ist GESPEICHERT …").
Sprint 10 nimmt den **Anlass** weg. Der gemessene Ablauf: `git add` hinterlässt auf diesem
Mount eine `index.lock`, die es nicht löschen kann, und der **nachfolgende** `commit`
scheitert an ihr — der Fehler entsteht **zwischen den beiden Schritten, die der
Schreibpfad selbst macht**, und wird genau dort behandelt.

**Genau einmal wiederholt, nicht in einer Schleife**: ein echter Dauerfehler gehört
gemeldet, nicht abgewartet und dann trotzdem gemeldet. Räumt der Mechanismus nichts weg
oder fällt er aus, kommt die Meldung aus SWR-121 **unverändert** — eine scheiternde
Reparatur darf nie schlimmer sein als keine.

### ⚠ SWR-124 — der Befund stimmte, seine Erklärung nicht

Das auslösende Ticket nannte drei Ursachen; zwei fallen bei der Messung. Die Begründung,
die bei `FELD_MAX` niedergeschrieben steht — *„einzig `|` ist das Zeichen, das wirklich
etwas sprengt"* — stimmt fürs **Zerbrechen** und schweigt zur **Lesbarkeit**. Eine Zelle
mit 9.000 Zeichen zerbricht nichts und ist von niemandem zu lesen.

Ausgelagert wird **nach** der Bereinigung: sonst entschiede die Länge *vor* dem
Zusammenziehen der Umbrüche, und zwei Texte mit gleichem Inhalt landeten verschieden.
Volltext und Zeile gehen in **denselben** Commit; die Rücknahme nimmt beide mit.


### ✅⚠ Die neue Prüfung hat ihren eigenen Erbauer erwischt — vierter Sprint in Folge

Beim Abschluss-Preflight, **nach** dem Fortschreiben des Sprintplans, meldete die eine
Stunde zuvor gebaute Zeile:

```
[org] BEFUND: 5 Planzeile(n) nennen eine andere Sprintnummer als ihr Ticket:
    pm/T-0028, pm/T-0054, pm/T-0052, p11/T-0008, promt-team/T-0001
```

**Das ist wörtlich der Fehler, den dieser Sprint an Sprint 9 gefunden hat** — die
Plantabelle auf „Sprint 11" gesetzt, die Ticketfelder auf 10 stehen gelassen. Fünfmal, in
demselben Lauf, der den Befund erhoben hat.

Zwei Dinge stehen damit fest, und beide sind wichtiger als der Fehler selbst:

1. **Der Fehler ist keine Nachlässigkeit einer einzelnen Session, sondern eine Eigenschaft
   des Arbeitsschritts.** Wer eine Plantabelle mit 25 Zeilen fortschreibt, ändert Termine
   an einer Stelle und muss sie an einer zweiten nachziehen; das geht schief, und zwar
   zuverlässig. Sprint 9 war darin nicht schlechter als Sprint 10.
2. **Die Prüfung sitzt an der richtigen Stelle.** Sie hat den Fehler **vor** dem Bericht
   gefunden, nicht einen Sprint später. Genau das war ihre Begründung.

Damit ist es der **vierte Sprint in Folge**, in dem eine Verifikation einen Fehler des
Laufs findet, der sie gebaut hat (Sprint 7: SWR-109 nie committet; 8: `platform/T-0010`
offen; 9: SWR-118 über leerer Wurzel; 10: fünf Plan-Drifts im eigenen Abschluss).

### Verifikation

689 Tests grün (+30), Matrix 124 SWRs / 0 Lücken (+ Produktmatrix datakonv 18/0),
Preflight **STARTKLAR** — gemessen **nach** allen Änderungen dieses Laufs.

### Widerlegbare Vorhersage für Sprint 11

Der Startcheck meldet `Plan-Drift 0` und `Offen auf vergangenem Sprint 0` — **nicht weil
jemand daran denkt, sondern weil der Preflight es prüft**. Und `pm/T-0059` ist die erste
Sacharbeit; wird es ein sechstes Mal verschoben, ist der Grund aus Sprint 10
fortgeschrieben worden, obwohl er ausdrücklich mit diesem Lauf verfällt.

---

## Rückblick: Das Wichtigste aus Sprint 9

1. **✅ Die Zusage aus Sprint 8 hat gehalten.** Der Startcheck meldete
   `[org] Statusdrift Plan/Ticket: 0`, und **kein** in Sprint 8 als erledigt gemeldetes
   Ticket stand noch offen. Zum ersten Mal seit fünf Läufen fand der Startcheck **nichts**.
2. **⚠ Der wertvollste Inhalt kam deshalb aus einer anderen Quelle: dem Messen zweier
   Aussagen, die in den eigenen Tickets standen. Beide hielten der Messung nicht stand.**
3. **⚠ `pm/T-0047` — der erste Verschiebungsgrund, der *zirkulär* war.** Zweimal
   verschoben mit „Vertragsfrage vor Bau". Punkt 1 der Definition of Done desselben
   Tickets lautet: *„Entscheidung ausschreiben."* Das Ticket wurde verschoben, weil seine
   **erste Aufgabe** noch nicht erledigt war — ein Grund, der genau die Arbeit verschiebt,
   die ihn auflösen würde.
4. **⚠ Drei weitere Messungen an demselben Grund, alle negativ.** Klasse **C** nach
   Playbook Kap. 16 (das Team darf entscheiden); **kein** DR im Bestand — die Frage wurde
   nie vorgelegt; der B025-Nachbar (`aggregation.cockpit`, SWR-111) liegt seit **Sprint 7**
   zurück und wurde unverändert mitgeschleppt; und der in Sprint 8 ergänzte „neue Nachbar"
   `pm/T-0051` **wartet laut eigener DoD auf dieses Ticket** — die Abhängigkeit zeigte in
   die falsche Richtung.
5. **⚠ Und die Vertragsfrage selbst war falsch gestellt.** „Kopfblock **oder** Feld?"
   unterstellte, ein Kopfblock ändere die Antwort für **jeden** Leser. Gemessen liest jeder
   Leser `payload["projekte"]`; ein Schlüssel **daneben** ändert für keinen etwas. Die Frage
   zerfiel bei der ersten Messung in eine Erweiterung (keine Abstimmung nötig) und eine
   Änderung, die **niemand gewählt hätte**. Gebaut: **SWR-117**.
6. **⚠⚠ `pm/T-0048` sagte an drei Stellen „die **beiden** Altfälle". Es sind **52**.**
   Der erste Lauf der gebauten Historienprüfung (**SWR-118**) fand 52 unzulässige
   Statusübergänge in **acht** Repos: 28 × `open -> done`, 21 × `open -> in_review`,
   2 × `done -> open`, 1 × `in_progress -> done`. Die beiden genannten sind zwei der 28.
7. **⚠ Sie fielen nicht auf, weil sie schlimmer waren, sondern weil in Sprint 7 zufällig
   jemand hinsah** (SWR-110 war frisch gebaut). **Die Fehlerart ist kein Unfall aus
   Sprint 7, sondern der Normalfall seit dem ersten Sprint.** Eine Zahl, die niemand
   erhoben hatte, stand zwei Sprints lang in einem Ticket und lag um den **Faktor 25**
   daneben.
8. **⚠ Auch „teuer" war ungemessen.** Dasselbe Ticket verwarf den Weg über die Historie
   als teuer. Gemessen: **10 s** gegen einen Preflight, der ohne Tests **60 s** braucht.
   Die Kostenfrage war real — ihre Antwort lag in einer Minute vor und trug die
   **entgegengesetzte** Entscheidung.
9. **⚠ B066 — ein Vertrag, gegen den nichts geprüft wurde, verlor still ein Feld.**
   `widget-vertrag-v2.yaml` sagt von sich: DIE EINZIGE STELLE, DIE DIE FELDLISTE FÜHRT.
   Seit v2.1 fehlte darin `team`: beim Einschieben von `letzte_baseline_text` ging
   `- name: team` verloren, und YAML verschmolz beide **stillschweigend** zu einem Eintrag.
   **Die Datei parste zwei Sprints lang fehlerfrei** — die einzige Prüfung, die es gab,
   war Lesbarkeit.
10. **✅ Der neue Wächter hat im selben Lauf seinen Erbauer erwischt** — er meldete zwei
    Payload-Schlüssel, die eine Stunde zuvor selbst hinzugefügt worden waren.
11. **✅ Und `test_preflight` (aus Sprint 1) fand einen Fehler in SWR-118**: über einer
    leeren Wurzel „Altbestand hat 0, erwartet sind 52" — ein Fehlalarm aus einem
    Kategorienfehler. **Dritter Sprint in Folge, in dem eine Verifikation einen Fehler des
    Laufs findet, der sie gebaut hat.**
12. **Vier Sachtickets geschlossen** (`pm/T-0047`, `pm/T-0048`, `pm/T-0050`, `pm/T-0051`),
    alle über den legalen Weg mit je drei Commits, plus sechs Takt-Pflichten. **Zwei neue
    Tickets** aus Befunden (`pm/T-0053`) und aus dem Briefkasten (`pm/T-0054`).
13. **✅ Der DR `p11/T-0006` ist während des Laufs entschieden worden — LAY-a, 08:11,
    zwei Tage vor der Frist.** Verbucht als `D002`, Folgearbeit **im selben Lauf**:
    `p11/T-0003` von `blocked` auf `open`, nach D006 **zerlegt** statt verschoben
    (`T-0007`/`T-0008`/`T-0009`), und Teil a) gebaut — **`ADR-P11-002`**: die
    Korridor-Ausnahme sitzt an der **Ansicht**, nicht am Korridor. LAY-a legt die Fläche
    fest, nicht die Bauform; beide Bauformen sähen in der ersten Woche gleich aus.
    **Die Frist-Kette aus Sprint 8 ist gehalten** — die Inbox ist leer.
14. **⚠ Zwei Briefe kamen während des Laufs; der zweite meldete einen Bug, in den diese
    Session selbst dutzendfach gelaufen ist.** `pm/N-0039`: der Briefkasten meldet
    „Git-Commit fehlgeschlagen" und **verschweigt, dass die Nachricht gespeichert ist** —
    sie wird geschrieben, **bevor** Git startet. Am Bestand belegt: `pm/N-0038` hat **nie**
    einen eigenen Commit bekommen und wurde zwei Stunden später von einem fremden
    mitgenommen; bis dahin lag er unverbucht — der Zustand, den SWR-110 zum Befund erklärt.
    Ursache: eine verwaiste `index.lock`, die `git add` auf diesem Mount hinterlässt.
    **Teil 1 sofort behoben (SWR-121):** die Meldung nennt zuerst „GESPEICHERT" und „nicht
    erneut senden", ohne den technischen Grund zu unterschlagen — *eine Meldung, die den
    Ausgang schlechter darstellt, als er ist, kostet dasselbe wie eine beschönigende.*
15. **⚠ Ein dritter Brief berührte Klasse A — und wurde im selben Lauf entschieden und
    ausgeführt.** `pm/N-0040` („starte promt-team"): Team-Gründung entscheidet nach
    Playbook Kap. 16 **immer der Mensch**. Als DR `pm/T-0056` mit TG-a/b/c vorgelegt
    (Frist 20.08., Default TG-a) — der Auftraggeber wählte **TG-a nach drei Minuten**
    (`pm/D009`, 08:47). Team gegründet: Datenklasse **`sensibel`** (`.kein-remote`), weil
    es **Transkripte** anderer Rollen liest und ein Transkript alles enthalten kann, was je
    durch eine Rolle lief — *die Einstufung folgt dem schlechtestmöglichen Inhalt der
    Eingabe, nicht dem erwarteten.* **Erstauftrag ist die Messgrundlage, nicht das
    Optimieren:** die Rollenbeschreibung verlangt selbst „ohne Baseline kein
    Optimierungslauf", und die Baseline gab es nicht — das Audit-Ticket steht deshalb auf
    `blocked_by: [T-0001, T-0002]`, im **Feld** und nicht nur im Text.
16. **⚠ Zwei Auftraggeber-Entscheidungen kamen während des Laufs** (LAY-a 08:11, TG-a
    08:47) und wurden beide **im selben Sprint** verbucht und weiterverarbeitet. Ein DR ist
    damit nicht mehr zwangsläufig eine Sache für den nächsten Lauf — das spricht dafür, DRs
    früh im Lauf zu stellen statt am Ende zu sammeln.
17. **659 Tests grün** (+58), Matrix **121 SWRs / 0 Lücken**, Preflight STARTKLAR,
    unterminiert 0, überfällig 0, Plan-Drift 0, Statusdrift 0, Statusübergänge seit
    Stichtag 0. **Ein Brief eingegangen und beantwortet** (`pm/N-0038`).

---

## Sprint 9 (2026-08-17) im Detail

### ⚠ `pm/T-0047` — ein Grund, der die eigene Aufgabenliste zitierte

Vier Sprints in Folge ist ein Verschiebungsgrund an der Messung gescheitert
(L-2026-08-17j Regel 2). Neu ist die **Bauart**:

| Sprint | Ticket | Warum der Grund leer war |
|---|---|---|
| 6 | `platform/T-0008` | Der Grund ließ sich prüfen, ohne die Arbeit zu tun. |
| 7 | `pm/T-0036` | Der Grund galt nicht mehr. |
| 8 | `pm/T-0038` | Der Grund zeigte auf ein Ticket, **das es nicht mehr gab**. |
| **9** | **`pm/T-0047`** | **Der Grund war die erste Aufgabe des Tickets selbst.** |

Verankert als **L-2026-08-17p** mit fünf Regeln — darunter die Erkennungsfrage („steht der
Grund als Aufgabe in der eigenen DoD?"), der Klassentest in einer Minute (Klasse A → DR,
sonst ist die Entscheidung Arbeit dieses Sprints), und: **gibt es keinen DR zu einer
angeblich vorzulegenden Frage, wurde sie nie vorgelegt.**

### SWR-117 — Schwesterschlüssel statt Umhüllung

`cockpit_alle` liefert `{"projekte": [...], "organisation": {...}}`. Der Block steht
**neben** `projekte` und formt es nicht um: jeder heutige Leser bleibt unverändert. Die
Zahl „unterminiert" kommt org-weit **mit Referenzen** aus **einer** Quelle, die sich
`preflight` und Cockpit teilen — `unterminierte_tickets` ist nach `aggregation` gewandert,
weil `backend` bereits `scripts.board` importiert und der umgekehrte Weg einen Zyklus
schlösse. Die Weiterleitung in `preflight` ist **keine zweite Quelle, sondern der Beleg,
dass es nur eine gibt**; ein Test hält beide Rückgaben gegeneinander.

### ⚠⚠ SWR-118 — die Historie statt des Zeitpunkts

`board.py --check` hielt die Arbeitskopie gegen HEAD und war damit blind für einen bereits
committeten Sprung: **das Ergebnis hing an der Reihenfolge der Session.** SWR-110
verschärfte das sogar, weil sie auf frühes Committen drängt.

Die neue Prüfung liest die Folge der `status:`-Werte in der Historie — ein Sachverhalt,
der sich nicht dadurch ändert, wann man ihn abfragt. **Sie hängt an gar keinem Zeitpunkt
mehr.**

**Der Altbestand ist ein Stichtag, keine Liste.** 52 handgepflegte Einträge wären ein
Register, das niemand liest, und die 53. Zeile sähe aus wie die 52 davor. Stattdessen der
Beginn von Sprint 9 als Stichtag **plus die festgenagelte Größe** `ALTBESTAND_ERWARTET = 52`
— sie verhindert, dass der Stichtag still verschoben wird, **und** meldet ein Umschreiben
der Historie, denn die Vergangenheit kann sich sonst gar nicht ändern.

**Der Commit-Pfad, den das Ticket als Alternative anbot, existiert bereits.** `setze_status`
prüft den Übergang seit T-0062. Die 52 Fälle entstanden nicht, weil die Prüfung im
Schreibpfad fehlte, sondern weil **an ihr vorbei** geschrieben wurde.

### SWR-119 / SWR-120 — und ein Widerspruch, der im selben Lauf entstand

`BOARD.md` trägt jetzt die Spalte **Verantwortlich** (alle 16 Boards regeneriert und in
einem Zug committet; SWR-110 hat wie vorhergesagt gegriffen, bis alle committet waren).
Daneben meldet der Kopfblock org-weit „n Tickets warten auf den Menschen" **mit Refs**.

**⚠ Beide zusammen erzeugten prompt einen Widerspruch:** die Spalte las das **Feld** und
schrieb bei `projects/p11/T-0006` „Team", während der Zähler dasselbe Ticket als „wartet
auf den Menschen" führte — es ist ein `decision-request` und liegt qua **Typ** beim
Auftraggeber. Beide Aussagen waren für sich begründet und zusammen falsch (B033), und zwar
**entstanden im selben Lauf**. Aufgelöst durch `board.wartet_auf_mensch`: eine Stelle,
beide Anzeigen, plus ein Übereinstimmungstest über den ganzen Bestand.

**Gefunden beim Hinsehen, nicht durch eine Prüfung** — deshalb steht die Prüfung jetzt da.

### ⚠ B066 — Lesbarkeit ist keine Übereinstimmung

Der Widget-Vertrag hatte seit v2.1 den Feldeintrag `team` verloren, weil YAML zwei
Einträge stillschweigend verschmolz (doppelte Schlüssel gewinnen hinten). Zwei Sprints
unentdeckt, weil die Datei durchgehend sauber parste.

**Dieselbe Familie wie die Statusspalte aus SWR-115:** Text, der etwas zusichert, ohne
dass irgendwo gemessen wird, ob es stimmt. `test_vertrag_feldliste.py` hält die Feldliste
ab jetzt **in beide Richtungen** gegen den echten Payload; die Duplikatprüfung geht
bewusst **roh über den Text**, denn gegen einen Fehler, den der Parser schluckt, hilft der
Parser nicht. Verankert als **L-2026-08-17r**.

### Briefkasten: `pm/N-0038` beantwortet und eingeplant

Der Auftraggeber wünscht einen Knopf, mit dem er offene Aufgaben aller Teams/Projekte für
den nächsten Durchlauf priorisiert. **Klasse B** — kein DR nötig, das Team plant selbst
ein (`pm/T-0054`, Frist 24.08.).

**Die darin steckende Feldfrage ist im Ticket entschieden**, nicht als Vorbedingung
davorgestellt: der Knopf setzt `geplant_sprint` (Termin), nicht `prio` (Wichtigkeit) —
beides für eine Absicht wäre B033. Das ist die unmittelbare Anwendung von L-2026-08-17p
aus demselben Sprint.

---

## Aktueller Stand

**Sprint 8 (2026-08-17), der Lauf, in dem eine Prüfung fand, dass die Organisation sich
selbst geglaubt hat — vier Dokumente lang.**

### ⚠ `platform/T-0010` — die Arbeit war fertig, die Meldung hatte keine Deckung

Alle fünf Punkte der Definition of Done wurden in diesem Sprint einzeln nachgeprüft und
waren erfüllt:

```
$ git -C p9 show HEAD:...software-requirements.md | grep -c SWR-110      3
$ python -m unittest tests.test_preflight_arbeitskopie                   19 Tests, OK
$ grep -c 'BEFUND' platform/scripts/preflight.py                         vorhanden
$ grep -m1 '^status:' platform/tickets/T-0010.md                         status: open
```

**Über den legalen Weg geschlossen** — `open → in_progress → in_review → done` mit **drei**
Commits statt einem. Damit erzeugt die Reparatur nicht zusätzlich den Fehler, den
`pm/T-0048` beschreibt.

### ⚠ Der Befund über die Prüfungen — drei schwiegen, und jede hatte recht

| Prüfung | Frage, die sie stellt | Warum sie schwieg |
|---|---|---|
| `nicht_geplant` (SWR-106) | Kommt das Ticket im Plan **vor**? | Es kam vor. |
| `plan_drift` (SWR-109) | Sagt der Plan dieselbe **Sprintnummer** wie das Ticket? | Die Zeile sagt „dieser Sprint", trägt keine Nummer, wird **übersprungen**. |
| `sprint_vergangen` (SWR-112) | Ist der geplante Sprint **vorbei**? | `7 < 7` ist falsch. Frühester Zeitpunkt: der Folgesprint. |

**Die Lücke ist keine Schwäche einer der drei, sondern eine Spalte, die keine von ihnen
liest.** Die Plantabelle hat vier Spalten; drei wurden geprüft, die vierte — die, in der
„erledigt" steht — gegen nichts.

### `pm/T-0049` / SWR-115 — beide Richtungen, und die Ausnahme am Sachverhalt

`status_drift` meldet eine Planzeile „erledigt" über einem nicht geschlossenen Ticket
**und** ein `done`-Ticket unter einer Zeile, die offene Arbeit behauptet. Die zweite
Richtung erzwang eine neue Bestandsfunktion (`sprint.alle_tickets`): `offene_tickets` lässt
`done` weg, dieser Fall wäre darüber **grundsätzlich unsichtbar**.

**Takt-Dauerläufer sind ausgenommen, und die Ausnahme hängt am Ticketfeld `takt`, nicht am
Wortlaut der Planspalte.** Schriebe jemand „erledigt" statt „erfüllt", entstünde sonst ein
Befund aus einer Formulierung statt aus einem Sachverhalt. **Gegenprobe als Test:** dieselbe
Zeile **ohne** `takt` im Ticket **ist** ein Befund — ohne sie wäre die Ausnahme nicht
widerlegbar.

**Zwei geschlossene Wortmengen statt einer Heuristik.** Was in keiner steht, wird
**ignoriert** statt geraten: ein Ratefehler dieser Prüfung wäre ein Fehlalarm über einen
korrekt geführten Plan, und ein Fehlalarm trainiert das Wegsehen — dieselbe Abwägung wie bei
SWR-109, SWR-110 und SWR-112.

### ✅ Die Prüfung hat ihren eigenen Erbauer erwischt

Nachdem `pm/T-0049` auf `done` gesetzt war, meldete `preflight`:

```
[org] BEFUND: 1 Planzeile(n) widersprechen ihrem Ticket
    pm/T-0049: Ticket steht auf „done“, Plan sagt „offen“
```

Das ist die zweite Melderichtung, am Bestand belegt und nicht nur im Test. **Zum zweiten Mal
in zwei Sprints hat eine Verifikation einen Fehler des Laufs gefunden, der sie gebaut hat.**

### ⚠ `pm/T-0038` — ein Grund, der auf ein Ticket zeigte, das es nicht mehr gab

Der Verschiebungsgrund lautete wörtlich: *„gehört gebündelt mit `pm/T-0036` ausgeliefert."*
Gemessen: `pm/T-0036` ist seit Sprint 7 **geschlossen** und hat **nie** eine
Board-Formatänderung gemacht — Teil b) wurde eine Preflight-Zeile, Teil a) ging als
`pm/T-0047` weiter.

**Und der Grund galt nur für einen von fünf Teilen.** Nur b) ist eine Formatänderung; a), c)
und e) haben zwei Sprints auf einen Grund gewartet, der sie nicht betraf.

| Teil | Inhalt | Wohin |
|---|---|---|
| a) | Feld `verantwortlich` + Validierung | **gebaut**, SWR-116, 16 Tests |
| b) | `BOARD.md`-Spalte (**die** Formatänderung) | `pm/T-0050`, Sprint 9 |
| c) | Cockpit-/Preflight-Zähler mit Refs | `pm/T-0051`, Sprint 9 |
| d) | Ablaufregel Session-Agenda | erledigt seit Sprint 6 |
| e) | HMI „Für dich: Handlungen" | `pm/T-0052`, Sprint 10 |

**SWR-116** führt `verantwortlich` als **eigenes** Feld ein statt `rolle` umzudeuten:
`rolle: mensch` trägt bereits eine zweite, verhaltensändernde Bedeutung (Gate, von der
Übergangsprüfung ausgenommen), und eine Umdeutung hätte den betroffenen Tickets still die
Übergangsprüfung abgeschaltet — B033. Das Feld ist **optional**; alle 16 Boards validieren
unverändert. Steht `mensch`, verlangt die Validierung einen Abschnitt
`## Handlung beim Menschen` — sonst wäre „ein Mensch muss ran" eine Behauptung ohne Beleg
(B038).

### `projects/p11/T-0003` — Status korrigiert statt Termin verschoben

Es stand auf `open` mit `blocked_by: []` und sah wie unerledigte Teamarbeit aus, obwohl das
Team es nicht bewegen kann. Jetzt `blocked` mit `blocked_by: [T-0006]`. Die zweite Sperre
(`team-dashboard/T-0002`) ist in Sprint 7 gefallen und deshalb **nicht** eingetragen.

### ⚠ Drei eigene Abweichungen im Plan — von der Prüfung aus Sprint 6 gefunden

Beim Abschluss meldete `plan_drift` drei Tickets, die im Plan auf Sprint 9 standen und in
ihrem Feld noch auf 8 — dieselbe Sorte Fehler, für die die Prüfung gebaut wurde. Korrigiert,
bevor der Plan stand. **Die Prüfstrecke findet inzwischen in jedem Sprint mindestens einen
Fehler des laufenden Sprints.**

---

## Historie: Sprint 7 (2026-08-17)

**Sprint 7 (2026-08-17), der Lauf, in dem eine Prüfung ihren eigenen Erbauer überführt hat
— und ein fünf Sprints altes Problem sich als Abwesenheit herausstellte.**

### ✅ `pm/T-0043` — geschlossen, mit dem Beleg aus dem Lauf um 05:02

Der Wächterlauf 05:02 pushte `p3` (`4468678..673eacd`) und `p5` (`85c4570..0fde98c`) und
löste damit die CI-Läufe aus, die Sprint 6 **hergestellt** statt erhofft hatte:

| Repo | Commit | Zustand |
|---|---|---|
| p3 | `673eacd9` | **grün für diesen Commit** |
| p5 | `0fde98c3` | **grün für diesen Commit** |

`CI-STATUS: ALLES GRUEN (14 Abfragen)` — erstmals seit dem Bestehen von SWR-105 ist kein
Repo rot. Alle drei DoD-Punkte erfüllt, Frist 19.08. gewahrt.

**Die Lehre wiegt schwerer als das Ticket.** Ein rotes Ergebnis altert nicht und meldet
sich nicht. Der Zustand, auf dessen Änderung vier Sprints gewartet haben, **konnte** sich
nicht ändern, solange niemand etwas tat. Erkennungsfrage ab jetzt (L-2026-08-17n Regel 5):
*Kann sich der Zustand, auf den ich warte, überhaupt ändern, wenn ich nichts tue?*

### ⚠ `platform/T-0010` — die Verifikation misst die Arbeitskopie, der Push liefert HEAD

Sprint 6 schrieb SWR-109 um 04:25 nach `p9/requirements/software/software-requirements.md`
und committete `p9` nie. Belegt:

```
$ git -C p9 log -1 --format="%ci"          2026-08-17 03:03:31 +0200
$ git -C p9 show HEAD:...requirements.md | grep -c SWR-109        0
$ grep -c SWR-109 p9/requirements/...md                            2
```

Beide Werkzeuge sind für sich korrekt: `trace_matrix` liest die Platte (und **muss** das,
sonst könnte man eine Anforderung nicht schreiben und im selben Lauf prüfen), `abschluss.cmd
[4/5]` pusht HEAD. Falsch war, dass **niemand vor dem Push gefragt hat, ob das Gemessene
das Gelieferte ist**.

**Sofort repariert** (`p9` committet, `c2be4b0`), **dann gebaut** (SWR-110): `preflight`
nennt die unsauberen Dateien statt sie zu zählen und macht eine unverbuchte Anforderungs-,
Ticket- oder `BOARD.md`-Datei zum **Befund**, der `abschluss.cmd` in `[1/5]` anhält.

**Die Ausnahme ist der Teil, der das Werkzeug brauchbar macht.** Ohne sie hätte der Befund
**täglich** gefeuert — fünf Repos sind jeden Tag unsauber, weil die `Stand:`-Zeile
regeneriert wird. Sie wird deshalb am **Diff** entschieden und nie am Dateinamen, mit einem
Gegentest, der eine `BOARD.md` mit einer **zweiten** geänderten Zeile sehr wohl meldet.
Ohne diesen Gegentest wäre die Ausnahme nicht widerlegbar.

**⚠ Ein Test hat beim Schreiben eine zweite Lücke gefunden.** `git status` fasst einen nicht
getrackten **Ordner** zu einer Zeile `?? tickets/` zusammen — ein neu angelegtes Ticket in
einem neuen Ordner wäre unsichtbar geblieben, also genau der Fall „existiert nur in der
Arbeitskopie". Behoben mit `-uall`. Der Test war für die Regel geschrieben, nicht für diese
Zeile.

### `team-dashboard/T-0002` — der vierte Befund an einem Feld, und der erste ohne falschen Wert

`letzte_baseline` trug Tag **und** Annotation in einem String (`p1`: 300 Zeichen).
Entschieden wurde Weg 1: zwei Felder, getrennt in der **Quelle** (`aggregation`), wo
`git tag -n1` sie ohnehin trennt — nicht im Widget, wo die Regel im JavaScript stünde und
Cockpit und Dashboard Verschiedenes sagen würden. Am echten Payload geprüft: p1 → 7 + 284
Zeichen, platform → Tag + kurzer Text, pm → `null`/`null`, p11 → `""`/`""`. Vertrag **v2.1**,
SWR-111, Leser mitgezogen.

Nach B064 (geerbte Nachbar-Baseline), B065 (lexikografisch statt jüngste) und SWR-108 ist
das der **vierte** Befund an diesem Feld — und der erste, bei dem **beide** Werte richtig
waren und trotzdem etwas nicht stimmte. Ein Feld, das dreimal auffällig war, verdient die
Frage, ob es **eine** Sache benennt.

### Drei Befunde in den eigenen Zahlen — alle geschlossen

* **`pm/T-0045` / SWR-112:** offene Tickets auf einem **vergangenen** Sprint werden
  gemeldet. `widersprueche` hielt den Sprint gegen die Frist, `plan_drift` gegen die
  Planzeile — gegen die **Gegenwart** hielt ihn niemand. Drei Abgrenzungen entschieden:
  erledigte Tickets kein Fall, `in_review` zählt mit, `decision-request` ausgenommen.
  Ohne die letzte hätte die Prüfung an ihrem **ersten Tag** `p11/T-0006` fehlgemeldet.
* **`pm/T-0046` / SWR-113:** „nicht geschlossen" hat eine aufgeschriebene Zählweise
  (Takt-Dauerläufer eingeschlossen), kommt aus dem Werkzeug und trägt `sachtickets` als
  eigene Zahl daneben. Die Reihe 2–5 bleibt **unkorrigiert** mit ⚠.
* **`pm/T-0036` / SWR-114:** der „ohne Frist"-Zähler wird org-weit **mit Namen** gemeldet
  statt kachelweise gezählt. Teil a) als `pm/T-0047` abgetrennt (B025: `aggregation.cockpit`
  war in diesem Lauf schon angefasst).

### ⚠ Die Prüfung aus Sprint 6 hat ihren eigenen Erbauer überführt

Beim Fortschreiben des Plans wurden `pm/T-0038` und `projects/p11/T-0003` eine Nummer nach
hinten gesetzt — und die Ticketfelder blieben stehen. `plan_drift` meldete **2**, also genau
den Fehler, gegen den sie in Sprint 6 gebaut wurde, im Lauf danach und beim selben Team.
Nachgezogen, danach **0**. Das ist kein Rückfall, sondern der Beleg, dass die Prüfung an der
richtigen Stelle sitzt: sie hat den Fehler gefunden, **bevor** der Plan stand.

### Board-Check gegen die Erwartung gelesen (B041 Regel 3)

Tickets gesamt **261** (+3: `platform/T-0010`, `pm/T-0047`, `pm/T-0048`). Nicht
geschlossen **15** (Start 16; sechs zu, drei neu, eines davon zu) — nach der in diesem Sprint **festgelegten**
Zählweise, davon 6 Takt-Dauerläufer und **9 Sachtickets**. Matrix **114 SWRs / 0 Lücken**
(+5: SWR-110 bis SWR-114). **568 Tests** (vorher 514). `nicht_geplant: []`,
`widersprueche: []`, `plan_drift: []`, `sprint_vergangen: []`, Briefe: **kein offener**.

### Ehrlich zur Grenze (B027) und widerlegbare Vorhersage

`preflight` bricht ab jetzt bei unverbuchten Verifikationsquellen ab. Dieser Sprint hat
alles committet — **also läuft der nächste Wächterlauf durch**. Bricht er in `[1/5]` mit
einer `BEFUND:`-Zeile ab, ist die Stand-Zeilen-Ausnahme aus SWR-110 zu eng gefasst und
`platform/T-0010` wird wiedereröffnet. Die Ausnahme ist am Host **nicht** erprobt: diese
Sandbox erzeugt dieselben `BOARD.md`-Diffs, aber der Host schreibt CRLF — sollte das den
Diff verändern, meldet der Lauf es an dieser Zeile.

**Lessons sofort verankert (D005, noch in diesem Lauf): L-2026-08-17n** mit fünf Regeln.
Die wichtigste ist aus **vier** gleichartigen Abwägungen in vier Sprints entstanden
(SWR-109, SWR-110, SWR-112, B049) und ab jetzt eine Bauregel: *zu jeder neuen Prüfung
gehört die Frage, was sie am ersten Tag melden würde, und ein Test für den Fall, den sie
**nicht** melden soll.*

---

## Vorheriger Stand (Sprint 6, 2026-08-17)

**Sprint 6 (2026-08-17), der Lauf, in dem eine Reparatur ihren eigenen Folgeschaden
vorgeführt hat — und die Organisation vier eigene Zahlen widerlegt hat.**

**Der Startcheck war diesmal Pflicht, nicht Spürsinn.** Sprint 5 hatte eine widerlegbare
Vorhersage hinterlassen: *„bleibt `abschluss-auto.log` bei derselben Meldung, ist die
Diagnose falsch."* Der Blick ins Protokoll war damit vorgeschrieben. **Das ist der
Unterschied zwischen Sprint 5 und Sprint 6** — nicht Aufmerksamkeit, sondern dass es eine
Zeile gab, die geprüft werden musste.

**`platform/T-0009` — zwei Ursachen, und die zweite ist älter als die erste.**

*Ursache A, der Folgeschaden:* `T-0007` setzte `encoding="utf-8", errors="replace"` an
allen 33 Textmodus-Aufrufen. Für `git` (fremdes Programm, schreibt UTF-8) ist das richtig.
An den drei Stellen, an denen Python **Python** aufruft (`preflight.board_check`,
`preflight.unit_tests`, `teams._standard_runner`), schreibt das Kind aber in der
Locale-Kodierung des Hosts. Vorher lasen und schrieben beide Seiten cp1252 — **zufällig
passend**. Danach schrieb das Kind cp1252 und der Elternprozess las UTF-8: jedes `ü` in
`ungültiger status` wurde zu **U+FFFD** — und U+FFFD ist genau das Zeichen, das cp1252 auf
dem Rückweg nicht ausgeben kann. `errors="replace"` hat den Fehler nicht behoben, sondern
**eine Stufe weitergereicht**. Nachgestellt und gegengeprobt: derselbe Aufruf mit
`encoding="cp1252"` (Stand vor Sprint 5) liefert den Text sauber.

*Ursache B, unabhängig und älter:* die Meldungen dieser Organisation zitieren
Ticketinhalte. **121 Ticketdateien** tragen ein „→", dazu `↔`, `⟳`, `⚠`, `≤`, `≠`, `≈`,
`✅`, `⏳`, `✓`, `✔`, `↻`. Ein Validierungsbefund an einem Ticket mit einem Pfeil im Titel
beendet `preflight` mit demselben Fehler — **auch ohne Ursache A**. Sie hat nur nie
zugeschlagen, weil der Lauf vorher schon an der Leseseite starb.

*Die Korrektur:* neu `platform/scripts/konsole.py`, beide Enden an **einer** Stelle.
`kind_umgebung()` setzt `PYTHONIOENCODING=utf-8` für Python-Kindprozesse (Ursache A
verschwindet, das Zeichen entsteht nicht mehr); `sichere_ausgabe()` stellt `stdout`/`stderr`
auf `errors="backslashreplace"` in allen **zwölf** Einstiegspunkten. Bewusst
`backslashreplace` und nicht `replace`: letzteres erzeugt U+FFFD, also genau das Zeichen,
an dem cp1252 scheitert — dieselbe Reparatur, die diesen Befund verursacht hat, ein zweites
Mal. Bewusst **nicht** `reconfigure(encoding="utf-8")`: das tauschte einen Absturz gegen
unlesbare Umlaute in jeder Zeile.

**Warum der Regel-Test aus T-0007 blind war.** Er prüfte den gesamten Produktionscode —
**auf das Lesen**. Ein Rohr hat zwei Enden, und die Regel beschrieb eines. Der neue
Regel-Test prüft beide.

**⚠ Die Zahl aus Sprint 5 ist widerlegt, die Diagnose ist bestätigt.** Sprint 5 schrieb an
vier Stellen *„seit dem 17.08. kein einziger Push, rund zweihundert Mal"*. Das Protokoll
zählt für den 17.08.: **12 Startmarken, 4 erfolgreiche Pushes, 9 Fehler**. Die Fehlserie
beginnt um **02:14**. Und genau das macht die Diagnose **stärker** als in Sprint 5:

| Zeit | Ereignis |
|---|---|
| 01:31:53 | letzter **erfolgreicher** Push |
| 01:52–01:54 | die Commits, die das „⏳" in `pm/tickets/T-0042.md` einbrachten |
| 02:14 | erster Lauf danach — **FEHLER** |
| 02:14–03:59 | acht Läufe, alle FEHLER |

Zwischen dem letzten grünen und dem ersten roten Lauf liegt genau ein Ereignis. Hätte
jemand in Sprint 5 nachgezählt statt zu schätzen, wäre dieser Zeitpunkt schon dort sichtbar
gewesen.

**`pm/T-0044` — der Befund kam aus der Kernpflicht selbst.** Beim Sichten aller offenen
Tickets wichen **sieben** Planzeilen von ihrem Ticket ab: Sprint 5 hatte fünf Aufgaben in
`sprint-aktuell.md` „eine Nummer nach hinten" geschoben und die Ticketfelder nicht
angefasst. Die vorhandenen Prüfungen konnten das **zu Recht** nicht finden — `nicht_geplant`
fragt, ob ein Ticket **vorkommt** (alle kamen vor), `sprint_widerspruch` hält den Sprint
gegen die **Frist** (beide drifteten gemeinsam). **Anwesenheit ist nicht Übereinstimmung.**
Gebaut als `sprint.plan_drift()`, **SWR-109**.

**⚠ Und die Prüfung fand beim ersten Lauf einen Fehler in sich selbst.** Die nackte
Ticket-ID `T-0003` gibt es in `p11` **und** `p12`; blind aufgelöst ordnete sie die
p12-Planzeile dem p11-Ticket zu und meldete einen Drift, den es nicht gibt. Eine Prüfung
mit Fehlalarmen trainiert das Wegschauen. Behoben: volle Referenz gewinnt, nackte ID nur
bei Eindeutigkeit — zwei Tests halten beide Hälften fest.

**`platform/T-0008` — der Verschiebungsgrund war messbar und leer.** Sprint 5 hatte es mit
*„die Korrektur schaltet eine Prüfung ein, die nie lief; was dabei auftaucht, braucht
Urteil"* vertagt. Es wäre zum **zweiten** Mal mit demselben Grund verschoben worden — und
L-2026-08-17j Regel 2 verlangt dann eine **Prüfung der Quelle**. Alle Tickets von p10/p11/p12
gegen HEAD gehalten: **0 Statusänderungen, 0 Befunde**. Danach war die Korrektur eine Zeile
(`git rev-parse --show-prefix` statt eines angenommenen Pfads). **Die Regel ist in Sprint 5
aus einem Wartegrund entstanden und hat hier zum ersten Mal einen Verschiebungsgrund
gekippt.**

**⚠ Ein Regressionstest aus T-0007 hat einen Fehler in dieser Korrektur gefangen.** Die
erste Fassung schrieb `praefix.stdout.strip()` — also denselben `AttributeError` auf `None`,
der drei Sprints lang jeden Push verhindert hat, **eine Zeile weiter neu eingebaut**, im
selben Modul, von einem Lauf, der dieses Muster kannte. Gefangen hat ihn ein Test, der für
eine *andere* Zeile geschrieben wurde. Das ist der beste Beleg für diesen Testtyp: er
sichert nicht eine Korrektur, sondern eine **Stelle**.

**⚠ Und die vierte Zahl fand die eigene Regel, nachdem sie geschrieben war.** Beim
Abschluss trug die erste Fassung „nicht geschlossen **14**" — geschätzt, in demselben
Absatz, der drei geschätzte Zahlen korrigiert. Nachgezählt: das Werkzeug sagt **17 beim
Start, 18 beim Abschluss**. Die seit Sprint 2 gemeldete **15** passt zu keiner Zählweise,
und ihre Zählweise steht nirgends. Aufgenommen als `pm/T-0046`, **nicht rückwirkend
korrigiert** — eine still ersetzte Zahl nimmt dem nächsten Leser den Hinweis.

**Ehrlich zur Grenze (B027).** Dass der Wächter am Host jetzt weiterkommt, ist **nicht**
belegt: diese Sandbox ist UTF-8 und hat auch diesen Fehler nie gesehen. Dieselbe Grenze wie
bei T-0007 — und sie hat dort genau einmal getäuscht. **Widerlegbare Vorhersage, diesmal
schärfer formuliert:** der nächste Lauf erreicht `[3/5]` oder weiter. Bricht er wieder in
`[1/5]`/`[2/5]` mit einem Kodierungsfehler ab, ist `T-0009` widerlegt und wird
wiedereröffnet. *Der Unterschied zu Sprint 5:* dort hieß die Erwartung „läuft durch", und
jeder Abbruch hätte sie widerlegt. Hier ist sie ein **Fortschritt der Abbruchstelle** —
prüfbar an einer Zeile, auch wenn ein dritter Defekt dahinterliegt.

**Lessons sofort verankert (D005, noch in diesem Lauf):** **L-2026-08-17l** (eine Reparatur,
die nur ein Ende eines Rohrs anfasst, verschiebt den Fehler ans andere; `errors="replace"`
ist eine Verschiebung, keine Reparatur; ein Werkzeug, dessen Aufgabe das Melden ist, darf am
Melden nicht sterben; ein Regel-Test deckt genau so viel ab, wie seine Regel sagt) und
**L-2026-08-17m** (eine Zahl in einer Begründung wird gezählt oder weggelassen; die eigene
Verifikation ist die wahrscheinlichste Stelle für eine ungeprüfte Zahl; ein
Verschiebungsgrund ist prüfbar, bevor die Arbeit getan ist; wer eine Doppelaussage
absichert, zählt vorher, wie viele Stellen dieselbe Frage beantworten).

## ⚠ Der Lauf, der während dieses Sprints ankam — und drei Wartezeilen auflöste

**Um 04:29 startete der Wächter, um 04:32:10 meldete er „OK - alles geprueft und
gepusht".** Er lief mit `platform/T-0009` (committet 04:20:54) und ging durch alle fünf
Schritte: `PREFLIGHT: STARTKLAR`, `Ran 510 tests`, Projektstatus versioniert, Push,
CI-Status. **Der erste erfolgreiche Push seit 01:31:53.**

Das ist kein Nebenergebnis, sondern der Beleg für die eigene Vorhersage — und er kam
**innerhalb** des Sprints, der sie gestellt hat. Erwartet war `[3/5]` oder weiter;
geliefert wurde der ganze Lauf.

**`platform/T-0004` / SWR-107 — geschlossen, Frist 18.08. gewahrt.** Der Bericht nennt
jetzt Job und Schritt: *p3 (failure): Schritt „BOARD.md aktuell?"*, ebenso p5. Alle fünf
Zusicherungen von SWR-107 sind am echten Lauf geprüft — besonders die vierte, für die es
bisher nur Tests mit injizierter Abruffunktion gab: `p1` meldete einen **echten** HTTP 504,
und der Bericht behielt ihn als eigenen Zustand, statt ihn zu grün oder rot zu verbiegen.
Das Ticket stand seit Sprint 2 auf `in_review` mit der Begründung *„der Netzweg wird beim
nächsten Hostlauf belegt"*. Der Satz war richtig — falsch war die stille Annahme, dass der
nächste Hostlauf **stattfindet**.

**Die Vorhersage aus Sprint 3 ist eingetroffen.** `platform` ist grün, für den Commit
`f3a71b0d`. Sie stand drei Sprints offen und war in dieser Zeit **nicht prüfbar**, weil
kein Bericht entstand — kein Zeichen von Geduld, sondern die Folge desselben Defekts.

**`pm/T-0043` — zwei Ursachen ausgeschlossen, der entscheidende Lauf angestoßen.** Der rote
Schritt heißt „BOARD.md aktuell?" und liegt **zwei Schritte nach** dem Checkout von
`platform`, für den `PLATFORM_READ_TOKEN` gebraucht wird. **Also kein Zugangsproblem** — die
seit Sprint 2 in Aussicht gestellte Klasse-A-Entscheidung entfällt ersatzlos. Zweitens:
`p3` und `p5` regenerieren ihre `BOARD.md` heute byte-gleich bis auf die Stand-Zeile, und
genau die ignoriert der Vergleich (`-I "^Stand:"`, der Fix aus `pm/T-0010`); dieselbe
Gegenprobe für die grünen `p7`/`p4` ergibt dasselbe.

**Der eigentliche Fund dabei ist ein Lesefehler von vier Sprints.** `p3` und `p5` wurden
seit dem **16.08. 07:0x** nicht gepusht — ohne Push kein neuer Lauf. Das „ROT" ist seit über
21 Stunden **dasselbe eingefrorene Ergebnis** und wurde vier Sprints lang als fortlaufende
Störung gelesen. Deshalb wurde der Auslöser diesmal **hergestellt** statt erhofft: `BOARD.md`
in beiden Repos neu erzeugt (die Stand-Zeile ist heute tatsächlich veraltet), committet,
beide in der Push-Anforderung. **Widerlegbare Vorhersage:** beide werden grün. Wenn nicht,
ist „am heutigen Inhalt liegt es nicht" widerlegt.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** gesamt **258** (+4: `T-0009`,
`pm/T-0044`, `pm/T-0045`, `pm/T-0046`), platform **9** (+1), pm **46** (+3),
team-dashboard 2 (unverändert). Nicht geschlossen **17** (Start 17; zwei zu, zwei
neu) — **erstmals mit Werkzeugzahl statt von Hand**, siehe `pm/T-0046`. Briefe **48**, davon **0 offen**. Matrix
**109 SWRs / 0 Lücken** (+1: SWR-109). **514 Tests** (vorher 492). `nicht_geplant: []`,
`widersprueche: []`, `plan_drift: []`.

---

## Vorheriger Stand (Sprint 5, 2026-08-17)

1. **⚠ Seit dem 17.08. ist kein einziger Push durchgekommen — nicht mangels Lauf, sondern
   weil jeder Lauf abbrach.** Der Wächter versuchte es alle 15 Minuten, rund zweihundert
   Mal. Ursache gefunden und behoben: **`platform/T-0007`**.
2. **`board.py` las die Git-Ausgabe ohne feste Kodierung.** Auf dem Windows-Host gilt
   cp1252; `pm/T-0042.md` trägt seit Sprint 3 ein Zeichen, dessen UTF-8-Folge ein dort
   unbelegtes Byte enthält. Der Lese-Thread starb, `stdout` wurde `None` **bei
   `returncode == 0`**, und der Absturz nannte weder Datei noch Ursache.
3. **⚠ Damit ist die Auskunft von drei Sprints widerlegt.** „Der Beleg kommt von selbst"
   war falsch — er konnte nicht kommen. Der Beweis lag die ganze Zeit im Arbeitsordner.
4. **`p11/T-0005` erledigt, und der Entwurf dreht die Frage um:** nicht die Kachelzahl
   sprengt das Budget, sondern **ein Feld** — `letzte_baseline`, bis zu 300 Zeichen, ohne
   Grenze im Vertrag. Eine Entscheidung liegt in der Inbox (`p11/T-0006`, Frist 19.08.).
5. **492 Tests grün**, Matrix **108 SWRs / 0 Lücken**, Preflight STARTKLAR, kein offener
   Brief (48 Briefe), unterminiert 0, überfällig 0.

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Sprint 5 (2026-08-17), der Lauf, in dem der geplante Inhalt nicht der wertvollste war.**

**Der Startcheck hat den Sprint umgeschrieben.** Geplant waren der Layout-Entwurf
`p11/T-0005` und zwei Tickets, die „auf einen Hostlauf warten". Beim Nachsehen in
`abschluss-auto.log` stand dort seit dem 17.08. bei **jedem** Lauf im Abstand von 15
Minuten derselbe Abbruch: `board-check` von `pm` mit einem `UnicodeDecodeError`, danach
ein `AttributeError`, danach *„ABBRUCH — nichts wurde gepusht"*.

**`platform/T-0007` — zwei Defekte, und der zweite ist der schlimmere.**

*Defekt 1, die Ursache:* `subprocess.run(..., text=True)` **ohne `encoding=`** nimmt die
Locale-Kodierung des Systems. In der Sandbox ist das UTF-8, auf dem Host cp1252 — der
Fehler ist hier **prinzipiell unsichtbar**. `pm/T-0042.md` trägt an Byte 10338 ein „⏳",
dessen UTF-8-Folge das in cp1252 unbelegte Byte `8f` enthält. Bemerkenswert: **jede
DATEI-Lesung in `board.py` war schon utf-8-fest** (sechs Stellen), nur diese eine
GIT-Lesung nicht.

*Defekt 2, die Behandlung:* `returncode` war **0** — aus Sicht von git war der Aufruf
erfolgreich —, die Prüfung `if out.returncode != 0` ließ durch, und
`parse_frontmatter(None)` starb an einem `AttributeError`, der **weder in der
`except`-Liste stand noch die Datei, das Repo oder die Kodierung nannte**.

*Korrektur:* `encoding="utf-8", errors="replace"` an **allen 33 Produktionsaufrufen** im
Textmodus (15 Dateien) — die Regel gilt nicht für eine Zeile. Und `status_in_head` gibt
bei einem Lesefehler `UNLESBAR` statt `None` zurück: `None` heißt „Ticket ist neu" und
lässt die Übergangsprüfung **zu Recht** aus; ein Lesefehler, der ebenfalls `None` gäbe,
hätte den Absturz gegen eine **still übersprungene Prüfung** getauscht — die schlechtere
Hälfte des Tauschs. `validiere` macht daraus einen **Befund mit Dateinamen**.

**⚠ Wie das drei Sprints überstehen konnte.** Das Erkennungsmuster war seit dem 16.08.
aufgeschrieben (L-2026-08-16): *„`PUSH-ANFORDERUNG.txt` bleibt liegen +
`abschluss-auto.log` ansehen"*. Genau das lag vor — die Datei war liegengeblieben und trug
**zwei** Zeilen, aus Sprint 3 und Sprint 4. Der Wächter löscht sie bei Erfolg; zwei Zeilen
sind zwei gescheiterte Läufe, ausgeschrieben, an der Stelle, an die das Team bei jedem
Sprintende selbst schreibt. Sprint 3 hatte sogar vorhergesagt, die wiederholte Zeile werde
„beim dritten Mal auffallen" — sie fiel nicht auf, weil sie dieselbe blieb.

**Testdeckung aufgeschlüsselt statt gezählt (L-2026-08-17g Regel 2).** 6 neue Tests
(486 → **492**): **3** fallen gegen den Altstand um, zwei davon mit **wörtlich der Meldung
aus dem Hostprotokoll**, der dritte listet die 33 ungesicherten Aufrufstellen auf; **2**
stellen die Ursache nach (dieselben Bytes über cp1252 → `UnicodeDecodeError`, über UTF-8 →
sauber); **1** ist eine Gegenprobe (`OSError` bleibt `None`, damit die Reparatur nicht
lauter wird als der Fehler). Der wertvollste ist der Regel-Test über den **gesamten**
Produktionscode — sein Anlass steht in `preflight.py` selbst: dort trägt eine Funktion
seit `pm/T-0024` die richtige Einstellung samt Begründung, und die drei Nachbaraufrufe
**derselben Datei** haben sie nie bekommen.

**`p11/T-0005` — der Entwurf dreht die Frage um.** Gefragt war, wie viele Kacheln bei
1920×1080 ohne Scrollen passen. Die Antwort liegt nicht in der Zahl, sondern im **Rahmen**:
`main { max-width: 62rem }` gilt seit P1 für jede Ansicht, und in dieser 992-px-Spalte
passen 16 Kacheln bei **keiner** Anordnung (gestapelt Faktor 4,3; als Raster im Korridor
1536 px gegen 948 px verfügbar). Über die volle Breite: **7 Spalten × 3 Reihen = 768 px**,
180 px Reserve. Die drei Optionen des Projektauftrags (gruppieren, nur Auffälliges,
Favoriten) sind bewusst verworfen — sie lösen ein Überlaufproblem, das bei 16 Einträgen
nicht besteht, und für den Überlauf gibt es mit SWR-093 bereits eine freigegebene Antwort.

**⚠ Der Fund, der nicht in der Frage stand.** `letzte_baseline` ist im Widget-Vertrag
`typ: string` **ohne** Längengrenze und trägt im echten Payload bis zu **300 Zeichen**
(p1) — in einer 240-px-Spalte rund 430 px, mehr als das ganze Reihenbudget. Der Vertrag
begrenzt `aufgaben` mit `max_eintraege: 3` und lässt ausgerechnet das Feld frei, das
wächst. Die Ursache ist nicht die Länge, sondern die **Vermischung**: das Feld trägt Tag
**und** Annotation unter einem Namen, so wie `git tag -n1` sie ausgibt (B033). **Nicht im
Widget gelöst** — ein `.slice()` im Dashboard wäre die eigene Regel neben dem Vertrag, die
`T-0003` verbietet und die ADR-P11-001 als zweite Liste beschreibt. Weitergegeben an den
Vertragsinhaber: `team-dashboard/T-0002`, Frist 19.08.

**`platform/T-0008` — der zweite Befund kam aus derselben Frage.** Wer wissen will, was
ein `None` aus `status_in_head` alles heißen kann, findet den nächsten Fall: für `p10`,
`p11` und `p12` (verschachtelt im Repo `projects`) sucht die Funktion die Datei unter
`HEAD:tickets/…` statt `HEAD:p11/tickets/…`. `git show` scheitert, das gilt als „Ticket
ist neu", und der `board-check` meldet `OK`. **Für drei von sechzehn Einträgen hat SWR-002
nie geprüft.** Live-Beleg aus diesem Lauf: `p11/T-0005` wurde versehentlich direkt
`open → done` gesetzt — ein unzulässiger Übergang, und der Check über alle 16 Einträge lief
fehlerfrei durch. Von Hand korrigiert, bewusst nicht mitgebaut (B025 — und weil die
Korrektur eine nie gelaufene Prüfung einschaltet, was Urteil braucht).

**Ehrlich zur Grenze (B027).** Dass der Wächter am Host jetzt durchläuft, ist **nicht**
belegt: diese Sandbox ist UTF-8 und hat den Fehler nie gesehen. Der Layout-Entwurf ist
gerechnet, nicht gemessen — kein Browser hat die Seite gesehen. Beides sind widerlegbare
Vorhersagen: bleibt `abschluss-auto.log` bei derselben Meldung, ist die Diagnose falsch
und `T-0007` wird wiedereröffnet.

**Der DR, der nicht gestellt wurde.** Die Planung sah einen Inbox-DR an den Auftraggeber
vor („bitte einen Hostlauf auslösen"; die Frist von `platform/T-0004` läuft am 18.08. ab).
Er wurde hinfällig, bevor er geschrieben war — die Ursache war kein Mensch, sondern ein
Werkzeug. Das steht hier, weil ein nicht gestellter DR sonst spurlos verschwindet: **erst
nachsehen, dann eskalieren.**

**Lessons sofort verankert (D005, noch in diesem Lauf):** **L-2026-08-17j** (ein
ausbleibendes Ergebnis hat zwei Erklärungen, und nur eine heißt warten; die **zweite**
Wiederholung eines Wartegrundes ist der Auslöser für eine Prüfung der Quelle, nicht für
einen weiteren Vermerk; ein Protokoll, das niemand liest, ist keines; eine Lehre, die nur
an ihrem Fundort steht, schützt genau eine Zeile) und **L-2026-08-17k** (ein Rückgabewert,
der „alles in Ordnung" und „ich konnte nicht nachsehen" zusammenfasst, ist ein stiller
Ausfall mit Ansage).

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** gesamt **254** (+4), platform
**8** (+2), p11 **6** (+1), team-dashboard **2** (+1); nicht geschlossen **15** — zum
dritten Mal dieselbe Zahl und zum dritten Mal Zufall (zwei zu, zwei neu). Briefe **48**,
davon **0 offen**. Matrix **108 SWRs / 0 Lücken** (unverändert: die Korrektur fällt unter
SWR-002 und braucht keine neue Anforderung — Präzedenz B065). **492 Tests** (vorher 486).
`nicht_geplant: []`, `widersprueche: []`.

---

## Vorheriger Stand (Sprint 4, 2026-08-17)

**Sprint 4 (2026-08-17), der Lauf, in dem ein Ticket seine eigene Problembeschreibung
widerlegt hat.**

**Der Plan war klein und ist aufgegangen.** Sprint 4 hatte ein Sachticket (`platform/T-0006`)
und zwei, die auf einen Hostlauf warten. Dazu kam im Lauf eine Planungsaufgabe, die aus dem
Sachticket folgte: mit `T-0006` fiel der Grund weg, mit dem `p11/T-0003` auf Sprint 5 gesetzt
worden war.

**`platform/T-0006` — warum `null` und nicht ein zweites Feld.** Das Ticket hatte den Weg
bewusst offen gelassen und drei Varianten mit ihrem Preis genannt. Gewählt ist Variante 2,
und zwar am **Objekt**: `kpi` ist ganz `null`, wenn nichts erhoben wurde, nicht `{laeufe:
null}`. Der Grund ist nicht Eleganz, sondern Bestand — `team: null` heißt im Payload seit P7
sauber „kein Team", der Widget-Vertrag hatte das ausdrücklich als in Ordnung befunden. Eine
vorhandene Redewendung zu erweitern ist billiger als eine neue zu erfinden, für die Quelle wie
für jeden Leser.

**Die drei Tatsachen, und warum zwei davon nicht die naheliegenden sind.**

| Feld | `null` genau dann, wenn | echte Null |
|---|---|---|
| `kpi` | **keine Run-Registry-Datei** vorhanden | Registry da, keine Läufe → `{laeufe: 0}` |
| `team.letzter_digest` | die **SLA** nennt keinen `digest` | SLA nennt einen, noch keiner da → `""` |
| `letzte_baseline` | das **Profil** kennt kein G4 (Playbook Kap. 15) | G4 vorgesehen, noch kein Tag → `""` |

`laeufe == 0` als Kriterium hätte einer echten Null-Messung ihre 0 genommen. `isdir("digest")`
hätte genau im Moment vor dem ersten Digest „führt keine Digests" gesagt — also in dem
einzigen Moment, für den man die Unterscheidung braucht. Und die Baseline hängt am **Profil**
und nicht an der Cockpit-**Gruppe**: die Gruppe sagt, WER ein Eintrag ist, das Profil sagt,
WELCHE Gates gelten. An dieser Verwechslung war der erste Widget-Vertrag schon einmal
gescheitert (`platform` ist festes Team **und** trägt eine Baseline).

**⚠ Der Befund des Laufs steht in der Problembeschreibung des eigenen Tickets.**
`platform/T-0006` führte `team.letzter_digest` mit dem Fall *„`team-dashboard`: führt Digests,
hatte noch keinen"*. Gegen den eigenen Steckbrief gehalten stimmt das nicht: `team-dashboard`
hat drei SLAs — `widget-inhalte`, `widget-vertrag`, `nur-darstellen` — und darunter keinen
Digest. Es führt keine. Der Satz stand da, weil eine leere Stelle nach „noch nicht" aussieht:
**dieselbe Verwechslung, die das Ticket beheben sollte, in seiner eigenen
Problembeschreibung.** Er bleibt wörtlich als widerlegt im Ticket stehen (L-2026-08-17g Regel
4). Ohne den Fund wäre die Verzeichnisregel gebaut worden — die Widerlegung hat also nicht nur
einen Satz korrigiert, sondern die Bauart.

**Der Preis, benannt und nicht kleingeredet.** `null` weitet den Wertebereich von drei Feldern
für **jeden** Leser. Wer `p.kpi.kosten_eur.toFixed(2)` schreibt, ohne auf `null` zu prüfen,
bekommt keinen falschen Wert, sondern einen **Absturz** — im HMI die ganze Kachel. Das ist ein
anderer Fehlermodus als vorher und ein schlechterer, wenn man ihn übersieht; deshalb steht das
Mitziehen des einen heutigen Lesers (`backend/static/app.js`) in der **Verifikation** der
Anforderung und nicht als Folgeticket. Zweiter Teil des Preises: `letzte_baseline` wird jetzt
immer gezeigt, auch als „noch keine" — vorher fiel die Zeile bei leerem Wert stillschweigend
weg, und genau das verbietet SWR-096.

**Der Widget-Vertrag steht als v2.** Die drei `null_unklar`-Marken und alle
`bis_dahin`-Behelfsregeln sind **ersatzlos** weg, nicht umformuliert; `v1` bleibt als Beleg
daneben stehen. Der Gewinn ist dabei nicht die Marke, sondern ihr **Ort**: vorher musste ein
Widget drei Sonderregeln für drei Felder kennen, jetzt gilt für alle Felder derselbe Satz, und
er steht **einmal** oben in der YAML. Ein Vertrag, der je Feld eine Ausnahme trägt, ist eine
Liste von Ausnahmen und kein Vertrag.

**`p11/T-0003` — zerlegt, nicht verschoben.** In Sprint 3 stand das Ticket mit einem sauber
begründeten Termin auf Sprint 5: drei Vertragsfelder waren nur über eine Behelfsregel bedient,
und davor zu bauen hätte geheißen, die SWR-096-Tests zweimal zu schreiben. Dieser Sprint hat
den Grund aufgelöst — **und damit stand der Termin nur noch da, weil er einmal dorthin
geschrieben worden war.** Übrig blieb „zu groß", und dafür sieht `pm/D006` nicht Verschieben
vor, sondern Zerlegen: `p11/T-0004` (ADR) in diesem Sprint erledigt, `p11/T-0005`
(Layout-Entwurf) auf Sprint 5, der Rest bleibt in `T-0003`. Frist 20.08. unverändert.

**Der ADR sagt einen Satz, den es ohne diesen Sprint nicht gäbe.** `ADR-P11-001` legt fest,
dass der Server für das Dashboard **nichts** aufbereitet — keine zweite Sicht auf dieselbe
Quelle. Der Punkt, der neu ist: SWR-108 hat die drei Fälle ausgeschrieben in `cockpitKarte`
untergebracht, an einer Stelle, die ein Widget nicht mitbenutzen kann. Der ADR macht daraus
eine Auflage: **erst herausziehen, dann rendern.** Ohne sie wäre die naheliegende erste
Handlung des Baus gewesen, sie abzuschreiben — und die zweite Liste wäre da, in JavaScript
statt in YAML, also dort, wo sie niemand sucht.

**Zwei Tickets ohne Arbeit, zum zweiten Mal mit demselben Grund.** `platform/T-0004` (Netzweg
der Jobs-Abfrage) und `pm/T-0043` (welcher Schritt macht `p3`/`p5` rot) warten beide auf einen
`CI-STATUS.md`, der **nach** dem SWR-107-Commit (01:17) entstanden ist. Die Datei steht
unverändert auf **00:46**. Beide auf Sprint 5, keine Handlung. Dass es der **zweite** Sprint
in Folge ist, steht ausdrücklich in der Agenda für den Auftraggeber — nicht weil etwas zu tun
wäre, sondern weil zwei Sprints in Folge dieselbe Zeile zu schreiben der Moment ist, an dem
man es sagt statt still weiterzulaufen.

Für `pm/T-0043` hat dieser Sprint die Liste des Ausgeschlossenen trotzdem verlängert: der
`board-check` läuft in dieser Session über **alle 16** Einträge fehlerfrei durch, auch über
`p3` und `p5`. Am Ticketbestand dieser Repos, wie er heute im Git steht, liegt der rote Lauf
also nicht. Das ist kein Beweis für die Umgebung, sondern eine Möglichkeit weniger.

**Testdeckung aufgeschlüsselt statt gezählt (L-2026-08-17g Regel 2).** 15 neue Tests sind
nicht 15 Belege: **6** fallen ohne die Korrektur um (Rückbau in einer Kopie geprüft), **4**
fallen gegen eine nachgestellte **falsche** Umsetzung um — `laeufe == 0` als Kriterium, das
Verzeichnis statt der Zusage, die Gruppe statt des Profils, die Profilprüfung vor der
Tag-Prüfung, jede einzeln nachgebaut —, **5** sichern unveränderte Normalfälle. Suite 471 →
**486**.

**Ehrlich zur Grenze.** Die HMI-Zeilen sind gegen den Quellcode gelesen und nicht in einem
Browser gesehen; Mission Control läuft am Host, nicht in dieser Sandbox. Dieselbe Grenze wie
bei SWR-105/107, und sie steht hier, statt in einer grünen Zahl unterzugehen (B027).

**Lessons sofort verankert (D005, noch in diesem Lauf):** **L-2026-08-17h** (eine leere Stelle
sieht immer nach „noch nicht" aus; die Tatsache für „nicht geliefert" ist die Zusage und nicht
ihr Nebenprodukt; eine vorhandene Redewendung erweitern schlägt eine neue erfinden; wer den
Wertebereich weitet, zieht die Leser im selben Commit mit; zu jedem verworfenen Weg gehört ein
Test, der ihn nachstellt) und **L-2026-08-17i** (ein Verschiebungsgrund hat eine Verfallszeit
und wird von dem Sprint geprüft, der die Sperre auflöst; „zu groß" heißt zerlegen, nicht
verschieben).

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** gesamt **250** (+2, beide aus der
Zerlegung), platform **6** (unverändert — `T-0006` hat nur den Status gewechselt), p11 **5**
(+2), pm **43** (unverändert); nicht geschlossen **15** — dieselbe Zahl wie in Sprint 3, und
das ist Zufall und kein Stillstand: zwei zu, zwei neu. Briefe **48**, davon **0 offen**. Matrix
**108 SWRs / 0 Lücken** (+1: SWR-108). **486 Tests** (vorher 471). `nicht_geplant: []`,
`widersprueche: []`.

**Die Vorhersage aus Sprint 3 ist weiterhin offen.** `platform` sollte im nächsten
`CI-STATUS.md` grün sein; ohne Hostlauf gibt es dazu nichts zu berichten. Sie bleibt stehen und
bleibt widerlegbar.

---

## Vorheriger Stand (Sprint 3, 2026-08-17)

**Sprint 3 (2026-08-17), der Lauf, in dem eine Entscheidung fällig war und eine Feldliste einen
Fehler fand.**

**Der Plan war klein und ist aufgegangen.** Sprint 3 hatte drei Sachaufgaben: die Entscheidung aus
`pm/T-0042`, den Widget-Vertrag, und den Blick auf die beiden Tickets, die auf einen Hostlauf
warten. Alle drei sind erledigt, zwei davon durch Arbeit und eines durch die ehrliche Feststellung,
dass es nichts zu tun gibt.

**`pm/T-0042` — warum keiner der vier Wege gewählt wurde.** Das Ticket beschrieb die Zwickmühle
korrekt: `platform` prüft `p0`/`p9`, die Projekt-Repos prüfen `platform`, alle werden im selben
Lauf gepusht. Die vier angebotenen Wege behandelten das als Reihenfolge- oder Wiederholungsfrage.
Es ist keine. **Die SWR↔Test-Matrix ist eine Aussage über alle Repos zur gleichen Zeit** — eine
CI, die je Repo läuft, sieht die anderen immer so, wie der Push sie hinterlassen hat, und kein
Push-Auftrag der Welt erzeugt Gleichzeitigkeit. Das Gate stand am falschen Ort, nicht in der
falschen Reihenfolge.

**Der Satz, der die Entscheidung trägt.** `abschluss.cmd` Schritt [2/5] fährt **dieselbe** Prüfung
über den vollständigen, gleichzeitigen lokalen Stand — **vor** dem Push, mit Abbruch. Für jeden
Push über `abschluss.cmd` konnte das Gate in der CI deshalb nur zweierlei sein: überflüssig (grün)
oder falsch (rot). Es hat in seiner Laufzeit **keinen** echten Befund erbracht, den [2/5] nicht
schon verhindert hätte — und zwei falsche in zwei beobachteten Pushes. Der Lauf checkt jetzt
**drei** Repos aus statt vierzehn.

**Der Preis steht an zwei Stellen, nicht an einer.** Ein Push an `platform`, der `abschluss.cmd`
umgeht, wird nicht mehr gegen die Matrix geprüft. Dieser Satz steht im Ticket **und im Kopf der
Workflow-Datei** — wer den Workflow liest, soll den Preis sehen, ohne ein Ticket zu suchen. Ein
„aufgeräumtes" Gate ohne benannten Preis wäre eine stille Schwächung.

**Und was bewusst stehen geblieben ist.** Der Katalog-Check in derselben CI hat dieselbe Bauart und
hat noch nie falsch rot gemeldet. Ihn auf theoretischen Verdacht mit abzuräumen wäre das Gegenteil
der Sorgfalt, die den Befund gefunden hat. Stattdessen **eine Zeile** in `abschluss.cmd`: `process`
geht vor `platform`, damit ist die häufigere Hälfte seines Rennens weg. (Das ist die einzige
Änderung an der in Sprint 1 rekonstruierten Datei, sauber kommentiert.)

**Der Widget-Vertrag — und warum er mehr war als Schreibarbeit.** `team-dashboard/T-0001` verlangte
vier Antworten: welche Felder, woher, was optional, wie versioniert. Die Antworten stehen in
`team-dashboard/vertrag/widget-vertrag-v1.yaml` (**normativ**, die einzige Stelle mit der
Feldliste) und `team-dashboard/docs/02-widget-vertrag.md` (die Begründung, die die Liste
ausdrücklich **nicht** wiederholt — zwei Listen wären B033, und das wäre eine schlechte erste
Arbeit für ein Team, dessen Zweck es ist, dass eine Seite dasselbe sagt wie ihre Quelle).

**Die wichtigste Frage war die leichteste.** *Woher kommen die Felder?* Aus der **vorhandenen**
Cockpit-Aggregation, aus keiner zweiten Quelle. Eine zweite Erhebung hätte Dashboard und Cockpit
auseinanderlaufen lassen — und sie wäre unnötig gewesen.

**Eine Annahme des Auftrags hat die Prüfung korrigiert.** Ticket und Team-Charter hielten fest,
kein Projekt liefere heute etwas Abgreifbares. Gegen den echten Bestand gehalten liefert
`aggregation.cockpit` für **alle 16** Projekte und Teams **dieselben 17 Felder**. Gefehlt hat nicht
die Lieferung, sondern die **Zusage**. Das ist eine gute Nachricht und macht P11 kleiner als
gedacht — sie steht hier, weil eine widerlegte Annahme genauso berichtenswert ist wie ein Fehler.

**⚠ B064 — und dass niemand danach gesucht hat, ist der Punkt.** Beim Feld-für-Feld-Abgleich gegen
den echten Payload meldeten `p11` und `p12` als ihre letzte Baseline **`p10-v1.0`**. `git tag`
beantwortet die Frage nach dem **Repository**, nicht nach dem Ordner; seit dem Monorepo-Beschluss
`pm/D003` liegen Projekte ab P10 als Ordner in `projects`. Das Cockpit nahm die letzte Zeile, wem
auch immer sie gehörte. **Kein fehlender Wert, ein falscher** — und nicht erst im geplanten
Dashboard, sondern seit P10 in Mission Control.

**Warum es so lange unentdeckt blieb.** Der Nachbar in derselben Funktion war **zufällig** richtig:
`einstufung` sucht nach `"<projekt>-v1.0"` und filtert damit implizit nach dem Projektnamen; nur
die Baseline-Zeile daneben las denselben Text ungefiltert. Eine geteilte Quelle mit zwei
Auflösungen — dieselbe Familie wie **B059**, dieselbe Lesson wie **L-2026-08-16m**. Dass die
Organisation diese Lesson schon hatte und den Fall trotzdem trug, ist der eigentliche Wert des
Befundes.

**Behoben und gegengeprüft.** Eine gemeinsame Funktion `aggregation.projekt_tags` für **beide**
Leser; aus dem Substring-Test wurde ein Präfix-Test. **Fünf Regressionstests** (Suite 463 →
**468**), darunter ausdrücklich der Fall, der die Korrektur **widerlegen** würde: `p0` trägt
`genesis-v1.0`, ein globaler Filter hätte ihm Baseline **und** Status `abgeschlossen` genommen.
**Gegenprobe über den echten Bestand** (Regel 3 aus L-2026-08-16h): der Altstand aus
`git archive HEAD`, gegen die tatsächlichen 16 Repos gestartet, meldet für `p11` und `p12`
weiterhin `p10-v1.0`; der Neustand meldet leer.

**Was der Vertrag nicht heilen konnte und deshalb als Ticket abgibt.** `SWR-096` verlangt, ein
nicht geliefertes Feld als „keine Daten" zu zeigen — und setzt damit voraus, dass man es von einer
echten Null unterscheiden kann. Bei drei Feldern kann man das heute nicht: **15 von 16** Einträgen
melden `kpi: {laeufe: 0}`, obwohl nur `p0` eine Run-Registry führt. Ein Widget, das diese Null
rendert, behauptet fünfzehnmal eine Messung, die es nicht gibt — in der Form, die am meisten nach
Fakt aussieht. Als `platform/T-0006` beauftragt (Sprint 4), **Weg bewusst offen**: drei Varianten
mit ihrem jeweiligen Preis stehen im Ticket. Bis dahin steht die Behelfsregel **an einer Stelle**,
in der YAML.

**Ehrlich zur Prüfbarkeit des Vertrags.** Gedeckt ist er heute durch **eine einmalige Gegenprobe**:
17 Feldnamen gegen den echten Payload aller 16 Einträge, keine Abweichung in beide Richtungen,
jedes Pflichtfeld überall vorhanden. Einen **laufenden** Test gibt es nicht — er gehört zu SWR-096
und damit zu P11, mit der Auflage, die YAML zu **lesen** statt die Liste in Python abzuschreiben.
Das offen zu sagen ist B027; es als „getestet" zu führen wäre B038.

**Zwei Tickets ohne Arbeit, mit Grund.** `platform/T-0004` (Netzweg der Jobs-Abfrage) und
`pm/T-0043` (welcher Schritt macht `p3`/`p5` rot) warten beide auf **denselben** Beleg: einen
`CI-STATUS.md`, der **nach** dem SWR-107-Commit (01:17) entstanden ist. Der letzte Hostlauf war
00:46. Beide auf Sprint 4, **keine Handlung nötig**. Für `T-0043` hat dieser Sprint die Liste des
Ausgeschlossenen trotzdem verlängert: die Workflow-Dateien von `p3`, `p5` und `p7` unterscheiden
sich **ausschließlich in Kommentarzeilen**, und keines der drei Repos hat eine zweite
Workflow-Datei. Kein Raten, nur eine Möglichkeit weniger.

**Kein `blocked`, obwohl blockiert.** `pm/T-0043` wartet auf einen Hostlauf, nicht auf ein Ticket
des **eigenen** Repos — und nur solche kann `blocked_by` ausdrücken (B047). Eine erfundene
pm-interne Sperre einzutragen, um ein Statusfeld zu bedienen, wäre eine Falschaussage im Board.
Dieselbe Entscheidung wie bei `p11/T-0003` im August.

**Lessons sofort verankert (D005, noch in diesem Lauf):** **L-2026-08-17e** (B064 — wechselt der
Behälter, wechselt die Bedeutung jeder Frage an ihn; ein Nachbar, der richtig aussieht, kann aus
Versehen richtig sein), **L-2026-08-17f** (B061-Auflösung — vor dem Justieren eines Gates kommt
die Frage nach seinem Ort; wer ein Gate entfernt, schreibt auf, welcher echte Befund verloren
geht) und **L-2026-08-17g** (die Gegenprüfung prüft auch die **Begründung** — vier Sätze dieses
Laufs waren nachweislich falsch; Testdeckung wird durch Rückbau bewiesen, nicht durch Zählen).

## ⚠ Die unabhängige Gegenprüfung hat vier falsche Sätze dieses Laufs gefunden

Nach dem ersten Commit lief die Gegenprüfung (L-2026-08-16m). Die Suite war grün. Sie fand elf
Punkte — bemerkenswert ist ihre **Art**: die schwersten waren keine Codefehler, sondern
**Behauptungen dieses Laufs über den eigenen Code**.

* *„Aus dem Substring-Test wurde ein Präfix-Test."* **Falsch.** Das galt nur für den Zeilenfilter;
  `einstufung` suchte weiter im ganzen Text **inklusive Tag-Annotation**. Nachgestellt: ein
  Zwischenstand `p11-v0.9` mit der Nachricht *„Vorbereitung auf p11-v1.0"* wies das Projekt als
  **abgeschlossen** aus, ohne dass es je eine Baseline hatte. Der Satz stand **dreimal** — im
  Ticket, in der Doku und in einem Test-Docstring. **Jetzt behoben:** Vergleich Name gegen Name.
* *„Getragen wird das von `preflight.py` und Schritt [2/5]."* **Falsch.** `preflight.py` kennt die
  Matrix nicht. Das ausgesprochene Sicherheitsnetz war doppelt so groß gemalt wie das echte —
  ausgerechnet in dem Absatz, der den Preis einer Gate-Entfernung ehrlich nennen sollte.
* *„Fünf Regressionstests."* Einer davon war **ohne** die Korrektur grün. Durch Rückbau in einer
  Kopie geprüft: 6 von 8 fallen um, einer ist eine Gegenprobe, einer bewies nichts — er ist jetzt
  um die fehlende Zusicherung ergänzt.
* *„Teams haben kein G4, also keine Baseline."* Am echten Payload **widerlegt**: `platform` ist
  `festes-team` und trägt eine. Ein Widget, das dem ersten Vertragsentwurf gefolgt wäre, hätte
  einen real vorhandenen Wert unterdrückt.

**Dazu ein weiterer echter Fehler am selben Feld — B065.** „Letzte Baseline" war die
**lexikografisch** letzte, nicht die jüngste: `platform` zeigte `p9-v1.0`, während `p10-v1.0`
dreieinhalb Stunden jünger war, und `p10-v1.10` stünde vor `p10-v1.2`. Behoben
(`--sort=creatordate`), mit einem Test, der ohne die Änderung umfällt.

**Die widerlegten Sätze stehen wörtlich als widerlegt in den Tickets** und wurden nicht
stillschweigend ersetzt — sonst fehlt dem nächsten Leser der Hinweis, welche Art Satz hier schon
einmal ungeprüft durchging. Verankert als **L-2026-08-17g**. Suite **463 → 471**.


**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** platform **6** Tickets (+2), pm **43**
(unverändert — `T-0042` hat nur den Status gewechselt), gesamt **248** (+2); nicht geschlossen
**15** (unverändert: zwei zu, zwei neu). Briefe **48**, davon **0 offen**. Matrix **107 SWRs / 0
Lücken** — unverändert, und das ist richtig: dieser Sprint hat keine neue Anforderung gebracht,
sondern einen Fehler behoben und einen Vertrag geschrieben. **471 Tests** (vorher 463).
`nicht_geplant: []`, `widersprueche: []`.

**Eine Vorhersage, damit sie widerlegbar bleibt.** Nach der Änderung sollte `platform` im nächsten
`CI-STATUS.md` **grün** sein. Trifft das nicht ein, ist die Diagnose aus `pm/T-0042` widerlegt und
das Ticket wird wiedereröffnet — das steht so in der DoD und nicht nur hier.

---

## Vorheriger Stand (Sprint 2, 2026-08-17)

## Das Wichtigste (Stand Sprint 2, 2026-08-17)

1. **Die CI-Statusprüfung aus Sprint 1 hat beim ersten Lauf drei rote Repos gefunden** — `p3`,
   `p5`, `platform`. `p3` und `p5` waren seit dem 16.08. 07:00 rot: rund **siebzehn Stunden
   unbemerkt**. Das ist der erste Ertrag von SWR-105 und die Rechtfertigung des Tickets.
2. **Vier Tickets geschlossen** (`platform/T-0003`, `pm/T-0010`, `pm/T-0013`, `pm/T-0026`) — alle
   mit dem Fremdnachweis, auf den sie seit dem 16.08. warteten.
3. **Eine plausible Erklärung wurde widerlegt statt übernommen.** Dass `p3`/`p5` an der
   Board-Formatänderung liegen, klang zwingend. `p7` trägt denselben Commit-Zeitpunkt **auf die
   Sekunde**, dieselbe Workflow-Datei, dieselbe Formatänderung — und ist **grün**. Ohne die
   Gegenprobe wären zwei Tickets mit falscher Begründung geschlossen worden (L-2026-08-17c).
4. **`platform` ist rot, weil zwei Gates einander auschecken** und im selben Lauf gepusht werden.
   Es gibt **keine** Push-Reihenfolge, die beide grün macht (B061, `pm/T-0042`). Nachgestellt:
   104 SWRs / 1 Lücke gegen 105 / 0, je nach Stand von `p0`/`p9`.
5. **463 Tests grün**, Matrix **107 SWRs / 0 Lücken**, Preflight STARTKLAR, kein offener Brief
   (48 Briefe), unterminiert 0, überfällig 0.

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Sprint 2 (2026-08-17), der Lauf, in dem die CI-Prüfung zum ersten Mal etwas gefunden hat.**

**Der Plan war klein, der Ertrag nicht.** Sprint 2 hatte eine Aufgabe: den ersten `CI-STATUS.md`
auswerten und die vier Tickets schließen, die darauf warteten. Der Bericht (Stand 00:31, **15
Abfragen**, `budget_erschoepft: false`) meldete acht Repos grün **für ihren eigenen Commit**,
`team-dashboard` als „kein CI zu erwarten" — und **drei rot**.

**Was geschlossen wurde und woran.** `pm/T-0010`: acht grüne board-checks, darunter zwei mit
Commits **nach** Mitternacht — der `-I "^Stand:"`-Fix trägt über die Datumsgrenze. `pm/T-0013`:
Kriterium 2 erfüllt, die Reihenfolgeregel tut für den board-check, was sie soll. `pm/T-0026`: der
`projects`-Checkout ist als Ursache **ausgeschlossen** (in beiden Rekonstruktionen vorhanden).
`platform/T-0003`: alle fünf DoD-Punkte belegt, **Netzweg nachgewiesen**.

**Die Stichprobe wurde stärker erbracht als vorgesehen.** Der Auftraggeber sollte prüfen, ob das
Urteil des Berichts mit der Actions-Seite übereinstimmt. Statt dessen wurde das rote Urteil über
`platform` **unabhängig rekonstruiert**: derselbe Commit, derselbe Repo-Satz, zwei Stände von
`p0`/`p9` — vor dem Push Exit 1 mit *104 SWRs, 1 Lücke (SWR-105)*, nach dem Push Exit 0 mit
*105 SWRs, 0 Lücken*. Ein roter Befund, der sich auf einem zweiten, unabhängigen Weg herstellen
lässt, ist besser belegt als einer, den jemand angesehen hat.

**Der Befund dahinter ist struktureller Art (B061).** `platform` prüft mit seinem Matrix-Gate
`p0`/`p9`; die Projekt-Repos prüfen mit ihrem board-check `platform`. Alle werden im selben Lauf
gepusht — wer zuerst geht, sieht den anderen alt. `pm/T-0013` hat die eine Hälfte gelöst und die
andere erzeugt, ohne dass es auffiel, weil der Beleg fehlte. **Die Asymmetrie entscheidet:** das
Board-Format ändert sich zweimal im Projektleben, eine neue Anforderung entsteht in fast jedem
Sprint — die heutige Reihenfolge macht also den Regelfall rot. Vier Wege mit ihrem jeweiligen Preis
stehen in `pm/T-0042`; entschieden wird in Sprint 3, weil die Behebung `abschluss.cmd` oder ein
Gate ändert und `abschluss.cmd` in Sprint 1 rekonstruiert werden musste (B025).

**Noch im selben Sprint bestätigt — die Diagnose war eine Vorhersage.** Der Host-Wächter pushte um
**00:46** erneut und erzeugte einen zweiten Bericht. `platform` ist **wieder rot**, jetzt für den
Commit `9c25a1f6` (SWR-106) statt `34a44d57` (SWR-105). Vorher nachgerechnet, hinterher
eingetroffen: die Lücke ist **jedes Mal genau die Anforderung des jeweiligen Sprints** (105 SWRs /
1 Lücke gegen 106 / 0). Zwei von zwei beobachteten Pushes rot, beide aus demselben Grund. Damit ist
die Häufigkeitsannahme aus `pm/T-0042` keine Schätzung mehr, und die Kosten des Nichtstuns sind
höher als die jedes der vier Lösungswege.

**Wo nicht geraten wurde.** Für `p3`/`p5` lag die Erklärung fertig da und ist widerlegt: gegen
**jede** `board.py`-Fassung seit dem 16.08. sind `p3`, `p5` **und** `p7` grün, gegen die Fassung
davor alle drei rot. Es gibt keine Version, die p3/p5 rot und p7 grün macht; alle 16 Repos
regenerieren ihre `BOARD.md` heute byte-gleich. Was bleibt, ist ein Workflow-Schritt, den die
Sandbox nicht nachstellen kann. Der Befund steht als `pm/T-0043` **ohne Ursachenbehauptung**, mit
dem Vermerk, dass die Behebung **Klasse A** wäre (Zugang), falls es das Secret ist — dann geht sie
als Inbox-DR an den Auftraggeber und wird nicht vom Team entschieden.

**Gebaut im selben Sprint: SWR-107 (`platform/T-0004`).** Der Bericht sagte `ROT` und nicht
**warum** — und ließ damit genau die Lücke offen, die er schließen sollte: ein Mensch hätte doch
wieder die Actions-Seite öffnen müssen. `GET /repos/{slug}/actions/runs/{id}/jobs` ist dieselbe
anmeldefreie API-Familie; der Bericht nennt jetzt **Job und Schritt**. **19 neue Tests** (Suite 444 → **463**, davon 8 aus der Gegenprüfung), alle mit injizierter Abruffunktion. Die Nachfrage läuft **nach** der Warteschleife
(rot ist ein Endzustand), **einmal je rotem Repo**, gegen **dasselbe** Budget; scheitert sie,
bleibt das Repo **rot** und der Bericht sagt „Schritt unbekannt" — eine Diagnose, die einen Befund
verschluckt, wäre schlimmer als keine (B038). `in_review`, weil der Netzweg der Jobs-Adresse erst
der nächste Hostlauf belegt; das geschieht **ohne Handlung**.

**Guardrail 2 erneut bestätigt.** Der Versuch, die Actions-API aus der Sandbox zu erreichen,
scheiterte. Es wurde **kein** Umweg gesucht — die Regel steht, und die Konsequenz (Netzweg
unbelegt) steht im Ticket statt in einer grünen Zahl.

**Lessons sofort verankert (D005, noch in diesem Lauf):** **L-2026-08-17b** (B061) und
**L-2026-08-17c** (B062 — *„Was tut der Leser als Erstes, nachdem er das gelesen hat, und kann der
Melder ihm das abnehmen?"* sowie *„Welcher Nachbar müsste nach dieser Erklärung dasselbe Ergebnis
haben — und hat er es?"*).

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** pm **43** Tickets (+2), platform **4**
(+1), gesamt **246** (+3); nicht geschlossen **15** (vorher 16). Briefe **48**, davon **0 offen**.
Matrix **107 SWRs / 0 Lücken** (vorher 106), **463 Tests** (vorher 444). `nicht_geplant: []`,
`widersprueche: []`.

**Offen und benannt:** `team-dashboard/T-0001` trägt `takt: je-session` **und**
`geplant_sprint: 3` — nach der eigenen Regel aus SWR-106 eine Doppelaussage (B033). Die
Widerspruchsprüfung schlägt nicht an, weil keine Frist verletzt wird. Als Feldkorrektur in der
Agenda vermerkt, kein eigenes Ticket.

---

## Vorheriger Stand (Sprint 1, 2026-08-17)


## Das Wichtigste (Stand Sprint 1, 2026-08-17)

1. **Die Planeinheit ist ab jetzt der Sprint, nicht der Kalendertag** (Auftraggeber, 2026-08-17).
   Ein Sprint = ein Routine-Lauf, Takt stündlich. Wir sind in **Sprint 1**; alle **17 offenen
   Aufgaben** tragen eine Sprintnummer oder einen Takt. Verankert als **SWR-106**.
2. **Erstmals wartet nichts mehr auf den Menschen.** `pm/T-0034` geschlossen (die Digests im Repo
   belegen IMAP und Ollama), die drei CI-Tickets laufen jetzt über **SWR-105**.
3. **444 Tests grün**, Matrix **106 SWRs / 0 Lücken**, Preflight STARTKLAR, kein offener Brief
   (48 Briefe, 5 in diesem Lauf beantwortet).
4. **⚠ `abschluss.cmd` wurde versehentlich geleert und aus dem Protokoll rekonstruiert.** Jeder
   Schritt einzeln nachgefahren, gleiche Ausgaben — aber nicht zeichengleich. Bitte gegen eine
   Vorgängerversion vergleichen.
5. **`frist` bleibt neben `geplant_sprint`** — auf Wunsch des Auftraggebers. Die bekannte Schwäche
   dieser Wahl wird geprüft statt vorausgesetzt (B060 / L-2026-08-17a).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Sprint 1 (2026-08-17), erster Lauf nach der Umstellung auf Sprintplanung.**

**Was sich grundsätzlich geändert hat.** `pm/D006` erklärt seit dem 16.08. jeden Routine-Lauf zum
Sprint — geplant wurde trotzdem auf Kalenderdaten. Bei stündlichem Takt sind das rund **24 Sprints
am Tag**; „23.08." wäre etwa Sprint 150 gewesen, ein Abstand, den niemand umrechnet. Ab jetzt trägt
jedes offene Ticket ein `geplant_sprint` — oder ein `takt`, das sagt, dass es in **jedem** Sprint
läuft (die fünf Dauerläufer bekommen bewusst keine Nummer, sonst stünde dieselbe Aussage zweimal).

**Der Zähler ist eine Datei und keine Schätzung.** `pm/management/sprints.jsonl`, eine Zeile je
Sprint, nur angehängt, **idempotent über eine Laufkennung**. Nicht aus der Git-Historie abgeleitet:
eine Session schreibt mehrfach, Commits sind keine Läufe (**B056**, belegt mit 42 Commits auf rund
30 Läufe). Rückwirkend wird nicht nummeriert — die Läufe des 16.08. ließen sich nur schätzen.

**Der Horizont ist ehrlich beschriftet.** Sprint 1–3 sind fest, ab Sprint 4 ist die Nummer eine
**Reihenfolge**. Dieselbe Zahl, aber mit ausgesprochener Verbindlichkeit statt suggerierter.

**Die Entscheidung des Auftraggebers, die das Team anders empfohlen hatte.** `frist` und
`geplant_sprint` laufen **parallel**. Das Team hatte diese Option als die schwächste bezeichnet
(zwei Angaben zu „wann ist es dran" driften, B033). Sie wurde umgesetzt **und abgesichert**: beide
Felder beantworten schriftlich **zwei verschiedene Fragen** — Zusage nach außen gegen Lauf des
Teams —, und `board.sprint_widerspruch` meldet jedes Ticket, dessen geplanter Sprint **auch bei
ununterbrochenem Takt** nach seiner Frist läge, über der Plantabelle. Aktuell: keiner. Verankert
als **L-2026-08-17a**; dort steht auch, warum der Melder nur den günstigsten Fall prüft (ein
Melder, der Risiken als Fehler ausgibt, erzieht zum Wegsehen).

**Gegenprobe über den echten Bestand.** Der Altstand aus `git archive HEAD`, gegen die **neue**
Plandatei gestartet, meldet **16 von 17 Zeilen als „ohne Zustand"** — grau, also ungeplant — und
kennt `sprint_nr` nicht; der Neustand meldet 0 und `Sprint 1 · Takt 60 Min`. Das belegt den
Schaden und nicht bloß ein fehlendes Modul (Regel 3 aus L-2026-08-16h). Und beim Zwischenstand hat
der Bestandsabgleich aus SWR-103 `pm/T-0041` selbst als **nicht geplant** gemeldet — die Prüfung
hat die Umstellung überwacht, die sie erweitert.

**Vorher im selben Lauf.** `platform/T-0003` / **SWR-105** gebaut: die CI-Statusprüfung ohne
Zugangsdaten (die Repos sind öffentlich, die Actions-API antwortet unangemeldet — es war also
kein Klasse-A-Vorgang). Fünf Briefe beantwortet; `pm/T-0034` geschlossen, weil die Digests im Repo
IMAP und lokales Ollama **belegen** statt sie zuzusagen.

**⚠ Ein Fehler dieses Laufs, unverstellt.** Beim Einbau von Schritt [5/5] hat ein fehlgeschlagener
Schreibbefehl `abschluss.cmd` **geleert**. Die Datei liegt am Wurzelverzeichnis und damit in keinem
Repo — es gab nichts zurückzuholen. Sie ist aus `abschluss-auto.log` und dem zuvor wörtlich
gelesenen Push-Abschnitt **rekonstruiert**; jeder Schritt wurde einzeln gegen die echten Skripte
nachgefahren und liefert dieselben Ausgaben wie im Protokoll. Sie tut dasselbe, ist aber **nicht
zeichengleich**. Ein Kopf-Kommentar in der Datei sagt das, und die Bitte an den Auftraggeber, eine
Vorgängerversion zu vergleichen, steht in der Agenda und im Brief `pm/N-0036`.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** pm **41** Tickets (+1: `T-0041`),
platform **3** (+1: `T-0003`); Briefe organisationsweit **48** (+5), davon **0 offen**. Matrix
**106 SWRs / 0 Lücken** (vorher 104), **444 Tests** (vorher 380 zu Beginn des Abends).

---

## Vorheriger Stand (2026-08-16 23:06)

## Das Wichtigste (Stand 2026-08-16 23:06)

1. **`pm/T-0032` ist erledigt — beide Teile.** Der Wunsch aus `pm/N-0025` („wiederkehrende aufgaben
   müssen auch terminiert werden … z.b. jeden tag, woche um 14 Uhr") ist gebaut: `takt:
   taeglich@14:00`, `woechentlich@Mo-14:00`, Feld `zuletzt_erledigt`, Meldung in der Cockpit-Kachel
   als **„überfällig seit HH:MM"**. Verankert als **SWR-104**.
2. **Vorgezogen vom 19.08.** — nach der Zerlegung des Vorlaufs trug das Ticket keine Denkarbeit
   mehr und hielt die früheste Frist der Organisation. Die früheste **Team**-Frist ist jetzt der
   23.08.
3. **402 Tests grün** (vorher 380), Matrix **104 SWRs / 0 Lücken**, Preflight STARTKLAR,
   `unterminiert = 0`, `überfällig = 0`.
4. **⚠ Zwei Befunde — und der zweite kam von außen.** B059 fand eine **unabhängige
   Gegenprüfung** bei **grüner Suite**: eine `frist` mit Uhrzeit hätte die ganze Cockpit-Seite
   mitgerissen, der Ticket-Editor hätte den neuen Takt beim Speichern gelöscht. Beides behoben.
   B058 beim Bauen: die geteilte Ampelregel rechnete in **Tagen** und hätte den um
   15:00 versäumten 14:00-Takt als „gelb — heute fällig" ausgewiesen. Sie liegt jetzt auf Momenten;
   für reine Datumsfristen ist sie über **961** Tag-gegen-Tag-Vergleiche nachweislich unverändert.
5. **Für dich heute: `pm/T-0034`** (17.08., nur am Host); ein Blick auf die GitHub-Actions-Seite
   schließt drei weitere Tickets (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Routine-Session 23:06–23:5x, gefahren als Genesis-Gesamtsprint (D004/D006).** Briefkasten beim
Start: **43 Briefe, kein offener**; die Zweitprüfung am Sessionende bestätigte das (**B036 zum
zehnten Mal gefahren**, zum dritten Mal in Folge ohne Fund). Inbox beim Start und am Ende leer.
**Kein überfälliges Ticket.**

**Sprint-Planning (Kernpflicht nach `pm/D006`):** **241 Tickets** aller 16 Repos gesichtet — 220
`done`, 4 `rejected`, **14 `open`, 3 `in_review`**. Die 17 nicht geschlossenen stehen vollständig
in `pm/management/sprint-aktuell.md`, je Zeile mit Rolle, Fälligkeit, Status und Grund. Keine
Auswahl, keine Kürzung. **Organisationsweit `unterminiert = 0` und `überfällig = 0`** — zum zweiten
Mal in Folge.

**Warum dieser Sprint `pm/T-0032` genommen hat.** Die Auswahl war nach der Vorsession nicht mehr
frei: sie hatte das Ticket **zerlegt statt zum vierten Mal verschoben** und schriftlich
festgehalten, dass ab dort keine Denkarbeit mehr darin steckt. Ein Ticket mit der frühesten Frist,
ohne offene Vorfrage und mit fertiger Abgrenzung noch einmal liegen zu lassen, hätte genau das
Muster fortgesetzt, gegen das die Zerlegung geschrieben wurde (B043/B049). Die `23.08.`-Tickets
ändern dagegen alle das `BOARD.md`-Format oder berühren Klasse A und gehören gebündelt in einen
eigenen Lauf (B053/B025).

**Was jetzt anders ist.** Das Feld `takt` nimmt eine Uhrzeit an — `taeglich@HH:MM` und
`woechentlich@<Mo–So>-HH:MM`, und **nur** diese beiden: für `monatlich@…` gibt es keine Regel,
welcher Tag gemeint wäre, und sie zu erfinden wäre Raten. Ein neues Feld `zuletzt_erledigt` trägt
den Fortschritt eines Takt-Tickets; **fehlt es, ist es unlesbar oder trägt es nur ein Datum ohne
Uhrzeit, gilt der früheste vertretbare Zeitpunkt** — im Zweifel fällig, nie frisch (dieselbe
Vorsichtsregel wie `session.stille`). Die Cockpit-Kachel listet fällige Takte neben den
überfälligen Fristen und nennt den **übersprungenen** Termin.

**Der Takt ist ausdrücklich kein Scheduler.** Die Abgrenzung aus Teil 1 trägt: *was ohne laufende
Session feuern muss, gehört zum Host-Scheduler; was nur bemerkt werden muss, ans Ticket.* Läuft
keine Session, feuert nichts — und die Anzeige sagt „überfällig seit HH:MM" statt „erledigt". Das
ist die ehrliche Grenze der Umsetzung (B038), keine Schwäche, die man verschweigt.

**⚠ Befund B058 — die geteilte Regel hatte die falsche Auflösung.** Teil 1 hatte entschieden, den
abgeleiteten Termin durch die **bestehende** `board.frist_ampel` zu schicken („eine Ampelregel,
zwei Quellen"; eine zweite Rechnung wäre B033). Genau das wurde gebaut — und war beim ersten Test
falsch: die Funktion verglich **Kalendertage**. „Heute 14:00" ist um 15:00 verstrichen, der **Tag**
aber nicht; die geteilte Regel hätte ausgerechnet den **versäumten** Takt als „gelb, heute fällig"
ausgewiesen. Kein Tippfehler: die Funktion beantwortete korrekt die Frage, die sie kannte, und
wurde nach einer anderen gefragt — dieselbe Familie wie **B057** und **B053**. Die Regel liegt
jetzt auf **Momenten**, und dass sie für reine Datumsfristen dasselbe sagt wie vorher, wird
**bewiesen statt behauptet**: ein Test vergleicht beide Fassungen Tag für Tag gegen jeden Bezugstag
desselben Monats (**961** Vergleiche). Die naheliegende Abkürzung — den Tagesbezug des Cockpits
einfach als Moment zu behandeln — wurde **nicht** genommen: sie hätte `taeglich@23:00` jeden
Morgen als fällig gemeldet, und Vorsicht, die zur Fehlmeldung wird, erzieht zum Wegsehen.
Verankert als **L-2026-08-16l**.

**⚠ Zweiter Befund B059 — gefunden von einer Gegenprüfung, nicht von der Suite.** Nach dem Commit
prüfte eine **unabhängige** Instanz die Änderung und fand **zwei** echte Fehler, während **alle 400
Tests grün waren**. Beide vom selben Muster: die geteilte Regel wurde erweitert, **zwei Nachbarn
lasen denselben Wert weiter mit der alten Auflösung.** (1) `aggregation.cockpit` filterte über
`ist_ueberfaellig` (akzeptiert seit SWR-104 eine Uhrzeit) und rechnete die Tage-über daneben mit
`date.fromisoformat` (nur reines Datum) — `frist: 2026-08-15 14:00` hätte einen `ValueError`
geworfen, **erst nach Ablauf des Termins**, und über `cockpit_alle` hätte **ein** Ticket in **einem**
Repo die **gesamte** Cockpit-Seite mitgerissen, nach außen als irreführendes
`HTTP 404 „unbekanntes Projekt"`. (2) Der Ticket-Editor baut sein Auswahlfeld aus einem festen
Vokabular; `taeglich@14:00` stand nicht darin — der Browser wäre auf „einmalig" zurückgefallen und
das Speichern eines **beliebigen anderen Feldes** hätte den Takt **stillschweigend gelöscht**
(B051 + B038). Beides behoben, je ein Regressionstest, Gegenprobe gegen den Commit, der den Fehler
trug. Verankert als **L-2026-08-16m**: wer eine geteilte Regel erweitert, muss ihre **Nachbarn**
mitziehen; zu jedem neuen Wertebereich gehört ein Test am **alten** Feld mit dem **neuen** Wert;
und eine grüne Suite ersetzt keinen fremden Blick — der gehört als **letzter Schritt** zur
Änderung, nicht als Zugabe.

**Gegenprobe über den echten Abrufweg, nicht über einen Import** (Regel 3 aus L-2026-08-16h).
Dieselbe Testwelt, dasselbe Ticket (`takt: taeglich@14:00`, `zuletzt_erledigt: 2026-08-15 14:30`),
beide Server antworten auf `GET /api/cockpit` mit **HTTP 200** — der Server aus `git archive HEAD`
meldet `ueberfaellig: []`, `unterminiert: 0` und **kein Feld** `takt_faellig`. Das Ticket sah über
die HMI **kerngesund** aus, während sein 14:00-Termin seit Stunden versäumt war. Zweite Gegenprobe
über die **Skript-Route**, die auch die CI fährt: `board.py --check` endet im Altstand mit
**exit 1** (*„ungültiger takt: taeglich@14:00"*), im Neustand mit **exit 0** — der Wunsch aus dem
Brief war vorher nicht nur unbeantwortet, er war **nicht aufschreibbar**.

**Nicht als getestet geführt: Kachelposition und Telefondarstellung.** Die Organisation hat **402
Python-Tests und null JS-Tests**; „JS-Frontend-Tests" ist Pool-Kandidat #8 und nicht beauftragt.
Der Nachweis ist eine **Stichprobe des Auftraggebers** und steht als solche im Ticket und in der
Agenda — das offen zu sagen ist B027, es als „getestet" zu führen wäre B038.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** **pm 40 Tickets** (unverändert —
`T-0032` hat den Status gewechselt, es kam keins dazu), offene pm-Tickets **12 → 11**; Briefe
organisationsweit **43** (unverändert), davon **0 offen**. Matrix **104 SWRs / 0 Lücken** (vorher
103), **402 Tests** (vorher 380), Architektur-Gate grün. Fremde Änderungen: nur die bekannte
`team-mail`-Anzeige (`digest/2026-08-16-woche-digest.md`, `git diff --quiet` = 0) — der
Index-Refresh aus R7, erneut geprüft, erneut kein Commit.

**⚠ Heute fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein IMAP/Ollama
in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`, terminiert auf
18.08.

---

## Vorheriger Stand (2026-08-16 22:19)

## Das Wichtigste (Stand 2026-08-16 22:19)

1. **Erster echter Gesamtsprint nach `pm/D006`.** Alle **241 Tickets aller 16 Repos** gesichtet;
   **18 offene Aufgaben, alle terminiert** — 6 in diesem Sprint, 5 warten auf dich, 11 mit Datum
   und Grund im Ticket. Der Plan steht in `pm/management/sprint-aktuell.md`.
2. **Diese Tabelle steht ab jetzt in Mission Control** — Cockpit, Kachel „Sprint aktuell", direkt
   unter „Letzte Session". `pm/T-0016` ist **erledigt**.
3. **Erstmals hat die Organisation kein unterminiertes und kein überfälliges Ticket mehr**
   (`unterminiert = 0` über alle Kacheln).
4. **`pm/T-0032` wurde zerlegt statt zum vierten Mal verschoben.** Die Abgrenzung ist geschrieben,
   der Bau bleibt der 19.08. **380 Tests grün** (vorher 353), Matrix **103 SWRs / 0 Lücken**.
5. **Für dich heute: `pm/T-0034`** (17.08., nur am Host); ein Blick auf die GitHub-Actions-Seite
   schließt drei weitere Tickets (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Routine-Session 22:19–23:05, gefahren als Genesis-Gesamtsprint (D004/D006).** Briefkasten beim
Start: **43 Briefe, kein offener**; die **Zweitprüfung am Sessionende bestätigte das** — weiterhin
43, keiner offen (**B036 zum neunten Mal gefahren**, zum zweiten Mal in Folge ohne Fund). Inbox
beim Start und am Ende **leer und beweisbar nichts Unverbuchtes** — gegen die DR-Rohdaten geprüft
(Ablaufregel aus B047): **44 Decision Requests, alle `done`**. **Kein überfälliges Ticket.**

**Was diese Session anders macht als die vorigen: sie hat geplant, bevor sie gebaut hat.** Mit
`pm/D006` ist jeder Routine-Lauf ein vollwertiger Sprint über das **gesamte** Projekt Genesis. Die
Kernpflicht ist nicht mehr „arbeite ab, was anliegt", sondern „**sichte alle offenen Aufgaben aller
Repos und terminiere jede einzelne**". Gesichtet: **241 Tickets** — 219 `done`, 4 `rejected`,
**15 `open`, 3 `in_review`**. Die 18 nicht geschlossenen stehen **vollständig** im Plan, je Zeile
mit Rolle, Fälligkeit, Status und Grund. Keine Auswahl, keine Kürzung.

**⚠ Und genau dieses Sichten hat sofort etwas gefunden.** `pm/T-0016` — `prio: hoch`,
`change-request`, **ohne Frist**, ohne `takt` — stand in **keiner** der drei Agendalisten und war
das **einzige unterminierte Ticket der Organisation** (`cockpit_alle`: `unterminiert = 1`). Das ist
der **vierte** Auftritt von **B049**: die Eskalationsregel B044 sieht nur Tickets **mit** Frist,
und der einzige Melder für den Rest ist eine Zahl je Kachel, die niemand als Summe liest. **Die
Pointe:** getroffen hat es den CR, der die Workflow-Sicht liefern soll. Der Vorgang, der die
Unsichtbarkeit beheben sollte, war selbst unsichtbar. Er wurde terminiert (Frist 16.08.) und in
diesem Sprint **gebaut und geschlossen**.

**Was jetzt anders ist.** Neues Modul `platform/backend/sprint.py`, neuer Endpunkt
`GET /api/sprint`, Kachel **„Sprint aktuell"** direkt unter „Letzte Session" im Cockpit. Gelesen
wird die Datei, die die Session ohnehin schreibt — **kein zweiter Plan** (eine zweite Quelle wäre
B033 und würde irgendwann abweichen). Der Zeitstempel kommt aus dem **Git-Commit**, und die
Staleness-Regel („seit HH:MM keine Session") wird aus `session.stille` **importiert**, nicht
abgeschrieben — dieselbe Falle, dieselbe Regel, **ein** Ort.

**Der Teil, der mehr tut als abschreiben — und der Grund, warum er drinsteht.** Die Plantabelle ist
von Hand geschrieben. Sie *muss* es sein: welches Ticket in diesen Sprint geht, ist eine
**Entscheidung** des PM und hat im Ticket kein Feld. Genau darum kann sie vom Bestand abdriften —
ein Ticket, das nach dem Schreiben entsteht, fehlt im Plan und fällt niemandem auf. Die Sicht
vergleicht deshalb den Plan **gegen alle entdeckten Repos** und meldet jedes offene Ticket ohne
Planzeile (`nicht_geplant`), **über** der Tabelle, nicht darunter. Eine Sicht, die nur wiedergibt,
was ihr vorgelegt wird, hätte den Befund oben grundsätzlich nicht finden können.

**⚠ Befund B057 — der Zähler widersprach dem Klartext derselben Datei.** Beim **ersten Lauf gegen
den echten Plan** meldete er `wartet_auf_mensch = 1`, während oben in derselben Datei **fünf**
Aufgaben als „wartet auf eine Handlung am Host" standen. Kein Tippfehler, ein Denkfehler: **Termin
und Zuständigkeit sind zwei Fakten.** `pm/T-0034` trägt ein Datum (17.08.) **und** wartet auf den
Host; wer beides in *einen* Zustand faltet, wirft eine der Aussagen weg. **Alle 22 Tests der ersten
Fassung waren grün**, weil die Testdaten dieselbe Annahme trugen wie der Code — gefunden hat es
allein der Lauf gegen den **Bestand**, wörtlich Regel 1 aus L-2026-08-16h. Die Zahl liegt jetzt
**quer** zur Zerlegung und wird aus Fälligkeits- **und** Statusspalte gelesen. Verankert als
**L-2026-08-16j**; der B049-Fall als **L-2026-08-16k**.

**`pm/T-0032` zerlegt statt zum vierten Mal verschoben.** Die Vorsession hatte schriftlich
zugesagt, dass die nächste freie Session `T-0032` nimmt und die Abgrenzung **schreibt statt baut**
— die Begründung für den Aufschub hatte sich zum dritten Mal wortgleich wiederholt (B043/B049).
Eingelöst: die Trennlinie steht — *was ohne laufende Session feuern muss, gehört zum
Host-Scheduler; was nur bemerkt werden muss, ans Ticket* —, damit ist `takt@HH:MM` **keine dritte
Taktlogik**, sondern eine Fälligkeitsfrage. Die vier offenen Punkte sind entschieden (auswertend
ist die ohnehin laufende Session; ein fehlendes `zuletzt_erledigt` gilt als **fällig**, nie als
frisch; der abgeleitete Termin geht durch **dieselbe** `board.frist_ampel`; bei geschlossener App
sagt die Anzeige „überfällig seit HH:MM" und nicht „erledigt"). **Teil 2 bleibt der 19.08. — jetzt
ohne offene Vorfrage.**

**Gegenprobe über den echten Abrufweg, nicht über einen Import.** Der Server aus
`git archive HEAD` (Altstand), gegen dieselbe Plandatei gestartet, beantwortet `GET /api/sprint`
mit **HTTP 404 „unbekannter Endpunkt"** — während `GET /api/session` im selben Lauf **200**
liefert. Das belegt den Schaden und nicht bloß ein fehlendes Modul (Regel 3 aus L-2026-08-16h).

**Nicht als getestet geführt: die Kachelposition.** Die Organisation hat **380 Python-Tests und
null JS-Tests**; „JS-Frontend-Tests" ist Pool-Kandidat #8 und nicht beauftragt. Der Nachweis ist
eine **Stichprobe des Auftraggebers** und steht als solche im Ticket und in der Agenda — das offen
zu sagen ist B027, es als „getestet" zu führen wäre B038.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** **pm 40 Tickets** (unverändert —
`T-0016` hat den Status gewechselt, es kam keins dazu), offene pm-Tickets **13 → 12**; Briefe
organisationsweit **43** (unverändert), davon **0 offen**. Matrix **103 SWRs / 0 Lücken** (vorher
102), **380 Tests** (vorher 353), Architektur-Gate grün. **Organisationsweit erstmals
`unterminiert = 0` und `überfällig = 0`.** Fremde Änderungen: nur die bekannte `team-mail`-Anzeige
(`digest/2026-08-16-woche-digest.md`, `git diff --quiet` = 0) — der Index-Refresh aus R7, erneut
geprüft, erneut kein Commit.

**⚠ Heute fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein IMAP/Ollama
in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`, terminiert auf
18.08.

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 21:06-Session ist
abgearbeitet). Diese Session legt sie neu an (Repos: platform, pm, process, p0, p9). Alle
Änderungen committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (21:25)

## Das Wichtigste (Stand 2026-08-16 21:25)

1. **Dein Wunsch aus `pm/N-0032`/`N-0033` ist gebaut.** Mission Control, Reiter *Cockpit*, ganz
   oben: Kachel **„Letzte Session"**. Sie zeigt genau den Kurzblock, den du sonst in Cowork
   nachlesen musstest. `pm/T-0040` ist **erledigt** (Frist war 23.08.).
2. **Es lag nichts an — deshalb wurde gebaut.** 43 Briefe, **kein offener**; Inbox leer und gegen
   die DR-Rohdaten geprüft (44 DRs, alle `done`); kein überfälliges Ticket.
3. **Die Kachel kann sagen, dass keine Session lief** — *„seit HH:MM keine Session"*. Ihr
   Zeitstempel kommt aus dem **Git-Commit**, nicht aus dem Text der Datei; sonst sähe ein
   stehengebliebener alter Stand aus wie ein frischer.
4. **Doppelklick auf „Absenden" erzeugt keinen zweiten Brief mehr.** Das war die Ursache von
   `N-0028`/`N-0029` und `N-0032`/`N-0033`. **353 Tests grün** (vorher 336), Matrix **102 / 0**.
5. **Heute für dich: `pm/T-0034`** (17.08., nur am Host); ein Blick auf die GitHub-Actions-Seite
   schließt drei weitere Tickets (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Routine-Session 21:06–21:25.** Briefkasten beim Start: **43 Briefe, kein offener** (alle
Projekte/Teams auf `status: offen` durchsucht); die **Zweitprüfung am Sessionende bestätigte das** —
weiterhin 43, keiner offen. **B036 zum achten Mal gefahren, diesmal ohne Fund** — das ist die
Ausnahme, nicht die Regel, und deshalb erwähnenswert. Inbox beim Start und am Ende: **leer und
beweisbar nichts Unverbuchtes** — gegen die DR-Rohdaten geprüft (Ablaufregel aus B047): **44
Decision Requests, alle `done`**. **Kein überfälliges Ticket** (frühester Termin `pm/T-0034`,
17.08.).

**Der Routine-Teil war leer — und statt „nichts zu tun" zu melden, hat die Session den nächsten
geplanten CR gebaut.** Präzedenzfall ist die 19:06-Session (`pm/T-0037`). Genommen wurde
**`pm/T-0040`** und **nicht** `pm/T-0032`, obwohl das die frühere Frist trägt (19.08.): dort steht
vor dem Bau eine Abgrenzungsfrage zwischen drei Taktlogiken, die eine halbe Stunde nicht trägt;
`T-0040` hatte eine ausgeschriebene DoD. **Dass diese Begründung jetzt zum dritten Mal wortgleich
dasteht, ist selbst der Befund** — das Muster aus B043/B049. In der Agenda steht `T-0032` ab jetzt
als **Rückstand** und nicht als Abwägung; die nächste Session mit freiem Routine-Teil nimmt es und
klärt zuerst die Abgrenzung schriftlich, statt zu bauen.

**Was jetzt anders ist.** Neues Modul `platform/backend/session.py`, neuer Endpunkt
`GET /api/session`, Kachel **„Letzte Session"** als **erstes** Element des Cockpit-Tabs. Sie zeigt
den Block „Das Wichtigste" **wörtlich** aus `pm/management/session-agenda.md`. Es entsteht **kein
zweiter Text** — eine zweite Quelle neben der Agenda wäre B033 und würde irgendwann abweichen.
Quelle ist die Agenda und nicht diese Datei hier, weil sie im pm-Repo liegt und committet ist;
`PROJEKTSTATUS-UPDATE.md` liegt im Wurzelordner, also in **keinem** Repo.

**⚠ Der Punkt, an dem die Kachel hätte lügen können.** Im Kopf des Blocks steht ein „(Stand …)".
Fällt der geplante Lauf aus, bleibt die Datei stehen — und diese Zeile behauptete weiter Frische
(B038). Deshalb kommt der Zeitstempel **ausschließlich aus dem Git-Commit**, und die
**Überschriftzeile wird gar nicht erst mit ausgeliefert**: sie war die einzige Stelle, über die die
Textzeit hätte hereinkommen können. Nach zwei stillen Takten (2 × 30 Min) sagt die Kachel *„seit
HH:MM keine Session"*; ein unlesbarer Zeitpunkt gilt als **veraltet**, nie als frisch. Die
Überschrift selbst wird an ihrem **Anfang** erkannt, nicht an ihrer Fassung — Regel 2 aus
**L-2026-08-16h**, derselben Lehre, die am selben Tag 10 von 30 Briefen unlesbar gemacht hat.

**Gegen den Bestand geprüft, nicht nur gegen Testdaten (Regel 1 derselben Lehre).** Nach dem
Schreiben des neuen Blocks lief `session.stand()` über die **echte** Agenda: **820 Zeichen**, genau
die fünf Punkte, ohne Überschriftzeile, ohne die Stand-Angabe `21:25`, ohne den Folgeabschnitt „Für
dich". Genau dieser billige Vollzug hat gestern gefehlt und B054 erzeugt.

**Punkt 6 mitgeliefert: der Doppeleingang ist an der Ursache repariert.** Der Absende-Knopf im
Briefkasten bleibt gesperrt, bis der Verlauf neu gezeichnet ist. Vorher gab er sich sofort frei und
lud erst 900 ms später neu — ein zweiter Klick in dieses Fenster erzeugte einen zweiten Brief.
**Kein Filter, keine Dublettenerkennung** (B050 unverändert): der Klick wird verhindert, nie ein
Brief verschluckt.

**⚠ Befund B056 — eine Zahl aus der Historie ist noch keine Messung dessen, wonach gefragt war.**
Die DoD des Tickets verlangt „die Zahl der **Sessions** des Tages". Die Git-Historie kennt keine
Sessions, nur **Commits**: heute **42 Commits** auf die Agenda bei rund **30** Läufen. Die
naheliegende Brücke — Commits über eine Zeitlücke bündeln — unterschätzt nachweislich: zwischen
`16:35:24` und `16:51:41` liegen 16 Minuten und **zwei verschiedene** Sessions. Geliefert wird
deshalb `fortschreibungen_heute`, unter seinem eigenen Namen; eine Schätzung unter dem Namen einer
Messung wäre B027/B038. Die Abweichung von der DoD steht offen im Ticket. Als **L-2026-08-16i** in
`process/knowledge/cm/lessons.md`.

**⚠ Zweiter Befund, in eigener Sache.** Ein `board.py`-Aufruf in der falschen CLI-Form
(`pm --status T-0040=in_progress` statt `pm status T-0040 in_progress`) hat klaglos nur `BOARD.md`
neu erzeugt und `OK: 40 Tickets validiert` gemeldet. Der Statuswechsel fand **nicht** statt — die
bereits geschriebene Commit-Botschaft behauptete ihn trotzdem. Gefunden nur beim Nachlesen von
`grep '^status:'`, von keiner Meldung. Richtiggestellt per `--amend`, danach die drei Übergänge mit
**je einem Commit** neu gefahren (B052). Dazwischen kamen die R7-Lock-Artefakte
(`.git/index.lock`, `.git/HEAD.lock`, nicht löschbar auf diesem Mount) — weggeräumt nach
`.git/verwaiste-locks/`, Arbeitskopie vorher per `git diff --quiet` als bitgleich zu HEAD belegt.

**⚠ Die erste Gegenprobe war wertlos, und sie steht trotzdem im Nachweis.** Gegen den Altstand
scheitert die neue Testdatei mit `ImportError: cannot import name 'session'` — das belegt, dass ein
Modul fehlt, und nichts über den Schaden; wortwörtlich Regel 3 aus L-2026-08-16h. Die zweite
Gegenprobe läuft über den **echten Abrufweg**: der Server aus `git archive HEAD`, gegen dieselbe
Agenda gestartet, beantwortet `GET /api/session` mit **HTTP 404 „unbekannter Endpunkt"**. Das ist
die Beschwerde aus den Briefen, nicht ein fehlender Import.

**Nicht als getestet geführt: Punkt 6.** Die Organisation hat **353 Python-Tests und null
JS-Tests**; „JS-Frontend-Tests" ist Pool-Kandidat #8 und nicht beauftragt. Der Nachweis für den
Absende-Knopf ist eine **Stichprobe des Auftraggebers** und steht als solche im Ticket und in der
Agenda — das offen zu sagen ist B027, es als „getestet" zu führen wäre B038.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** **pm 40 Tickets** (unverändert —
`T-0040` hat den Status gewechselt, es kam keins dazu), offene pm-Tickets **13 → 12**; Briefe
organisationsweit **43** (unverändert), davon **0 offen**. Matrix **102 SWRs / 0 Lücken** (vorher
101), **353 Tests** (vorher 336), Architektur-Gate grün. Fremde Änderungen: nur die bekannte
`team-mail`-Anzeige (`digest/2026-08-16-woche-digest.md`, `git diff --quiet` = 0) — der
Index-Refresh aus R7, erneut geprüft, erneut kein Commit.

**⚠ Heute fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein IMAP/Ollama
in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`, terminiert auf
18.08.

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 20:50-Session ist
abgearbeitet). Diese Session legt sie neu an (Repos: platform, pm, process, p0, p9). Alle
Änderungen committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (20:50)

### Das Wichtigste (Stand 2026-08-16 20:50)

1. **Drei Briefe waren offen, alle drei sind beantwortet** (`pm/N-0031`, `N-0032`, `N-0033`). Beim
   Startcheck war nur einer da — die anderen beiden kamen um 20:40 herein und fand die
   Zweitprüfung (**B036**, siebter Fund in Folge).
2. **⚠ Befund in eigener Sache, und er betrifft dich direkt: Mission Control hat unsere Antworten
   als deine Nachrichten dargestellt.** Bei **10 von 30** beantworteten Briefen — darunter
   `pm/N-0030` — standen Frage und Antwort als **ein** Textblock da, ohne Absender und ohne Datum.
   **Behoben, heute**, mit zwei Tests. 336 Tests grün.
3. **Gut möglich, dass genau das dein Brief war.** `N-0031` wünscht „direkt weiterkommentieren" —
   und im Chat war Frage und Antwort ein Klumpen Text.
4. **Zwei CRs eingeplant, nicht gebaut:** `pm/T-0039` (am Brief weiterkommentieren) und
   `pm/T-0040` (Session-Zusammenfassung in Mission Control), beide Frist **23.08.**
5. **Weiterhin für dich:** `pm/T-0034` ist **morgen** fällig; ein Blick auf die
   GitHub-Actions-Seite schließt drei Tickets (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

## Aktueller Stand

**Routine-Session 20:36–20:50.** Briefkasten beim Start: **ein offener Brief** — `pm/N-0031`
(18:36); die **Zweitprüfung fand zwei weitere**, `N-0032` (20:40:14) und `N-0033` (20:40:32),
wortgleich. **Alle drei beantwortet.** Inbox beim Start: **leer und beweisbar nichts
Unverbuchtes** — gegen die DR-Rohdaten geprüft (Ablaufregel aus B047): kein `decision-request` mit
Status ≠ `done`. **Kein überfälliges Ticket** (frühester Termin `pm/T-0034`, 17.08.).

**⚠ Der Befund: Mission Control hat unsere Antworten als deine Nachrichten dargestellt (B054).**
`briefkasten._parse` trennte Nachricht und Team-Antwort an einer **wörtlichen** Überschrift
(`## Antwort (Team, JJJJ-MM-TT)`) — genau der Fassung, die der zugehörige Test **selbst erzeugt**.
Die Routine-Sessions schreiben seit dem 15.08. `## Antwort des Teams (Routine-Session,
JJJJ-MM-TT HH:MM)`, mit Uhrzeit, weil bei einem 30-Minuten-Takt das Datum nicht mehr
unterscheidet. **Bei 10 von 30 beantworteten Briefen** blieb `antwort` deshalb leer und die
komplette Team-Antwort stand im **Nachrichtenblock**; die Chat-Ansicht rendert den Antwortblock nur
bei gefülltem `b.antwort` (`app.js`) und zeigte beides als einen Text. Betroffen war auch
**`pm/N-0030`**, der Brief, auf den `N-0031` sich bezieht.

**⚠ Warum es niemandem auffiel.** Der Fehler hat keine Meldung, kein rotes Gate, keinen
Stacktrace — er sieht nur falsch aus, und zwar ausschließlich in der HMI des Auftraggebers. Der
Preflight zählt Briefe nach `status`, nicht nach Lesbarkeit; die SWR-Matrix meldete SWR-050 als
verifiziert, durch einen Test, der seine eigene Eingabe schreibt. Als **L-2026-08-16h** in
`process/knowledge/cm/lessons.md`: *Wo ein Parser ein Format liest, das andere Teile des Systems
schreiben, muss mindestens ein Testfall die Fassung benutzen, die tatsächlich im Repo steht.*

**Behoben (Klasse C, Werkzeugpflege).** `briefkasten.spalte_antwort` erkennt die **Überschrift**
statt ihrer Fassung; das Datum kommt aus der Kopfzeile. Alle 30 beantworteten Briefe werden jetzt
getrennt gelesen — `N-0030`: Nachricht **292** statt 5527 Zeichen, Antwort **5175** statt 0.
**336 Tests** (vorher 334), Matrix **101 SWRs / 0 Lücken**, SWR-050 von 1 auf **3** Tests.

**⚠ Eigene Lehre über die Gegenprobe.** Der erste Gegenprobentest scheiterte gegen den Altstand
nur mit `AttributeError` — die Funktion existierte dort nicht, das belegt nichts über den Schaden.
Der zweite läuft über den echten Lesepfad `liste()` und sichert zu, dass die Team-Antwort **nicht
in `nachricht`** landet; gegen den Altstand scheitert er mit `AssertionError`. Danach
`briefkasten.py` bitgleich zurückgeschrieben (DoD-Punkt 4).

**Nicht gebaut, eingeplant: `pm/T-0039`** (Klasse B, Frist 23.08.) — der Brief wird ein Verlauf aus
beliebig vielen Beiträgen, „Antworten"-Feld je Karte, die 33 bestehenden Briefe ohne Migration
lesbar. **Der Punkt, an dem die Minimallösung schaden würde:** Ein Kommentar an einem Brief mit
`status: beantwortet` wird von **keiner** Session gesehen (`offene()` zählt nur `status: offen`,
und diese Zahl trägt Preflight und Cockpit). Ohne Status-Rücksetzung wäre der CR schädlich statt
nützlich.

**Die zweite Frage aus `N-0031` beantwortet, als Punkt e) in `pm/T-0038` verbucht.** *Warum stehen
die Mensch-Tasks nicht in der Inbox?* Weil die Inbox **unentschiedene Decision Requests** zeigt —
zwei Filter in `inbox._dr_tickets` (`typ == "decision-request"`, kein Entscheidungsvermerk,
SWR-039). Die vier Tickets haben `typ: problem`; die Inbox lehnt sie nicht ab, sie **kennt sie
nicht**. Es fehlt kein Filter, sondern der **Kanal** — derselbe Befund wie `N-0030`, von der
anderen Seite: dort fehlte das Feld, hier die Ansicht. **Nicht in dieselbe Liste**, sondern als
eigener Abschnitt am selben Ort: an der Inbox-Liste hängen die Entscheidungsknöpfe
(`optionen`/`default`, SWR-042) — ein Eintrag ohne Optionen erzwänge Knöpfe, die nichts tun, also
**B033** zum zweiten Mal in zwei Tagen.

**`N-0032`/`N-0033` beantwortet — der Inhalt existiert, die Ausgabe fehlt (`pm/T-0040`, Frist
23.08.).** Jede Session schreibt den Stand in `pm/management/session-agenda.md` (Block „Das
Wichtigste", max. fünf Zeilen seit B050) und in diese Datei; **kein** HMI-Endpunkt liefert eine der
beiden aus. Quelle wird die Agenda, weil sie im pm-Repo liegt und committet ist —
`PROJEKTSTATUS-UPDATE.md` liegt im Wurzelordner, also in **keinem** Repo. **Der Zeitstempel der
Kachel kommt aus dem Commit, nicht aus dem Text:** fällt der geplante Lauf aus, bleibt die Datei
stehen, und ein alter Stand sähe aus wie ein frischer (B038). Und die Kachel muss sagen können,
dass **keine** Session lief — *„seit HH:MM keine Session"*.

**Zweiter Doppeleingang, Ursache lokalisiert, weiterhin kein Filter.** Nach `N-0028`/`N-0029`
(B050) sind `N-0032`/`N-0033` der zweite Fall. Der Absende-Knopf gibt sich frei, **bevor** der
Verlauf neu geladen ist (`app.js`, `setTimeout(lade, 900)`). Als Punkt 6 in `T-0040`. Eine
Dublettenerkennung bleibt abgelehnt — ein Filter, der Briefe still verschluckt, ist teurer als ein
doppelter Brief.

**Board-Check gegen die Erwartung gelesen (B041 Regel 3):** **pm 40 Tickets** (vorher 38,
+`T-0039`, +`T-0040`), offene pm-Tickets **11 → 13**; Briefe organisationsweit **43** (vorher 40),
davon **0 offen** nach dieser Session. Fremde Änderungen: nur die bekannte `team-mail`-Anzeige
(`digest/2026-08-16-woche-digest.md`, `git diff --quiet` = 0) — der Index-Refresh aus R7, erneut
geprüft, erneut kein Commit.

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein
IMAP/Ollama in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`,
terminiert auf 18.08.

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 20:35-Session ist
abgearbeitet). Diese Session legt sie neu an (Repos: platform, pm, process, p0). Alle Änderungen
committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (20:06)

1. **Dein Brief `pm/N-0030` ist beantwortet — er hat einen echten Werkzeugbefund getroffen
   (B053).** Du wolltest wissen, wer an welchem Task arbeitet. **Das Board kann das nicht sagen:**
   die einzige Zuordnungsspalte ist `rolle`, und die nennt die **Fachrolle** (`prob`, `cm`), nicht
   den Ausführenden.
2. **Die Zuordnung selbst steht jetzt in der Agenda, getrennt nach „Für dich" und „Für das
   Team":** von 15 offenen Tickets warten **4 auf dich**, **6 auf das Team**, **5 sind
   Takt-Dauerläufer** ohne Rückstand. Nicht so viele, wie es sich anfühlt.
3. **Der Beleg:** Vier offene Tickets sind nur von dir am Host lösbar (`pm/T-0034`, `T-0013`,
   `T-0010`, `T-0026`) — das steht in allen vieren im **Fließtext** und in **keinem Feld**.
4. **Nicht gebaut, eingeplant: `pm/T-0038`** (Feld `verantwortlich`, Frist 23.08., gebündelt mit
   `pm/T-0036` — beide ändern das `BOARD.md`-Format).
5. **Weiterhin für dich:** `pm/T-0034` ist **morgen** fällig; ein Blick auf die
   GitHub-Actions-Seiten schließt drei Tickets (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

**Belege der Session 20:06–20:35**

**Routine-Session 20:06–20:35.** Briefkasten beim Start: **ein offener Brief** — `pm/N-0030`
(18:02), gefunden bei der Durchsuchung aller **40** Briefe aller Projekte/Teams auf
`status: offen`; **beantwortet**. Inbox beim Start: **leer und beweisbar nichts Unverbuchtes** —
gegen die DR-Rohdaten geprüft (Ablaufregel aus B047): **kein einziger `decision-request` mit
Status ≠ `done`** (47 DRs). **Kein überfälliges Ticket** (frühester Termin `pm/T-0034`, 17.08.).

**Der Brief war die Arbeit — und er war kein Auskunftswunsch.** `pm/N-0030` stellt zwei Fragen in
einem Satz: *was ist als nächstes geplant* (aus dem Bestand beantwortbar) und *wer arbeitet daran,
Team oder Mensch* (**nicht** beantwortbar). Die zweite ist ein Werkzeugbefund.

**⚠ Die Auflösung „Rolle → Mensch oder KI" existiert und wird von niemandem gelesen.**
`process/roles/registry.yaml` trägt je Rolle `besetzung: ki | mensch | script` — elf Rollen auf
`ki`, genau eine (`MENSCH`) auf `mensch`. Gelesen wird das Feld von **keiner** Ausgabe: nicht vom
generierten `BOARD.md`, nicht von der Cockpit-Kachel, nicht vom Preflight. Was im Board steht, ist
`prob` oder `cm` — die Fachrolle des Autors (`board.py`: *„reviewer darf nicht der Autor (rolle)
sein"*).

**⚠ Der Beleg, dass das nicht theoretisch ist.** `pm/T-0034`, `pm/T-0013`, `pm/T-0010` (`prob`)
und `pm/T-0026` (`cm`) sind ausschließlich am Host durch den Menschen lösbar. In `T-0034` heißt
eine Abschnittsüberschrift wörtlich *„Was zu prüfen ist (am Host, eine Handlung des
Auftraggebers)"*, in `T-0026` *„Voraussetzung beim Menschen"* — im Fließtext, in keinem Feld.
**Vier von zehn terminierten offenen Tickets sehen im Board aus wie Teamaufgaben.** Muster
**B043**: die Information ist vollständig da, nur an einer Stelle, an die keine Übersicht sieht.

**⚠ Die naheliegende Abkürzung wäre ein stiller Schaden gewesen.** `rolle: mensch` auf die vier
Tickets zu setzen, hätte die Frage scheinbar gelöst. Das Feld hat in `board.py` aber eine
**zweite, verhaltensändernde** Bedeutung: Tickets mit `rolle: mensch` sind Gates und von der
Status-Übergangsprüfung **ausgenommen** (`t.get("rolle") != "mensch"` in `validiere`). Vier
Tickets hätten ohne eine einzige Meldung ihre Übergangsprüfung verloren — ein Feld für zwei
Zwecke, die Familie aus **B033**. Deshalb ein eigenes Feld. Als **L-2026-08-16g** in
`process/knowledge/cm/lessons.md`.

**Nicht gebaut, eingeplant als `pm/T-0038`** (Klasse B, Frist **23.08.**): Feld
`verantwortlich: team | mensch`, sichtbar als Board-Spalte und im Cockpit, Preflight-Zeile mit den
**Refs** statt nur einer Zahl (B038), und bei `mensch` ein Pflichtabschnitt *„Handlung beim
Menschen"* im Ticket. Ticket-Schema, Board-Format, Cockpit-Vertrag und Preflight gleichzeitig in
einer 30-Minuten-Routine wäre B025/B038. **Dieselbe Frist wie `pm/T-0036`** ist Absicht: beide
fügen dem generierten `BOARD.md` etwas hinzu, und zwei getrennte Formatänderungen am Board haben
am 16.08. früh sämtliche board-check-Workflows rot gemacht (`pm/T-0013`).

**Sofort von Hand angewandt, was ohne Code geht:** Die Session-Agenda trennt ab jetzt **„Für
dich"** von **„Für das Team"** — zwei Tabellen nach Frist, ganz oben. Dieselbe Zuordnung steht als
Momentaufnahme mit Zeitstempel in der Brief-Antwort.

**Kein Code geändert, deshalb keine neuen Tests.** **334 Tests**, Matrix **101 SWRs / 0 Lücken**
unverändert. Board-Check gegen die Erwartung gelesen (B041 Regel 3): **pm 38 Tickets** (vorher 37,
+`T-0038`), offene pm-Tickets **10 → 11**; Briefe organisationsweit **40** (vorher 39), davon
**0 offen** nach dieser Session. Fremde Änderungen: nur die bekannte `team-mail`-Anzeige
(`digest/2026-08-16-woche-digest.md`, `git diff --quiet` = 0) — der Index-Refresh aus R7, erneut
geprüft, erneut kein Commit.

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein
IMAP/Ollama in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`,
terminiert auf 18.08.

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 19:35-Session ist
abgearbeitet). Diese Session legt sie neu an (Repos: pm, process). Alle Änderungen committet,
`preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (19:06)


1. **Deine Inbox ist leer, dein Brief ist beantwortet.** Du hast `p12/T-0002` um **19:11** mit
   **G1a** entschieden — mitten in der Session. Verbucht: Sprint 1 für P12 ist beauftragt
   (`p12/T-0003`, Frist 30.08.). Und `team-dashboard/N-0001` („wie ist der stand zum projekt")
   ist beantwortet. **Beides fand erst die Zweitprüfung am Sessionende** (B036, sechster Fund).
2. **Der Routine-Teil war beim Start leer — deshalb wurde der nächste geplante CR gebaut:
   `pm/T-0037` ist erledigt.** Der
   „Starten"-Knopf verschiebt den Pool-Kandidaten jetzt nach „Realisiert" statt ihn zu löschen,
   und das erzeugte Decision-Log bekommt seinen Tabellenkopf. Der nächste Knopfdruck braucht
   keine Handarbeit mehr. **334 Tests grün** (vorher 329).
3. **Der Test, der den Schaden benennt:** Gegen den alten Stand findet der Tabellen-Parser im
   erzeugten Decision-Log **0 Tabellen**. Die Entscheidung war im HMI also nicht als Eintrag
   lesbar — nicht bloß unschön formatiert.
4. **Ein eigener Befund über die eigene Fußzeile (B052):** „über die erlaubten Übergänge
   geschlossen" stimmt nur, wenn **je Übergang committet** wird — die Prüfung liest die Historie,
   nicht die Arbeitskopie. Sieben Sessions haben das so geschrieben; belegt war es zur Hälfte.
5. **Weiterhin für dich:** `p12/T-0002` (G1, Frist 23.08.) wartet; `pm/T-0034` ist **morgen**
   fällig und nur am Host lösbar; ein Blick auf die GitHub-Actions-Seiten schließt drei Tickets
   (Frist 18.08.).

*Ab hier: Belege und Details zum Nachlesen. Übergabepunkt zwischen Cowork-Sessions, wird per
Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*


**Routine-Session 19:06–19:35.** Briefkasten beim Start **leer** (38 Briefe aller Projekte/Teams
auf `status: offen` durchsucht) — die **Zweitprüfung am Ende fand einen neuen**
(`team-dashboard/N-0001`, beantwortet). Inbox beim Start: ein wartender DR (`p12/T-0002`), nichts
Unverbuchtes. Um **19:11** entschieden mit **G1a** — mitten in der Session, gefunden über die
DR-Rohdaten (B047), nicht über `inbox.liste`. **Verbucht.** Am Ende: **kein wartender und kein
unverbuchter DR.** **Kein überfälliges Ticket, Org-Summe „ohne Frist" = 0** (alle sieben Kacheln
einzeln gelesen, B049), `mail_digest.faellig(1)` und `faellig(7)` beide `False`.

**⚠ Zum sechsten Mal war die Zweitprüfung am Sessionende der Grund, dass nichts liegenblieb
(B036).** Beide Vorgänge — Entscheidung und Brief — kamen **nach** dem Startcheck herein. Bei einem
30-Minuten-Takt ist das kein Ausnahmefall, sondern der Regelfall: die Wahrscheinlichkeit, dass ein
Vorgang genau in das Fenster einer laufenden Session fällt, ist so hoch wie das Fenster lang ist.

**`p12/D001`/G1a verbucht (Klasse C — die Entscheidung war Klasse A und ist gefallen).** G1-Vermerk
in beiden Requirements-Dokumenten; **SWR-097–101 bleiben `draft`** (B027 — G1a beauftragt den
Sprint, es verifiziert keine Anforderung); Sprint-1-Ticket **`p12/T-0003`** (Frist 30.08.) mit
ausgeschriebener Reihenfolge: erst die Teststrecken-Entscheidung (R5) im ADR, dann das Delta zu
ADR-002, dann der Vollständigkeitsnachweis (SWR-099) gegen den **Bestand**, erst dann die
Umstellung. Ausdrücklich im Ticket: führt der Weg zu Kosten oder einem neuen externen Werkzeug, ist
das **Klasse A** und geht als DR in die Inbox, nicht in den Sprint. `T-0002` über die erlaubten
Übergänge geschlossen, mit Commit je Übergang.

**Brief `team-dashboard/N-0001` beantwortet** („wie ist der stand zum projekt"): P11 hat beide
Freigaben und einen beauftragten Sprint 1 — was anhängt, ist der **Widget-Vertrag dieses Teams**
(`team-dashboard/T-0001`, Frist 23.08., noch nicht entworfen). Die ehrliche Zuordnung gehört in die
Antwort, sonst liest sich „das Projekt hängt" wie ein Problem des Projekts.

**Der Routine-Teil war in wenigen Minuten leer — und statt „nichts zu tun" zu melden, hat die
Session den nächsten geplanten CR gebaut.** `pm/T-0037` war von der Vorsession mit einer
ausdrücklichen Begründung aufgeschoben worden: *„nicht nebenbei, weil diese Session eine
Klasse-A-Entscheidung zu vollziehen hat" (B025/B038)*. Diese Session hatte nichts daneben — damit
fällt der Grund weg. `pm/T-0032` (Frist 19.08., also früher) wurde bewusst **nicht** genommen:
dort steht vor dem Bau eine Abgrenzungsfrage zwischen drei Taktlogiken, die eine halbe Stunde
nicht trägt; `T-0037` hatte eine ausgeschriebene DoD.

**Was jetzt anders ist:** `kandidat_starten` verschiebt die Kandidatenzeile nach „Realisiert"
(`# | Kandidat | Wohin | Beleg`) statt sie zu löschen — im selben Schreibvorgang und Commit, den
Abschnitt legt es an, wenn er fehlt. Und das Decision-Log entsteht mit **Tabellenkopf**; der
Platzhaltersatz entfällt, weil er nach der ersten Entscheidung falsch wurde.

**⚠ Der Test, der den Schaden wirklich benennt.** Für den Tabellenkopf hätte ein „steht er da?"
gereicht. Stattdessen hängt ein Test eine echte D000-Zeile an und lässt
`aggregation.parse_md_tabellen` darüberlaufen: **gegen den Altstand findet der Parser 0 Tabellen.**
Die Entscheidung war im HMI also nicht als Eintrag lesbar. Gegenprobe gefahren (DoD-Punkt 4):
**alle fünf neuen Tests scheitern gegen `git show HEAD:backend/pool.py`**, danach `pool.py`
bitgleich zurückgeschrieben. **334 Tests**, Matrix **101 SWRs / 0 Lücken** unverändert (SWR-089
zählt 22 statt 17 Tests — keine neue Anforderungsfläche).

**⚠ Eigener Befund dieser Session (B052): die eigene Fußzeile war zur Hälfte unbelegt.** Die Kette
`open → in_progress → in_review → done` wurde in drei `board.py status`-Aufrufen **ohne
Zwischencommit** gefahren — so, wie „über die erlaubten Übergänge geschlossen" seit sieben
Sessions in den Fußzeilen steht. `board.py pm --check` meldete danach `unzulässiger
Status-Übergang: open -> done`: `board.validiere` vergleicht gegen **HEAD**. Für die Prüfung
existieren Zwischenschritte nur, wenn sie committet sind — und das ist die richtige Prüfung an der
einzigen Stelle, die sie belegen kann. Behoben mit **einem Commit je Übergang**, jeder mit der
Begründung in der Botschaft (`-> in_review: DoD vollständig`, `-> done: Tests grün`). Als
**L-2026-08-16f** in `process/knowledge/cm/lessons.md`.

**Fremde Änderung geprüft und verbucht (B041).** `projects/p12/tickets/T-0002.md` trug beim Start
den uncommitteten Marker **„Benachrichtigt: 2026-08-16 per E-Mail (SWR-033)"** aus
`dr_benachrichtigung.py` (DR-Mailversand am Host nach der 18:35-Session) — inhaltlich echt,
deshalb eigener Commit **vor** der Sessionarbeit. Die bekannte `team-mail`-Anzeige ist unverändert
der Index-Refresh aus R7 (`git diff --quiet` = 0) — erneut geprüft, erneut kein Commit.

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein
IMAP/Ollama in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`,
terminiert auf 18.08.

Board-Check gegen die Erwartung gelesen (B041 Regel 3): **pm 37 Tickets** (unverändert — `T-0037`
hat den Status gewechselt, es kam keins dazu), offene pm-Tickets **11 → 10**; **p12 3 Tickets**
(vorher 2, +`T-0003`); Briefe organisationsweit **39** (vorher 38).

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 18:35-Session ist
abgearbeitet, Wächter-Erfolg **18:30:26**). Diese Session legt sie neu an (Repos: platform, pm,
process, p0, projects, team-dashboard — letzteres bleibt lokal-only, bis das GitHub-Repo besteht). Alle Änderungen committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (18:04)

**Routine-Session 18:04–18:35.** Briefkasten **leer** (38 Briefe aller Projekte/Teams auf
`status: offen` durchsucht, zweimal geprüft). Inbox: `inbox.liste` meldete **leer** — und das war
für die Verbuchung **falsch**: `p12/T-0001` trug seit **18:04** den Vermerk **G0a** bei Status
`open`. Gefunden hat es die Prüfung gegen die **DR-Rohdaten** (Ablaufregel aus B047, sechster Fund
dieser Klasse). Am Ende: ein wartender DR (`p12/T-0002`, von dieser Session vorgelegt), kein
unverbuchter. **Kein überfälliges Ticket, Org-Summe „ohne Frist" = 0**, `mail_digest.faellig(1)`
und `faellig(7)` beide `False`.

**P12 ist gestartet, freigegeben und hat Sprint 0 — und der Lauf war der erste echte Prüfstein für
den „Starten"-Knopf (B051).** Ordner, Auftragsentwurf, leeres Decision-Log und der G0-Antrag kamen
vom Werkzeug (`pm/T-0022` Teil 2), die Freigabe vom Auftraggeber. Vollzogen (Klasse C):
Projektauftrag **v1.0** mit sechs messbaren Abnahmekriterien, **STK-022 + SWR-097–101** als `draft`
(B027), Sprint-0-Plan mit sechs Risiken, G1-DR `p12/T-0002` (Frist 23.08., Default G1a). `T-0001`
über die erlaubten Übergänge geschlossen. **Matrix 101 SWRs / 0 Lücken** (vorher 96).

**⚠ Der inhaltliche Kern wurde in Sprint 0 gefunden, nicht vorausgesetzt.** Im HMI stehen **zwei**
Textwege nebeneinander, und jedem fehlt genau die Fähigkeit des anderen: `mdRender` (SWR-059/060,
aus P7) formatiert, kennt aber **keine Ticket-Links**; `preMitLinks`/`tlinks` (SWR-040) verlinkt
Tickets, formatiert aber nichts. Der Renderer läuft heute an **zwei** Stellen (Digest, Charter),
der Rohtext-Weg an **sieben**. Briefe und Reports naiv umzuhängen hätte die Ticket-Links **genau
dort verloren, wo die meisten stehen** — Sprint-Reports und DR-Bodys. SWR-098 verlangt deshalb die
Ticket-Erkennung **im Inline-Pass des vorhandenen Renderers**: P12 ist eine Zusammenführung, kein
Anstrich. Zweiter Punkt, der bei P7 keiner sein musste: Briefe sind **Freitext eines Menschen** —
daher SWR-100 (kein `innerHTML`, keine Bibliothek, Markup erscheint als Text) und SWR-099 (kein
stiller Textverlust; Code-Blöcke kennt der Renderer heute nicht, `platform/N-0002` enthält welche).

**⚠ Nicht zugesagt: die Prüfung.** Die Abnahmekriterien verlangen Nachweise an JavaScript — es gibt
**329 Python-Tests und null JS-Tests**; „JS-Frontend-Tests" ist Pool-Kandidat **#8** und nicht
beauftragt. Das steht als **R5** im Plan und als Punkt 1 im G1-Antrag: *wie* geprüft wird, ist die
erste Entscheidung in Sprint 1 und gehört in den ADR — vor der Umstellung. Ein „Tests" im
Kriterium, aus dem am Ende eine Stichprobe wird, wäre wörtlich B027/B038.

**⚠ Werkzeugbefund B051: eine Konvention, die nur von Hand existierte, hat den ersten
Werkzeuglauf nicht überlebt.** Zwei Sachen, beide lautlos: Der **Pool-Kandidat #7 wurde gelöscht
statt nach „Realisiert" verschoben** (Diff des Knopf-Commits: `1 file changed, 1 deletion(-)`) —
den Abschnitt gibt es seit **16:15 desselben Tages**, von Hand eingeführt für Kandidat #13 mit der
Begründung aus B029; der Knopf war da schon gebaut. Und das erzeugte **Decision-Log hat keinen
Tabellenkopf**: `pool.py` schreibt einen Platzhaltersatz, `inbox.entscheide` hängt die D000-Zeile
an — ohne Kopf ist das keine Tabelle, sondern Pipe-Text, und der Platzhaltersatz behauptet danach
weiter, es gebe keine Entscheidung. Gefunden nur beim Gegenlesen des fremden Commits (B041
Regel 3). **Von Hand sofort behoben**, was ohne Code geht; die Werkzeugänderung ist als
`pm/T-0037` eingeplant (Klasse B, Frist 23.08.) und **nicht** nebenbei gebaut (B025/B038).

**⚠ Eigener Fehler dieser Session, gefunden und behoben.** Beim Erkunden lief `trace_matrix.py`
ohne `--repos . --alle-projekte` und schrieb `p0/verification/reports/swr-test-matrix.md` auf einen
Teilstand (24 SWRs, 56 Lücken). Sofort gegengelesen (`git diff --stat`: 116+/74−), **in-place** aus
`git show HEAD:` zurückgeschrieben (`git checkout` scheitert am `unable to unlink` des Mounts, R7)
und per `git diff --quiet` als bitgleich zu HEAD belegt — **bevor** irgendetwas committet wurde.
**Lehre:** Ein Werkzeug, das Dateien schreibt, ist kein Erkundungsmittel.

**Kein Code geändert, deshalb keine neuen Tests.** 329 Tests, Matrix 101 SWRs / 0 Lücken, Katalog-
und Architektur-Gate grün. Board-Check gegen die Erwartung gelesen (B041 Regel 3): **pm 37
Tickets** (vorher 36), **p12 2 Tickets** (vorher 1).

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert, kein
IMAP/Ollama in dieser Sandbox (Guardrail 2). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`,
terminiert auf 18.08. — sie warten auf den Blick auf die GitHub-Actions-Seiten.

Push: `PUSH-ANFORDERUNG.txt` war beim Start **nicht vorhanden** (die Zeile der 17:06-Session ist
abgearbeitet, Wächter-Erfolg 17:30:26). Diese Session legt sie neu an (Repos: projects, pm,
process, p0). Alle Änderungen committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession (17:06)

**Nachtrag 17:28 — zwei Vorgänge kamen während der Session herein (B036, fünfter Fund):**
Der Auftraggeber hat `pm/T-0035` um **17:17** mit **AK-b** entschieden — beim Inbox-Check um
17:06 lag der Antrag noch wartend da. Sichtbar wurde die Entscheidung erst im Abschluss-`git
status` als fremde Änderung am Ticket, **nicht** über `inbox.liste` (die filtert entschiedene DRs
bauartbedingt heraus, SWR-039/B047). Verbucht: `p0/T-0008` → `rejected` mit Begründung und Beleg,
`pm/T-0035` über die erlaubten Übergänge (`open → in_progress → in_review → done`) geschlossen.
**Damit haben P0 und P1 kein offenes Ticket mehr, und der „ohne Frist"-Zähler steht zusammen mit
B049 organisationsweit erstmals auf 0.** Zeitgleich kamen die Briefe **`pm/N-0028`/`N-0029`**
(wortgleich, eine Sekunde auseinander): *„du schreibst zu viel text"* — beantwortet und sofort
angewandt, siehe **B050** und der Block „Das Wichtigste" oben.

**Routine-Session 17:06:** Briefkasten **leer** (36 Briefe aller Projekte/Teams auf `status: offen`
durchsucht, zweimal geprüft). Inbox: **ein wartender Antrag, nichts Unverbuchtes** — `pm/T-0035`
(Klasse A zu `p0/T-0008`) steht seit 16:50 zur Entscheidung und ist **nicht entschieden**; gegen die
DR-Rohdaten geprüft (B047): kein weiterer `decision-request` mit Status ≠ `done`, kein
Entscheidungsvermerk in `T-0035`. **Kein überfälliges Ticket** (frühester Termin `pm/T-0034`,
17.08.), `mail_digest.faellig(1)` und `faellig(7)` beide `False`.

**Der Agenda-Punkt war wieder der Zähler aus SWR-091 — und er war wieder nicht zu Ende gelesen
(B049).** `cockpit_alle` meldete beim Start **p0 = 1** *und* **pm = 3**. Die 16:15-Session hatte die
pm-Kachel für abgearbeitet erklärt (sie ging von 4 auf **3**, nicht auf 0), die 16:50-Session
erklärte den Zähler für „zu Ende gelesen" und las dabei nur p0. Dahinter stehen **`pm/T-0010`,
`pm/T-0013`, `pm/T-0026`** — drei `in_review`-Problemtickets ohne Frist, die in **sieben**
Session-Fußzeilen wortgleich als *„bleiben `in_review`, Grund unverändert: kein `gh`/Netzzugriff"*
stehen. Das Muster aus **B043**, diesmal an der eigenen Fußzeile.

**Die Eskalationsregel aus B044 kann sie bauartbedingt nicht sehen.** „Überfällig" ist
`board.ist_ueberfaellig`, und das setzt eine **Frist** voraus — ohne Frist ist die Ampel „grau", ein
unterminiertes Ticket wird nie überfällig. Die Regel gegen das Liegenbleiben hat ihren blinden Fleck
genau dort, wo das Liegenbleiben stattfindet. Einziger Melder ist der `unterminiert`-Zähler — und
der ist eine **Zahl je Kachel**, keine Summe. Drei Sessions haben je eine Kachel gelesen und
„erledigt" notiert; eine Org-Summe hätte jedes Mal ≠ 0 gemeldet.

**⚠ Der schärfste Teil: bei `pm/T-0013` war die halbe Verifikation die ganze Zeit lokal prüfbar.**
Das Ticket hat **zwei** Kriterien, die der alte Vermerk unter einem Satz zusammenfasste. Kriterium 1
— *„`platform` erscheint als erstes Repo in der Push-Ausgabe"* — steht in `abschluss-auto.log`,
einer Datei, für die es keinen Netzzugriff braucht: `platform` ist dort seit dem Lauf **07:59:59** in
**jedem** erfolgreichen Wächter-Lauf das erste Repo (13 Läufe, zuletzt 17:00:23; davor, 00:44–07:15,
war es `p0`). Der Vermerk, der den Nachweis für unerreichbar erklärte, nennt selbst *„letzter
erfolgreicher Push 08:30"* — **genau dieser Lauf trug den Beleg schon.** Und der Hinderungsgrund von
`T-0010`/`T-0026` (Wächter bricht seit 09:44 ab) ist **seit 10:30 weg**: 13 grüne Läufe, alle Repos
`ahead 0/behind 0`.

**Getan (Klasse C):** Kriterium 1 in `T-0013` mit Zeitstempeln als **erfüllt** belegt; die überholten
Vermerke in `T-0010`/`T-0026` richtiggestellt; alle drei mit **Frist 18.08.** und der Begründung im
Ticket. Gegenprobe zum CR-Kandidaten in `T-0026`: die Repo-Liste in
`platform/.github/workflows/ci.yml` deckt P11 ab (liegt im gelisteten Sammel-Repo `projects`) — sie
hat gehalten, weil P11 dorthin gelegt wurde, nicht weil sie sich selbst pflegt. **pm meldet jetzt
`unterminiert=0`; organisationsweit bleibt 1** (`p0/T-0008`, begründet nach B048).
**`T-0013` bleibt `in_review`** — ein Kriterium erfüllt heißt nicht beide erfüllt, und ein Gate, das
nur lokal grün ist, war bei `T-0026` genau der Fehler.

**Warum eine Frist hier keine Behauptung ist (Unterschied zu B048):** `p0/T-0008` wartet auf eine
Entscheidung, die der Auftraggeber zweimal vertagt hat — ein Datum hätte dort einen Termin
behauptet, den niemand zugesagt hat. Diese drei warten auf **einen Blick auf eine Seite, die der
Wächter ohnehin öffnet** ([5/5] seiner Ausgabe). Präzedenzfall steht: `pm/T-0034` ist ebenfalls nur
am Host lösbar und trägt trotzdem einen Termin.

**Nicht gebaut, eingeplant als `pm/T-0036` (Klasse B, Frist 23.08., Priorität hoch):** Org-Summe
statt Kachelzahl, Preflight-Zeile mit den **Namen** der unterminierten Tickets, Ablaufregel *„Kachel
X erledigt ist keine gültige Abschlussmeldung"*. Das ist ein Eingriff in die Prüfstrecke selbst
(Cockpit-Vertrag + Preflight-Ausgabe, berührt SWR-091); nebenbei in einer 30-Minuten-Routine wäre das
das Risiko aus B025/B038. Von Hand sofort angewandt wurde, was ohne Code geht.

**Fremde Änderung geprüft und übernommen (B041).** `pm/T-0035` trug beim Start eine uncommittete
Zeile **„Benachrichtigt: 2026-08-16 per E-Mail (SWR-033)"** — der Marker aus
`platform/scripts/dr_benachrichtigung.py`, geschrieben vom DR-Mailversand am Host nach der
16:50-Session. Inhaltlich echt und historienwürdig, deshalb **eigener Commit vor der Sessionarbeit**,
damit Fremdes und Eigenes nicht in einer Zeile stehen. Die bekannte `team-mail`-Anzeige
(`digest/2026-08-16-woche-digest.md` in `git status`, `git diff` leer) ist unverändert der nicht
durchlaufende Index-Refresh aus R7 — **erneut geprüft, erneut kein Commit**.

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (17.08., hoch) — unverändert. Kein IMAP/Ollama
in dieser Sandbox (Guardrail 2): **kein übergangenes Ticket im Sinne von B044**, sondern die Grenze
der Ausführung.

**Kein Code geändert, deshalb keine neuen Tests** — der Befund war eine Recherche in Log und Tickets.
**329 Tests, Matrix 96 SWRs / 0 Lücken, Katalog- und Architektur-Gate grün.** Board-Check gegen die
Erwartung gelesen (B041 Regel 3): **pm 36 Tickets** (vorher 35, +`T-0036`).

**⚠ Werkzeug-Notiz (R7) — ein Umgehungsweg, der beinahe Arbeit vernichtet hätte.** `git status`
hinterlässt auf diesem Mount ein `.git/index.lock`, das es nicht mehr löschen kann; jeder folgende
`git`-Aufruf im selben Repo bricht dann ab. Der in dieser Session zuerst versuchte Ausweg —
`GIT_INDEX_FILE` auf eine **Kopie** des Index — läuft zwar durch, lässt aber die echte `.git/index`
auf altem Stand: **jede Datei, die nicht ausdrücklich im `git add` steht, wird aus diesem alten Stand
mitcommittet.** Der Sammelcommit hat so `pm/T-0035` um **26 Zeilen zurückgesetzt** (Status wieder
`open`, Vollzugsvermerk weg) — die Historie hätte „T-0035 → done" behauptet, während das Ticket
wieder offen dastand. **Gefunden über die Zahl `-26` in der Diffstat beim Gegenlesen (B041 Regel 3),
mit einem Korrektur-Commit behoben.** Richtig ist: Locks per **`mv`** nach `.git/verwaiste-locks/`
wegräumen (Umbenennen ist erlaubt, Löschen nicht — wie in `pm/T-0023`), dann `git reset` gegen den
echten Index und normale `git add`/`commit`-Aufrufe.

Push: die Zeile der 16:50-Session in `PUSH-ANFORDERUNG.txt` ist **abgearbeitet** — Wächter-Erfolg
**17:00:23** (`OK - alles geprueft und gepusht`), alle Repos `ahead 0/behind 0`, die Datei
entsprechend nicht mehr vorhanden. Diese Session legt sie für ihre eigenen Commits neu an (Repos:
pm, process). `pm/T-0010`/`T-0013`/`T-0026` bleiben `in_review`, jetzt aber **terminiert** statt
unterminiert. Alle Änderungen committet, `preflight.py` meldet STARTKLAR.

---

## Stand der Vorsession

*Zuletzt aktualisiert: 2026-08-16 16:50 (Routine-Session) — **DER „OHNE FRIST"-ZÄHLER IST ZU ENDE GELESEN: HINTER DER LETZTEN OFFENEN KACHEL (p0) STAND `p0/T-0008`, DAS EINZIGE OFFENE TICKET IN ZWEI ABGESCHLOSSENEN PROJEKTEN — ZWEIMAL VERTAGT, ABER OHNE JEDEN HINWEIS DARAUF IM TICKET. SEIN ZWILLING AUS DEMSELBEN ABNAHMEKRITERIUM IST LÄNGST `rejected`. BELEGKETTE NACHGETRAGEN (KLASSE C), ENTSCHEIDUNG NICHT SELBST GETROFFEN — `pm/T-0035` LIEGT ALS KLASSE-A-ANTRAG IN DER INBOX.** Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

### Aktueller Stand der 16:50-Session

**Routine-Session 16:50:** Briefkasten **leer** (37 Briefe aller Projekte/Teams auf `status: offen`
durchsucht, zweimal geprüft). Inbox beim Start leer — und **erstmals beweisbar** nach der neuen
Ablaufregel aus B047: gegen die **DR-Rohdaten** geprüft, es existiert **kein einziger
`decision-request` mit Status ≠ `done`**. Die Klasse „entschieden, aber nicht verbucht" ist damit
leer, nicht nur laut `inbox.liste`. **Kein überfälliges Ticket** (frühester Termin `pm/T-0034`,
17.08.), `mail_digest.faellig(1)` und `faellig(7)` beide `False`.

**Der einzige offene Agenda-Punkt war der Zähler aus SWR-091 — und er hat etwas gefunden
(B048).** Die 16:15-Session hatte den „ohne Frist"-Zähler **nur für die pm-Kachel** abgearbeitet
(`pm/T-0003` bekam sein `takt`-Feld); `cockpit_alle` meldet für **p0 unverändert
`unterminiert=1`**. Dahinter: **`p0/T-0008`** (Anthropic-API-Key, `open`, `prio: hoch`, ohne
Frist, erstellt **05.08.**) — das **einzige offene Ticket in zwei abgeschlossenen Projekten**
(P0 `genesis-v1.0`, P1 `p1-v1.0`).

**Es ist nicht liegengeblieben, sondern zweimal ausdrücklich vertagt:** `p0/D008` („kommt später",
Ollama vorgezogen), `p0/D015` („weiter verschoben", Budget-Review vertagt), im
P0-Abschlussbericht als Kriterium 9 **„teilweise"** mit Backlog-Punkt **B9** abgenommen und als
Epic **P1-E5** weitergereicht („optional nach Budgetfreigabe"). **Nur stand davon nichts im
Ticket.** Wer es heute öffnet, liest eine elf Tage alte hochpriorisierte Sprint-1-Aufgabe ohne
Termin — das Muster aus **B043**, diesmal nicht durch Vergessen, sondern weil der Kontext in drei
anderen Dokumenten liegt. Der Zähler kann das nicht unterscheiden: er zählt „ohne Frist", er liest
keine Decision-Logs.

**⚠ Der schärfere Teil des Befunds: der Zwilling ist längst entschieden.** P0-Kriterium 9 hatte
**zwei** Betriebsreste, beide als P1-E5 weitergereicht — der **Copilot-Lauf** ist als `p0/T-0072`
**und** `p1/T-0018` **rejected**, der **Claude-API-Tick** blieb `open`. Zwei gleichrangige Reste
desselben Kriteriums, einer geschlossen, einer nicht. Das ist der Kern, nicht die 20 €.

**Getan (Klasse C):** Belegkette und die Begründung für die fehlende Frist stehen jetzt **im
Ticket selbst** — die nächste Session muss nicht neu recherchieren. **Status unverändert `open`.**
**Nicht getan (Klasse A):** über das Ticket entschieden. Ein API-Key ist eine Budget- und
Zugangsfreigabe (Playbook Kap. 16), **in beide Richtungen** — ihn anzulegen ist eine
Geldentscheidung, ihn abzuräumen eine Scope-Entscheidung über ein Abnahmekriterium. Vorgelegt als
**`pm/T-0035`**: AK-a jetzt umsetzen · **AK-b schließen wie den Zwilling** · AK-c offen lassen mit
Frist. Frist **23.08.**, **Default AK-b** — Schweigen darf nie in Richtung Geldausgabe oder neuer
Credentials laufen, und AK-c wäre der dritte Aufschub.

**Eine Frist hat das Ticket bewusst nicht bekommen.** Es wartet nicht auf Arbeit des Teams,
sondern auf eine Entscheidung, die der Auftraggeber zweimal vertagt hat; ein von der Session
gesetztes Datum hätte einen Termin behauptet, den niemand zugesagt hat (B038-Familie). Die Frist
trägt der Antrag, nicht das Ticket.

**⚠ Morgen fällig, nur am Host lösbar: `pm/T-0034`** (Frist 17.08., Priorität hoch). Der
Wochendigest liegt; offen ist der eigentliche Befund — warum Ollama um 15:28 nicht erreichbar war
und ob `ASPICE-MailAutopilot` überhaupt eingerichtet ist. Kein IMAP/Ollama in dieser Sandbox
(Guardrail 2): **kein übergangenes Ticket im Sinne von B044**, sondern die Grenze der Ausführung.

**Kein Code geändert, deshalb keine neuen Tests** — der Befund war eine Recherche in vorhandenen
Dokumenten und ein Antrag. **329 Tests, Matrix 96 SWRs / 0 Lücken, Katalog- und Architektur-Gate
grün.** Board-Check gegen die Erwartung gelesen (B041 Regel 3): **pm 35 Tickets** (vorher 34), p0
72 unverändert. Die bekannte `team-mail`-Anzeige (`digest/2026-08-16-woche-digest.md` erscheint in
`git status` als geändert, `git diff` ist leer) ist unverändert der nicht durchlaufende
Index-Refresh aus R7 — **erneut geprüft, erneut kein Commit**.

Push: die Zeile der 16:15-Session in `PUSH-ANFORDERUNG.txt` (16:32) war beim Start **noch
unverarbeitet** (letzter Wächter-Erfolg damals 16:30:26) — und ist **während dieser Session
abgearbeitet worden**: Wächter-Start **16:44:00**, Erfolg **16:45:25** (`OK - alles geprueft und
gepusht`). Aufgefallen ist das nur, weil `pm` nach dem eigenen Commit **ahead 1** statt **ahead 2**
meldete; eine bereits geschriebene Notiz („Zeile ggf. noch offen") wäre sonst als plausibel
klingende Falschaussage stehen geblieben — dieselbe Prüfung wie in B041 Regel 3 („Zahlen aus
Werkzeugausgaben gegen die Erwartung lesen"), diesmal an einer Zahl, die *kleiner* war als
erwartet. Korrigiert in `PUSH-ANFORDERUNG.txt`, Agenda und hier. Diese Session hängt eine neue
Zeile für ihre eigenen Commits an (Repos: pm, p0). `pm/T-0010`/`T-0013`/`T-0026` bleiben
`in_review` (kein `gh`/Netzzugriff). Alle Änderungen committet, `preflight.py` meldet STARTKLAR.

---

### Ältere Stände

*Zuletzt aktualisiert: 2026-08-16 16:15 (Routine-Session) — **PROJEKT P11 „WIDGET-DASHBOARD" IST ANGELEGT UND HAT G1 — BEIDE KLASSE-A-ENTSCHEIDE FIELEN UND WURDEN IN DERSELBEN SESSION VERBUCHT (G0a/D007 um 15:55, G1a/p11-D001 um 16:07 — 51 Sekunden nach dem Commit, mit dem das Projekt entstand). DIE INBOX IST LEER. ZWEI BEFUNDE AM WERKZEUG: EIN ENTSCHIEDENER, NICHT VERBUCHTER DR IST IN DER INBOX UNSICHTBAR, UND `blocked_by` REICHT NICHT ÜBER REPO-GRENZEN.** Wird per Abschluss-Skript als `p0/PROJEKTSTATUS.md` versioniert.*

### Aktueller Stand der 16:15-Session

**Routine-Session 16:15:** Briefkasten **leer** (zweimal geprüft; alle Briefkästen aller
Projekte/Teams auf `status: offen` durchsucht, kein Treffer). Inbox: **zwei Klasse-A-Entscheidungen
verbucht**, beide vom Auftraggeber im laufenden Betrieb getroffen.

**`pm/T-0033` → D007/G0a (15:55): Projekt P11 „Widget-Dashboard" ist beauftragt und angelegt.**
`projects/p11` im Sammel-Repo (`pm/D003`), fachlicher Auftraggeber ist `team-dashboard` — das
**erste Projekt der Organisation mit einem Team als Abnehmer**. Geliefert ist Sprint 0:

- **Projektauftrag v1.0** mit fünf **messbaren** Abnahmekriterien (u. a. „passt bei 1920×1080 ohne
  Scrollen — mit dem vollen Bestand, nicht mit einer Auswahl") und ausgeschriebener Abgrenzung.
- **STK-021 und SWR-092–096 — alle auf `draft`** (B027). Sie auf `reviewed` zu setzen, weil eine
  Freigabe vorliegt, wäre wörtlich der Fehler, gegen den B027 geschrieben wurde: fünf leere
  Anforderungen unter einem grünen Lücken-Gate. Matrix: **96 SWRs / 0 Lücken.**
- **Sprint-0-Plan mit fünf Risiken**, darunter R1 („keine zweite Datenquelle neben
  `aggregation.cockpit`" — die Falle aus B033) und R2 („‚nicht scrollbar' wird beim Bau
  stillschweigend aufgeweicht").
- **G1-DR `p11/T-0002`** mit drei offengelegten Punkten: die Layout-Frage bleibt **bewusst offen**
  (SWR-092 formuliert das Kriterium, nicht den Weg dorthin — der Entwurf fällt vor dem Bau),
  Sprint 1 startet erst mit dem Widget-Vertrag, „vom Handy aus dem Internet" bleibt außen vor.

**`p11/T-0002` → p11/D001/G1a (16:07), 51 Sekunden nach dem Projekt-Commit.** Zweiter
vollständiger Roundtrip Lieferung → Antrag → Knopf → Freigabe innerhalb einer Session (nach
B035). Verbucht: G1-Vermerk in beiden Requirements-Dokumenten, **SWRs bleiben `draft`** — die
Freigabe beauftragt den Sprint, sie verifiziert keine Anforderung. Sprint-1-Ticket `p11/T-0003`
angelegt (Frist 30.08.). Beide DRs über die erlaubten Übergänge geschlossen
(`open → in_progress → in_review → done`), nicht per Direktsetzung.

**⚠ Befund am Werkzeug: Ein entschiedener, aber noch nicht verbuchter DR ist in der Inbox
unsichtbar.** `inbox.liste` meldete `{"inbox": []}`, während `pm/T-0033` seit 15:55 entschieden
dalag — `_dr_tickets` filtert jeden DR heraus, dessen Text schon einen Entscheidungsvermerk trägt
(SWR-039). Für die Inbox ist das korrekt (dort steht, was *wartet*); als Verbuchungsprüfung taugt
sie nicht. Gefunden nur, weil die Agenda `pm/T-0033` namentlich als „wartend" nannte und **gegen
die Rohdaten** geprüft wurde — der fünfte Beleg für B025 („ein leeres Werkzeugergebnis ist kein
Beweis für ‚nichts zu tun'"). Neue Ablaufregel in der Agenda; ein Werkzeug dafür steht als CR im
Betriebs-Backlog, nicht nebenbei gebaut.

**⚠ Zweiter Befund, unbehoben und offengelegt: `blocked_by` reicht nicht über Repo-Grenzen.**
`p11/T-0003` **sollte** `blocked` sein — die Sperre ist der Widget-Vertrag
`team-dashboard/T-0001` (Frist 23.08.). `board.py` verlangt zu `blocked` einen
`blocked_by`-Verweis und prüft ihn gegen die IDs **desselben** Repos. Die Abhängigkeit *Projekt
wartet auf Team* ist mit `team-dashboard` als Auftraggeber zum ersten Mal entstanden und im Board
nicht ausdrückbar. Einen erfundenen p11-internen Verweis einzutragen, nur damit das Feld gefüllt
ist, wäre eine behauptete Sperre, die es nicht gibt (B038-Familie). Deshalb `open`, Ursache im
Klartext, **Frist 30.08.** — der Termin trägt die Aussage, die sonst der Status getragen hätte.

**Zwei kleinere Punkte mit erledigt:** `pm/T-0003` hat sein fehlendes `takt`-Feld bekommen
(`je-session`); der Beleg stand im Ticket selbst („prüft je Routine-Session") — der Titel nennt
den *Anlass*, `takt` den *Rhythmus des Aufgreifens*, und diese Verwechslung war der Grund für das
Zögern der Vorsession. Ein **ereignisgebundener** Takt fehlt `TAKTE` weiterhin und bleibt bei
`pm/T-0032` (Frist 19.08.). Und **Pool-Kandidat #13** ist aus der Kandidatenliste heraus — nicht
gelöscht, sondern in einen neuen Abschnitt **„Realisiert"** verschoben, mit dem Weg (Team +
Projekt) und den Belegen; ein Kandidat, der geräuschlos verschwindet, sieht aus wie einer, den
nie jemand wollte (B029). Nächste freie Nummer bleibt 14.

**Fremde Änderung in `team-mail` geprüft, nicht verworfen und nicht mitverbucht (B041).** Preflight
meldete beim Start eine unsaubere Arbeitskopie an `digest/2026-08-16-woche-digest.md` — einer
Datei, die diese Session nie angefasst hat. Der Diff umfasst **zwei Zeilen mit identischem Text**,
Unterschied ausschließlich **CRLF statt LF**; ohne Zeilenenden bitgleich (`md5sum` gegengeprüft).
Herkunft: der Zustellschritt am Host um 15:45. In-place zurückgesetzt (`git checkout` scheitert am
bekannten `unable to unlink` des Mounts, R7 — Überschreiben ohne Löschen ist der Ausweg aus
`pm/T-0023`). `git diff` ist leer; dass `git status` die Datei weiter als geändert zeigt, ist der
nicht durchlaufende Index-Refresh, kein Inhalt. **Bewusst kein Commit** — eine Historienzeile über
null inhaltliche Änderung behauptet etwas, das nicht stattgefunden hat.

**329 Tests, Matrix 96 SWRs / 0 Lücken, Katalog- und Architektur-Gate grün** — diese Session hat
keinen Code geändert, deshalb keine neuen Tests: Projektanlage und Verbuchung sind Dokumente und
Ticketzustände, und ein Test, der nur bezeugt, dass eine Datei existiert, prüft nichts.

**⚠ Beobachtung, offen: ein Testlauf war einmal rot, und die Testnamen sind verloren.** Der
Abschluss-Preflight meldete einmalig `FAILED (failures=4)`; sechs anschließende Läufe der Suite
und zwei weitere Preflight-Läufe waren grün — nicht reproduzierbar. Verfolgen ließ es sich
nicht, weil `preflight.unit_tests` die Ausgabe auf die **letzten drei Zeilen** kürzt: bei einem
roten Lauf ist das die Zusammenfassung, die `FAIL:`-Zeilen mit den Namen stehen darüber und
werden verworfen. Der Fehlschlag ist also sichtbar, aber unbrauchbar — dieselbe Familie wie B038,
eine Stufe später. Als CR vermerkt (bei `returncode != 0` die Fehlerzeilen mitgeben); **nicht auf
Verdacht repariert**, weil ohne Testnamen jede Änderung geraten wäre. **Zweimal aufgetreten**,
beide Male in einem Preflight-Lauf direkt nach einem `git commit`, nie in einem nackten Suite-Lauf
— Verdacht: parallele Git-Aktivität gegen einen nicht ganz hermetischen Test (B038, dritter Teil).
Eine naheliegende Spur ist **ausgeschlossen und dokumentiert**, damit sie niemand zweimal geht:
`TestLockArtefakte` hat genau vier Tests und nagelt als einzige Klasse `git_prozess_aktiv` nicht
fest — mit erzwungenem `True` bleiben trotzdem alle vier grün. Verwandt mit `pm/T-0010`.

Push: `PUSH-ANFORDERUNG.txt` aus der 15:35-Session war beim Sessionstart **bereits abgearbeitet**
(Wächter-Erfolg **15:45:30**, Log `OK - alles geprueft und gepusht`) — diese Session schreibt am
Ende eine neue Zeile für ihre eigenen Commits (Repos: projects, pm, p0; `team-dashboard` bleibt
lokal-only, bis das GitHub-Repo besteht). `pm/T-0010`/`T-0013`/`T-0026` bleiben unverändert
`in_review` (kein `gh`/Netzzugriff in dieser Sandbox). `pm/T-0034` (team-mail-Autopilot, Frist
17.08.) bleibt offen — nur am Host lösbar. Alle Änderungen committet, `preflight.py` meldet
STARTKLAR.

---

### Stand davor

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

**⬜ NEU (16:50-Session): `pm/T-0035` liegt in der Inbox — Klasse A, drei Knöpfe, Frist 23.08.,
Default AK-b.** Es geht um `p0/T-0008`, den Anthropic-API-Key (~20 € Limit nach `D003`). Das
Ticket steht seit dem **05.08.** offen, hochpriorisiert und ohne Termin — und ist damit das
**einzige offene Ticket in zwei abgeschlossenen Projekten**. Du hast es zweimal vertagt (`D008`,
`D015`), P0 wurde **mit** dieser Abweichung abgenommen (Kriterium 9 „teilweise", Backlog-Punkt
B9), P1 hat es als Epic E5 „optional nach Budgetfreigabe" mitgenommen und ist inzwischen ebenfalls
geschlossen. **Der Zwilling aus demselben Kriterium — der Copilot-Lauf — ist längst `rejected`
(`p0/T-0072`, `p1/T-0018`); dieser hier blieb stehen.** Das Team hat die Belegkette ins Ticket
nachgetragen, aber **nicht entschieden**: Ein API-Key ist eine Budget- und Zugangsfreigabe, und
das gilt in beide Richtungen. **AK-a** jetzt umsetzen (Key anlegen, erster Claude-Tick mit
Kostendaten, Kriterium 9 wird voll erfüllt — der Executor ist gebaut und getestet, es fehlt nur
der Key). **AK-b** schließen wie den Zwilling (Empfehlung; die Organisation läuft seit dem 05.08.
auf Cowork-Session + Ollama, 0,00 € API — Wiederaufnahme kostet ein neues Ticket, nichts wird
zurückgebaut). **AK-c** offen lassen mit einer Frist, die du setzt. Ohne Antwort bis zum 23.08.
gilt **AK-b** — Schweigen soll nie Geld ausgeben oder neue Credentials anlegen.

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

**⚠ BEFUND pm/T-0017 (Routine-Session, B024) — bitte zuerst lesen: Eine Entscheidung, die dir nie vorgelegt wurde.** Beim Pflichtpunkt „Inbox prüfen" lieferte die Inbox eine **leere Liste** — obwohl Agenda und dieser Statusbericht seit heute Vormittag sagen, der G1-Antrag `p10/T-0002` warte dort auf dich. Ursache: `aggregation.projekte()` fand `p10` korrekt, aber **vier** Stellen bauten den Pfad danach selbst als `root/<name>` zusammen; für ein Projekt im Sammel-Repo ergibt das `./p10` statt `./projects/p10` — Ordner existiert nicht, **null Tickets, keine Fehlermeldung**. Betroffen: Inbox (SWR-027), Inbox-Zähler (SWR-076), Übersicht (SWR-026), Entscheidungshistorie (SWR-042) — und, am schwersten, die **Frist-Warnmail (SWR-033/034)**. Heißt konkret: Am 23.08. wäre der Default **G1a** gelaufen und P10 Sprint 1 hätte begonnen, ohne dass du den Antrag je gesehen oder auch nur eine Warnmail bekommen hättest. Genau das schließt Playbook Kap. 16 aus. Verschärfend: Dass hier „liegt in deiner Inbox" stand, hat die Lücke zugedeckt. **Behoben** — alle vier Stellen nutzen jetzt `aggregation.projekt_pfad`, dazu **8 Tests (6 mit nachgewiesener Deckung), die gegen den alten Code nachweislich scheitern**; kein neuer SWR (SWR-070 war richtig, nur unvollständig umgesetzt). Es ist derselbe Fehler wie in p9/T-0007 vom Vormittag, nur eine Ebene tiefer — die Lesson war richtig und wurde zu eng angewendet; sie ist jetzt aufs ganze Repo verschärft (B025). **210 Tests, Matrix 83/0, 0,00 € API.** **Die Frist von `p10/T-0002` bleibt unverändert 23.08.** — sie zu verschieben wäre ein Eingriff in einen Klasse-A-Vorgang; wenn dich die verlorenen Tage stören, genügt ein Wort im Briefkasten. **Deine Stichprobe: Server neu starten, Inbox öffnen — steht der G1-Antrag jetzt da?**

**Brief platform/N-0002 beantwortet und behoben (B023):** Der `ConnectionResetError`-Traceback (WinError 10054) in deinem Server-Log war **kein Fehler** — ein Gerät in deinem LAN (sehr wahrscheinlich das Handy) kappt die offen gehaltene Verbindung, wenn du den Bildschirm sperrst oder den Tab schließt. Trotzdem behoben, weil ein Log, in dem Normalvorgänge wie Abstürze aussehen, den nächsten *echten* Traceback unsichtbar macht: Ab jetzt steht dort eine Klartextzeile statt fünfzehn Zeilen Stack. Gefangen werden **nur** die drei Abbruch-Arten, echte Fehler behalten ihren vollen Traceback (zwei Tests sichern genau das ab). Nebenbefund mitgeprüft: Der Ruhe-Zähler des Selbst-Neustarts (SWR-073) wird auch im Abbruchfall freigegeben — sonst hätte ein einziger Handy-Abbruch den Server dauerhaft als „beschäftigt" markiert. Nachweis: Symptom nachgestellt, **vorher 2 Tracebacks, nachher 0**, Folge-Anfrage weiter `200`. `pm/T-0016`, kein neuer SWR.

**Brief N-0018 sofort erledigt (B022):** Der **Team-Chat zeigt die neuesten Nachrichten zuerst** (SWR-083, P4-Fläche v1.1, pm/T-0015). Gedreht wird nur die Anzeige — die API liefert weiterhin chronologisch (SWR-050 unverändert), umgekehrt wird eine Kopie der Liste, damit andere Leser derselben Daten unberührt bleiben. **Das Schreibfeld ist mit nach oben gewandert**: nicht verlangt, aber zwingend, weil es sonst hinter dem gesamten Verlauf läge und man zum Schreiben erst durch alles scrollen müsste — im Brief ausdrücklich benannt, damit du widersprechen kannst. **199 Tests, Matrix 83/0, 0,00 € API.** Deine Stichprobe: Server neu starten, Team-Chat von `pm` öffnen — N-0018 oben, Schreibfeld direkt unter der Kopfkarte, auf dem Handy genauso.


</details>
