# Official Source Watch

Use this reference when updating the skill, checking PHAST/Safeti behavior against public authority, or deciding whether a method belongs in a report.

## Source Hierarchy

1. DNV official software pages, My DNV Software Knowledge Centre, release notes, user manuals, help library, official training, official videos, and Veracity marketplace/support pages.
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
- Phast/Safeti FAQ: https://www.dnv.com/software/services/plant/phast-safeti-FAQ/
- Safeti product page: https://www.dnv.com/services/safeti/
- QRA software overview: https://www.dnv.com/software/services/plant/quantitative-risk-analysis/
- Phast product page: https://www.dnv.com/software/services/plant/consequence-analysis-phast.html

## Current Public Version Watch

As checked on 2026-05-10:

- The DNV downloads page lists Phast/Safeti 9.11 as the latest version dated 29-Jul-2025.
- The same downloads page states that Phast/Safeti 9.1 is no longer supported due to a licensing issue and recommends using 9.11. Do not recommend 9.1 as a target upgrade without checking this note.
- Starting with version 9.1, the downloads page states that an access key is required to activate Phast and Safeti. Keep licensing and activation handling outside public skills and reports.
- The DNV Knowledge Centre release-notes page lists Phast 9.11 Release Notes as the latest Phast release note entry dated 29-Jul-2025.
- The DNV user-manual index lists Phast User Manual, Safeti User Manual, and Safeti Study Manager User Manual at version 9.11 with July 2025 release dates.
- The DNV FAQ states that Phast is consequence modelling software, whereas Safeti is consequence and risk modelling software. Do not describe a Phast-only run as Safeti QRA.
- The FAQ states that Safeti risk results are stored using Microsoft SQL Server. For formal handoff, preserve database/result artifacts or exports needed to reproduce LSIR, PLL, F-N and contour outputs.
- The FAQ distinguishes free-field modelling from CFD: where obstacles or undulating terrain matter, CFD is the preferred solution. If a project excludes 3D/CFD, document the free-field simplification.
- The Safeti product page states that Safeti provides LSIR contours, F-N curves, PLL, and risk ranking points as standard risk metrics.
- The same Safeti product page states that detailed CFD result integration by importing `.asc` files is available from Safeti 9.1 or later.
- The FAQ confirms Phast/Safeti can model hydrogen, CO2, nitrogen, ammonia, LNG/LPG, toxic/asphyxiation releases, in-building releases, GIS imports/exports, and that DNV uses verification, validation, and sensitivity testing for the software.

## How To Apply Version Updates

- For an 8.7-locked project, do not silently apply 9.x features to the active model. Record them as upgrade or sensitivity review items.
- If a method depends on a version-specific feature, include the minimum version in the assumption or method note.
- For Safeti 9.1+ projects, consider whether CFD `.asc` import, Extended Explosions, or updated licensing/workflow behavior changes the recommended model path.
- Always keep the report clear about what was actually run in software versus what was identified from newer official documentation.
