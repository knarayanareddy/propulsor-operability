# Verification and acceptance plan

**Status:** draft; tests NOT RUN. Commands are planned, not executed. The future project chooses its test runner in P1; no command syntax is asserted here. Produce versioned test logs and the acceptance record below instead of relying on exit status.

## Freeze policy and evidence grades

Exploratory model-development runs may investigate candidate models, settings and thresholds before a protocol is frozen. Mark them `EXPLORATORY`, log inputs, changes and outputs, and never count them as acceptance or validation. Reserve independent held-out acceptance cases and experimental validation data before exploration; prevent their use for tuning. When suitable held-out cases cannot be reserved, the affected acceptance or validation claim is BLOCKED.

Before the first **preregistered acceptance** run, P0 freezes the model, case IDs and data hashes, quantities, normalization scales, exact bounds, map domain, initial guesses, uncertainty and acceptance thresholds, with an independent reviewer and dated protocol ID. Proposed starting engineering defaults, not validated accuracy targets: scaled matching residual infinity norm ≤ `1e-8`; relative mass and energy closure ≤ `1e-6`, each using a positive case-specific reference scale; uniform-limit and sector-split outputs agree within `1e-8` relative to frozen nonzero scales. P0 may adopt or justify different values before the relevant acceptance run. It must separately define absolute floors for near-zero values, torque tolerance, sector/time refinement, initial-guess spread, code comparison and experiment error/uncertainty limits. Missing threshold or suitable data means BLOCKED.

Never change thresholds after acceptance results and rebrand a failure as a pass. Retain the failed result and original protocol. Changes require a separately reviewed, versioned protocol and newly reserved untouched acceptance cases; data used to select the revision are no longer held out. Report outcomes under both protocol versions and mark revised runs as new acceptance, not a retroactive pass. Experimental validation remains independently held out from both calibration and development.

Numerical convergence demonstrates equation solution; calibration fits selected data; independent code comparison checks agreement under aligned assumptions; experimental validation compares held-out measurements within specified uncertainties. None substitutes for another. Synthetic data verify mechanics only. CFD is code comparison, not experimental truth. Analytic fixed-map fixtures may establish verification, not predictive accuracy.

## Test catalogue and traceability

| Test | Method and acceptance | Tasks | Requirements |
|---|---|---|---|
| **V01** | Review exploration logs and held-out separation; before acceptance, verify feasibility, case/data hashes, rights and signed protocol. Demonstrate a failed acceptance remains failed after a revised protocol; otherwise BLOCKED. | T01,T02 | PROP-R01, PROP-R10, PROP-R12 |
| **V02** | Round-trip known fields and references; reject missing units, total/static confusion, bad frame, incompatible fluid, out-of-domain map and unsupported swirl; compare declared weighted averages. | T03 | PROP-R02, PROP-R03 |
| **V03** | Validate exploratory `NOT_EVALUATED` and accepted, failed, blocked and unsupported acceptance records; reject exploratory-to-acceptance reclassification, require diagnostics and prevent instability labels. | T04 | PROP-R07, PROP-R11 |
| **V04** | Uniform synthetic analytic fixture plus rights-cleared frozen baseline: independently recompute residuals, mass, energy, torque; reject map extrapolation. | T05 | PROP-R03, PROP-R04, PROP-R07 |
| **V05** | Run every frozen initial guess, report convergence histories and root clusters against predeclared spread; retain numerical failures. | T06 | PROP-R04, PROP-R07 |
| **V06** | Compare one sector with N uniform sectors: total flow, power, torque, pressure ratio and efficiency agree within frozen tolerances. Split/duplicate any sector into identical proportional-weight sectors and assert unchanged totals, with no multiplication of throughput; test nonuniform cases and reject unsupported swirl/radial redistribution. Preserve both fields. | T07 | PROP-R02, PROP-R05, PROP-R06, PROP-R07 |
| **V07** | At least three frozen sector resolutions, with normalized area weights, projection error and output differences measured against pre-run limits. Repeat proportional-weight duplication at each resolution. A converged coarse field alone is insufficient. | T08 | PROP-R05, PROP-R06 |
| **V08** | For enabled dynamics, initialize from steady equilibrium; check state derivatives, torque and storage conservation against frozen limits. | T09 | PROP-R08 |
| **V09** | Run three time steps, compare trajectories at common times; inject rejected trial and envelope crossing, verify complete rollback and stop. | T10 | PROP-R08, PROP-R07 |
| **V10** | Run same contract suite on second adapter; compare matched conditions and disclose fluid, solver, map and boundary differences. | T11 | PROP-R09, PROP-R10 |
| **V11** | Independent clean-environment reproduction and code/data rights review; check artifact hashes, governance and claim/evidence ledger. | T12 | PROP-R10, PROP-R11, PROP-R12 |
| **V12** | A qualified domain reviewer evaluates a documented physical basis for common discharge total pressure or comparison against an appropriate alternate closure, including conditions, uncertainty and limitations. Before any predictive claim, missing or inconclusive review is BLOCKED; review is not experimental validation. | T01,T08,T12 | PROP-R01, PROP-R06, PROP-R10, PROP-R12 |

Each row is planned, not passed. This table maps all PROP-R01–R12 to task and test IDs. Measurements, calibration and holdout experiments require separate case-level review and independent data; no Rotor 67 case is presumed complete or redistributable.

## Acceptance artifact schema

One immutable machine-readable record per run: `schema_version`, `run_id`, `timestamp`, `run_class` (`EXPLORATORY` or `PREREGISTERED_ACCEPTANCE`), `source_revision`, `environment`, `case_id`, `input_hashes`, `data_rights`, `model_and_adapter_versions`, `fluid_and_map_references`, `frames_units_averaging`, `operating_envelope`, `protocol_version`, `thresholds_and_scales`, `data_role` (development, calibration, acceptance holdout or validation holdout), `prior_protocol_and_results`, `initial_conditions`, `solver_settings`, `residual_history`, `conservation_errors`, `resolution_or_time_study`, `uncertainties`, `outputs_and_units`, `status`, `reason`, `evidence_grade`, `reviewer`, and `artifact_hashes`. Missing applicable evidence must be `null` with reason, never a fabricated pass. Acceptance status is `PASS`, `FAIL`, `BLOCKED`, or `UNSUPPORTED`; exploratory runs use `NOT_EVALUATED` and cannot be reclassified as acceptance. Describe numerical/domain cause separately. A `PASS` is scoped to the named test and case, not a safety or physical stability certificate.
