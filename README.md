# Physics-Informed Deep Learning for Turbulent Radiative Layer

This repository contains the code and experiments for a 3rd-year project at ESPCI Paris – PSL, developed as part of the course *Apprentissage profond avancé*. The project investigates the use of deep neural networks, including Physics-Informed Neural Networks (PINNs), for modeling the spatio-temporal evolution of turbulent astrophysical systems with radiative cooling.

## Project Overview

Standard numerical solvers for partial differential equations are accurate but computationally intensive. This work explores surrogate modeling with convolutional architectures and spectral operators to learn short-term physical dynamics from data, while integrating physical laws to improve generalization and consistency.

## Dataset

- **Name:** `turbulent_radiative_layer_2D`
- **Source:** [The Well Benchmark (Ohana et al., 2024)](https://arxiv.org/abs/2412.00568)
- **Size:** 90 spatio-temporal trajectories
- **Shape:** `(T=101, C=4, H=128, W=384)`
- **Fields:** Density, Pressure, Velocity_X, Velocity_Y
- **Format:** HDF5 (loaded via `WellDataset` PyTorch interface)

## Models Implemented

- `CNN`, `CNN2`, `CNN3`, `CNN4`: Progressive convolutional architectures with increasing depth and capacity
- `SkipCNN`: U-Net style with skip connections
- `FNO`: Fourier Neural Operator (spectral baseline)
- `CNN4 + PINN`: CNN4 with physical constraints:
  - Mass conservation
  - Energy conservation (with radiative loss term)
