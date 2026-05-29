# Tensile-Testing Rig Fixture Packet

**Status:** L1 concept. This packet defines the first build-toward shape for tensile-test grips, adapters, load path, and operator safety. It is not a released drawing set, procedure, or permission to run a test.

## Purpose

Create a shop-ready starting point for a guarded tensile-test fixture system that can hold standard metallic tensile specimens while keeping the load path predictable and the operator separated from stored-energy release if a specimen, grip, adapter, or fastener fails.

## Scope

- Covers fixture concept, grip strategy, load path, workholding, and safety gates for monotonic tensile testing.
- Uses the repo-local ASTM E8 method note as context for metallic coupons.
- Assumes the universal testing machine, load cell, and controller already exist and are maintained under their own manufacturer procedures.
- Excludes proprietary employer data, test results, active medical-device methods, and any released manufacturing drawings.

## Packet Files

- [`design-brief.md`](design-brief.md) - concept dimensions, materials, load path, assumptions, and TBDs.
- [`fabrication-plan.md`](fabrication-plan.md) - maker route from concept to P1 fixture.
- [`jig-decision.md`](jig-decision.md) - grip and adapter strategy tradeoffs.
- [`workholding-checklist.md`](workholding-checklist.md) - alignment, retention, inspection, and test setup checks.
- [`safety-checklist.md`](safety-checklist.md) - stop-work safety gates for stored-energy failure.
- [`safety-reference.md`](safety-reference.md) - safety and welfare references to verify before build or test.
- [`make-order-buy-borrow.md`](make-order-buy-borrow.md) - sourcing decision for grips, guards, and adapters.

## L1 Readiness

This packet is ready for concept review only when the reviewer can answer:

- What specimen geometry is being gripped?
- What is the estimated peak tensile load, and what margin exists below load-cell and grip ratings?
- Which parts are purchased rated components and which parts are custom adapters?
- Where can stored energy release, fragments, or whipping occur on failure?
- What shield, interlock, distance, and PPE controls are required before anyone runs a pull?

## Current Limits

- Load ratings are TBD until the actual machine, load cell, grip model, fastener sizes, and coupon material are known.
- Shield material and thickness are concept placeholders until verified against the machine vendor and a failure-energy assessment.
- Custom grip inserts or adapters require engineering review before fabrication.
- No human-subject, animal, or product-use testing is in scope; "welfare" here means operator and bystander welfare in a mechanical-test environment.
