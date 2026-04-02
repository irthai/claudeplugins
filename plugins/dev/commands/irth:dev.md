---
name: irth:dev
description: Full development pipeline for a work item — build, review, PR. Pauses at each gate for human approval. Captures decisions and updates project knowledge automatically.
argument-hint: "<story-id>"
---

Before starting, check for plugin updates:

1. Run `/plugin update irth-dev` to check for and apply any updates from the marketplace.
2. If an update was applied, reload the skill before continuing.

You are orchestrating the full `irth:dev` pipeline for story **$ARGUMENTS**.

This pipeline has 4 gates. You will invoke two specialized agents in sequence, pausing for human approval at each gate.

## Pipeline Flow

### Gates 1–2 + Build: Dev Agent

Invoke the **dev-agent** to handle the first part of the pipeline:

1. **Gate 1 — Clarifying Questions**: The dev agent reads the story, maps the codebase, and asks clarifying questions with default assumptions. Wait for human confirmation before proceeding.
2. **Gate 2 — Implementation Plan**: The dev agent presents the implementation plan. Wait for human approval before any code is written.
3. **Build & Test**: After Gate 2 approval, the dev agent builds the feature with atomic commits, writes unit tests, runs the test suite, and produces `.planning/$ARGUMENTS-SUMMARY.md`.

The dev agent signals handoff when the summary is written. **Do not proceed to Gate 3 until the dev agent completes.**

### Gate 3: Code Review Agent

Invoke the **code-review-agent** to review the work:

1. The review agent loads the story, reads the branch diff, and reviews across correctness, tests, security, code quality, and scope.
2. It presents all findings grouped by severity (BLOCKING, IMPORTANT, SUGGESTION, NOTE).
3. Wait for the human to accept or reject findings.
4. Hand accepted comments back to the **dev-agent** for implementation.
5. After fixes, the review agent re-checks BLOCKING items only.

### Gate 4: PR Creation

Once all blocking review items are resolved:

1. Create the pull request using the branch and summary from the dev agent.
2. Include the story ID, summary of changes, and test results in the PR description.
