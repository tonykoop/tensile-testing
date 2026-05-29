# Design Brief

## Design Intent

Build toward a repeatable tensile-test fixture packet that lets a maintained universal testing machine pull metallic specimens while:

- keeping the specimen axis concentric with the load frame,
- preventing grip slip before specimen fracture,
- avoiding load-cell saturation,
- containing or distancing the operator from stored-energy release, and
- preserving ASTM E8/E8M context without claiming a released test method.

## Starting Geometry

Use the existing repo skill as the concept source:

- Default metallic coupon family: ASTM E8/E8M proportional round specimen.
- Typical small-size reference geometry: 0.250 in reduced-section diameter and 1.000 in gage length.
- Smaller fallback geometry: 0.125 in reduced-section diameter when predicted peak load would exceed the frame/load-cell/grip range.
- Actual shoulder, fillet, thread, or button-end geometry: TBD per specimen source and grip selection.

These values are concept anchors from the repo narrative, not a fabrication drawing.

## Target Fixture Architecture

Primary load path:

1. Test-frame crosshead.
2. Load cell or upper adapter.
3. Rated upper grip or custom adapter into a rated grip.
4. Tensile specimen.
5. Rated lower grip or custom adapter into a rated grip.
6. Lower adapter/base fixture.
7. Test-frame base.

The preferred architecture uses purchased rated grips for specimen contact and limits custom fabrication to adapters, alignment aids, shield mounts, and non-load-bearing setup tools.

## Materials and Components

Concept candidates:

- Purchased wedge, collet, threaded, or button-head grips rated above the calculated peak load.
- Custom adapters from 4140 prehard steel, 17-4PH stainless, or another engineer-approved material with traceable stock and heat-treatment state.
- Rated alloy-steel fasteners matched to adapter design and proof load.
- Guarding from clear polycarbonate or machine-vendor shield components, with thickness and fastening method TBD after energy review.
- Alignment aids such as spherical seats, clevis joints, or self-aligning grips when bending strain is a risk.

Do not substitute printed plastic, mild unknown scrap, or unverified hardware in the primary load path.

## Load and Safety Assumptions

- Peak load must be estimated before machining or pulling any specimen.
- The limiting rating is the lowest rated item in the load chain: frame, load cell, grip, adapter, pin, fastener, shield, or specimen.
- Load-cell saturation is a failed test design, not an acceptable endpoint.
- Fracture is expected; uncontrolled release of fragments, grip jaws, pins, adapters, or specimen halves is not acceptable.

## Open Questions

- Which exact machine, load cell, and grip models will this packet target?
- What coupon end geometry is preferred for the next physical test: threaded, button-head, wedge-grip, or shoulder-grip?
- What peak load range should the first fixture cover?
- Will the first build be a demonstration fixture, a shop training fixture, or a real lab-use accessory?
- What local shop safety authority signs off before the first pull?

## L1 Exit Criteria

- Actual machine and load-cell rating recorded.
- Grip approach selected and rated documentation captured.
- Peak-load estimate completed for the first material and coupon diameter.
- Shielding and operator-distance plan reviewed by the machine owner.
- P1 drawing brief opened for only the adapters that still need custom fabrication.
