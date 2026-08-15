# SWR ↔ Test-Matrix (generiert von platform/scripts/trace_matrix.py — nicht von Hand editieren)

Stand: 2026-08-15 · SWRs: 18 (reviewed: 18) · Tests mit SWR-Bezug: 47 · ohne Bezug: 0

| SWR | Status | Unit-Tests | Abdeckung |
|---|---|---|---|
| SWR-D01 | reviewed | test_cli.py::DirectionTest::test_missing_to_is_usage_error<br>test_cli.py::DirectionTest::test_invalid_to_value_is_usage_error | 2 Test(s) |
| SWR-D02 | reviewed | test_cli.py::IoTest::test_stdin_to_stdout<br>test_cli.py::IoTest::test_file_to_file<br>test_cli.py::IoTest::test_unreadable_input_is_data_error<br>test_e2e.py::PipelineTest::test_pipe_csv_to_json<br>test_e2e.py::PipelineTest::test_file_to_file_roundtrip | 5 Test(s) |
| SWR-D03 | reviewed | test_cli.py::DelimiterTest::test_delimiter_applies_to_input_and_output<br>test_cli.py::DelimiterTest::test_multichar_delimiter_is_usage_error<br>test_e2e.py::PipelineTest::test_semicolon_delimiter_end_to_end | 3 Test(s) |
| SWR-D04 | reviewed | test_cli.py::ConventionTest::test_help_exits_0_on_stdout<br>test_cli.py::ConventionTest::test_version_exits_0_on_stdout<br>test_e2e.py::RobustnessTest::test_version_end_to_end | 3 Test(s) |
| SWR-D05 | reviewed | test_c2j.py::ShapeTest::test_array_of_objects_with_header_keys<br>test_c2j.py::ShapeTest::test_key_order_follows_columns<br>test_c2j.py::ShapeTest::test_missing_header_is_data_error<br>test_e2e.py::PipelineTest::test_pipe_csv_to_json | 4 Test(s) |
| SWR-D06 | reviewed | test_c2j.py::TypingTest::test_typing_table<br>test_c2j.py::TypingTest::test_non_json_number_forms_stay_strings | 2 Test(s) |
| SWR-D07 | reviewed | test_c2j.py::QuotingTest::test_rfc4180_quoting | 1 Test(s) |
| SWR-D08 | reviewed | test_c2j.py::ErrorTest::test_field_count_mismatch_names_record | 1 Test(s) |
| SWR-D09 | reviewed | test_c2j.py::ErrorTest::test_duplicate_header_rejected<br>test_c2j.py::ErrorTest::test_empty_header_rejected | 2 Test(s) |
| SWR-D10 | reviewed | test_j2c.py::StructureTest::test_parse_error_distinguished<br>test_j2c.py::StructureTest::test_structure_error_distinguished | 2 Test(s) |
| SWR-D11 | reviewed | test_j2c.py::HeaderTest::test_key_union_first_occurrence_order_and_missing_empty | 1 Test(s) |
| SWR-D12 | reviewed | test_j2c.py::SerializationTest::test_serialization_table<br>test_j2c.py::SerializationTest::test_rfc4180_quoting_applied | 2 Test(s) |
| SWR-D13 | reviewed | test_j2c.py::NestingTest::test_nested_value_rejected_with_path | 1 Test(s) |
| SWR-D14 | reviewed | test_cli.py::EncodingTest::test_utf8_round_trip<br>test_cli.py::EncodingTest::test_bom_input_is_stripped<br>test_cli.py::EncodingTest::test_invalid_utf8_is_data_error<br>test_e2e.py::RobustnessTest::test_umlauts_survive_utf8<br>test_e2e.py::RobustnessTest::test_excel_bom_header_is_clean | 5 Test(s) |
| SWR-D15 | reviewed | test_cli.py::DirectionTest::test_missing_to_is_usage_error<br>test_cli.py::IoTest::test_unreadable_input_is_data_error<br>test_cli.py::EncodingTest::test_invalid_utf8_is_data_error<br>test_cli.py::ExitCodeTest::test_data_error_never_writes_stdout<br>test_cli.py::ExitCodeTest::test_unexpected_exception_exits_1<br>test_e2e.py::RobustnessTest::test_exit_codes_and_stream_separation | 6 Test(s) |
| SWR-D16 | reviewed | test_c2j.py::DeterminismTest::test_double_run_byte_identical<br>test_j2c.py::DeterminismTest::test_double_run_byte_identical | 2 Test(s) |
| SWR-D17 | reviewed | test_e2e.py::PipelineTest::test_file_to_file_roundtrip<br>test_j2c.py::DeterminismTest::test_roundtrip_csv_json_csv | 2 Test(s) |
| SWR-D18 | reviewed | test_c2j.py::IndentTest::test_compact_single_line<br>test_c2j.py::IndentTest::test_custom_indent_width<br>test_cli.py::DelimiterTest::test_indent_option_end_to_end | 3 Test(s) |

## Lücken (reviewed ohne Testabdeckung)

Keine.

## Tests ohne SWR-Bezug (informativ — Prozess-Tooling mit CR-Bezug erlaubt, T-0025)

Keine.
