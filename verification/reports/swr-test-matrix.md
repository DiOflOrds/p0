# SWR ↔ Test-Matrix (generiert von platform/scripts/trace_matrix.py — nicht von Hand editieren)

Stand: 2026-08-16 · SWRs: 87 (reviewed: 82) · Tests mit SWR-Bezug: 234 · ohne Bezug: 19

| SWR | Status | Unit-Tests | Abdeckung |
|---|---|---|---|
| SWR-001 | reviewed | test_board.py::TestBoard::test_gutfall<br>test_board.py::TestBoard::test_pflichtfeld_fehlt<br>test_board.py::TestBoard::test_ungueltiger_status<br>test_board.py::TestBoard::test_id_dateiname_mismatch<br>test_board.py::TestBoard::test_blocked_ohne_blocker<br>test_board.py::TestBoard::test_in_review_ohne_reviewer<br>test_board.py::TestBoard::test_in_review_reviewer_ist_autor<br>test_board.py::TestBoard::test_in_review_mit_reviewer_ok<br>test_board.py::TestBoard::test_crlf_toleranz<br>test_board.py::DecisionRequestFelderTest::test_gueltige_felder<br>test_board.py::DecisionRequestFelderTest::test_ungueltige_frist<br>test_board.py::DecisionRequestFelderTest::test_default_nicht_in_optionen<br>test_board.py::DecisionRequestFelderTest::test_neuer_dr_ohne_optionen_abgelehnt<br>test_board.py::DecisionRequestFelderTest::test_bestands_dr_ausgenommen<br>test_board.py::DecisionRequestFelderTest::test_optionstoken_zerlegung | 15 Test(s) |
| SWR-002 | reviewed | test_board.py::TestBoard::test_uebergangsmatrix<br>test_board.py::TestBoard::test_mensch_tickets_ohne_uebergangspruefung<br>test_board.py::SetzeStatusTest::test_gueltiger_uebergang_schreibt_ticket_und_board<br>test_board.py::SetzeStatusTest::test_unzulaessiger_uebergang_wird_abgelehnt<br>test_board.py::SetzeStatusTest::test_in_review_erfordert_reviewer<br>test_board.py::SetzeStatusTest::test_status_cli | 6 Test(s) |
| SWR-003 | reviewed | test_board.py::TestBoard::test_blocked_by_unbekannt<br>test_board.py::TestBoard::test_blocked_by_selbstverweis | 2 Test(s) |
| SWR-004 | reviewed | test_board.py::TestBoard::test_board_deterministisch<br>test_board.py::TestBoard::test_prio_sortierung<br>test_board.py::TestBoard::test_offene_blocker<br>test_board.py::TestBoard::test_main_schreibt_board | 4 Test(s) |
| SWR-005 | reviewed | test_board.py::TestBoard::test_main_check_modus<br>test_board.py::TestBoard::test_main_fehlerfall | 2 Test(s) |
| SWR-006 | reviewed | test_gateway.py::GatewayTest::test_vertrag_ok<br>test_gateway.py::GatewayTest::test_unbekannter_provider | 2 Test(s) |
| SWR-007 | reviewed | test_copilot_executor.py::CopilotExecutorTest::test_fehlende_cli_faellt_zur_naechsten_stufe<br>test_gateway.py::GatewayTest::test_kettenfallback_bei_notimplemented<br>test_gateway.py::GatewayTest::test_claude_ohne_key_nicht_verfuegbar<br>test_orchestrator.py::RoutingTest::test_aufgaben_typ_kette<br>test_orchestrator.py::RoutingTest::test_default_kette<br>test_provider_apifrei.py::OllamaExecutorTest::test_nicht_erreichbar_faellt_in_kette_zurueck | 6 Test(s) |
| SWR-008 | reviewed | test_copilot_executor.py::CopilotExecutorTest::test_fehlende_cli_faellt_zur_naechsten_stufe<br>test_copilot_executor.py::CopilotExecutorTest::test_dateibloecke_werden_eingepflegt<br>test_copilot_executor.py::CopilotExecutorTest::test_cli_fehler_liefert_log_statt_crash<br>test_copilot_executor.py::CopilotAusgabeHaertungTest::test_ansi_dekoration_wird_gestrippt<br>test_copilot_executor.py::CopilotAusgabeHaertungTest::test_markdown_zaeune_werden_toleriert<br>test_copilot_executor.py::CopilotAusgabeHaertungTest::test_ohne_bloecke_landet_rohantwort_im_log<br>test_gateway.py::GatewayTest::test_stub_executoren_nicht_verfuegbar<br>test_provider_apifrei.py::SessionExecutorTest::test_phase1_erzeugt_prompt_und_wartet<br>test_provider_apifrei.py::SessionExecutorTest::test_phase2_liest_antwort_ein<br>test_provider_apifrei.py::SessionExecutorTest::test_antwort_ohne_bloecke_kein_erfolg<br>test_provider_apifrei.py::SessionExecutorTest::test_wartet_wird_protokolliert<br>test_provider_apifrei.py::OllamaExecutorTest::test_modellwahl | 12 Test(s) |
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
| SWR-020 | reviewed | test_backend.py::InboxTest::test_liste_nur_offene_drs<br>test_backend.py::InboxTest::test_entscheidung_roundtrip_mit_commit<br>test_backend.py::InboxTest::test_fehlerfaelle<br>test_backend.py::InboxTest::test_optionen_validierung<br>test_backend.py::InboxTest::test_freitext_ohne_optionen_feld_bleibt_gueltig<br>test_backend.py::HttpTest::test_post_entscheidung<br>test_backend.py::VerbindungsabbruchTest::test_abbruch_erkannt<br>test_backend.py::VerbindungsabbruchTest::test_echte_fehler_nicht_als_abbruch<br>test_backend.py::VerbindungsabbruchTest::test_handler_verwirft_abbruch_mit_einer_zeile<br>test_backend.py::VerbindungsabbruchTest::test_handler_laesst_echte_fehler_durch<br>test_backend.py::VerbindungsabbruchTest::test_serverklasse_schweigt_nur_bei_abbruch | 11 Test(s) |
| SWR-021 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-022 | reviewed | test_backend.py::AggregationTest::test_board_gruppiert_nach_status<br>test_backend.py::AggregationTest::test_reports_und_kpi<br>test_backend.py::HttpTest::test_get_endpunkte<br>test_backend.py::VerbindungsabbruchTest::test_abbruch_erkannt<br>test_backend.py::VerbindungsabbruchTest::test_echte_fehler_nicht_als_abbruch<br>test_backend.py::VerbindungsabbruchTest::test_handler_verwirft_abbruch_mit_einer_zeile<br>test_backend.py::VerbindungsabbruchTest::test_handler_laesst_echte_fehler_durch<br>test_backend.py::VerbindungsabbruchTest::test_serverklasse_schweigt_nur_bei_abbruch | 8 Test(s) |
| SWR-023 | reviewed | test_backend.py::MailerTest::test_unkonfiguriert_wirft_nicht<br>test_backend.py::MailerTest::test_kaputter_host_wirft_nicht<br>test_backend.py::HttpTest::test_post_entscheidung<br>test_backend.py::VerbindungsabbruchTest::test_abbruch_erkannt<br>test_backend.py::VerbindungsabbruchTest::test_echte_fehler_nicht_als_abbruch<br>test_backend.py::VerbindungsabbruchTest::test_handler_verwirft_abbruch_mit_einer_zeile<br>test_backend.py::VerbindungsabbruchTest::test_handler_laesst_echte_fehler_durch<br>test_backend.py::VerbindungsabbruchTest::test_serverklasse_schweigt_nur_bei_abbruch | 8 Test(s) |
| SWR-024 | reviewed | test_backend.py::AggregationTest::test_neustart_aequivalenz<br>test_backend.py::InboxTest::test_entscheidung_roundtrip_mit_commit<br>test_backend.py::VerbindungsabbruchTest::test_abbruch_erkannt<br>test_backend.py::VerbindungsabbruchTest::test_echte_fehler_nicht_als_abbruch<br>test_backend.py::VerbindungsabbruchTest::test_handler_verwirft_abbruch_mit_einer_zeile<br>test_backend.py::VerbindungsabbruchTest::test_handler_laesst_echte_fehler_durch<br>test_backend.py::VerbindungsabbruchTest::test_serverklasse_schweigt_nur_bei_abbruch | 7 Test(s) |
| SWR-025 | reviewed | test_backend.py::MultiProjektTest::test_discovery_und_scoping<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte<br>test_backend.py::HttpTest::test_unbekanntes_projekt_404 | 3 Test(s) |
| SWR-026 | reviewed | test_backend.py::MultiProjektTest::test_uebersicht_je_projekt<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte<br>test_org_cockpit.py::VerschachtelteDrsTest::test_uebersicht_zaehlt_tickets_aus_sammelrepo | 3 Test(s) |
| SWR-027 | reviewed | test_backend.py::MultiProjektTest::test_inbox_ueber_alle_projekte<br>test_backend.py::MultiProjektTest::test_entscheidung_im_richtigen_projekt<br>test_backend.py::HttpTest::test_multi_projekt_endpunkte<br>test_org_cockpit.py::VerschachtelteDrsTest::test_inbox_zeigt_dr_aus_sammelrepo | 4 Test(s) |
| SWR-028 | reviewed | test_orchestrator.py::ProjektValidierungTest::test_unbekanntes_projekt_bricht_ab | 1 Test(s) |
| SWR-029 | reviewed | test_preflight.py::MultiProjektBoardCheckTest::test_invalides_zweitprojekt_ist_befund<br>test_trace_matrix.py::MehrereSwrQuellenTest::test_merge_zweier_quellen_ohne_luecken<br>test_trace_matrix.py::AlleProjekteTest::test_discovery_findet_projekt_swr_dokumente | 3 Test(s) |
| SWR-030 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines<br>test_backend.py::RequirementsUeberAlleTest::test_einzelprojekt_unveraendert | 2 Test(s) |
| SWR-031 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines | 1 Test(s) |
| SWR-032 | reviewed | test_backend.py::MultiProjektTest::test_views_requirements_verifikation_baselines | 1 Test(s) |
| SWR-033 | reviewed | test_dr_benachrichtigung.py::BenachrichtigungTest::test_erfolg_setzt_marker_und_verhindert_doppelversand<br>test_dr_benachrichtigung.py::BenachrichtigungTest::test_fehlschlag_ohne_marker_wird_wiederholt<br>test_dr_benachrichtigung.py::BenachrichtigungTest::test_mailinhalt_traegt_projekt_und_frist<br>test_org_cockpit.py::VerschachtelteDrsTest::test_fristwarnung_sieht_dr_aus_sammelrepo | 4 Test(s) |
| SWR-034 | reviewed | test_dr_benachrichtigung.py::BenachrichtigungTest::test_erfolg_setzt_marker_und_verhindert_doppelversand<br>test_dr_benachrichtigung.py::BenachrichtigungTest::test_fehlschlag_ohne_marker_wird_wiederholt<br>test_dr_benachrichtigung.py::FristWarnungTest::test_schwelle_zwei_tage<br>test_dr_benachrichtigung.py::FristWarnungTest::test_warnung_nur_einmal<br>test_dr_benachrichtigung.py::FristWarnungTest::test_entschiedene_drs_ohne_warnung<br>test_dr_benachrichtigung.py::FristWarnungTest::test_unparsebare_frist_ohne_warnung | 6 Test(s) |
| SWR-035 | reviewed | test_dr_benachrichtigung.py::FristWarnungTest::test_warntext_mit_und_ohne_default | 1 Test(s) |
| SWR-036 | reviewed | test_catalog.py::KatalogTest::test_neuer_eintrag_erzeugt_yaml_und_seite<br>test_catalog.py::KatalogTest::test_update_ersetzt_version<br>test_catalog.py::KatalogCheckTest::test_konsistenter_katalog_ohne_befund<br>test_catalog.py::KatalogCheckTest::test_versionskonflikt_und_fehlender_tag<br>test_catalog.py::KatalogCheckTest::test_release_repo_ohne_eintrag | 5 Test(s) |
| SWR-037 | reviewed | test_backend.py::NutzerUndHaertungTest::test_registry_parsen_und_fallback<br>test_backend.py::HttpTest::test_nutzer_endpunkt | 2 Test(s) |
| SWR-038 | reviewed | test_backend.py::NutzerUndHaertungTest::test_entscheider_pflicht<br>test_backend.py::HttpTest::test_nutzer_endpunkt | 2 Test(s) |
| SWR-039 | reviewed | test_backend.py::NutzerUndHaertungTest::test_entschiedener_dr_verschwindet_und_sperrt | 1 Test(s) |
| SWR-040 | reviewed | test_backend.py::HttpTest::test_ticket_detail | 1 Test(s) |
| SWR-041 | reviewed | test_backend.py::HttpTest::test_board_felder_fuer_filter | 1 Test(s) |
| SWR-042 | reviewed | test_backend.py::HttpTest::test_inbox_optionen_und_historie<br>test_org_cockpit.py::VerschachtelteDrsTest::test_historie_zeigt_entschiedene_drs_aus_sammelrepo | 2 Test(s) |
| SWR-043 | reviewed | test_backend.py::HmiSprint2Test::test_md_tabellen_parser<br>test_backend.py::HmiSprint2Test::test_requirements_liefern_tabellen | 2 Test(s) |
| SWR-044 | reviewed | test_backend.py::HmiSprint2Test::test_md_tabellen_parser<br>test_backend.py::HmiSprint2Test::test_requirements_liefern_tabellen | 2 Test(s) |
| SWR-045 | reviewed | test_arch_diagramm.py::ArchDiagrammTest::test_svg_enthaelt_komponenten_und_pfeile<br>test_arch_diagramm.py::ArchDiagrammTest::test_deterministisch_und_drift_erkennbar<br>test_arch_diagramm.py::ArchDiagrammTest::test_unbekannte_komponente_wird_abgelehnt<br>test_arch_diagramm.py::ArchDiagrammTest::test_eingecheckte_quelle_konsistent_zum_bild | 4 Test(s) |
| SWR-046 | reviewed | test_backend.py::HmiSprint2Test::test_cockpit_mit_frist_ampel<br>test_backend.py::HmiSprint2Test::test_cockpit_alle_ueber_api_form<br>test_backend.py::EindeutigeKennungTest::test_cockpit_und_inbox_tragen_die_kennung | 3 Test(s) |
| SWR-047 | reviewed | test_backend.py::HttpTest::test_version_endpunkt | 1 Test(s) |
| SWR-048 | reviewed | test_backend.py::FernzugriffTest::test_schreibschutz_regeln | 1 Test(s) |
| SWR-049 | reviewed | test_backend.py::FernzugriffTest::test_schreibschutz_regeln | 1 Test(s) |
| SWR-050 | reviewed | test_backend.py::FernzugriffTest::test_briefkasten_senden_und_lesen | 1 Test(s) |
| SWR-051 | reviewed | test_backend.py::FernzugriffTest::test_cockpit_zaehlt_offene_briefe | 1 Test(s) |
| SWR-052 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-053 | reviewed | test_teams.py::TeamsTest::test_team_daten_vollstaendig<br>test_teams.py::TeamsTest::test_digest_inhalt_und_pfadschutz<br>test_teams.py::TeamsTest::test_kein_team_projekt | 3 Test(s) |
| SWR-054 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-055 | reviewed | test_teams.py::TeamsTest::test_cockpit_team_kachel | 1 Test(s) |
| SWR-056 | reviewed | test_teams.py::TeamsTest::test_konfiguration_schreiben_und_commit<br>test_teams.py::TeamsTest::test_konfiguration_validierung | 2 Test(s) |
| SWR-057 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-058 | reviewed | test_digest_zustellung.py::DigestZustellungTest::test_sendet_einmal_und_vermerkt<br>test_digest_zustellung.py::DigestZustellungTest::test_deaktivierte_teams_werden_uebersprungen<br>test_digest_zustellung.py::DigestZustellungTest::test_fehler_blockiert_nicht_und_vermerkt_nicht<br>test_digest_zustellung.py::DigestZustellungTest::test_dry_run_sendet_nichts | 4 Test(s) |
| SWR-059 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-060 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-061 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-062 | reviewed | test_mail_autopilot.py::MailAutopilotTest::test_verdichte_erfolg_und_fallback<br>test_mail_autopilot.py::MailAutopilotTest::test_lauf_takt_schreibt_und_stellt_zu | 2 Test(s) |
| SWR-063 | reviewed | test_teams.py::TeamsTest::test_digest_jetzt | 1 Test(s) |
| SWR-064 | reviewed | test_mail_autopilot.py::MailAutopilotTest::test_konfiguration_takte_und_fallback<br>test_mail_autopilot.py::MailAutopilotTest::test_faelligkeit_je_takt | 2 Test(s) |
| SWR-065 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-066 | reviewed | test_org_cockpit.py::OrgCockpitTest::test_steckbrief_und_gruppen<br>test_org_cockpit.py::OrgCockpitTest::test_status_fallback_ueber_baseline_tag<br>test_org_cockpit.py::VerschachtelteDrsTest::test_top_level_projekte_unveraendert | 3 Test(s) |
| SWR-067 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-068 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-069 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-070 | reviewed | test_board.py::ProjektDiscoveryTest::test_findet_top_level_und_verschachtelte_projekte<br>test_board.py::ProjektDiscoveryTest::test_top_level_gewinnt_bei_namensgleichheit<br>test_board.py::ProjektDiscoveryTest::test_fehlender_wurzelordner_ist_leer<br>test_org_cockpit.py::OrgCockpitTest::test_projects_sammelrepo_discovery<br>test_preflight.py::MultiProjektBoardCheckTest::test_kaputtes_ticket_im_sammelrepo_ist_befund<br>test_trace_matrix.py::SwrQuellenDiscoveryTest::test_verschachteltes_projekt_liefert_swr_quelle<br>test_trace_matrix.py::SwrQuellenDiscoveryTest::test_projekt_ohne_anforderungsdokument_wird_uebersprungen | 7 Test(s) |
| SWR-071 | reviewed | test_mail_autopilot.py::MailAutopilotTest::test_ki_hinweis_im_prompt<br>test_teams.py::TeamsTest::test_modellwahl_und_ki_hinweis_rundlauf<br>test_teams.py::TeamsTest::test_modellwahl_und_hinweis_validierung<br>test_teams.py::TeamsTest::test_ollama_modelle_liste | 4 Test(s) |
| SWR-072 | reviewed | test_mail_autopilot.py::MailAutopilotTest::test_ki_hinweis_im_prompt | 1 Test(s) |
| SWR-073 | reviewed | test_backend.py::SelbstNeustartTest::test_entscheidung_nur_bei_neuem_stand_ruhe_und_schleife<br>test_backend.py::SelbstNeustartTest::test_wache_beendet_prozess_mit_42<br>test_backend.py::SelbstNeustartTest::test_wache_ohne_marker_beendet_nie<br>test_backend.py::VerbindungsabbruchTest::test_zaehler_wird_auch_bei_abbruch_freigegeben | 4 Test(s) |
| SWR-074 | reviewed | test_board.py::TestBoard::test_takt_wiederkehrend_sichtbar<br>test_board.py::TestBoard::test_takt_ohne_feld_unveraendert<br>test_board.py::TestBoard::test_takt_ungueltig_wird_abgelehnt<br>test_org_cockpit.py::OrgCockpitTest::test_takt_im_cockpit_und_board | 4 Test(s) |
| SWR-075 | reviewed | test_org_cockpit.py::OrgCockpitTest::test_altlasten_erkennung<br>test_org_cockpit.py::OrgCockpitTest::test_board_reicht_veraltet_durch | 2 Test(s) |
| SWR-076 | reviewed | test_backend.py::NutzerUndHaertungTest::test_inbox_zaehler_fuer_den_menschen | 1 Test(s) |
| SWR-077 | draft | — | offen (Status draft) |
| SWR-078 | draft | — | offen (Status draft) |
| SWR-079 | draft | — | offen (Status draft) |
| SWR-080 | draft | — | offen (Status draft) |
| SWR-081 | draft | — | offen (Status draft) |
| SWR-082 | reviewed | test_backend.py::HttpTest::test_navigation_endpunkt<br>test_org_cockpit.py::NavigationTest::test_gruppen_reihenfolge_und_trennung<br>test_org_cockpit.py::NavigationTest::test_gleiche_einstufung_wie_cockpit<br>test_org_cockpit.py::NavigationTest::test_leere_gruppen_entfallen<br>test_org_cockpit.py::NavigationTest::test_nur_abgeschlossene_bleiben_erreichbar | 5 Test(s) |
| SWR-083 | reviewed | — | manuelle Abnahme dokumentiert (p0/verification/reports/) — kein Unit-Test |
| SWR-084 | reviewed | test_backend.py::InboxTest::test_zeitpunkt_mit_uhrzeit_in_log_und_ticket<br>test_backend.py::InboxTest::test_zeitpunkt_formatiert_uebergebene_uhr<br>test_backend.py::InboxTest::test_historie_liest_vermerk_mit_uhrzeit<br>test_backend.py::InboxTest::test_alte_eintraege_ohne_uhrzeit_bleiben_gueltig | 4 Test(s) |
| SWR-085 | reviewed | test_backend.py::RequirementsUeberAlleTest::test_alle_projekte_in_einer_antwort<br>test_backend.py::RequirementsUeberAlleTest::test_herkunft_je_datei_fuer_den_filter | 2 Test(s) |
| SWR-086 | reviewed | test_backend.py::ProjektPoolTest::test_kandidaten_nach_kategorie<br>test_backend.py::ProjektPoolTest::test_ohne_datei_keine_ausnahme<br>test_backend.py::ProjektPoolTest::test_abschnitte_ohne_tabelle_werden_uebersprungen | 3 Test(s) |
| SWR-087 | reviewed | test_backend.py::EindeutigeKennungTest::test_ref_ist_eine_quelle<br>test_backend.py::EindeutigeKennungTest::test_gleiche_nummer_zwei_projekte_unterscheidbar | 2 Test(s) |

## Lücken (reviewed ohne Testabdeckung)

Keine.

## Tests ohne SWR-Bezug (informativ — Prozess-Tooling mit CR-Bezug erlaubt, T-0025)

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
