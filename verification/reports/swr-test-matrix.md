# SWR ↔ Test-Matrix (generiert von platform/scripts/trace_matrix.py — nicht von Hand editieren)

Stand: 2026-08-06 · SWRs: 21 (reviewed: 19) · Tests mit SWR-Bezug: 62 · ohne Bezug: 9

| SWR | Status | Unit-Tests | Abdeckung |
|---|---|---|---|
| SWR-001 | reviewed | test_board.py::TestBoard::test_gutfall<br>test_board.py::TestBoard::test_pflichtfeld_fehlt<br>test_board.py::TestBoard::test_ungueltiger_status<br>test_board.py::TestBoard::test_id_dateiname_mismatch<br>test_board.py::TestBoard::test_blocked_ohne_blocker<br>test_board.py::TestBoard::test_in_review_ohne_reviewer<br>test_board.py::TestBoard::test_in_review_reviewer_ist_autor<br>test_board.py::TestBoard::test_in_review_mit_reviewer_ok<br>test_board.py::TestBoard::test_crlf_toleranz | 9 Test(s) |
| SWR-002 | reviewed | test_board.py::TestBoard::test_uebergangsmatrix<br>test_board.py::TestBoard::test_mensch_tickets_ohne_uebergangspruefung | 2 Test(s) |
| SWR-003 | reviewed | test_board.py::TestBoard::test_blocked_by_unbekannt<br>test_board.py::TestBoard::test_blocked_by_selbstverweis | 2 Test(s) |
| SWR-004 | reviewed | test_board.py::TestBoard::test_board_deterministisch<br>test_board.py::TestBoard::test_prio_sortierung<br>test_board.py::TestBoard::test_offene_blocker<br>test_board.py::TestBoard::test_main_schreibt_board | 4 Test(s) |
| SWR-005 | reviewed | test_board.py::TestBoard::test_main_check_modus<br>test_board.py::TestBoard::test_main_fehlerfall | 2 Test(s) |
| SWR-006 | reviewed | test_gateway.py::GatewayTest::test_vertrag_ok<br>test_gateway.py::GatewayTest::test_unbekannter_provider | 2 Test(s) |
| SWR-007 | reviewed | test_gateway.py::GatewayTest::test_kettenfallback_bei_notimplemented<br>test_gateway.py::GatewayTest::test_claude_ohne_key_nicht_verfuegbar<br>test_orchestrator.py::RoutingTest::test_aufgaben_typ_kette<br>test_orchestrator.py::RoutingTest::test_default_kette<br>test_provider_apifrei.py::OllamaExecutorTest::test_nicht_erreichbar_faellt_in_kette_zurueck | 5 Test(s) |
| SWR-008 | reviewed | test_gateway.py::GatewayTest::test_stub_executoren_nicht_verfuegbar<br>test_provider_apifrei.py::SessionExecutorTest::test_phase1_erzeugt_prompt_und_wartet<br>test_provider_apifrei.py::SessionExecutorTest::test_phase2_liest_antwort_ein<br>test_provider_apifrei.py::SessionExecutorTest::test_antwort_ohne_bloecke_kein_erfolg<br>test_provider_apifrei.py::SessionExecutorTest::test_wartet_wird_protokolliert<br>test_provider_apifrei.py::OllamaExecutorTest::test_modellwahl | 6 Test(s) |
| SWR-009 | reviewed | test_orchestrator.py::ArbeitskopieTest::test_auftrag_enthaelt_repo_hinweis<br>test_provider_apifrei.py::DateiblockTest::test_parse_zwei_bloecke<br>test_provider_apifrei.py::DateiblockTest::test_parse_crlf<br>test_provider_apifrei.py::DateiblockTest::test_pfad_traversal_verboten<br>test_provider_apifrei.py::DateiblockTest::test_schreiben<br>test_provider_apifrei.py::DateiblockTest::test_keine_bloecke<br>test_provider_apifrei.py::DateiblockTest::test_repo_praefix_wird_entfernt<br>test_provider_apifrei.py::DateiblockTest::test_repo_praefix_nur_bei_treffer | 8 Test(s) |
| SWR-010 | reviewed | test_gateway.py::GatewayTest::test_modellaufloesung<br>test_orchestrator.py::RoutingTest::test_gate_relevanter_typ | 2 Test(s) |
| SWR-011 | reviewed | test_gateway.py::GatewayTest::test_tick_limit_ueberschreitung_bricht_ab<br>test_gateway.py::GatewayTest::test_unvollstaendige_guardrails | 2 Test(s) |
| SWR-012 | reviewed | test_gateway.py::GatewayTest::test_monatslimit_verhindert_lauf<br>test_gateway.py::GatewayTest::test_monatsreserve_zu_klein<br>test_gateway.py::GatewayTest::test_monatskosten_nur_laufender_monat | 3 Test(s) |
| SWR-013 | reviewed | test_gateway.py::GatewayTest::test_run_registry_wird_geschrieben | 1 Test(s) |
| SWR-014 | reviewed | test_gateway.py::GatewayTest::test_verbotene_aktion | 1 Test(s) |
| SWR-015 | reviewed | test_orchestrator.py::ArbeitskopieTest::test_sauber<br>test_orchestrator.py::ArbeitskopieTest::test_unsauber<br>test_orchestrator.py::ArbeitskopieTest::test_ausnahme_praefix | 3 Test(s) |
| SWR-016 | reviewed | test_orchestrator.py::AuswahlTest::test_waehlt_hoechste_prio<br>test_orchestrator.py::AuswahlTest::test_ignoriert_nicht_open<br>test_orchestrator.py::AuswahlTest::test_ignoriert_blockierte<br>test_orchestrator.py::AuswahlTest::test_blocker_done_gibt_frei<br>test_orchestrator.py::AuswahlTest::test_ignoriert_inaktive_und_mensch_rollen<br>test_orchestrator.py::RoutingTest::test_script_route | 6 Test(s) |
| SWR-017 | reviewed | test_orchestrator.py::StatusTest::test_setze_status_und_board<br>test_orchestrator.py::StatusTest::test_setze_status_invalide_wirft<br>test_orchestrator.py::SlugTest::test_slug | 3 Test(s) |
| SWR-018 | reviewed | test_orchestrator.py::AuswahlTest::test_nur_ticket_filter | 1 Test(s) |
| SWR-019 | reviewed | — | über CI-Workflow verifiziert (kein Unit-Test) |
| SWR-020 | draft | — | offen (Status draft) |
| SWR-021 | draft | — | offen (Status draft) |

## Lücken (reviewed ohne Testabdeckung)

Keine.

## Tests ohne SWR-Bezug (informativ — Prozess-Tooling mit CR-Bezug erlaubt, T-0025)

- test_preflight.py::TestLockArtefakte::test_findet_bekannte_artefakte
- test_preflight.py::TestLockArtefakte::test_sauberes_repo_ohne_funde
- test_preflight.py::TestLockArtefakte::test_entfernen_meldet_erfolg
- test_preflight.py::TestLockArtefakte::test_entfernen_meldet_fehlschlag
- test_preflight.py::TestPreflightGesamt::test_fehlende_repos_sind_befunde
- test_trace_matrix.py::TestScannen::test_methode_vor_klasse_vor_modul
- test_trace_matrix.py::TestScannen::test_ohne_bezug_wird_gemeldet
- test_trace_matrix.py::TestMatrix::test_luecken_und_ci_ausnahme
- test_trace_matrix.py::TestMatrix::test_unbekannte_swr_in_tests_ist_luecke
