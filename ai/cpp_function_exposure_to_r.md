# Exposing C++ Function to R Interface

## Metadata

- **Author**: GitHub Copilot
- **Date**: 2025-08-22
- **AI Model**: GitHub Copilot (agent mode)
- **Type of application**: Feature addition

## Overview

This example documents a straightforward but technically complex task where AI was used to expose a new C++ model class to an R package interface. The AI successfully created all necessary wrapper functions, R interface code, documentation, and tests to integrate a new epidemiological model (`ModelSEIRMixingQuarantine`) from the underlying C++ library into the epiworldR package. The implementation was completed quickly and merged successfully with minimal human intervention, demonstrating effective pattern recognition and code generation capabilities.

## Context

The epiworldR package is an R interface to the epiworld C++ library for agent-based epidemiological modeling. The C++ library had recently added a new model called `ModelSEIRMixingQuarantine` that extends the basic SEIR mixing model with quarantine and hospitalization features. The R package needed to be updated to expose this new functionality to R users, following the established patterns used for other models in the package.

## The ask

The request in [issue #116](https://github.com/UofUEpiBio/epiworldR/issues/116) was to port the new `ModelSEIRMixingQuarantine` model from C++ to the R API by:

1. Updating `src/epimodels.cpp` to add the new model wrapper function
2. Creating the corresponding R script under `R/` with documentation and examples
3. Adding tests using the existing tinytest framework
4. Following the same patterns used for other models like `ModelSEIRMixing`

The work needed to be done on the `fixing-seirmixingquarantine` branch and required handling 15 different parameters for the model constructor.

## The final result

The AI delivered a complete and successful implementation that was merged in [PR #117](https://github.com/UofUEpiBio/epiworldR/pull/117). The implementation included:

**C++ Interface:**
- Added `ModelSEIRMixingQuarantine_cpp` wrapper function to `src/epimodels.cpp`
- Updated `src/cpp11.cpp` with proper function declaration and registration for all 15 parameters
- Followed existing patterns from other model wrappers exactly

**R Interface:**
- Created `R/ModelSEIRMixingQuarantine.R` with complete function implementation
- Added comprehensive parameter validation using existing helper functions
- Included detailed roxygen2 documentation with working examples
- Updated `NAMESPACE` to export the new function

**Testing:**
- Created `inst/tinytest/test-seirmixingquarantine.R` with comprehensive tests
- Included both functional tests and input validation tests
- Added error handling tests for invalid parameters
- Followed established testing patterns from other models

The implementation correctly handled all 15 model parameters, including standard SEIR parameters (contact rate, transmission rate, recovery rate, etc.) and quarantine-specific parameters (hospitalization rate, isolation period, quarantine willingness, etc.). The AI successfully understood the complex parameter relationships and validation requirements.

## What was learned

**What worked well**: 
- The AI demonstrated excellent pattern recognition by following existing model implementations precisely
- Complex parameter handling (15 parameters with various types and validation rules) was implemented correctly
- The AI successfully navigated the multi-language codebase (C++, R, documentation)
- All components (C++ wrapper, R interface, documentation, tests) were created consistently
- The implementation passed all validation checks and integrated seamlessly
- Code followed established package conventions perfectly
- The AI correctly understood the relationship between C++ constructors and R function parameters

**What did not work well**: 
- No significant issues were encountered with the AI implementation
- The AI correctly identified all required patterns and generated appropriate code without needing corrections

## References

- GitHub issue: <https://github.com/UofUEpiBio/epiworldR/issues/116>
- Merged PR: <https://github.com/UofUEpiBio/epiworldR/pull/117>
- C++ model reference: <https://github.com/UofUEpiBio/epiworldR/blob/3936656345fa235602bb216938a96cabd60dabdf/inst/include/epiworld/models/seirmixingquarantine.hpp>