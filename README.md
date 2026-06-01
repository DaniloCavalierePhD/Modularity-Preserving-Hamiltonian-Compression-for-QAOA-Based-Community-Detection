# Modularity-Preserving Hamiltonian Compression for QAOA-Based Community Detection

This repository contains the implementation and experimental material accompanying the paper:

> **Modularity-Preserving Hamiltonian Compression for QAOA-Based Community Detection**  
> Danilo Cavaliere, Giuseppe Fenza, Vincenzo Loia

## Overview

Community detection can be formulated as a modularity maximization problem and solved using the Quantum Approximate Optimization Algorithm (QAOA). However, directly encoding the modularity matrix produces dense Hamiltonians containing O(n²) two-qubit interactions, resulting in circuits that are difficult to execute on simulators and near-term quantum hardware.

This work investigates a family of Hamiltonian compression techniques designed to reduce circuit complexity while preserving the structural information required for community detection.

The proposed approaches include:

- Magnitude-based sparsification
- Top-K filtering
- Energy-based sparsification
- Low-rank spectral projection
- Penalty-augmented modularity formulations

The methods are evaluated against:

- Classical Louvain community detection
- Full modularity Hamiltonian encoding (QAOA baseline)

using multiple graph quality metrics, runtime measurements, scalability experiments, and noisy simulations.

---

## Main Findings

The experimental results show that:

- **Energy-based sparsification** and **Top-K filtering** achieve the best accuracy-runtime trade-off.
- **Low-rank projection** and **magnitude-based sparsification** preserve higher partition quality but are more sensitive to noise.
- **Penalty-based formulations** exhibit higher variability and lower reliability.
- Scalability experiments on **16-, 20-, and 24-qubit encodings** confirm these trends.
- Simulations with depolarizing noise indicate that energy-based and Top-K methods are among the most robust approaches.

---

## Repository Contents

### `notebooks/`

Contains the Jupyter notebook implementing:

- Hamiltonian construction
- QAOA optimization
- Community detection experiments
- Scalability analysis
- Noise robustness evaluation
- Plot generation

### `paper/`

Contains the manuscript associated with the project.

### `figures/`

Contains the figures generated during the experimental evaluation.

### `data/`

The experiments use graphs from the **SPINOS** dataset.

The dataset is available from:

https://github.com/SophiaVei/Community-Detection-in-Social-Networks

Please download the dataset from the original source and place it in the appropriate directory before running the experiments.

---

## Requirements

Main dependencies include:

- Python 3.10+
- PennyLane
- NetworkX
- NumPy
- SciPy
- Matplotlib
- Pandas
- Scikit-learn

