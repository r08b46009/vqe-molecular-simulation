
# VQE Molecular Simulation

This project explores the use of the **Variational Quantum Eigensolver (VQE)** for simulating molecular ground-state energies and bond-dissociation behavior of small diatomic molecules.

The implementation uses **Qiskit** and **PySCF** to compare:

- **VQE energy**
- **Hartree–Fock energy**
- **Exact eigensolver energy**

The focus of the project is to study how VQE behaves across different **bond distances** and different **optimizer iteration limits**, and to visualize how closely the variational method follows classical baselines.

## Project Overview

This repository contains a cleaned version of a course-style quantum computing / quantum chemistry project. The original materials included multiple scripts, figures, a notebook, and presentation files. In this GitHub-oriented version, the main ideas from the presentation are summarized here directly, so the repository can be understood without opening the slides first.

The workflow is centered on small-molecule simulation:

1. Define a diatomic molecule and sweep across a range of bond distances.
2. Construct the molecular Hamiltonian with PySCF/Qiskit chemistry tools.
3. Estimate the ground-state energy using:
   - Hartree–Fock
   - exact eigensolver
   - VQE
4. Compare the resulting energy curves.
5. Visualize how optimizer settings affect VQE convergence and approximation quality.

## Molecules and Experiments

From the current files, the project appears to focus on small diatomic molecules such as:

- **HF**
- **HCl**

and also includes comparison figures for additional molecule labels such as:

- **HK**
- **HH**

The experiments are designed to evaluate how the predicted molecular energy changes as interatomic distance varies, which is a standard way to study **bond dissociation curves** in quantum chemistry.

## Methods

### Variational Quantum Eigensolver (VQE)
VQE is a hybrid quantum-classical algorithm that uses a parameterized quantum circuit to approximate the ground-state energy of a Hamiltonian. A classical optimizer updates the circuit parameters to minimize the expected energy.

### Hartree–Fock
Hartree–Fock provides a classical mean-field approximation and serves as a baseline.

### Exact Eigensolver
The exact eigensolver provides a reference solution for small enough systems, allowing the project to compare the approximation quality of VQE.

## What This Project Examines

This project mainly investigates three questions:

1. **Can VQE recover reasonable ground-state energy curves for small molecules?**
2. **How close is VQE to the exact eigensolver and Hartree–Fock baselines?**
3. **How does the optimizer iteration limit affect VQE performance?**

The plotting script and comparison figures suggest that the project studies VQE under multiple `maxiter` settings and compares the resulting energy curves.

## Main Takeaways

Among the tested molecules, the method performed most consistently on HK, where the VQE curve closely tracked the exact energy across the bond-distance range. It also performed well on H2, where even a low iteration setting produced a close approximation to the exact solution. However, the quality of the results still depends strongly on optimization behavior and parameter settings.

In particular:

- VQE is compared directly against exact and Hartree–Fock references
- bond-distance sweeps are used to evaluate physical trends
- convergence settings such as optimizer iteration count affect final performance
- plotted curves make it easier to inspect whether VQE tracks the expected dissociation behavior

## Repository Structure

```text
vqe-molecular-simulation/
├── README.md
├── run_vqe.py
├── plot_results.py
├── notebooks/
│   └── vqe_molecules.ipynb
└── figures/
    ├── HF_compare.svg
    ├── HF_compare.jpg
    ├── HCl_compare.jpg
    ├── HCl_refined.svg
    ├── HK_compare.jpg
    ├── HK_refined.svg
    └── HH_compare.jpg
```

Only two subfolders are kept here:

- `notebooks/` for exploratory or prototype notebook work
- `figures/` for final output plots and comparison images

The main scripts are left in the repository root for easier access.

## Files

- `run_vqe.py`  
  Main experiment script for sweeping molecular distances and computing energies with VQE and classical baselines.

- `plot_results.py`  
  Plotting utility for comparing energy curves under different settings.

- `notebooks/vqe_molecules.ipynb`  
  Notebook version of the molecular VQE workflow, useful for exploration and presentation.

- `figures/`  
  Output figures comparing molecular energy curves across different methods or settings.

## Notes on Cleanup

The original project files included some near-duplicate materials. In this cleaned version:

- only one main VQE script is kept
- figures are renamed into a more consistent format
- the notebook is separated into its own folder
- presentation content is summarized in this README rather than relying on slide viewing

## Possible Future Improvements

- Add convergence plots for optimizer behavior
- Document the quantum ansatz and optimizer configuration in more detail
- Modernize the code for newer Qiskit package versions

## Requirements

This project appears to rely on packages such as:

- `numpy`
- `matplotlib`
- `qiskit`
- `pyscf`

Depending on the original environment, additional Qiskit chemistry components may also be required.

## Disclaimer

This repository is intended for educational and project-archival purposes.
