# Retrospektive Sprint 3 — P0 „Genesis" (COACH)

*2026-08-06, Rollen-Kontexte der Session. Regel: max. 3 Verbesserungs-CRs (Playbook Kap. 8).*

## Was lief gut

- **Requirements-first hat beim ersten echten Anlauf funktioniert:** SWR-020–024 waren reviewed, bevor eine Zeile MVP-Code entstand; alle 4 Plattform-Tickets trugen SWR-Bezug (T-0025-Erwartungswert: 100 % erreicht).
- **Retro-CRs zahlten sich im selben Sprint aus:** Preflight (T-0024) fing den erneut aufgetretenen R7-Fall ab Verfügbarkeit ab und lief in beiden Ticks als Precondition; die Matrix (T-0026) machte die einzige Lücke (SWR-021) sichtbar und ihre Schließung nachweisbar.
- **Tick-Pfad wieder in Betrieb:** Session-Provider-Zweiphasenlauf end-to-end (Warte-Eintrag, Antwort, selektiver Branch-Commit, in_review) — der QM-Punkt 2 aus Sprint 2 ist abgearbeitet.
- 11 team-seitige Tickets done, 0,00 € API-Kosten, Suite 62 → 81 Tests.

## Was hakte (ehrlich)

1. **R7 erneut vor Preflight-Verfügbarkeit:** Der HEAD.lock-Block trat beim Planning-Commit auf — das Preflight-Skript existierte da noch nicht; zusätzlich kann die Sandbox Mount-Dateien nicht löschen, bis die Berechtigung erteilt ist (neu dokumentiert im Geräteregister).
2. **Zweiphasen-Tick erzeugt Status-Rauschen:** Jeder Warte-Lauf produziert open→in_progress→open-Commits im p0 — verwässert die Wiederöffnungs-KPI und bläht die Historie.
3. **DR-Optionen sind Freitext:** Die Inbox-API akzeptiert jede Options-Zeichenkette; Tippfehler landen ungeprüft im Decision Log (beim ersten echten Inbox-DR T-0035 noch manuell beherrschbar).
4. **CI kann die Matrix noch nicht prüfen:** `trace_matrix.py --check` braucht beide Repos (platform + p0) — der platform-CI-Workflow checkt nur platform aus.

## Verbesserungs-CRs für Sprint 4 (max. 3)

| CR | Inhalt | Erwartungswert (messbar) |
|---|---|---|
| T-0037 | trace-matrix-Gate in CI: p0-Checkout im platform-Workflow (Muster board-check umgekehrt) + `--check`-Step | Matrix-Lücken brechen CI; 0 manuelle Matrix-Läufe nötig |
| T-0038 | Zweiphasen-Tick idempotent: Phase 1 („wartet") ohne Statuswechsel-Commits | 0 open→in_progress→open-Zyklen je Warte-Lauf |
| T-0039 | DR-Struktur maschinenlesbar: Optionen/Frist/Default als YAML-Frontmatter-Felder; Inbox validiert die Option | Ungültige Option → 400 statt Log-Eintrag |

Nicht als CR gezogen: R7-Restrisiko (Preflight + Geräteregister-Hinweis gelten als ausreichend; Wirkung wird in Sprint 4 gegen den Erwartungswert „0 Blöcke" geprüft).
