# Release Notes

## v1.0.4
GH#1100 migration wave (batch 4) — stop naming a step that belongs to the consumer.

The body read `{{steps.Research Gap Identification.output}}` **twice**, under two different labels — *Research question* and *Proposed methodology*. Both resolved to the same step, so the prompt has always received ONE value for two declared purposes.

Both reads now come from `{{step.context.source}}`, declared **required**. That preserves the behaviour exactly: one value, both labels, nothing silently changed.

**The conflation is pre-existing and is NOT fixed here.** Whether this prompt should receive two distinct upstream values is a content question about what it is for, not a migration step, and inventing a second slot would assert a distinction the author may not have intended. Flagged on GH#1100.

Reach verified before migrating: the named step exists and runs EARLIER than this prompt's step in all four consumers, so each receives what it received before.

## v1.0.3
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.0.2
GH#657 Framing B — republish wave. Bundle now ships `dependencies: []` in its signed manifest (injected by `publish-skrpt.mjs` for `--shared` publishes), so the App's dep-referenced install pipeline (post-PR #47) accepts it on standalone update via Hub Update-all. No content changes.

## v1.0.1
GH#645 Row 3a — republish with `manifest.id` aligned to Hub catalog UUID. Pre-K-037 v1.0.0 bundle carried a local `manifest.id` that drifted from the catalog UUID. Row 5 (`0d9c9dbe`) reconciled the source file but not the signed bundle; v1.0.1 ships the corrected `manifest.id` so the batch-of-81 consumer migrations (GH#645 Row 3b) can pin this version and pass engine STEP 4d. No content changes.

## v1.0.0
Initial catalog release as independent shared object (GH#625 Step 2; canonical pick + rename surface per audit).
