# G1-Erweiterungsvorlage — Backend/Frontend-MVP (Sprint 3, T-0030)

*An: Mensch (Gate G1, Anforderungs-Baseline-Erweiterung zu D013). Von: RM. Datum: 2026-08-06.*

## Gegenstand

Erweiterung der Anforderungs-Baseline (D013: STK-001–011 + SWR-001–019) um den Backend/Frontend-MVP:

- **STK-012** (präzisiert): Backend/Frontend zur Steuerung ohne Git-Rohzugriff; MVP-Schnitt fixiert: lesend + Decision-Inbox (P0 Kap. 8); Live-Updates/Push außerhalb des P0-Scopes.
- **SWR-020** (präzisiert): Decision-Inbox-API — offene DRs listen (Optionen/Frist/Default), Entscheidung entgegennehmen, ins Decision Log und ans Ticket schreiben.
- **SWR-021** (präzisiert): Frontend-Ansichten Board/Reports/Kosten-KPI/Inbox inkl. Entscheidungsabgabe, smartphone-tauglich, ohne Git-Zugriff.
- **SWR-022** (neu): Read-only-Aggregations-API aus den Git-Artefakten (Board, Sprint-Reports, Run-Registry-Kosten).
- **SWR-023** (neu): E-Mail-Benachrichtigung (D004) über SMTP; Ausfall des Versands legt die API nicht lahm.
- **SWR-024** (neu): Kein Zustand außerhalb der Git-Arbeitskopie; Neustart verlustfrei (verteilungsfähig, API-first — P0-Architektur-Leitplanke).

## Review-Status

DoD-Checkliste „SW-Anforderung" angewandt (alle 6: eindeutige ID, atomar, testbar, Trace auf STK, Verifikationskriterium benannt). Reviews: Machbarkeit (ARCH-Kontext, T-0031 — Architektur ordnet alle 5 SWR Komponenten zu), Prüfbarkeit (QM/TEST-Kontext — je SWR API-/Abnahmetest benannt). Traceability-Zusammenfassung aktualisiert, keine SWR ohne STK-Trace.

## Empfehlung

Freigabe als Baseline-Erweiterung; Tag erfolgt mit der Sprint-3-Baseline (`genesis-v0.3`, CM). Bis zur Freigabe gelten die 6 Einträge als reviewed, aber nicht baselined; Implementierung (T-0032/T-0033) läuft auf eigenes Risiko des Teams gegen den reviewten Stand (requirements-first eingehalten).

**Entscheidung Mensch:** ☑ **freigegeben** (2026-08-06, D015) — Baseline-Erweiterung Bestandteil von `genesis-v0.3`.
