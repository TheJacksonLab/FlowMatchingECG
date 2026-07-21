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
- `generate_CG_beads.py` – example script for constructing a CG bead mapping used for ST3M.

## Usage

Run either example script after specifying the paths to your dataset.

```bash
python fixed_temperature_example.py
```

or

```bash
python temperature_condition_example.py
```


## Data format 
homo.npy: (nsamples,) 
features_CG.npy: (nsamples, nfeatures) containing nbeads*(nbeads-1)//2 distance features.
coords_AA.npy: (nsamples, natoms, 3) containing Cartesian coordinates of AA structures for constructing different CG mappings.

See the comments in each script for the required input data format.
