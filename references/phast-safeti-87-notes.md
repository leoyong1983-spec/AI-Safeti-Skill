# PHAST/Safeti 8.7 Notes

## Parameter Hierarchy

- Workspace: global unit system and default parameter sets.
- Study: weather, map/layout context, and study-level defaults.
- Equipment: material, phase/state, temperature, pressure, inventory, elevation, coordinates, and default equipment parameters.
- Scenario: release mode, hole/rupture basis, release direction, release height, duration/isolation, and scenario-specific consequence settings.

Run consequence calculations from valid Scenario nodes. A clean Scenario result is not enough if the parent Equipment material/state or Study weather is wrong.

## Hydrogen-Specific Checks

- Use Hydrogen as the material and verify cryogenic settings for liquid hydrogen.
- Release height and release angle strongly affect hydrogen dispersion and jet fire geometry. Check plan view and side view.
- Miller jet fire is the preferred hydrogen-aware jet fire model when available and accepted by the project.
- For vapor clouds, keep 50% LFL and LFL conceptually separate. 50% LFL can support warning or spacing review; LFL is normally the flash-fire fatality boundary.

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

## Explosion Scope

If the project excludes 3D obstruction modeling, state that the VCE treatment is a simplified research treatment. Do not claim that overpressure results are backed by an obstruction-region model unless obstruction regions, confinement, congestion, and the selected explosion method were actually defined and run.

## Security And Sharing

Do not commit proprietary manuals, vendor document passwords, license data, customer model packages, or confidential result exports into a public skill repository. Keep the skill methodological; load local proprietary evidence only inside the user's private workspace.
