# Self-Check gegen die Basispraktiken — P0 „Genesis" (T-0065, QM+COACH)

*2026-08-07. Pragmatisches Arbeits-Mapping (D010, kein PAM-Wortlaut-Audit): je Stufe-1-Prozessgebiet die Kernpraktiken gegen reale Artefakte geprüft — mit Fundstelle und ehrlicher Lückenliste. Grundlage für Abnahmekriterium 3 (P0 Kap. 3).*

| Prozess | Kernpraktiken — Evidenz (Fundstellen) | Bewertung | Lücken → Maßnahme |
|---|---|---|---|
| MAN.3 Projektmanagement | Sprint-Pläne 2–6 + Reports + Retros (`p0/management/sprint-*/`), Backlog EP1–EP9, Risikoliste R1–R8 (gepflegt, R2/R8 geschlossen), Decision Log D000–D023 (append-only), transparente Re-Planung (D017, Plan-Addendum) | **belegt** | Aufwandsschätzung/Kalenderplanung rudimentär (Sprints als Arbeitspakete ohne Terminplan) → **P1-Backlog** |
| SWE.1 Anforderungen | 2 reale Sets: Plattform (STK-001–012, SWR-001–024) + Produkt (STK-D01–D05, SWR-D01–D18); Clarifications an den Menschen (T-0043, T-0059); DoD-Checkliste je SWR; G1-Gates D013/D015/D018; Änderungen nur baselineiert (req-v1.0→v1.1) | **belegt** | — |
| SWE.2 Architektur | `platform/architecture/` + `produkt-datakonv/docs/` (Units, Schnittstellen, ADR-001–003 + ADR-D01–D03), SWR↔Unit-Zuordnung vollständig, G2-Gates D015/D019 | **belegt** | — |
| SWE.3 Implementierung | Units mit SWR-Referenz je Commit (T-0025-Regel, 100 %), DoD Code, requirements-first nachweislich (SWR-D18 reviewed vor Code) | **belegt** | Unabhängigkeit der Code-Reviews eingeschränkt (Rollen-Kontexte derselben Session, Bootstrap) → **P1-Backlog** |
| SWE.4 Unit-Verifikation | Suiten 112 (platform) + 42 (produkt) grün in CI; Matrizen 24/0 und 18/0 Lücken, CI-Gates in 3 Repos | **belegt** | — |
| SWE.5/6 Integration/SW-Verifikation | E2E-Suite (reales CLI, 8 Szenarien), Integrationsverifikations-Report, Roundtrip-Nachweis, Befund→Problem-Kette (T-0052→T-0053) | **belegt** | Integrationsstrategie nur implizit (in Verifikationsstrategie v1 nicht als eigener Abschnitt) → **P1-Backlog** |
| SUP.1 Qualitätssicherung | reviewer≠autor je Ticket (board-erzwungen), DoD-Checklisten, QM-Abschnitte „ungefiltert" in jedem Report, QM-Mitzeichnung aller Baseline-Manifeste | **belegt** | Wie SWE.3: Review-Unabhängigkeit (Bootstrap-Modus dokumentiert in jedem Report) → **P1-Maßnahme:** externe Stichproben (Mensch/Zweitsession) |
| SUP.8 Konfigurationsmanagement | CM-Strategie v1.1 mit realer Landkarte, Baselines genesis-v0.1–v0.5 + Manifeste, Release-Tags v1.0.0/req-v1.x, Geräteregister, .gitignore-Hygiene | **belegt** | Betriebs-Runbook → **in diesem Sprint (T-0067)** |
| SUP.9 Problemmanagement | Realer Zyklus mehrfach: T-0013/T-0014 (Sprint 1), T-0040 (Sprint 3), **T-0053** (Produkt, mit Ursache/Korrektur/Wirksamkeit); Feedback-Routing v1.1 | **belegt** | — |
| SUP.10 Änderungsmanagement | 14 Prozess-CRs mit messbaren Erwartungswerten (Retro-Mechanik), Produkt-CR T-0060 mit dokumentierter Impact-Analyse, Anforderungsänderungen nur per CR + Baseline | **belegt** | — |
| SPL.2 Release | Release 1.0.0: Tag + Manifest-Prinzip, Release Notes, G3-Gate (D021), Katalog-Registrierung | **belegt** | Distribution nur Git/`pip install .` (kein Registry-Publish) → bewusster Schnitt, **P1+** |
| REU.2 (light) Katalog | `process/catalog/` mit Generator-Skript, 1 Eintrag | **teilweise** | CI-Automatik + MCP-Verpackung → bewusste Abweichung, **nach P0** |

## Zusammenfassung

Alle Stufe-1-Prozessgebiete sind mit realen Artefakten belegt; 5 benannte Lücken, davon 1 in diesem Sprint geschlossen (Runbook) und 4 begründet ins P1-Backlog übernommen (T-0066). Die wiederkehrende strukturelle Einschränkung ist die Review-Unabhängigkeit im Bootstrap-Modus — in jedem Sprint-Report offen ausgewiesen und durch die Mensch-Gates (G1–G4) kompensiert.
