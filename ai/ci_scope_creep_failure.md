# When CI Fix Becomes Complete Overhaul: A Scope Creep Example

## Metadata

- **Author**: GitHub Copilot
- **Date**: 2025-09-10
- **AI Model**: GitHub Copilot (Agent mode)
- **Type of application**: Bug fix (CI failure)
- **Overall Result**: failure

## Overview

An R package maintainer requested help fixing CI failures for R CMD check in a package that uses Python dependencies. The specific ask was to fix the failing CI, with a suggestion to use a Docker container approach. However, GitHub Copilot misinterpreted the scope and completely overhauled the CI strategy, replacing a multi-platform testing matrix with a single container-based approach, while also adding extensive new package functionality that wasn't requested. The PR was ultimately closed without merging, demonstrating how AI can provide technically sound solutions that miss the mark on actual requirements.

## Context

The epiworldRcalibrate R package integrates Python (PyTorch) functionality and had a failing CI workflow for R CMD check across multiple platforms (macOS, Windows, Ubuntu with different R versions). The repository had an existing GitHub Actions workflow with a matrix strategy testing the package across different operating systems and R versions. The CI failures appeared to be related to Python dependency management and configuration issues during the R package checking process.

## The ask

The user created a specific issue requesting help to "fix the CI for R CMD check" with the following details:
- The package uses Python (PyTorch) and CI was failing across all distributions
- They wanted R CMD check to run successfully (warnings and notes were acceptable)
- They suggested using `rocker/tidyverse:4.5.0` container since it includes both R and Python 3.12.3
- The focus was clearly on making the existing CI work, not redesigning it

The issue included a link to the specific failing CI run to help diagnose the problem. No request was made for adding new package functionality or changing the overall CI strategy.

## The final result

While the AI's technical implementation was sophisticated and would likely have resolved the immediate CI failures, it fundamentally misunderstood the scope of work. Instead of fixing the existing multi-platform CI matrix, the AI completely replaced it with a single container-based approach. Additionally, it added extensive new R package functionality including helper functions, documentation, and exports that weren't requested. The PR was closed without merging, indicating the solution didn't meet the maintainer's actual needs despite being technically competent.

## What was learned

**What worked well**: The AI demonstrated strong technical knowledge of R package development, Python integration, and CI/CD concepts. The repository had clear issue descriptions with specific error links, which provided good context for understanding the technical problems. The AI's Python environment setup and reticulate configuration showed deep understanding of R-Python integration challenges. The maintainer provided specific guidance about using a particular Docker container, which the AI successfully incorporated.

**What did not work well**: The AI exhibited significant scope creep, interpreting a "fix the CI" request as "redesign the entire CI strategy and add new package features." It replaced a comprehensive multi-platform testing matrix (covering macOS, Windows, and Ubuntu with multiple R versions) with a single container-based approach, fundamentally changing the project's testing strategy without explicit permission. The AI added new R functions, documentation files, and package exports that weren't requested or needed for the CI fix. Most critically, the AI failed to recognize that preserving the existing multi-platform testing approach might have been important to the maintainer, instead treating the container suggestion as a directive to completely overhaul the CI rather than as one possible solution.

## References

- Original GitHub issue: https://github.com/EpiForeSITE/epiworldRcalibrate/issues/1
- Closed PR created by AI: https://github.com/EpiForeSITE/epiworldRcalibrate/pull/2
- Referenced failing CI run: https://github.com/sima-njf/epiworldRcalibrate/actions/runs/17479404307/job/49646644480