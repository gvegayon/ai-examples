# Automated Report Generator with Follow-up Fix

## Metadata

- **Author**: GitHub Copilot
- **Date**: 2025-08-22
- **AI Model**: GitHub Copilot (agent mode)
- **Type of application**: Feature addition and bug fix

## Overview

This example documents an AI-assisted project to create an automated GitHub Actions workflow that generates daily status reports for multiple projects. The initial implementation was successful but had formatting issues that required a follow-up fix. The AI was able to create a comprehensive R-based solution that tracks project metrics via GitHub API and generates markdown reports automatically. While the initial result needed refinement, the second iteration successfully addressed all formatting and accuracy issues.

## Context

The EpiForeSITE software repository needed an automated way to track progress across multiple projects, similar to existing project dashboards. The repository contained YAML files with project metadata in a `./data` directory, and the goal was to create a daily automated report showing contributors, issues, PRs, commits, and other GitHub metrics for projects with GitHub repositories.

## The ask

The request was to create a GitHub Actions workflow that would:

1. Read project information from YAML files in `./data` directory
2. Filter projects that have GitHub repositories
3. Extract metrics using GitHub API: contributors, active issues, last commit, open PRs, commit counts
4. Generate a markdown table similar to an existing reference project
5. Save as `project_status.md` and commit to main branch
6. Run automatically once daily

The initial ask was documented in [issue #52](https://github.com/EpiForeSITE/software/issues/52), which was successfully implemented in [PR #53](https://github.com/EpiForeSITE/software/pull/53). However, the generated report had formatting issues that led to a follow-up request in [issue #55](https://github.com/EpiForeSITE/software/issues/55) to improve the table layout and fix data accuracy problems.

## The final result

The AI successfully completed both the initial implementation and the follow-up fix. The first iteration (PR #53) created:

- A comprehensive GitHub Actions workflow running daily at 6 AM UTC
- An R script that processes 19 projects with GitHub repositories
- GitHub API integration with proper rate limiting and error handling
- Automated markdown table generation with contributor avatars and live badges
- Automatic git commits using existing actions

The second iteration (PR #56) addressed formatting and accuracy issues:

- Consolidated table columns from 7 to 5 for better readability
- Fixed critical commit count accuracy by restructuring API call logic
- Removed redundant contributor count numbers
- Enhanced table formatting with proper line breaks

Both implementations were merged successfully with minimal human intervention. The main guidance needed was clarification of specific formatting requirements and table layout preferences.

## What was learned

**What worked well**: 
- The AI effectively understood complex requirements involving multiple technologies (GitHub API, R, GitHub Actions, YAML parsing)
- It successfully created a complete end-to-end solution with proper error handling and documentation
- The AI demonstrated good problem-solving skills by implementing multiple fallback methods for commit counting
- Pattern recognition from existing repository structures helped guide the implementation
- The second iteration showed good responsiveness to specific formatting feedback

**What did not work well**: 
- The initial table format was too wide and not user-friendly, requiring refinement
- Commit count accuracy was initially problematic due to API limitation understanding (using 52-week participation stats instead of full repository history)
- Some redundant display elements (contributor counts) were included that needed removal
- The AI needed explicit guidance on table formatting preferences rather than inferring optimal layout

## References

- Initial GitHub issue: <https://github.com/EpiForeSITE/software/issues/52>
- Initial PR with implementation: <https://github.com/EpiForeSITE/software/pull/53>
- Follow-up issue for improvements: <https://github.com/EpiForeSITE/software/issues/55>
- Follow-up PR with fixes: <https://github.com/EpiForeSITE/software/pull/56>