# Create Measles Package as epiworldR Spinoff

## Metadata

- **Author**: GitHub Copilot
- **Date**: 2025-11-13
- **AI Model**: GitHub Copilot (agent mode)
- **Type of application**: Re-factoring
- **Overall Result**: successful

## Overview

This example documents an AI-assisted creation of a new R package as a spinoff from epiworldR. The task involved extracting only the measles-specific models from the larger epiworldR package and creating a standalone "measles" package that depends on epiworldR for core functionality. The AI successfully reduced the package to 89% fewer R files, 65% fewer C++ files, and properly configured dependencies to avoid code duplication.

## Context

The epiworldR package contains multiple epidemiological models for various diseases. Over time, the team had collected multiple measles-specific models and wanted to release them as a separate toolkit for easier sharing and focused development. The challenge was to create a clean spinoff that leverages epiworldR's core functionality without duplicating the entire epiworld C++ library, while maintaining a complete, buildable R package.

## The ask

The request (issue #1 in the new measles repository) asked the AI to create a new R package called "measles" by:

1. Updating DESCRIPTION to rename the package and make it dependent on epiworldR
2. Keeping only measles models in the `src` folder while linking to epiworldR's include directory
3. Keeping only measles models in the `R` folder
4. Dropping vignettes that weren't measles-specific
5. Updating README to describe the measles models and indicate it's a spinoff

The branch was intended to become the main branch of a new repository, not to be merged back into epiworldR.

## The final result

The AI successfully completed the task with 14 commits, achieving remarkable code reduction:

**Package Structure:**
- R files: 36 → 4 (89% reduction)
- C++ files: 17 → 6 (65% reduction)  
- Tests: 30+ → 5 (83% reduction)
- Documentation: 33+ → 3 (91% reduction)

**Key deliverables:**
1. **Focused models**: Retained only three measles models (ModelMeaslesSchool, ModelMeaslesMixing, ModelMeaslesMixingRiskQuarantine)
2. **Proper dependency management**: Updated DESCRIPTION with `Depends: epiworldR (>= 0.10.0.0)` and `Remotes: UofUEpiBio/epiworldR@main`
3. **C++ integration**: Modified C++ files to link against epiworldR's include directory instead of duplicating the epiworld library
4. **Clean NAMESPACE**: Configured to import functions from epiworldR (entity, add_entity, run, summary, plot, etc.) and export only measles models
5. **Updated documentation**: New README focused on measles models, updated CITATION to reflect the spinoff

The PR was closed (not merged) as intended, since the branch became the foundation for the new measles repository at github.com/UofUEpiBio/measles.

## What was learned

**What worked well**: The AI demonstrated excellent understanding of R package structure and dependency management. The comprehensive file reduction showed good judgment about what to keep versus remove. The proper use of the Remotes field in DESCRIPTION to reference the development version of epiworldR showed sophisticated understanding of R package dependencies. The AI successfully avoided code duplication by properly linking to epiworldR's C++ headers.

**What did not work well**: With 14 commits, there were likely several iterations needed to get all the details right, particularly around the C++ integration and NAMESPACE configuration. The large number of file deletions (49,499 deletions) could have been handled more efficiently if the AI had started from a cleaner base. Some back-and-forth may have been needed to determine exactly which helper functions to import from epiworldR versus keeping local copies.

## References

- GitHub issue: <https://github.com/UofUEpiBio/measles/issues/1>
- GitHub PR: <https://github.com/UofUEpiBio/epiworldR/pull/141>
- Closed on: November 17, 2025 (not merged, branch moved to new repository)
- New repository: <https://github.com/UofUEpiBio/measles>
