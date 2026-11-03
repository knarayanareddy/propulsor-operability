# Propulsor Operability

Design specifications for an installed-propulsor modeling framework connecting nonuniform inlet conditions, component response and propulsion-system operation.

**Status: reviewed design draft.** This repository contains specifications and implementation plans. No component solver, engine simulator or experimental validation has been delivered.

## Vision

Support reproducible research across inlet, fan/compressor and system-modeling workflows, with explicit reference frames, map conventions, conservation checks and model-applicability limits.

The proposed first version covers one fan or compressor under stable operating conditions. It starts with a uniform-inlet baseline and then a declared sector-based pressure-distortion approximation. Dynamic shaft modeling and additional adapters are separately gated extensions.

## Documentation

| Document | Contents |
| --- | --- |
| [Specification](SPEC.md) | Requirements, scope and unsupported claims |
| [Architecture](ARCHITECTURE.md) | Inlet fields, map conventions, sector weighting and coupling |
| [Implementation plan](IMPLEMENTATION_PLAN.md) | Phased tasks, dependencies and definitions of done |
| [Verification plan](VERIFICATION_PLAN.md) | Conservation, split invariance, reference comparisons and negative tests |
| [Evidence](EVIDENCE.md) | Primary sources, existing tools and data-access questions |

## Starting point

Begin with phase P0: define the research question, select a reference case and establish usable data and rights. The proposed discharge-pressure closure requires domain review. Map endpoints and solver failures must not be interpreted as surge or stall boundaries.

## Contributing

Contributions are welcome on inlet representations, model adapters, reference datasets and verification design. Identify relevant requirement/task IDs and provide sources and applicability limits. Numerical agreement, calibration and independent experimental validation must remain distinct.

## Licensing

An open-source release is intended; a license has not yet been selected. Public visibility alone does not grant an open-source license. Component maps, geometry, code and measurements require separate rights review before reuse or redistribution.
