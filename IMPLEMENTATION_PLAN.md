# Implementation plan

**Status:** draft; all work future. No software, tests, installation or publishing performed. T-numbers are tasks; V-numbers are tests in [verification](VERIFICATION_PLAN.md). Each task's unchecked item is its definition of done (DoD). Dependencies govern acceptance of tasks, not labelled exploratory work, which must preserve untouched holdouts.

## P0 — question, data, license and thresholds

- [ ] **T01:** Inputs: stakeholder question, candidate machines and sources; dependencies: none. Output: signed feasibility record specifying conditions, candidate load closure, stable-use envelope, first adapter choice and rights inventory. Verify: V01 and conditional V12 review; DoD: ownership, provenance and every blocker explicit.
  1. Define the intended question, envelope and alternative-closure review route; identify domain reviewer.
  2. Inventory datasets, rights and missing inputs; record whether predictive and validation claims are blocked.
- [ ] **T02:** Inputs: T01, independent references and labelled exploration logs; dependency: T01. Output: immutable benchmark protocol with case IDs, calibration/holdout split, uncertainty and frozen numeric tolerances. Verify: V01 audit; DoD: reviewer signs before acceptance results; no usable benchmark means BLOCKED, not a guessed pass.
  1. Reserve untouched acceptance and experimental validation holdouts; log exploration separately.
  2. Select models, scales and limits; preregister case/data hashes and reviewer approval before acceptance runs.
  3. Preserve prior failures and require new untouched cases for any revised protocol.

**Phase DoD:** [ ] T01–T02 approved and relevant data rights available; [ ] no experiment-dependent claim without partnership. Synthetic-only engineering tests may proceed if explicitly signed off.

## P1 — interfaces

- [ ] **T03:** Inputs: T02 contracts and synthetic fixtures; dependency: T02. Output: versioned inlet/map/flow/shaft schemas and validation examples. Verify: V02; DoD: units, frames, averaging, fluid and rejection cases executable and documented.
  1. Specify required fields, area fractions, units, frames, property and map reference conventions.
  2. Build round-trip and malformed fixtures, including unsupported swirl and radial redistribution.
- [ ] **T04:** Inputs: T03; dependency: T03. Output: result/acceptance schema and status taxonomy. Verify: V03; DoD: every run is attributable, failures remain visible, unsupported results are unambiguous.
  1. Define exploratory versus acceptance records, provenance fields and status vocabulary.
  2. Exercise missing fields, failure, blocked and unsupported examples without physical-instability labels.

**Phase DoD:** [ ] T03–T04 pass; [ ] field preservation and reference-state checks reviewed.

## P2 — uniform baseline

- [ ] **T05:** Inputs: T02–T04, rights-cleared or synthetic map; dependencies: T02–T04. Output: single-component map response and matching closure. Verify: V04; DoD: residual and mass/energy/torque balances meet frozen bounds, invalid domain rejected.
  1. Implement map interpolation, corrections and explicit no-extrapolation handling.
  2. Connect the declared load and recompute mass, energy and torque balances independently.
- [ ] **T06:** Inputs: T05 case suite and frozen guesses; dependency: T05. Output: residual histories and initialization sensitivity report. Verify: V05; DoD: report every start, distinct roots and failure without treating failure as physical instability.
  1. Run the preregistered initial guesses and retain all residual histories.
  2. Compare root clusters and failures against frozen limits; report ambiguity without stability claims.

**Phase DoD:** [ ] T05–T06 pass frozen numerical gates; [ ] benchmark scope and shortcomings disclosed.

## P3 — distorted response

- [ ] **T07:** Inputs: T03 inlet, T05 map and frozen sector model; dependencies: T05–T06. Output: sector reducer and response with retained source field. Verify: V06; DoD: uniform limit, proportional split invariance, sensitivity and invalid-physics rejection pass.
  1. Preserve input field, project to sectors and validate positive area fractions summing to one.
  2. Scale whole-annulus-equivalent local flows by sector area once; integrate flow and power once, leaving pressure ratio and efficiency unscaled.
  3. Exercise one-versus-N sectors, proportional splits, distortion and unsupported input cases.
- [ ] **T08:** Inputs: T07 and frozen sector grids/cases; dependency: T07. Output: spatial-resolution, field-preservation and closure-review records. Verify: V07; V12 before predictive claims. DoD: refinement and conservation meet frozen gates, or result is failed/blocked; unresolved V12 blocks predictive claims.
  1. Compare three frozen grids and proportional splits; record weights, projection errors and output differences.
  2. Obtain domain review of closure basis or alternate-closure comparison; record conditions, uncertainty and decision without presenting it as validation.

**Phase DoD:** [ ] T07–T08 pass engineering gates; [ ] V12 passes before predictive claims; [ ] limitations and lack of validation are labelled.

## P4 — optional dynamic extension

- [ ] **T09:** Inputs: T08 and approved dynamics design; dependency: T08. Output: state/equilibrium/energy design and bounded dynamic driver. Verify: V08; DoD: equilibrium holds and shaft/storage balances close in declared domain.
  1. Define physical stored states, algebraic variables, bounds and equilibrium equations.
  2. Initialize from the verified steady solution and measure shaft/storage residuals.
- [ ] **T10:** Inputs: T09, frozen time grids and fault cases; dependency: T09. Output: convergence, rollback and envelope-stop report. Verify: V09; DoD: rejected steps restore state/history; event terminates without extrapolation.
  1. Compare the frozen time-step sequence at common sample times.
  2. Inject rejected steps and envelope crossings; verify restored state, time and history or stopped integration.

**Phase DoD:** [ ] T09–T10 pass and extension is clearly experimental; [ ] physical transient validation remains blocked without independent data. P4 is not a v1 prerequisite.

## P5 — second adapter

- [ ] **T11:** Inputs: T03–T08, candidate runtime/license assessment; dependencies: T08, not P4. Output: adapter and provenance/compatibility record. Verify: V10; DoD: contract suite passes and frozen comparison identifies differing assumptions; no equivalence claim.
  1. Review candidate API, version, runtime and rights; document incompatible assumptions.
  2. Implement the interface and run the shared cases with the comparison protocol.

**Phase DoD:** [ ] T11 passes or is explicitly deferred; [ ] rights and limitations reviewed.

## P6 — public release

- [ ] **T12:** Inputs: T01–T08, and T09–T11 only if included; dependencies: T08 plus all included optional tasks. Output: license/data ledger, governance policy, reproducibility bundle and external review record. Verify: V11 and V12 for predictive claims; DoD: independent user reproduces frozen cases, unresolved restrictions excluded, supported claims trace to results.
  1. Audit code and data rights, prepare pinned cases and governance/security policies.
  2. Have an external user reproduce results and review the evidence and closure-claim ledger.
  3. Remove or explicitly block claims without the required review, independent data or rights.

**Phase DoD:** [ ] T12 passes; [ ] maintainers accept security reporting, contributions, versioning and compatibility policy; [ ] release remains blocked if external reproduction or redistribution rights fail.
