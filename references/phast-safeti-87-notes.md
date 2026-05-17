# PHAST/Safeti 8.7 Notes

Primary 8.7 public source to check before applying any later-version method:

- DNV Phast/Safeti 8.7 release notes: https://mysoftware.dnv.com/download/public/phast/release_notes/phast_08_7_0_release_notes.pdf

## Parameter Hierarchy

- Workspace: global unit system and default parameter sets.
- Study: weather, map/layout context, and study-level defaults.
- Equipment: material, phase/state, temperature, pressure, inventory, elevation, coordinates, and default equipment parameters.
- Scenario: release mode, hole/rupture basis, release direction, release height, duration/isolation, and scenario-specific consequence settings.

Run consequence calculations from valid Scenario nodes. A clean Scenario result is not enough if the parent Equipment material/state or Study weather is wrong.

## Hydrogen-Specific Checks

- Use Hydrogen as the material and verify cryogenic settings for liquid hydrogen.
- Release height and release angle strongly affect hydrogen dispersion and jet fire geometry. Check plan view and side view.
- Miller jet fire is the preferred hydrogen-aware jet fire model when available and accepted by the project. DNV public hydrogen guidance states that Miller was introduced in Phast/Safeti 8.6 but became the default for hydrogen vapour releases only in 8.9, so an 8.7 review must explicitly check and record the selected jet-fire model rather than assume the default.
- For vapor clouds, keep 50% LFL and LFL conceptually separate. 50% LFL can support warning or spacing review; LFL is normally the flash-fire fatality boundary.

## 8.7 Release-Note Checks

- Phast 8.7 supports standalone jet-fire CFD. If using this capability, record whether the required Phast CFD - jet fires licence is present; without that licence, 3D geometries may be available for visualisation but must not be reported as geometry inputs to the CFD calculation.
- For CFD calculations, do not assume edited component properties in the Phast material database are used by the CFD engine. Record whether the case depends on edited component properties, especially for mixtures or non-standard hydrogen property assumptions.
- For standalone pool and jet fires, check the release orientation, wind direction, and GIS event rotation labels before comparing plots or exporting contours. Do not mix an 8.7 event-rotation plot with an older crosswind-angle interpretation.
- Phast/Safeti 8.7 uses OpenXML for Excel data input/output, so Microsoft Excel is not required for those import/export actions. Excel-style input/output remains useful for auditable bulk edits and multi-file consistency checks.
- Safeti 8.7 risk calculations can use CUDA 11.6 on NVIDIA hardware. For performance troubleshooting or large-study reruns, record whether CUDA-capable hardware was available and whether calculations were CPU-only or GPU-assisted.
- Studies from version 6.7 or earlier saved as compressed `*.psc` files cannot be upgraded directly to 8.7. Convert through a supported path or rebuild the study with traceable inputs.

## Known 8.7 Review Traps

- After parallel calculations, recheck standalone radiation calculation selections and requested fire-radiation outputs before exporting contours or tables.
- For flammable scenarios with delayed ignition/free-field treatment, confirm the Run Row plant boundary is actually set even if the field is not shown as mandatory.
- For standalone jet fire, pool fire, or fireball transects, verify that the transect direction captures the critical radiation side; 8.7 transect results can miss upwind points.
- Run CFD studies from a local drive rather than a OneDrive-synchronised folder when possible, especially for pool-fire CFD reruns.
- When importing weather data into a new workspace from Excel, delete unused default weathers if the project does not require them.

## Fire Radiation Level Setup

When a project requires thresholds such as 4, 9, 15, and 30 kW/m2, configure those thresholds in the software before rerunning.

Audit both:

- the field containing radiation-level values; and
- the field containing the number of radiation levels.

Do not switch on dose, probit, or lethality options solely to force extra intensity outputs. Those options create a different result family and can pollute a clean consequence-distance export.

## Result Object Discipline

When extracting or reviewing exports, distinguish these result families:

- Flammable dispersion consequence distances.
- Jet fire consequence distances.
- Jet radiation ellipse or incident-radiation effects.
- Pool fire consequence distances.
- Pool radiation ellipse or incident-radiation effects.
- Explosion overpressure distances and explosion effects.
- Risk reports, risk contours, LSIR/IRPA, PLL, and F-N outputs.

Use exact software-exported object names when writing audit notes. If object names differ by version or localization, capture screenshots or CSV headers.

## Large Safeti Study Discipline

For large 8.7 studies, build and run the model in controlled stages:

- Use Smart run mode unless the project has a documented reason to force Series or Parallel. In 8.7, consequence calculations can benefit from parallel execution, while risk calculations are recombined and run in series.
- Run consequence calculations and examine scenario/weather families before running risk. If results are materially similar, combine or remove scenarios/weathers only with engineer approval and a recorded sensitivity basis.
- Keep the requested level of risk-result detail deliberate. Full outcome-contribution detail can make the Safeti SQL risk-results database much larger; preserve enough detail for audit without generating unnecessary database volume.
- When using Study Manager or multi-file workflows, save/archive the calculated workspace in a form that preserves the embedded risk-results database and map assets. Record which exported or archived file is the review artifact.
- Put route models and long-pipeline models in separate workspace files when they make the main analysis slow or memory-heavy.
- Use the Safeti Console runner for large calculation batches when the UI becomes the memory bottleneck. Capture the command, workspace folder, calculated output path, and log evidence.
- Avoid opening consequence reports or graphs for very large scenario sets at once. Inspect bounded scenario batches and keep exported result filenames tied to scenario IDs.

## Explosion Scope

If the project excludes 3D obstruction modeling, state that the VCE treatment is a simplified research treatment. Do not claim that overpressure results are backed by an obstruction-region model unless obstruction regions, confinement, congestion, and the selected explosion method were actually defined and run.

## Security And Sharing

Do not commit proprietary manuals, vendor document passwords, license data, customer model packages, or confidential result exports into a public skill repository. Keep the skill methodological; load local proprietary evidence only inside the user's private workspace.
