# QRA Input Prompting

Use this reference when the engineer has not provided enough data to close the QRA chain. Ask for project data first. If data are not available, provide reference-data candidates with source tier, assumption ID, and sensitivity requirements.

## Prompting Rule

Before running or claiming QRA results, actively ask for missing inputs in these groups:

- Model boundary: study purpose, software version, scenario list, layout, coordinates, exclusions.
- Source terms: material, phase, temperature, pressure, inventory, release height, hole-size basis, duration, isolation segment.
- Frequencies: component counts, line lengths, transfer counts, operation hours, failure-frequency source, run-time factors.
- Weather: wind rose, stability classes, day/night split, representative weather, wind directions.
- Event tree: detection/isolation credit, immediate ignition, delayed ignition, flash fire, jet fire, pool fire, VCE/DDT, no-ignition branch.
- Population: receptor coordinates, indoor/outdoor fractions, annual person-hours, concurrent people for F-N, transient-team overlap.
- Buildings and vulnerability: ordinary, blast-resistant, light building, semi-indoor, outdoor, window/roof/wall assumptions.
- Safeti outputs: result database, contours, LSIR/IRPA, PLL, F-N, contribution reports.

If more than five inputs are missing, summarize them by category and ask for the highest-impact items first: frequencies, population, weather, ignition, and building/vulnerability.

## Reference Data Ladder

Use this order when proposing reference data:

1. Project- or owner-approved data, P&ID, equipment list, operating philosophy, SIS/ESD cause-and-effect, layout, population table, met data.
2. PHAST/Safeti 8.7 native settings, local help, installed documentation, release notes, and software exports.
3. DNV public pages, DNV official webinars, DNV-authored public QRA/consequence material.
4. Hydrogen-specific public references such as Sandia/HyRAM for component leak frequency structure and hydrogen event-sequence logic.
5. IOGP Risk Assessment Data Directory for process, storage, pipeline, riser, and transport release-frequency benchmarks.
6. Energy Institute ignition-probability guidance or project-approved UKOOA/EI-style ignition model.
7. Government, standards, university, or peer-reviewed sources.

Never use uncited memory, leaked manuals, forum posts, cracked material, or unverifiable spreadsheets as reference data.

Useful public source links:

- DNV Phast/Safeti FAQ: https://www.dnv.com/software/services/plant/phast-safeti-FAQ/
- DNV Phast/Safeti downloads and release notes: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/softwaredownloads/
- Sandia HyRAM+ overview: https://energy.sandia.gov/programs/sustainable-transportation/hydrogen/hydrogen-safety-codes-and-standards/hyram/
- Sandia HyRAM technical reference publications: https://www.sandia.gov/research/publications/details/hydrogen-risk-assessment-models-hyram-v-3-1-technical-reference-manual-2021-05-01/
- IOGP RADD ignition probabilities: https://www.iogp.org/bookstore/product-tag/434-06/
- Energy Institute ignition probability guidance: https://www.energyinst.org/industry/publications/topics/process-safety/guidance-on-assigning-ignition-probabilities-in-onshore-and-offshore-quantitative-risk-assessments

## Reference Candidates When Data Are Missing

| Missing input | Reference candidate to offer | Constraint |
|---|---|---|
| Hydrogen leak-size set | HyRAM-style bins: 0.01%, 0.1%, 1%, 10%, and 100% of pipe flow area | Use as screening bins or sensitivity set; do not replace an engineer-selected credible hole size without approval. |
| Hydrogen component leak frequency | HyRAM component-count method for compressors, cylinders, valves, instruments, joints, hoses, pipes by length, filters, and flanges | Requires component counts; if counts are missing, request a count basis before calculating final frequency. |
| Process/storage release frequency | IOGP RADD 434-series benchmark data | Match equipment type and service; document mismatch if using as proxy for hydrogen or cryogenic service. |
| Ignition probability | Energy Institute ignition-probability guidance, or project-approved UKOOA/EI/DNV-style model | Do not invent a single ignition probability; define direct/delayed split and sensitivity cases. |
| Detection/isolation credit | No barrier credit as conservative screening if SIS/ESD performance is unavailable | Mark as conservative; replace with cause-and-effect and reliability data when available. |
| Operating factor | 1.0 for continuous equipment only when annual operation is unknown; transfer systems require hours/year or transfers/year | Do not use 1.0 for batch/transfer if it materially overstates or hides actual exposure without noting sensitivity. |
| Weather | Site meteorology or nearest official station; if unavailable, single-weather research case only | Single-weather output is not full weather-weighted QRA. |
| Release direction | Equal directional split or worst-credible orientation sensitivity | Use only when actual orientation is unknown; record orientation assumption per scenario. |
| Population | Engineer-approved stationing table | Do not invent formal population. For research only, propose a draft table and require approval. |
| Building resistance | Ordinary/unprotected building unless blast-resistant design evidence is provided | Do not credit blast resistance from building name or function alone. |
| Offsite receptors | Pending information item | Do not claim public-risk compliance without offsite population and receptor data. |

## User-Facing Prompt Pattern

Use this pattern when asking the engineer:

```text
To close the QRA calculation, I need these inputs:
1. [input] - needed for [risk metric/branch].
2. [input] - needed for [risk metric/branch].

If these are not available, I can proceed only as a reference/screening case using:
- [reference candidate], source: [source tier/source].
- Assumption_ID: [id].
- Sensitivity: [low/base/high or conservative/base].

Please confirm which reference assumptions are acceptable, or provide project data.
```

## Stop Conditions

Do not calculate final LSIR/PLL/F-N as a QRA result when these are missing and not approved:

- scenario source terms or PHAST/Safeti native consequence outputs;
- release frequency basis;
- population/concurrent occupancy;
- weather weighting or explicitly approved single-weather research boundary;
- ignition/event-tree model;
- building/vulnerability treatment for indoor receptors.
