# New epiworld model

## Metadata

- **Author**: George G. Vega Yon (in collaboration with GitHub copilot)
- **Date**: 2025-08-21
- **AI Model**: Unknown
- **Type of application**: feature addition

## Overview

The epiworld C++ library is a framework for agent-based modeling (ABM) framework developed by scientists at the University of Utah. Using epiworld (and the accompanying R package,) our team was implementing measles models for the Utah Department of Health and Human services. Using GitHub copilot's agent mode, we were able to combine two different models, extracting particular features of each, to create a more complex model. The AI was able to successfully add the feature with surprising accuracy.

## Context

The epiworld C++ library contains multiple canned models available for the users. The project also contains hundreds of unit tests and dozens of examples illustrating how the library works. Generally, the library is well documented. In addition, the repository contains multiple workflows for testing and validation.

## The ask

We asked the AI to create a new model (via inheritance in C++) combining the features of the `ModelSEIRMixingQuarantine` and `ModelMeaslesQuarantine` classes. The task was rather complex because it involved combining particular bits from two very different models. Here is the verbatim request ([issue #80](https://github.com/UofUEpiBio/epiworld/issues/80)):

> Using the `ModelSEIRMixingQuarantine` class, I need to create a new model that incorporates the rash state. The new model would be named `ModelMeaslesMixing`. The main differences would be:
> 
> - The `Infected` state would be replaced by `Prodromal` state, during which agents are infectious.
> - Agents on the `Prodromal` state would now transition to the `Rash` state. During this state, they are no longer infecting others (because of self-isolation).
> - The detection of infected individuals would now take place during the `Rash` state. Right now, in the `ModelSEIRMixingQuarantine` detection and quarantine are triggered while in the `Infected` state.
> - Detected individuals would transition to the `Isolated` period. They can recover and transition to the `Isolated recovered` state. You can learn more from the `ModelMeaslesQuarantine` which also describes the transitions to hospitalization and quarantine process.
>
> This new class also needs documentation and a test.

## The final result

Surprisingly, the AI was able to complete it with almost no assistance. It took me a few iterations to fix some minor issues. The biggest human intervention was the need to improve the tests; nonetheless, the initial tests (which you can see [here](https://github.com/UofUEpiBio/epiworld/blob/4404fb9ff0e845e189c38598af910d5d8041c965/tests/19-measles-mixing.cpp)) were accurate.

## What was learned

**What worked well**: Having lots of examples and unit tests, including mathematical ones, helped guide the AI in creating the new model. This was one of the most surprising parts of the process.

**What did not work well**: The AI tried modifying a single header file that is generated automatically (and should not be edited directly). The issue here was that I was not explicit about it. We should have added instructions in the `.github/copilot-instructions.md` file to prevent this (it works). In addition, the AI added a binary file that should not have been included.

## References

- GitHub issue assigned to the AI: <https://github.com/UofUEpiBio/epiworld/issues/80>
- PR created by the AI: <https://github.com/UofUEpiBio/epiworld/pull/81>
- AI session: <https://github.com/UofUEpiBio/epiworld/pull/81/agent-sessions/42aa49ae-d85f-4e65-93a0-916a0cbaf012>
