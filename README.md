# GPS-denied path-memory reproducibility

Reproducibility package for **Model-Gated Reference-Information Propagation and
Admissible Preview in GPS-Denied Heterogeneous Vehicle Platoons**.

[Download the existing reproducibility package](reproducibility_package.zip).

The ZIP is the existing integrated-final package uploaded on 2026-09-29. It
contains Python estimator/transport code, MATLAB nonlinear platoon code,
stored numerical records, figure/table sources, LaTeX source, and reproduction
instructions. No experiments or additional audit were run for this upload.

## Run

Extract the ZIP and open `REPRODUCE.md` for the complete commands. Commands
are run from the extracted directory.

Dependencies: Python with NumPy, SciPy, pandas and Matplotlib. MATLAB R2022b
is used for the nonlinear multi-vehicle studies. TeX Live with IEEEtran and
latexmk is required only to compile the manuscript.

Check the stored numerical records:

```sh
python scripts/verify_v3.py
```

Optional regeneration of the principal Python records:

```sh
python scripts/cross_model_audit.py
python scripts/admissible_preview_experiment.py
```

Principal nonlinear multi-vehicle study:

```sh
matlab -batch "addpath('matlab'); run_integrated_dynamics"
```

Regeneration commands overwrite the corresponding extracted result files.
The full 30-seed preview and paired D3/D4 recipes are in `REPRODUCE.md`.

Compile the integrated manuscript using both included bibliography files:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

## Simulation platforms

Path-information experiments use Python/MATLAB. Multi-vehicle closed-loop
studies use MATLAB. CarSim is reserved for independent single-vehicle
cross-validation; no CarSim result is claimed in this package.

## Provenance

The reference revision is documented in `reference_recheck_20260929.md`.
Two historical verifiers (`verify_final_audit.py` and `verify_integrated.py`)
require an earlier external frozen directory which is currently absent.
They retain their original checks; use `REPRODUCE.md` for this limitation.

This repository is currently private.
