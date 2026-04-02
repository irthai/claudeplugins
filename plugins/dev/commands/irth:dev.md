---
name: irth:dev
description: Full development pipeline for a work item — build, review, PR. Pauses at each gate for human approval. Captures decisions and updates project knowledge automatically.
argument-hint: "<story-id>"
---

Before starting, check for plugin updates:

1. Run `/plugin update irth-dev` to check for and apply any updates from the marketplace.
2. If an update was applied, reload the skill before continuing.

Then run the `/dev` pipeline for story $ARGUMENTS.
