# QRA Workflow Checklist

## Boundary Freeze

- Confirm latest model package and reject superseded packages.
- Confirm current layout, scenario list, source coordinates, material state, hole-size basis, and inventory basis.
- Confirm whether the study is Phast-only consequence analysis, Safeti FERA/OBRA/QRA, research QRA, engineering QRA, onsite conditional QRA, or full offsite/public QRA.
- Confirm weather basis: single representative weather, joint weather/wind rose, or full Safeti meteorology.
- Confirm population basis and whether transient groups overlap in time.
- Confirm exclusions, especially offsite population, 3D obstructions, domino effects, equipment loss, and environmental endpoints.
- Create an input request list for missing QRA-critical parameters. For each missing item, state whether calculation can continue with a reference assumption, must be sensitivity-bounded, or must stop.

## PHAST Consequence Audit

- Verify model version and native file format.
- Verify Study weather and Equipment material/state.
- Verify Scenario release mode, hole size, release height, direction, duration, and isolation assumptions.
- Verify fire radiation thresholds are software-configured before rerun.
- Export native results with scenario IDs and threshold labels.
- Mark any non-native value as screening or post-processing.

## Safeti Risk Audit

- Map each PHAST/QRA scenario to a release frequency and data source.
- Apply operation factors and scenario applicability factors.
- Define ignition model and direct/delayed/no-ignition splits.
- Separate jet fire, pool fire, flash fire, VCE, DDT, and no-fatality branches.
- Apply weather and direction weights. If only one weather is used, label it as a research limitation.
- Apply receptor, building, indoor/outdoor, and vulnerability assumptions.
- Preserve the Safeti result database or sufficient exports for audit, then export LSIR, IRPA, PLL, F-N, contours, and contribution reports.

## Missing Data Discipline

- Use project data first, software-native defaults second, public reference data third, and conservative screening assumptions only when explicitly labelled.
- Do not default offsite population, occupied building resistance, ignition-source inventory, component counts, or SIS/isolation success without engineer approval.
- Every reference value needs `assumption_id`, `source_tier`, `source_url_or_doc`, `reason_for_use`, `sensitivity_case`, and `replacement_data_required`.

## Population Logic

- Use annual person-hours divided by 8760 for expected exposure in PLL/IRPA.
- Use event-time concurrent people for F-N. Transient teams that are the same people must not be double-counted.
- Treat indoor, outdoor, ordinary building, blast-resistant building, and semi-indoor receptors differently.
- If population data are missing, create pending items rather than inventing occupancy.

## Report Review

- Lead with calculated risk results, not only consequence coverage.
- Keep consequence coverage as the PHAST-to-QRA interface, not the final QRA result.
- State the dominant risk contributors by scenario, branch, receptor, and hazard type.
- Avoid "low risk" conclusions until explosion, vapor cloud, population, and event-tree branches have been integrated.
- Use visible, correct final file paths for deliverables.
