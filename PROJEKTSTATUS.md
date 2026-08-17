# Projektstatus — Fortschreibung über Sessions

## Das Wichtigste (Stand Sprint 7, 2026-08-17)

1. **✅ Zum ersten Mal meldet `CI-STATUS.md` ALLES GRÜN — 14 Abfragen, kein rotes Repo.**
   `p3` und `p5` sind grün für ihren Commit (`673eacd9`, `0fde98c3`). Damit ist
   **`pm/T-0043` nach fünf Sprints geschlossen** und die widerlegbare Vorhersage aus
   Sprint 6 ist **eingetroffen**.
2. **Die Ursache war eine Abwesenheit, kein Defekt.** Beide Repos trugen einen Stand vom
   16.08. 07:0x, erzeugt von einer `board.py`-Fassung vor der Takt-Spalten-Änderung —
   und bekamen danach nie wieder einen Push. **Ohne Push kein CI-Lauf:** das „ROT" war
   ein Standbild und wurde vier Sprints lang als laufende Störung gelesen.
3. **⚠ Der Startcheck fand, dass Sprint 6 eine Anforderung gemeldet, aber nie committet
   hat.** „Matrix 109 SWRs / 0 Lücken" galt für die **Arbeitskopie**; im Git standen 108.
   Der Plattformcode für SWR-109 und seine sieben Tests waren gepusht — das Requirement
   nicht. Für einen Tag trug die Organisation Code ohne Anforderung im Git.
4. **⚠ Und der eigentliche Befund ist, warum es niemand sah.** `preflight` **hatte** es
   gemeldet: `[p9] Arbeitskopie nicht sauber (1 Datei(en))`. Daneben standen **fünf**
   gleich aussehende Zeilen, alle mit `1 Datei(en)`, alle eine `BOARD.md`, deren
   `Stand:`-Zeile das Werkzeug bei **jedem** Lauf neu erzeugt. Sechs identische Meldungen,
   fünf davon dauerhaft belanglos — die sechste hatte keine Chance.
5. **Sechs Sachtickets geschlossen:** `pm/T-0043`, `platform/T-0010` (neu, im selben
   Sprint), `team-dashboard/T-0002`, `pm/T-0045`, `pm/T-0046`, `pm/T-0036`. Dazu die sechs
   Takt-Pflichten.
6. **⚠ Und die Schlussverifikation hat einen eigenen Fehler dieses Laufs gefunden.**
   `board.py --check` hält den Status gegen HEAD und ist damit **blind für einen bereits
   committeten** Sprung: `pm/T-0043` und `team-dashboard/T-0002` sind mit `open -> done`
   in die Historie gegangen, weil zwischen Setzen und Commit nicht geprüft wurde. Die drei
   noch unverbuchten wurden erwischt und korrekt nachgeholt. Als `pm/T-0048` aufgenommen,
   **nicht** nachträglich geglättet.
7. **⚠ Zum zweiten Mal in zwei Sprints ist ein Verschiebungsgrund an der Messung
   gescheitert** — `pm/T-0036`: „Änderung an der Prüfstrecke, nicht nebenbei" gegen
   **0 unterminierte Tickets im Bestand** gehalten.
8. **568 Tests grün** (+54), Matrix **114 SWRs / 0 Lücken**, Preflight STARTKLAR, kein
   offener Brief, unterminiert 0, überfällig 0, Plan-Drift 0, sprint_vergangen 0.

---

## Aktueller Stand

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
