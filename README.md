# Tensile Testing — Mechanical Properties Characterization in R&D

> *A decade of tensile-testing work across three R&D contexts: metal additive manufacturing at Uniformity Labs (the deepest documented thread), drug-delivery device development at Johnson & Johnson, and minimally-invasive medical implant work at Teleflex on Instron load frames.*

![Hero photo — ASTM E8 sub-size tensile specimen mounted between extensometer arms in the TestResources frame](images/2023-04-11%2014.21.05.jpg)
*An ASTM E8/E8M sub-size proportional tensile specimen mounted between extensometer arms in a TestResources universal testing machine — the workhorse setup behind the additive-manufacturing process DoE work documented below.*

## What this is

A documentation repository for tensile-testing R&D work I've done across three roles. The deepest thread is the **metal additive-manufacturing DoE work at Uniformity Labs** — the section that follows. Two further chapters (Johnson & Johnson auto-injectors, Teleflex UroLift on Instron) are summarized after for context.

**No proprietary data, methods, formulations, or test results from any employer are included in this repository.** Photos are general-equipment and general-specimen views; written content is methodology and standards-application narrative.

## Test machines I've operated

Three different universal testing machines across three roles — the major players in mechanical-properties test:

| Machine | Where | What I did with it |
|---|---|---|
| **TestResources** universal testing machine | Uniformity Labs | AM-printed metal specimens, ASTM E8 sub-size and sub-sub-size pulls |
| **Zwick** universal testing machine | Johnson & Johnson | Auto-injector aging studies (force, displacement, viscosity-driven actuation) |
| **Instron** universal testing machine | Teleflex | UroLift 3 R&D — current role; friction reduction |

Test-frame fluency across vendors matters more than any single brand: the loading mechanics, control software, fixturing conventions, and load-cell selection logic transfer, but each vendor's interface and data-export quirks have to be re-learned per shop.

## Additive-manufacturing process DoE — Uniformity Labs

### The R&D goal

At **Uniformity Labs (Fremont, CA)** I ran the tensile-testing arm of metal additive-manufacturing process development. The objective was straightforward: produce SLM-printed metal parts whose tensile properties approached the **forged/wrought equivalent** of the same alloy, and identify the **powder-recipe** + **laser-parameter** combinations that got us closest. This is the R&D problem that has to be solved for metal AM to compete with traditional mill products on certified mechanical performance — the gating engineering question for serious end-use AM parts.

### Materials covered

| Alloy | Class | Why we tested it |
|---|---|---|
| **AlSi10(Mg)** | Aluminum-silicon-magnesium casting alloy | Workhorse aerospace AM material |
| **Ti-6Al-4V (Ti64)** | Alpha-beta titanium | Critical aerospace + medical-implant grade |
| **316 / 304 stainless steel** | Austenitic stainless | Corrosion-resistant, biocompatible |
| **Inconel 625** | Nickel-chromium superalloy | High-temperature corrosion + strength (aerospace, marine, chemical processing) |
| **Inconel 718** | Nickel-chromium-iron precipitation-hardening superalloy | High strength to ~700 °C — both 625 and 718 drove a specimen-size adaptation (below) |

### Equipment

Printing was done on **SLM Solutions SLM 125** and **SLM 280** machines. Tensile pulls were performed on a **TestResources** universal testing machine. The CNC specimen-prep work that turned printed cylindrical blanks into ASTM E8 sub-size geometry is documented separately in [`cnc`](https://github.com/tonykoop/cnc) (sister repo).

![Inside the lathe mid-cycle — partially-turned cylindrical tensile specimen blank between chuck and live center](images/2022-08-25%2010.31.42.jpg)
*Specimen prep mid-cycle: an AM-printed cylindrical blank held between three-jaw chuck (left) and live center (right) on the lathe, tool turret retracted between cuts. The moment between the rough-OD turning pass and the gage-section finish pass. Full lathe + mill operator narrative is in the [`cnc`](https://github.com/tonykoop/cnc) sister repo.*

![A batch of cylindrical AM tensile-specimen blanks on the SLM build plate](images/2023-02-14%2016.05.16.jpg)
*A batch of cylindrical AM-printed tensile-specimen blanks still attached to the SLM build plate, before separation and lathe finishing. Each blank becomes one E8 sub-size specimen. This study compared vertically printed vs. horizontally printed cylinder specimens.*

![TestResources universal testing machine in the lab](images/2022-11-15%2012.26.47.jpg)
*The TestResources load frame in its lab corner. Load-cell capacity here is what drove the Inconel specimen-size adaptation, next.*

### Specimen geometry — and why we sub-sub-sized for Inconel

All specimens followed **ASTM E8/E8M** ("Standard Test Methods for Tension Testing of Metallic Materials"). The default for this work was the **small-size proportional round specimen — 0.250" diameter, 1.000" gage length** (Table A1.1 in E8). It's the right size for AM coupon volumes: small enough to print efficiently, large enough that the gage section averages over multiple melt-pool widths for representative properties.

When we got to **Inconel 625** and **Inconel 718**, the math broke. At those alloys' UTS values (~120–200 ksi depending on heat treatment), a 0.250"-diameter specimen would have **exceeded the TestResources frame's load-cell capacity** — the test would have ended in load-cell saturation, not specimen failure. So we dropped to **0.125" diameter** sub-size geometry: still ASTM E8, still proportional, but small enough that the peak load fit the frame's range with margin.

This is the right way to apply a standard — not blindly pick "the standard size," but pick the size the standard accommodates *and* that fits the actual lab equipment and material under test.

### Methodology — DoE structure

The work was structured as **designs of experiments** spanning two orthogonal factor families:

- **Powder-recipe DoEs** — composition, particle-size distribution, flowability, recycle ratio
- **Laser-parameter DoEs** — power, scan speed, hatch spacing, layer thickness

Response variables included tensile properties (UTS, 0.2% yield, elongation at break), part density / porosity (cross-section measurement + Archimedes), and fracture-surface morphology. The objective every DoE iteration was the same: **maximum density, lowest porosity, properties as close to forged equivalents as possible.**

Specific DoE designs, factor levels, response data, and process parameters are proprietary to Uniformity Labs and are not in this repository.

### Sister project

The **[metal-powder-flow-device](https://github.com/tonykoop/metal-powder-flow-device)** repository documents another piece of my Uniformity Labs work — the scientific measurement instrument I designed and built for powder-flow characterization, whose data fed into the powder-recipe DoEs above.

## Prior tensile-testing experience

### Johnson & Johnson — auto-injector aging studies on Zwick

As Mechanical Lab Technician at **Johnson & Johnson (Milpitas, CA)**, I ran tensile and force-characterization testing on **Zwick** universal testing machines as part of **aging studies** on a variety of drug + auto-injector device combinations. Auto-injectors are tightly characterized devices: a single failed actuation in the field is a major safety event, and the mechanical behavior changes subtly over shelf life as elastomers relax, lubricants migrate, and stored fluids interact with materials. Aging studies are how the design organization bounds that drift.

The mechanical-test menu spanned the full lifecycle of a single actuation:

| Variable | What it bounds |
|---|---|
| **Fluid viscosity** | Injection time and back-pressure across the needle |
| **Fluid temperature** | Drug-handling tolerance + viscosity reference state |
| **Needle length / diameter** | Pressure drop across the needle (the dominant flow resistance) |
| **Spring force / plunger force** | The driving force pushing the drug out |
| **Syringe diameter** | The piston area converting plunger force into fluid pressure |
| **Fluid volume** | Total dose + duration of actuation |
| **Injection time** | The user-experience target the design has to hit |
| **Force to actuate** | What the user has to apply to fire the device |
| **Post-use safety-mechanism destruction force** | Validates the needle-shielding mechanism cannot be re-exposed after disposal |

#### Closing the loop with first-principles fluid mechanics

For predictive analysis I used the **Hagen-Poiseuille** equation for the needle (small diameter, viscous drug, low-Reynolds laminar flow) and the **Darcy-Weisbach** equation for the syringe-barrel section, to estimate injection time from device geometry, spring force, and fluid viscosity *before* test:

$$Q_{\text{needle}} = \frac{\pi r^4 \, \Delta P}{8 \mu L} \quad \text{(Hagen-Poiseuille, laminar flow through the needle)}$$

$$\Delta P = f \cdot \frac{L}{D} \cdot \frac{\rho v^2}{2} \quad \text{(Darcy-Weisbach, pressure loss in the syringe barrel section)}$$

Spring force gives ΔP across the plunger; Hagen-Poiseuille gives flow rate *Q* through the needle; Darcy-Weisbach accounts for losses in the larger-bore syringe barrel. Total injection time = fluid volume ÷ *Q*. Comparing the predicted injection time to the measured injection time on the Zwick is what told us when a design change had moved the needle (literally or figuratively) on the user-experience target — and which way to push the spring force, the needle gauge, or the formulation viscosity to get back to it.

*Specific drug formulations, devices, aging-study designs, and results are proprietary to Johnson & Johnson.*

### Teleflex — UroLift 3 R&D on Instron

Currently R&D Technician on the **Teleflex UroLift 3** program in Pleasanton, CA (via Oxford Corp), working with **Instron** universal testing machines as part of implant + delivery-device development. *Out of respect for active-employer confidentiality, the specifics of this work are not documented here; this section will be expanded after my Teleflex tenure concludes.*

## What this repository is for

- **Methodology + judgment demonstration.** Three different product domains (medical implants, drug-delivery devices, AM-printed metals), one through-line: tensile testing as a tool for engineering decision-making. Test-frame fluency across vendors, standards literacy (ASTM E8/E8M as a *toolkit* not a *recipe* — see the Inconel sub-sub-size story), and DoE-driven process development.
- **Portfolio frame.** This sits in a cluster of engineering-context repositories on my GitHub — alongside [`suction-cup-mount`](https://github.com/tonykoop/suction-cup-mount), [`metal-powder-flow-device`](https://github.com/tonykoop/metal-powder-flow-device), [`cnc`](https://github.com/tonykoop/cnc), and [`additive-manufacturing`](https://github.com/tonykoop/additive-manufacturing) — documenting my mechanical R&D practice across roles, with strict separation between portfolio narrative and proprietary employer IP.

## Repository structure

```
tensile-testing/
├── README.md                  ← you are here
├── LICENSE                    ← CC-BY 4.0 (scoped to original content only)
├── images/                    ← equipment and specimen photos
└── (future) reference/        ← public-domain methodology references (E8 figures, etc.)
```

## Status

| Section | Status |
|---|---|
| Repo description, license | ✓ done |
| Hero + equipment photos | ✓ done |
| AM DoE methodology narrative | ✓ done |
| Prior J&J + Teleflex experience summary | ✓ done |
| Public-domain methodology references (E8 figures, etc.) | forthcoming |

## License

Released under [CC-BY 4.0](LICENSE) — original written content and photographs in this repository are mine, free to reuse and adapt with credit. **The underlying medical-device, drug-delivery, and AM process IP belongs to the respective employers (Teleflex, Johnson & Johnson, Uniformity Labs).** This license does not apply to those proprietary methods, designs, formulations, or test results — none of which are included here.
