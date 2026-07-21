# CFM-ECG

Official implementation of

**Reconstructing Electronic Property Distributions from the Coarse-Grained Resolution with Conditional Flow Matching**

by Sijing Zhu and Nicholas E. Jackson

## Overview

CFM-ECG is a probabilistic electronic coarse-graining (ECG) framework that learns the conditional distribution of electronic observables from coarse-grained molecular configurations using Conditional Flow Matching (CFM).

This repository provides a minimal implementation of CFM-ECG together with data and example scripts demonstrating model training and inference.

## Repository contents

- `flow_matching.py` – implementation of the CFM model
- `fixed_temperature_example.py` – example workflow for training and inference at a fixed temperature
- `temperature_condition_example.py` – example workflow for temperature-conditioned training and inference
- `data/` – example datasets containing HOMO energies of sexi(3-methylthiophene) (ST3M) at multiple temperatures. See the paper for details of dataset generation.
- `generate_CG_beads.py` – a script for constructing physical CG bead mappings used for ST3M.
- `min.xyz` - an example energy minimum structure with the same connectivity and atomic indices used throughout this study.


## Usage

The example scripts are already configured to run with the provided datasets. The example runs are already configured with the parameters used by the paper.

To use a different temperature or CG resolution, modify the corresponding user parameters near the beginning of each script.

Only the 18-bead CG features are included in this repository. To generate CG coordinates and pairwise distance features for the other CG representations (6, 12, 24, 30, and 36 beads), run

```bash
python generate_CG_beads.py
```

Then run either example script:

```bash
python fixed_temperature_example.py
```

or

```bash
python temperature_condition_example.py
```


## Data format

- `homo.npy`: array of shape `(n_samples,)` containing the HOMO energy for each atomistic configuration.

- `features_CG_<n_beads>beads.npy`: array of shape `(n_samples, n_features)` containing all unique pairwise CG bead distances, where

  ```text
  n_features = n_beads * (n_beads - 1) // 2

See the comments in each script for the required input data format.
