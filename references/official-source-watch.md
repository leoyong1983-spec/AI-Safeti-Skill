# Official Source Watch

Use this reference when updating the skill, checking PHAST/Safeti 8.7-and-earlier behavior against public authority, or deciding whether a method belongs in an 8.7-locked report.

## Source Hierarchy

1. DNV official software pages, My DNV Software Knowledge Centre, release notes, user manuals, help library, official training, official videos, and Veracity marketplace/support pages. For model behavior in an 8.7 project, prefer 8.7-specific release notes, installed 8.7 help, installed 8.7 documentation, and software-native exports over current-version marketing pages.
2. DNV public service pages and DNV-authored QRA/consequence-analysis articles.
3. Government, regulator, standards body, university, or peer-reviewed material that is independent of DNV but relevant to QRA practice.
4. Third-party tutorials or consultant notes. Use only as orientation; never treat as software authority.

Never use cracked software sites, password-sharing posts, reposted manuals, leaked PDFs, or forum claims as authoritative sources.

## DNV Links To Check First

- Knowledge Centre: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/
- Downloads and licensing notes: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/softwaredownloads/
- Release notes: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/whatsnew/
- Help library: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/help-library/
- User manuals index: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/user-manuals/
- Official webinars: https://mysoftware.dnv.com/knowledge-centre/phast-and-safeti/webinars/
- Phast/Safeti FAQ: https://www.dnv.com/software/services/plant/phast-safeti-FAQ/
- Safeti product page: https://www.dnv.com/services/safeti/
- QRA software overview: https://www.dnv.com/software/services/plant/quantitative-risk-analysis/
- Phast product page: https://www.dnv.com/software/services/plant/consequence-analysis-phast.html

## 8.7-And-Earlier Version Watch

As checked on 2026-05-12:

- The DNV downloads page now lists Phast/Safeti 9.3 as the Latest Version with release date 11-May-2026. This is a later-version upgrade-watch item only; do not treat any 9.3 feature, installer behavior, or workflow change as available in the user's active 8.7 environment unless the user explicitly approves an upgrade.
- The DNV downloads page lists Phast/Safeti 8.7 with release date 02-Aug-2022; for this skill, 8.7 is the active upper-bound version.
- The DNV downloads page lists earlier Phast/Safeti versions including 8.61, 8.6, 8.4, 8.23, 8.22, 8.21, 8.2, 8.11, 8.1, 8.0, and 7.22. Versions 7.22 and earlier are marked as no longer technically supported.
- The DNV release-notes page lists Phast 8.7 and Safeti 8.7 release notes dated 02-Aug-2022, plus release notes for earlier 8.x and 7.x versions. The page also states that releases prior to 9.3 remain in the PDF archives.
- The DNV downloads and release-notes pages list KFX 7.2 as the latest KFX-EXSIM release dated 31-Mar-2026. Treat this as companion-product upgrade watch only; do not assume KFX 7.2 behavior is present in a Phast/Safeti 8.7 workflow.
- The DNV public user-manuals page currently lists Phast, Safeti, and Safeti Study Manager manuals for version 9.3, dated May 2026. Use these only as later-version context unless a statement is independently confirmed in 8.7 release notes, installed 8.7 help, installed 8.7 documentation, or 8.7 software-native exports.
- The DNV downloads page describes the 9.1+ access-key licensing system. For 8.7-and-earlier work, preserve the previous license workflow and keep license files, dongle/network setup, and activation data outside public skills and reports.
- The DNV FAQ states that Phast is consequence modelling software, whereas Safeti is consequence and risk modelling software. Do not describe a Phast-only run as Safeti QRA.
- The DNV FAQ lists Phast uses such as HAZOP/HAZID/PHA/LOPA consequence support, emergency planning, facility siting/layout optimisation, hazardous area classification, regulatory safety reports, and vent/flare design. Treat these as consequence-analysis applications unless Safeti risk integration is actually performed.
- The DNV FAQ lists Safeti uses such as FERA, OBRA, QRA, risk-based design, cost-benefit analysis, and sensitivity analysis. Treat fatality individual and societal risk as the core QRA output unless the project explicitly adds environmental, asset, or financial risk.
- The FAQ states that Safeti risk results are stored using Microsoft SQL Server. For formal handoff, preserve database/result artifacts or exports needed to reproduce LSIR, PLL, F-N and contour outputs.
- The FAQ distinguishes free-field modelling from CFD: where obstacles or undulating terrain matter, CFD is the preferred solution. If a project excludes 3D/CFD, document the free-field simplification.
- The Safeti product page states that Safeti provides LSIR contours, F-N curves, PLL, and risk ranking points as standard risk metrics.
- The FAQ confirms Phast/Safeti can model hydrogen, CO2, nitrogen, ammonia, LNG/LPG, toxic/asphyxiation releases, in-building releases, GIS imports/exports, and that DNV uses verification, validation, and sensitivity testing for the software.

## Later Official Material Watch

Later DNV official pages and webinars can be useful for upgrade awareness, but must not be converted into 8.7 instructions unless the same behavior is confirmed in 8.7 release notes, installed 8.7 help, or software-native 8.7 exports.

- Phast/Safeti 9.3, 9.11, 9.1, 9.0, 8.9, and 8.71 release material is non-applicable to active 8.7 modelling except as compatibility, upgrade-risk, or future-upgrade context.
- The current DNV Safeti product page says detailed CFD result import into Safeti risk analysis using `*.asc` files is available from Safeti 9.1 or later. Do not recommend this as an 8.7 executable workflow; for 8.7, keep CFD-to-QRA interfaces limited to workflows confirmed in 8.7 documentation or explicitly approved external/research integration.
- DNV official post-8.7 webinars such as hydrogen modelling, Phast-to-Safeti transition, Phast API, in-building modelling, and Phast 9.x overviews are training or upgrade-watch material. Use them only as prompts for checking 8.7 documentation, not as standalone authority for 8.7 reports.

## 8.7-And-Earlier Official Webinar Topics

Use official webinars as training and workflow evidence, not as a replacement for 8.7 release notes, local help, or software-native exports. Relevant 8.7-and-earlier DNV webinar topics include:

- Phast 8.7 live demo: CFD modelling for jet fires, 13-Jul-2022.
- Large study guidance for Safeti, 19-May-2022.
- Energy transition initiatives for hydrogen in Phast, Safeti and KFX, 30-Mar-2022.
- Facility siting and occupied building risk analysis using Phast and Safeti, 22-Sep-2021.
- Materials and mixtures setup in Phast and Safeti, 28-Aug-2021.
- GIS integration for Phast and Safeti, 14-Jul-2021.
- Ignition source modelling in Safeti and impact on results, 17-Jun-2020.
- Occupied buildings risk assessment using Phast and Safeti, 29-Jan-2020.
- Range and application of Phast and Safeti explosion models for facility siting, 03-Dec-2018.
- Introduction to QRA in oil, gas and chemical process industries, 14-Jun-2017.
- Explosion modelling in onshore facilities, 22-Jun-2016.

## How To Apply 8.7-Locked Updates

- Do not silently apply 8.71, 8.9, or 9.x features to an 8.7 model. Record later-version information only as non-applicable context or a future upgrade watch item.
- Prefer DNV 8.7 release notes, 8.7 local help, 8.7 installed documentation, and 8.7 software-native result exports over current-version public pages when resolving model behavior.
- If an external method depends on a feature introduced after 8.7, mark it "not available in active software" unless the user explicitly approves a version upgrade or separate sensitivity calculation.
- Always keep the report clear about what was actually run in PHAST/Safeti 8.7 versus what was identified from newer official documentation.
