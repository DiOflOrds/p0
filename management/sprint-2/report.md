# Sprint-2-Report — P0 „Genesis" (FINAL)

*Stand: 2026-08-06, Rolle: PL. **Sprint 2 abgenommen (G4, D013)**, Anforderungs-Baseline freigegeben (**G1**, D013), Budget-Review entschieden (**D012**: Testphase bestätigt). Baseline `genesis-v0.2` getaggt (T-0023). Retrospektive: `retro.md` (3 Prozess-CRs T-0024–T-0026).*

## Sprint-Ziel und Erreichung

Ziel („Prozesse & Selbstübernahme"): Das Team führt P0 selbst; die Requirements-Mechanik steht. **ERREICHT:** Sprint 2 wurde vom PL-Kontext geplant (plan.md, Tickets, Board) und vom Team in Rollen-Kontexten abgearbeitet; QM, RM, PROB, CHG sind scharfgeschaltet (Bootstrap-Stufe 2 nach P0 Kap. 1). Das erste echte SWE.1-Set (Plattform-Anforderungen, Englisch per D011) ist erstellt, reviewt und als G1-Baseline freigegeben.

## Ticket-Bilanz

Sprint 2: **9 von 9 team-seitigen Tickets done** — T-0015 (CI-Workflows), T-0016 (Wissensbasis CM), T-0017 (BP-Plausibilitätsreview, F7/D010), T-0018 (CM-Strategie v1.1 + Geräteregister), T-0019 (Rollenkarten QM/RM/PROB/CHG + Registry v1.1), T-0020 (Skills SUP.1/SWE.1/SUP.9 + Gold-Beispiele), T-0021 (SWE.1-Set + G1), T-0022 (Budget-DR → D012), T-0023 (Baseline genesis-v0.2). Offen bleibt nur T-0008 (Anthropic-API-Key, Mensch, bewusst).

## Gelieferte Artefakte

process: 4 neue Rollenkarten, Registry v1.1 (7 Rollen aktiv), 3 neue Skills + 3 Gold-Beispiele, Wissensbasis CM (L-001–L-004 + Heuristiken), CM-Strategie v1.1, Geräteregister v1, DoD-Checkliste SW-Anforderung, Baseline-Manifest genesis-v0.2. platform: CI-Workflow (Unit-Tests), guardrails-Update (D012). p0: Sprint-2-Plan, 12 STK + 21 SWR mit Traceability + G1-Vorlage, board-check-CI-Workflow, Decision Log D010–D013, dieser Report + Retro.

## Kosten

0,00 € API-Kosten (kumuliert seit Sprint 0: 0,00 €) — gesamte Sprint-2-Arbeit in der Cowork-Session (Abo). Budget-Review D012: Testphase 20 €/Monat bestätigt, nächstes Review Sprint 4 mit Claude-Ist-Daten.

## Risiken (Delta)

R1 (Bootstrap-Zirkel) **entschärft**: Stufe 2 erreicht. R5 (Budget zu knapp) **entschärft**: 0 € Verbrauch. R7 (Sandbox-/Mount-Artefakte, aus Sprint 1 nachgetragen) **erneut eingetreten**: stale `index.lock` in allen drei Repos blockierte Git, bis Löschrechte erteilt waren → Prozess-CR T-0024 (Preflight-Skript). **Neu R8**: p0-CI hängt am Secret `PLATFORM_READ_TOKEN` (Mensch-Aktion) — bis dahin ist der board-check auf GitHub rot; klare Fehlermeldung eingebaut.

## QM-Abschnitt (ungefiltert)

(1) Alle Rollen liefen als Kontexte einer Session (D007-bedingt); Vier-Augen-Prinzip über Reviewer-Felder (nie Autor-Rolle) + Mensch-Gates abgebildet — echte getrennte Agenten erst mit Team-Node-Ticks/VM. (2) T-0018 war als „zweiter autonomer Tick" vorgesehen, lief aber als Session-Arbeit, weil die Sandbox den Ollama-Dienst des Team-Nodes nicht erreicht; der Tick-Pfad bleibt damit seit Sprint 1 ungenutzt — auf dem Team-Node nachholbar (`tick.py --repos .`, T-0025-Kandidatenticket wäre geeignet). (3) Die CI-Workflows sind committet und lokal äquivalent verifiziert, aber noch nie auf GitHub gelaufen (Push + Secret ausstehend). (4) Das SWE.1-Set beschreibt überwiegend bereits implementiertes Verhalten (Requirements holen Realität ein) — ab Sprint 3 gilt: erst Anforderung/CR, dann Implementierung (Prozess-CR T-0025). (5) SWR↔Test-Zuordnung nur auf Suite-Ebene belegt (T-0026). (6) Die DoD-Checkliste SW-Anforderung entstand erst während T-0021 — Reihenfolge künftig: Checkliste vor erstem Artefakt des Typs.

## Anstehende Entscheidungen / Mensch-Aktionen

1. `sprint2-abschluss.cmd` ausführen (pusht alle Repos + Tags). 2. Secret `PLATFORM_READ_TOKEN` in p0 anlegen (Anleitung im Workflow-Kopf, R8). 3. T-0008 (API-Key) weiterhin offen — nötig für Claude-Stufe und Sprint-3/4-Daten. 4. Offene Fragen: F6, F8–F13 (F5/F7 in Sprint 2 entschieden).
