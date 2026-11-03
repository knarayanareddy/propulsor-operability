# Installed-propulsor operability framework

**Status:** draft; 2026-11-03. Research software proposal, not flight or certification software. No tests run.

## Purpose and scope

Hypothesis: a traceable, reduced-order bridge from an installed inlet field to a matched compression system can support early studies more conveniently than disconnected tools. It must not imply novelty or experimental accuracy. Start with one fan or compressor on a fixed-speed shaft and a downstream load under demonstrably stable operating conditions. Establish a uniform-inlet solution before adding one pressure-distortion approximation. A dynamic shaft extension and external model adapters are later, conditional work. See [architecture](ARCHITECTURE.md), [tasks](IMPLEMENTATION_PLAN.md), [verification](VERIFICATION_PLAN.md), and [evidence](EVIDENCE.md).

## Requirements

Each requirement is a proposed gate, mapped in the verification plan.

- **PROP-R01:** Before preregistered acceptance runs, P0 freezes the question, envelope, model, provenance, rights, benchmarks and thresholds; labelled exploratory runs may precede that freeze. Missing prerequisites block the affected claim.
- **PROP-R02:** Versioned inlet contracts retain spatial fields, physical units, frames, averaging, fluid and measurement provenance; reject ambiguous data.
- **PROP-R03:** Versioned map contracts identify corrected variables, reference states, efficiency definition, valid domain and fluid compatibility; reject extrapolation by default.
- **PROP-R04:** The uniform baseline closes component matching with reported scaled residuals and mass, energy and shaft-power balances; study initialization sensitivity.
- **PROP-R05:** One declared sector-based approximation consumes the spatial pressure pattern; area-weighted flow, power and torque must be invariant to splitting an identical sector, including the uniform limit. Do not scale pressure ratio or efficiency by area.
- **PROP-R06:** Show distortion sensitivity and spatial-resolution convergence on frozen cases; preserve fields and weights. Reject unsupported swirl and radial redistribution. Before predictive claims, obtain a domain-reviewed comparison with an alternate closure or a documented physical basis for the surrogate closure.
- **PROP-R07:** Distinguish invalid input, out-of-domain, numerical failure and accepted solution. No solver failure, map endpoint or data boundary may be called surge, stall, stability margin, or evidence of physical instability.
- **PROP-R08:** A future dynamic extension defines states, equilibrium and conservation, demonstrates time convergence, rolls back rejected steps, and stops at the declared envelope; it is not v1 capability.
- **PROP-R09:** An optional second adapter passes identical interface and consistency tests; never assume model equivalence or validity from code agreement.
- **PROP-R10:** Record numerical verification, calibration, independent code comparison, and experimental validation separately, with uncertainty and claim-specific limits.
- **PROP-R11:** Each acceptance artifact preserves configuration, provenance, thresholds, outcomes, diagnostics and reproducibility; unsupported outcomes are explicit.
- **PROP-R12:** Public release requires license review for code and data separately, independent reproduction, governance, and disclosure of missing experimental partnership and evidence.

## Exclusions and decisions pending

No surge/stall prediction, instability boundary, transient rotating-stall physics, blade-resolved aerodynamics, certification, control deployment or full-engine predictive claim. No claim of experimental validation without independent measurements and uncertainties. A synthetic fixture is a software test, not experimental evidence. Map rights, consistent boundary conditions, measurements and partner access are unresolved. The P0 owner and reviewer must be named before approval; absent owners or frozen criteria, acceptance and affected claims are blocked, not exploratory development.
