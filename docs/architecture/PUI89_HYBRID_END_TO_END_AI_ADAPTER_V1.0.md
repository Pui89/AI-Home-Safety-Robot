# PUI89 Hybrid End-to-End AI Adapter — PUI89 AI HOME

**Status:** Product-specific architecture allocation. This document is not evidence of model deployment, physical integration, field performance or certification.

## Product mission
Indoor assistive robotics.

## Approved input boundary
Indoor RGB/depth/audio/other sensors only with documented availability, consent and privacy controls.

Every input must preserve source, timestamp, modality, coordinate frame/units where relevant, quality, calibration and provenance. Unsupported or unavailable sensors remain out of scope.

## E2E-capable intelligence tasks
Indoor scene/context, object/person-aware assistance and bounded task planning.

The product may use modular pipelines, shared representations or joint/E2E models. Selection requires comparative evidence; no monolithic model is mandated.

## Product-specific safety and action boundary
Privacy, consent, human override, collision-risk limits and safe hold; no unverified autonomous manipulation or care claim.

The shared model may produce an **ActionProposal** or advisory result only. The product adapter and independent safety/control system enforce permitted actions, preconditions, expiry, safe hold and human authority.

## First research/engineering slice
Begin with offline indoor scene/object context; test lighting, occlusion, unseen rooms, privacy exclusions and low-confidence abstention.

## Required evaluation
- Task-specific metrics and per-condition breakdowns.
- Confidence calibration, uncertainty and abstention quality.
- Missing, stale, conflicting and corrupted input behaviour.
- Out-of-distribution and domain-shift tests.
- CPU-first runtime, memory and reproducibility; target hardware profiling only when available.
- FailureReport and Evidence Passport for every test run.

## Shared contracts and architecture
Follow [PUI89 Hybrid End-to-End Multimodal AI Architecture v1.0](https://github.com/Pui89/PUI89-Shared-AI-Core/blob/main/docs/architecture/PUI89_HYBRID_END_TO_END_MULTIMODAL_AI_V1.0.md). The Shared AI Core owns common contracts; this repository owns product-specific requirements, data rights, operating limits and acceptance criteria.

## Evidence status
This is a proposed adapter and test plan. It does not claim datasets, models, sensors, prototypes, product integrations, benchmarks or field tests are complete.
