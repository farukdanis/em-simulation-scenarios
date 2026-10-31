---
license: cc-by-nc-4.0
language:
- tr
- en
pretty_name: Emergency Medicine Simulation Scenarios — Open Sample (TR/EN)
size_categories:
- n<1K
task_categories:
- text-generation
- question-answering
tags:
- medical
- emergency-medicine
- simulation
- medical-education
- wilderness-medicine
- turkish
configs:
- config_name: sample_scenario
  data_files:
  - split: train
    path: data/sample_scenario.jsonl
  default: true
- config_name: sample_states
  data_files:
  - split: train
    path: data/sample_states.jsonl
---

# Emergency Medicine Simulation Scenarios — Open Sample (Turkish / English)

A bilingual, structured, instructor-ready simulation scenario library for emergency medicine teaching, written by an emergency physician. This repository is the **public showcase**: one complete scenario, catalogue cards for the rest of the library, and the data format.

## What is here

| | |
|---|---|
| **Full sample scenario** | *Exertional Heat Stroke* — [English](scenarios/wild-exertional-heat-stroke.en.md) · [Türkçe](scenarios/wild-exertional-heat-stroke.tr.md) · [JSON](data/wild-exertional-heat-stroke.json) |
| **Catalogue** | [catalog/CATALOG.md](catalog/CATALOG.md) — title, audience, objective headings, duration, difficulty for every scenario |
| **Format** | [schema/SCHEMA.md](schema/SCHEMA.md) and [JSON Schema](schema/scenario.schema.json) |

Each scenario contains learning objectives (technical and non-technical), an instructor summary, preparation (documents, roles, moulage, equipment, drugs), a learner briefing, a state-based flow with expected actions (★ critical), patient responses, vital signs and branch transitions, a debriefing guide, common errors, a critical-action checklist and references.

## Library at a glance

| Scenario | Domain | Duration | Difficulty | Access |
|---|---|---|---|---|
| Exertional Heat Stroke | Wilderness medicine | 18–22 min | Intermediate | **Open sample** |
| Pediatric Convulsive Status Epilepticus | Paediatric EM | 15–20 min | Intermediate | Licence |
| Septic Shock and Meningococcaemia in an Infant | Paediatric EM | 20 min | Advanced | Licence |
| Avalanche Burial: Severe Hypothermia and Hypothermic Arrest | Wilderness medicine | 20–25 min | Advanced | Licence |

## Full library available for institutional licensing

Simulation centres, medical schools, residency programmes and course organisers can licence the complete library. A licence includes:

- all scenarios in Turkish and English, as JSON (this schema) and as printable instructor packs;
- critical-action checklists and debriefing guides;
- updates when guidelines change, and new scenarios as they are released;
- optional adaptation to local protocols and equipment.

Contact: **[faruk.md](https://www.faruk.md)**

## Using the open sample

```python
from datasets import load_dataset

scenario = load_dataset("farukdanis/em-simulation-scenarios", "sample_scenario", split="train")
states = load_dataset("farukdanis/em-simulation-scenarios", "sample_states", split="train")
```

To run a session: print the instructor sections, read only the *learner briefing* to participants and drive the manikin from the *scenario flow*.

**Important:** fictional case, no real patient data. Not clinical guidance — verify drugs and algorithms against local protocols and current guidelines before teaching.

## Türkçe

Acil tıp eğitimi için iki dilli, yapılandırılmış simülasyon senaryo kütüphanesinin açık vitrinidir. Burada bir tam örnek senaryo (efor sıcak çarpması), diğer senaryoların katalog kartları ve veri formatı yer alır. Tam kütüphane kurumlara lisansla sunulur; iletişim: [faruk.md](https://www.faruk.md).

## Author

**Faruk Danış, MD** — Assistant Professor of Emergency Medicine, Bolu Abant İzzet Baysal University, Türkiye · ORCID [0000-0001-8722-5402](https://orcid.org/0000-0001-8722-5402)

## License

- Sample scenario (`scenarios/wild-exertional-heat-stroke.*`, `data/wild-exertional-heat-stroke.json`, `data/sample_*.jsonl`): [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).
- Catalogue, schema documentation and this README: © 2026 Faruk Danış, all rights reserved.

See [LICENSE](LICENSE).
