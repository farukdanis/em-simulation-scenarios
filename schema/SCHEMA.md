# Scenario format / Senaryo formatı

> Documentation: Proprietary — All rights reserved. The open sample in `data/` follows this format exactly.

Every scenario is a single bilingual JSON document (validated by [`scenario.schema.json`](scenario.schema.json), JSON Schema 2020-12). Text fields are `{"tr": "...", "en": "..."}` objects; list fields are `{"tr": [...], "en": [...]}`.

| Field | Type | Content |
|---|---|---|
| `id`, `version`, `domain`, `setting_type` | string | Identity and classification |
| `title`, `setting` | i18n | Display name and clinical setting |
| `patient` | object | `age`, `weight_kg` (nullable), `sex`, `profile` (i18n, always fictional) |
| `duration_min`, `participants` | string / i18n | Session length (excluding debrief), learner group and facilitators |
| `learning_objectives` | object | `technical` and `non_technical` (i18n lists) |
| `summary`, `progression` | i18n | Instructor overview and branching logic in prose |
| `preparation` | object | `documents`, `roles`, `costume`, `pre_post_materials`, `environment`, `actor_notes`, `equipment`, `medications` |
| `briefing` | i18n | Text read to learners |
| `initial_state` | object | `appearance` (i18n) + `vitals` |
| `states[]` | array | `id`, `time`, `label`, `expected_actions` (★ = critical), `patient_response`, `vitals`, `transitions[]` (`condition` → `to` state id) |
| `debriefing` | object | `key_points`, `common_errors` (i18n lists) |
| `assessment_checklist` | i18n list | Critical-action checklist items (may be empty) |
| `team_assessment` | string / null | Recommended non-technical rating instrument (cited, not reproduced) |
| `references` | string[] | Vancouver-style references |

`vitals` uses free keys with numeric or string values: `hr`, `bp`, `rr`, `spo2`, `temp_c`, `core_temp_c`, `glucose_mg_dl`, `gcs`, `crt_s`, `rhythm`, `k_mmol_l`.

## Flat exports (Hugging Face)

- `data/sample_scenario.jsonl` — one row per scenario × language; list fields stay lists, `initial_vitals` is a JSON string.
- `data/sample_states.jsonl` — one row per state × language with `expected_actions`, `critical_actions` (★ items), `patient_response`, `vitals` and `transitions` (JSON strings).

Licensed libraries are delivered in the same format, plus rendered Markdown/PDF instructor packs.
