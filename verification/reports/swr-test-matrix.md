# SWR ↔ Test-Matrix (generiert von platform/scripts/trace_matrix.py — nicht von Hand editieren)

Stand: 2026-08-07 · SWRs: 33 (reviewed: 33) · Tests mit SWR-Bezug: 113 · ohne Bezug: 21

| SWR | Status | Unit-Tests | Abdeckung |
|---|---|---|---|
| SWR-001 | reviewed | test_board.py::TestBoard::test_gutfall<br>test_board.py::TestBoard::test_pflichtfeld_fehlt<br>test_board.py::TestBoard::test_ungueltiger_status<br>test_board.py::TestBoard::test_id_dateiname_mismatch<br>test_board.py::TestBoard::test_blocked_ohne_blocker<br>test_board.py::TestBoard::test_in_review_ohne_reviewer<br>test_board.py::TestBoard::test_in_review_reviewer_ist_autor<br>test_board.py::TestBoard::test_in_review_mit_reviewer_ok<br>test_board.py::TestBoard::test_crlf_toleranz<br>test_board.py::DecisionRequestFelderTest::test_gueltige_felder<br>test_board.py::DecisionRequestFelderTest::test_ungueltige_frist<br>test_board.py::DecisionRequestFelderTest::test_default_nicht_in_optionen<br>test_board.py::DecisionRequestFelderTest::test_neuer_dr_ohne_optionen_abgelehnt<br>test_board.py::DecisionRequestFelderTest::test_bestands_dr_ausgenommen<br>test_board.py::DecisionRequestFelderTest::test_optionstoken_zerlegung | 15 Test(s) |
| SWR-002 | reviewed | test_board.py::TestBoard::test_uebergangsmatrix<br>test_board.py::TestBoard::test_mensch_tickets_ohne_uebergangspruefung<br>test_board.py::SetzeStatusTest::test_gueltiger_uebergang_schreibt_ticket_und_board<br>test_board.py::SetzeStatusTest::test_unzulaessiger_uebergang_wird_abgelehnt<br>test_board.py::SetzeStatusTest::test_in_review_erfordert_reviewer<br>test_board.py::SetzeStatusTest::test_status_cli | 6 Test(s) |
| SWR-003 | reviewed | test_board.py::TestBoard::test_blocked_by_unbekannt<br>test_board.py::TestBoard::test_blocked_by_selbstverweis | 2 Test(s) |
| SWR-004 | reviewed | test_board.py::TestBoard::test_board_deterministisch<br>test_board.py::TestBoard::test_prio_sortierung<br>test_board.py::TestBoard::test_offene_blocker<br>test_board.py::TestBoard::test_main_schreibt_board | 4 Test(s) |
| SWR-005 | reviewed | test_board.py::TestBoard::test_main_check_modus<br>test_board.py::TestBoard::test_main_fehlerfall | 2 Test(s) |
| SWR-006 | reviewed | test_gateway.py::GatewayTest::test_vertrag_ok<br>test_gateway.py::GatewayTest::test_unbekannter_provider | 2 Test(s) |
| SWR-007 | reviewed | test_copilot_executor.py::CopilotExecutorTest::test_fehlende_cli_faellt_zur_naechsten_stufe<br>test_gateway.py::GatewayTest::test_kettenfallback_bei_notimplemented<br>test_gateway.py::GatewayTest::test_claude_ohne_key_nicht_verfuegbar<br>test_orchestrator.py::RoutingTest::test_aufgaben_typ_kette<br>test_orchestrator.py::RoutingTest::test_default_kette<br>test_provider_apifrei.py::OllamaExecutorTest::test_nicht_erreichbar_faellt_in_kette_zurueck | 6 Test(s) |
| SWR-008 | reviewed | test_copilot_executor.py::CopilotExecutorTest::test_fehlende_cli_faellt_zur_naechsten_stufe<br>test_copilot_executor.py::CopilotExecutorTest::test_dateibloecke_werden_eingepflegt<br>test_copilot_executor.py::CopilotExecutorTest::test_cli_fehler_liefert_log_statt_crash<br>test_gateway.py::GatewayTest::test_stub_executoren_nicht_verfuegbar<br>test_provider_apifrei.py::SessionExecutorTest::test_phase1_erzeugt_prompt_und_wartet<br>test_provider_apifrei.py::SessionExecutorTest::test_phase2_liest_antwort_ein<br>test_provider_apifrei.py::SessionExecutorTest::test_antwort_ohne_bloecke_kein_erfolg<br>test_provider_apifrei.py::SessionExecutorTest::test_wartet_wird_protokolliert<br>test_provider_apifrei.py::OllamaExecutorTest::test_modellwahl | 9 Test(s) |
| SWR-009 | reviewed | test_copilot_executor.py::CopilotExecutorTest::test_dateibloecke_werden_eingepflegt<br>test_orchestrator.py::ArbeitskopieTest::test_auftrag_enthaelt_repo_hinweis<br>test_provider_apifrei.py::DateiblockTest::test_parse_zwei_bloecke<br>test_provider_apifrei.py::DateiblockTest::test_parse_crlf<br>test_provider_apifrei.py::DateiblockTest::test_pfad_traversal_verboten<br>test_provider_apifrei.py::DateiblockTest::test_schreiben<br>test_provider_apifrei.py::DateiblockTest::test_keine_bloecke<br>test_provider_apifrei.py::DateiblockTest::test_repo_praefix_wird_entfernt<br>test_provider_apifrei.py::DateiblockTest::test_repo_praefix_nur_bei_treffer | 9 Test(s) |
| SWR-010 | reviewed | test_gateway.py::GatewayTest::test_modellaufloesung<br>test_orchestrator.py::RoutingTest::test_gate_relevanter_typ | 2 Test(s) |
| SWR-011 | reviewed | test_gateway.py::GatewayTest::test_tick_limit_ueberschreitung_bricht_ab<br>test_gateway.py::GatewayTest::test_unvollstaendige_guardrails | 2 Test(s) |
| SWR-012 | reviewed | test_gateway.py::GatewayTest::test_monatslimit_verhindert_lauf<br>test_gateway.py::GatewayTest::test_monatsreserve_zu_klein<br>test_gateway.py::GatewayTest::test_monatskosten_nur_laufender_monat | 3 Test(s) |
| SWR-013 | reviewed | test_gateway.py::GatewayTest::test_run_registry_wird_geschrieben | 1 Test(s) |
| SWR-014 | reviewed | test_gateway.py::GatewayTest::test_verbotene_aktion | 1 Test(s) |
| SWR-015 | reviewed | test_orchestrator.py::ArbeitskopieTest::test_sauber<br>test_orchestrator.py::ArbeitskopieTest::test_unsauber<br>test_orchestrator.py::ArbeitskopieTest::test_ausnahme_praefix<br>test_preflight.py::TestReposImRoot::test_produkt_repo_wird_erkannt | 4 Test(s) |
| SWR-016 | reviewed | test_orchestrator.py::AuswahlTest::test_waehlt_hoechste_prio<br>test_orchestrator.py::AuswahlTest::test_ignoriert_nicht_open<br>test_orchestrator.py::AuswahlTest::test_ignoriert_blockierte<br>test_orchestrator.py::AuswahlTest::test_blocker_done_gibt_frei<br>test_orchestrator.py::AuswahlTest::test_ignoriert_inaktive_und_mensch_rollen<br>test_orchestrator.py::RoutingTest::test_script_route | 6 Test(s) |
| SWR-017 | reviewed | test_orchestrator.py::StatusTest::test_setze_status_und_board<br>test_orchestrator.py::StatusTest::test_setze_status_invalide_wirft<br>test_orchestrator.py::SlugTest::test_slug<br>test_orchestrator.py::WarteLaufTest::test_phase1_ohne_antwortdatei<br>test_orchestrator.py::WarteLaufTest::test_keine_phase1_mit_antwortdatei<br>test_orchestrator.py::WarteLaufTest::test_keine_phase1_ohne_session_oder_bei_script | 6 Test(s) |
| SWR-018 | reviewed | test_orchestrator.py::AuswahlTest::test_nur_ticket_filter | 1 Test(s) |
| SWR-019 | reviewed | — | über CI-Workflow verifiziert (kein Unit-Test) |
| SWR-020 | reviewed | test_backend.py::InboxTest::test_liste_nur_offene_drs<br>test_backend.py::InboxTest::test_entscheidung_roundtrip_mit_commit<br>test_backend.py::InboxTest::test_fehlerfaelle<br>test_backend.py::InboxTest::test_optionen_validierung<br>test_backend.py::InboxTest::test_freitext_ohne_optionen_feld_bleibt_gueltig<br>test_backend.py::HttpTest::test_post_entscheidung | 6 Test(s) |
| SWR-021 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-022 | reviewed | test_backend.py::AggregationTest::test_board_gruppiert_nach_status<br>test_backend.py::AggregationTest::test_reports_und_kpi<br>test_backend.py::HttpTest::test_get_endpunkte | 3 Test(s) |
| SWR-023 | reviewed | test_backend.py::MailerTest::test_unkonfiguriert_wirft_nicht<br>test_backend.py::MailerTest::test_kaputter_host_wirft_nicht<br>test_backend.py::HttpTest::test_post_entscheidung | 3 Test(s) |
| SWR-024 | reviewed | test_backend.py::AggregationTest::test_neustart_aequivalenz<br>test_backend.py::InboxTest::test_entscheidung_roundtrip_mit_commit | 2 Test(s) |
| SWR-025 | reviewed | test_backend.py::MultiProjektTest::test_discovery_und_scoping<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte<br>test_backend.py::HttpTest::test_unbekanntes_projekt_404 | 3 Test(s) |
| SWR-026 | reviewed | test_backend.py::MultiProjektTest::test_uebersicht_je_projekt<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte | 2 Test(s) |
| SWR-027 | reviewed | test_backend.py::MultiProjektTest::test_inbox_ueber_alle_projekte<br>test_backend.py::MultiProjektTest::test_entscheidung_im_richtigen_projekt<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte | 3 Test(s) |
| SWR-028 | reviewed | test_orchestrator.py::ProjektValidierungTest::test_unbekanntes_projekt_bricht_ab | 1 Test(s) |
| SWR-029 | reviewed | test_preflight.py::MultiProjektBoardCheckTest::test_invalides_zweitprojekt_ist_befund<br>test_trace_matrix.py::MehrereSwrQuellenTest::test_merge_zweier_quellen_ohne_luecken<br>test_trace_matrix.py::AlleProjekteTest::test_discovery_findet_projekt_swr_dokumente | 3 Test(s) |
| SWR-030 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines | 1 Test(s) |
| SWR-031 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines | 1 Test(s) |
| SWR-032 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines | 1 Test(s) |
| SWR-033 | reviewed | test_dr_benachrichtigung.py::BenachrichtigungTest::test_erfolg_setzt_marker_und_verhindert_doppelversand<br>test_dr_benachrichtigung.py::BenachrichtigungTest::test_fehlschlag_ohne_marker_wird_wiederholt<br>test_dr_benachrichtigung.py::BenachrichtigungTest::test_mailinhalt_traegt_projekt_und_frist | 3 Test(s) |

## Lücken (reviewed ohne Testabdeckung)

Keine.

## Tests ohne SWR-Bezug (informativ — Prozess-Tooling mit CR-Bezug erlaubt, T-0025)

- test_catalog.py::KatalogTest::test_neuer_eintrag_erzeugt_yaml_und_seite
- test_catalog.py::KatalogTest::test_update_ersetzt_version
- test_feedback_route.py::RoutingTest::test_wunsch_wird_change_request
- test_feedback_route.py::RoutingTest::test_fehler_wird_problem
- test_feedback_route.py::RoutingTest::test_feedback_geht_in_progress_mit_notiz
- test_feedback_route.py::RoutingTest::test_dry_run_aendert_nichts
- test_feedback_route.py::AbschlussTest::test_zwei_laeufe_schliessen_feedback
- test_feedback_route.py::AbschlussTest::test_offenes_folgeticket_blockiert_abschluss
- test_preflight.py::TestLockArtefakte::test_findet_bekannte_artefakte
- test_preflight.py::TestLockArtefakte::test_sauberes_repo_ohne_funde
- test_preflight.py::TestLockArtefakte::test_entfernen_meldet_erfolg
- test_preflight.py::TestLockArtefakte::test_entfernen_meldet_fehlschlag
- test_preflight.py::TestPreflightGesamt::test_fehlende_repos_sind_befunde
- test_trace_matrix.py::TestScannen::test_methode_vor_klasse_vor_modul
- test_trace_matrix.py::TestScannen::test_ohne_bezug_wird_gemeldet
- test_trace_matrix.py::TestMatrix::test_luecken_und_ci_ausnahme
- test_trace_matrix.py::TestMatrix::test_unbekannte_swr_in_tests_ist_luecke
- test_trace_matrix.py::TestIdMuster::test_produkt_muster_wird_erkannt
- test_trace_matrix.py::TestIdMuster::test_default_verhalten_unveraendert
- test_trace_matrix.py::ProduktCfgTest::test_cfg_aufloesung_und_unbekanntes_produkt
- test_trace_matrix.py::ProduktCfgTest::test_echte_cfg_kennt_datakonv
