# G1-Vorlage: Freigabe der Plattform-Anforderungs-Baseline (Sprint 2, T-0021)

*An: Mensch (Auftraggeber). Von: RM. Datum: 2026-08-06. Gate: G1 (Anforderungs-Baseline der eigenen Werkzeuge, P0 Sprint 2).*

## Was zur Freigabe vorliegt

Das erste echte SWE.1-Set des Teams — die Anforderungen an die eigene Plattform (Englisch, D011):

- **12 Stakeholder-Anforderungen** (`requirements/stakeholder/`): STK-001–011 reviewed, STK-012 (Backend/Frontend) draft.
- **21 SW-Anforderungen** (`requirements/software/`): SWR-001–019 reviewed (in Sprint 1/2 implementiert, durch die 62-Tests-Suite bzw. CI abgedeckt), SWR-020/021 draft (Sprint 3, nicht Baseline-Umfang).
- Traceability STK ↔ SWR vollständig (Zusammenfassung am Set-Ende); DoD-Checkliste `process/checklists/dod-sw-anforderung.md` angewandt.

## Baseline-Umfang

**STK-001–011 + SWR-001–019** als Anforderungs-Baseline; draft-Anforderungen (STK-012, SWR-020/021) bleiben außerhalb und reifen in Sprint 3. Nach Freigabe setzt CM den Tag (Bestandteil `genesis-v0.2`, T-0023); Änderungen danach nur per CR (SUP.10).

## Offene Punkte (ehrlich, QM-geprüft)

1. Die Zuordnung „SWR ↔ einzelner Unit-Test" ist auf Suite-Ebene belegt (test_board/test_gateway/test_orchestrator/test_provider_apifrei); die feingranulare, CI-generierte Traceability-Matrix kommt mit dem Backend (Sprint 3).
2. SWR-019 (CI) ist committet, aber der erste echte Actions-Lauf auf GitHub steht aus (Push + Secret `PLATFORM_READ_TOKEN` nötig, T-0015).
3. Besonderheit: Das Set beschreibt zu großen Teilen bereits implementiertes Verhalten (Requirements holen die Realität ein) — ab jetzt gilt die normale Reihenfolge: erst Anforderung/CR, dann Implementierung.

## Empfehlung

Freigeben. Das Set ist konsistent, verfolgt und durch Tests gedeckt; die offenen Punkte sind nachverfolgt (Sprint 3) und blockieren die Baseline nicht.

**Deine Optionen:** Freigeben („G1 ok") · Freigeben mit Auflagen (benennen) · Zurückweisen (Begründung → Nacharbeit).
