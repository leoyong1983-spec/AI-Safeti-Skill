---
name: ai-safeti-skill
description: >-
  DNV PHAST/Safeti 8.7 hydrogen and liquid-hydrogen QRA/FEA workflow skill.
  Use when Codex must audit, build, rerun, or report PHAST/Safeti models,
  hydrogen leak/fire/explosion consequences, Safeti risk integration, LSIR,
  IRPA, PLL, F-N curves, personal-risk contours, QRA report upgrades, or
  safety-model deliverables requiring software-native traceability rather than
  AI interpolation. 中文：用于 DNV PHAST/Safeti 8.7 氢气与液氢 QRA/FEA
  模型审查、重建、复算和报告，强调软件原生结果、版本边界、可审计性和资料安全。
---

# AI Safeti QRA / AI Safeti 定量风险评价

Use this skill for hydrogen or liquid-hydrogen consequence and QRA work where PHAST/Safeti results must be auditable, software-native, and aligned with a human safety review.

当任务涉及氢气或液氢后果分析、Safeti QRA、风险积分或报告审查时使用本技能。所有 PHAST/Safeti 结果必须可审计、来自软件原生输出，并与人工安全审查边界一致。

## Bilingual Scope / 双语说明

- English: This skill locks active modelling and report recommendations to DNV PHAST/Safeti 8.7 unless the user explicitly approves a software upgrade.
- 中文：本技能将主动建模和报告建议锁定在 DNV PHAST/Safeti 8.7，除非用户明确批准软件升级。
- English: It supports model audits, scenario rebuilds, consequence-result checks, Safeti QRA integration, LSIR/IRPA/PLL/F-N review, and report upgrades.
- 中文：本技能支持模型审查、场景重建、后果结果核查、Safeti QRA 集成、LSIR/IRPA/PLL/F-N 复核和报告升级。
- English: Later-version DNV material may be recorded only as non-applicable context, compatibility risk, or upgrade-watch evidence.
- 中文：后续版本 DNV 资料只能作为“不适用于 8.7”、兼容性风险或未来升级观察，不得写成 8.7 可执行方法。
- English: Public GitHub updates must remain methodological and must not include vendor manuals, licence artifacts, credentials, customer model files, private coordinates, or confidential results.
- 中文：公开 GitHub 更新只保留方法论内容，不得包含供应商手册全文、许可文件、凭证、客户模型、私有坐标或敏感计算结果。

## Non-Negotiables / 不可违反项

- Treat PHAST/Safeti as the governing calculation engine. Do not present AI interpolation, hand conversion, or spreadsheet extrapolation as a certified software result.
- If post-processing is unavoidable, label it as non-software screening and keep it out of formal PHAST/Safeti result tables unless the user explicitly approves that status.
- Keep the active model, software version, source package, run date, scenario IDs, and result-export filenames visible in every calculation note.
- Use the latest user-approved model package only. Remove superseded scenario names, hole sizes, layouts, and historical results from the active report.
- Do not publish or commit vendor manuals, license files, passwords, credentials, proprietary project paths, private coordinates, or confidential result tables to a shared repository.
- When data are missing, create a pending-information register. Do not silently invent population, ignition sources, equipment counts, isolation reliability, offsite receptors, or weather distributions.
- Proactively prompt the engineer for QRA-critical inputs before calculating. If inputs are missing, offer clearly sourced reference-data candidates and mark them as assumptions requiring approval, sensitivity, and later replacement.
- For public-risk standards, separate offsite/public compliance from onsite/conditional research QRA. Do not claim full GB 36894 or equivalent public-risk compliance unless offsite receptors and population are modeled.
- When a project excludes 3D obstruction modeling, do not add it implicitly. If VCE is retained without 3D obstruction, state the free-field/simplified explosion basis and its review status.
- Treat PHAST/Safeti 8.7 as the active upper-bound version unless the user explicitly approves an upgrade. Later-version material may be noted only as non-applicable context, compatibility risk, or upgrade watch item; do not import 8.71/8.9/9.x-only features into an 8.7 model workflow.

## Workflow / 工作流

1. Freeze the boundary: confirm model package, layout, weather set, scenario list, material state, hole-size basis, inventory basis, population basis, and accepted exclusions.
2. Audit the PHAST model hierarchy: Workspace -> Study -> Equipment -> Scenario. Confirm Study weather and Equipment material/state/inventory/location before running Scenario calculations.
3. Ask for missing QRA-critical inputs using `references/qra-input-prompting.md`. Provide reference-data candidates only with source tier, assumption ID, and sensitivity requirement.
4. Run or verify PHAST consequences from native software exports. For fire radiation levels, configure the software parameter set before rerun; do not interpolate target thresholds after the fact.
5. Build the Safeti QRA chain: release frequency -> operation factor -> direction/weather -> detection/isolation -> ignition event tree -> consequence branch -> receptors/buildings -> fatality model -> LSIR/IRPA/PLL/F-N/risk contours.
6. Confirm the analysis type: Phast-only consequence input, Safeti FERA/OBRA/QRA, or external research integration. Do not label a Phast-only calculation as Safeti QRA.
7. Integrate population correctly: use annual person-hours for PLL/IRPA exposure, but use event-level concurrent population for F-N. Do not generate F-N directly from equivalent continuous population.
8. Write the report around risk questions: maximum credible consequence, worst accident, dominant contribution, risk acceptability basis, uncertainty/sensitivity, and pending data needed for engineering QRA.
9. Hand off review artifacts: model files, Safeti result database or exports, exported CSVs, figures, calculation tables, assumptions register, pending-information register, and an explicit list of values that are software-native versus post-processed.

## PHAST/Safeti Guardrails / PHAST/Safeti 防护规则

- Select `Hydrogen` as material. For liquid hydrogen, verify cryogenic saturated or otherwise user-approved low-temperature storage state.
- Trigger calculations at Scenario level after upper-level validation passes.
- For hydrogen jet fire, prefer the Miller jet fire model when available and appropriate. Record the selected model and parameter set.
- Configure requested fire intensity levels in PHAST/Safeti parameter tables before rerun. Set both the number of radiation levels and the radiation-level values where the software exposes both controls.
- Keep dose/probit/lethality calculations disabled when the task is only to export intensity contours. Enable vulnerability models only when the QRA fatality calculation explicitly requires them.
- Treat 50% LFL as detection, warning, or spacing information unless a standard or user-approved method says otherwise. Do not substitute 50% LFL for LFL flash fatality boundary.
- Separate hole-size basis from inventory basis. A "10% area equivalent hole" is not a "10% inventory" assumption; collection-pit volume participation is a separate source-term assumption.
- For explosion, separate flash fire, VCE, DDT, and no-ignition vapor-cloud branches. Do not merge VCE and pool fire into one event-tree branch.

## QRA Calculation Rules / QRA 计算规则

Use the branch-frequency form below unless the project specifies a more detailed Safeti export:

```text
f_branch = f_release
         * F_operation
         * P_direction
         * P_weather
         * P_barrier
         * P_ignition
         * P_consequence

IR_r = sum(f_branch * P_fatality,r)

PLL = sum(f_branch * sum(N_r,eq * P_fatality,r))

N_r,eq = annual_person_hours_r / 8760
```

For F-N, calculate `N_branch` from the people concurrently present during that event state and time window, then sum frequencies where `N_branch >= n`.

## Deliverable Standard / 交付标准

The QRA report or calculation book should include:

- Boundary and assumption set with stable assumption IDs.
- Scenario register and source-term basis.
- Release-frequency table with operation factors and data status.
- Ignition/event-tree branch-frequency table.
- Weather and wind-direction weighting table, or a clear single-weather research limitation.
- Population, exposure, building, and vulnerability model table.
- PHAST/Safeti input-output traceability table.
- LSIR/IRPA table, personal-risk contours, PLL table, conditional F-N curve, and risk-contribution ranking.
- Sensitivity cases and pending-information register.
- A conclusion that distinguishes research QRA, engineering QRA, onsite conditional risk, and offsite public-risk compliance.

## Reference Files / 参考文件

Load only the reference needed for the task:

- `references/official-source-watch.md`: official-source hierarchy, current DNV knowledge links, and version-watch rules.
- `references/phast-safeti-87-notes.md`: PHAST/Safeti 8.7 parameter hierarchy, result-object checks, and software-native result discipline.
- `references/qra-input-prompting.md`: proactive engineer prompts and reference-data fallback rules for missing QRA inputs.
- `references/qra-workflow-checklist.md`: end-to-end QRA audit checklist for model rebuilds and report upgrades.
- `references/qra-register-templates.md`: reusable table schemas for scenarios, assumptions, event trees, population, and pending data.
