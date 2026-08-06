# Verifikationsstrategie Plattform P0 (v1, Sprint 3, T-0034)

*Rolle TEST (SWE.4–SWE.6). Gilt für die Plattform-Repos; Übungs-/Kundenprodukte erhalten ab Sprint 4 eigene Abschnitte.*

## Testebenen und Nachweisarten

| Ebene | Objekt | Nachweis | Automatisierung |
|---|---|---|---|
| Unit (SWE.4) | board, gateway, guardrails, orchestrator, preflight, trace_matrix, backend | `python -m unittest discover tests` — Docstrings tragen SWR-IDs (T-0026) | CI je Push (T-0015) |
| API/Integration (SWE.5) | Backend-HTTP Ende-zu-Ende (ephemerer Port, echte Git-Fixtures) | `test_backend.py::HttpTest` | CI je Push |
| Abnahme (SWE.6) | Frontend (SWR-021), Gate-Deliverables | UI-Abnahme-Checkliste (`reports/ui-abnahme-swr-021.md`); Gate-Vorlagen | manuell, dokumentiert |
| Betrieb | SMTP-Echtversand (SWR-023), Docker-Deployment (Infra) | Betriebsnachweis nach VM-/SMTP-Einrichtung (T-0035) | offen — ehrlich: noch kein Echtnachweis |

## Abdeckungsanspruch

Jede reviewed-SWR ist entweder (a) durch Unit-/API-Tests mit Docstring-ID abgedeckt, (b) durch CI-Workflow-Läufe nachgewiesen oder (c) durch eine dokumentierte manuelle Abnahme belegt — sonst ist sie eine Lücke in der Matrix (`trace_matrix.py`, Lückenliste = Pflichtteil jedes Sprint-Reports). Kein Gefälligkeitsgrün: manuelle Nachweise verweisen auf ein Dokument mit Schritten und Ergebnis.

## Regression und Rote-Stände-Regel

Volle Suite je Push (CI); lokal via Preflight (T-0024). Rot auf main = SUP.9-Problem-Ticket, kein stiller Rerun. Wiederholt instabile Tests werden als Problem geführt, nicht deaktiviert.

## Offene Verifikationsschulden (Stand Sprint 3)

1. SWR-023: Erfolgspfad E-Mail-Versand ungetestet (kein SMTP-Zugang) — Betriebsnachweis nach Einrichtung; Fehlerpfade sind unit-getestet.
2. Docker-Deployment (Infra-as-Code) ungebaut/ungetestet bis Hub-VM existiert (T-0035).
3. CI-Läufe auf GitHub für die Sprint-3-Commits stehen bis zum Push aus (D007).
