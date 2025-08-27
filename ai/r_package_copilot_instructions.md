# R Package Copilot Instructions Setup

## Metadata

- **Author**: GitHub Copilot
- **Date**: 2025-08-26
- **AI Model**: GitHub Copilot (agent mode)
- **Type of application**: Documentation and development workflow setup

## Overview

This example demonstrates AI-assisted creation of comprehensive GitHub Copilot instructions for an R package development workflow. The AI was tasked with setting up copilot-instructions.md following best practices to improve development efficiency for the epitraxr R package. The AI successfully created detailed instructions covering environment setup, testing workflows, repository structure, and development best practices. The implementation was comprehensive and merged successfully, providing validated workflows for common R package development tasks.

## Context

The epitraxr R package is designed for manipulating EpiTrax data and generating epidemiological reports. The repository had established R package structure with comprehensive testing using tinytest framework, GitHub Actions workflows for CI/CD, and sample data for development. The project needed GitHub Copilot instructions to standardize development workflows and provide clear guidance for AI-assisted development tasks.

## The ask

The request in [issue #60](https://github.com/EpiForeSITE/epitraxr/issues/60) was to "Configure instructions for this repository as documented in [Best practices for Copilot coding agent in your repository](https://gh.io/copilot-coding-agent-tips)." This was a high-priority task assigned to GitHub Copilot to create comprehensive development instructions that would improve AI-assisted coding efficiency for the R package.

## The final result

The AI successfully created a comprehensive `.github/copilot-instructions.md` file with 104 lines covering all aspects of R package development. The implementation included:

**Environment Setup & Dependencies:**
- Complete R installation and system dependency setup commands for Ubuntu/Debian systems
- Package dependency installation via apt to avoid network connectivity issues during development
- Pre-commit hook configuration with proper error handling expectations

**Testing and Validation Workflows:**
- Comprehensive testing strategy using the tinytest framework with precise timing measurements (0.5 seconds for full test suite)
- Individual test file execution guidance for targeted testing of specific components
- Clear requirement that all tests must pass before PR approval
- R CMD check validation procedures

**Development Operations:**
- Package building and installation procedures with verified 2-second install time
- Component-specific testing guidance for data processing, report generation, and filesystem modules
- Documentation requirements emphasizing roxygen blocks and unit tests for new functions

**Repository Structure Documentation:**
- Detailed explanation of core directories and their purposes
- Key development files and their roles in the package ecosystem
- Clear guidance on automatically generated files that should not be manually edited

The PR was successfully merged with positive feedback, providing a robust foundation for AI-assisted development in the repository.

## What was learned

**What worked well**: 
- The task aligned well with GitHub's established best practices documentation, providing clear guidance on what should be included in copilot instructions
- The R package had well-established patterns for testing, building, and validation that could be easily documented with specific commands and timing expectations
- The repository structure was clean and followed R package conventions, making it straightforward to document the development workflow
- The existing CI/CD workflows and testing framework provided concrete examples of validated development operations that could be included in the instructions
- The user provided a clear, focused request with a specific reference to established best practices documentation
- The package had precise timing measurements for common operations (package install: 2 seconds, test suite: 0.5 seconds) that could be accurately documented

**What did not work well**: 
- The initial implementation included a .gitignore update to exclude build artifacts (*.Rcheck) that, while useful, expanded beyond the core request for copilot instructions
- Based on the fact that the AI made changes to two files instead of just creating the instructions file, there may have been some scope expansion beyond the minimal requirements of the original issue

## References

- GitHub issue: <https://github.com/EpiForeSITE/epitraxr/issues/60>
- Merged PR: <https://github.com/EpiForeSITE/epitraxr/pull/61>
- Best practices reference: <https://gh.io/copilot-coding-agent-tips>