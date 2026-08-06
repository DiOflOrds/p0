# Retrospektive Sprint 4 — P0 „Genesis" (COACH)

*2026-08-06, Rollen-Kontexte der Session. Regel: max. 3 Verbesserungs-CRs (Playbook Kap. 8).*

## Was lief gut

- **Erster kompletter fremder SWE-Durchlauf:** SWE.1→SWE.4 am Übungsprodukt in einer Session — Clarifications, G1, Architektur mit G2, Implementierung, 31 Tests, Matrix 17/17 SWRs ohne Lücke. Mensch-Beteiligung exakt wie im P0-Zielbild (Auftrag präzisieren, Gates, DRs).
- **Retro-CRs S3 wirkten im selben Sprint:** DR-Template/Inbox-Validierung (T-0039) und Matrix-CI-Gate (T-0037) standen bereit; T-0038 beendet das Status-Rauschen der Warte-Läufe.
- **Re-Planung funktionierte transparent:** D017 (VM gestrichen) mid-sprint ohne Bruch — Plan-Addendum, R2 geschlossen, T-0047 rejected; T-0048 als CR aus laufender Arbeit sauber durchgezogen.
- 11 Tickets done, 0,00 € API-Kosten, Suite 81 → 92 (platform) + 31 (produkt).

## Was hakte (ehrlich)

1. **R7 erneut, zweimal:** Git-index.lock blockierte Commits, bis die Datei-Löschrechte in der Session erteilt waren — Preflight erkennt Locks, kann sie aber nicht selbst räumen.
2. **Produkt-Matrix ohne CI-Gate:** Der datakonv-Matrix-Lauf ist manuell (bräuchte platform-Checkout im Produkt-Workflow — Muster T-0037 existiert bereits).
3. **T-0041 nutzte noch Freitext-Optionen**, obwohl T-0039 im selben Sprint kam (Reihenfolge-Effekt); nichts erzwingt das neue Frontmatter für neue DRs.

## Verbesserungs-CRs für Sprint 5 (max. 3)

| CR | Inhalt | Erwartungswert (messbar) |
|---|---|---|
| T-0049 | Matrix-CI-Gate im Produkt-Repo (platform-Checkout via Secret, `trace_matrix --id-muster`) | Matrix-Lücken brechen die datakonv-CI; 0 manuelle Läufe |
| T-0050 | Preflight räumt verwaiste Git-Locks selbst (Alter > 5 min, kein laufender git-Prozess), sonst klare Meldung | 0 manuelle Lock-Eingriffe je Session |
| T-0051 | board.py: neue decision-request-Tickets ohne `optionen`-Frontmatter werden abgelehnt (Bestands-DRs ausgenommen) | 100 % neue DRs maschinenlesbar |

Nicht als CR gezogen: platform-CI-Rotphase bis zum Secret-Setzen (einmaliger, dokumentierter Zustand — kein Prozessdefekt).
