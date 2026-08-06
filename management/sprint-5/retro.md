# Retrospektive Sprint 5 — P0 „Genesis" (COACH)

*2026-08-07, Rollen-Kontexte der Session. Regel: max. 3 Verbesserungs-CRs (Playbook Kap. 8).*

## Was lief gut

- **E2E-Nachweis vollendet:** SWE.1–SWE.6, realer Problem-Zyklus (BOM aus echter Integrationsverifikation), realer CR (Mensch-Feedback → Routing → Impact → Umsetzung), Release mit G3 — der komplette Playbook-Maschinenraum lief einmal durch, mit Evidenz je Schritt.
- **Retro-CRs S4 wirkten sofort:** Die T-0051-Validierung fand beim Erstlauf den in der Retro übersehenen Bestands-DR T-0022; T-0050-Erweiterung nahm das Produkt-Repo in Preflight auf; T-0061 war der erste DR mit maschinenlesbaren Optionen.
- **Feedback-Routing v1 traf im Erstlauf** die richtige Klassifikation; Produktkatalog v0 ist mit dem ersten Release live.
- 12 Tickets done, 0,00 € API-Kosten, Suiten 92 → 101 (platform) und 39 → 42 (produkt), beide Matrizen 0 Lücken.

## Was hakte (ehrlich)

1. **Statuswechsel von Hand sind fehleranfällig:** Ein Commit-Versuch übersprang in_progress und wurde von der Übergangsprüfung korrekt geblockt — gut, aber vermeidbar: Es fehlt eine Skript-Route für Statuswechsel (Session nutzt sed statt `setze_status`-Mechanik des Orchestrators).
2. **Feedback-Abschluss zweistufig:** Das Feedback bleibt nach Routing in_progress, bis das Folge-Ticket done ist — der Abschluss musste manuell nachgezogen werden.
3. **Produkt-Matrix-Aufruf ist parameterlastig:** vier Optionen je Aufruf; die Produkt-Parameter (tests/swr/id-muster) gehören in eine Konfigurationsdatei.

## Verbesserungs-CRs für Sprint 6 (max. 3)

| CR | Inhalt | Erwartungswert (messbar) |
|---|---|---|
| T-0062 | board.py Status-Subkommando (`board.py status T-xxxx <neu> [--reviewer r]`) mit Übergangsprüfung + BOARD-Regeneration — Session und Tick nutzen denselben Pfad | 0 geblockte Status-Commit-Versuche |
| T-0063 | feedback_route v1.1: Feedback schließt automatisch, wenn das Folge-Ticket done ist (Abschluss-Lauf) | 0 manuell nachgezogene Feedback-Abschlüsse |
| T-0064 | Produkt-Konfig `produkte.yaml` (tests/swr/id-muster je Produkt); `trace_matrix --produkt <name>` | Ein-Parameter-Matrix-Aufruf je Produkt |

Nicht als CR gezogen: Katalog-CI-Automatik (bewusste v0-Abweichung, Wiedervorlage nach P0).
