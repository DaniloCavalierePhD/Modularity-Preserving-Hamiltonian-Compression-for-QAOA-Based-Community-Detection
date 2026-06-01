# Modularity-Preserving Hamiltonian Compression for QAOA-Based Community Detection

This repository contains the implementation and experimental material accompanying the paper:

> **Modularity-Preserving Hamiltonian Compression for QAOA-Based Community Detection**  
> Danilo Cavaliere, Giuseppe Fenza, Vincenzo Loia

## Overview

Community detection can be formulated as a modularity maximization problem and solved using the Quantum Approximate Optimization Algorithm (QAOA). However, directly encoding the modularity matrix produces dense Hamiltonians containing O(n²) two-qubit interactions, resulting in circuits that are difficult to execute on simulators and near-term quantum hardware.

This work investigates a family of Hamiltonian compression approaches designed to reduce circuit complexity while preserving the structural information required for community detection. The general idea is to start from the full modularity Hamiltonian and apply a compression step that removes, approximates, or reweights less informative interactions while preserving the most relevant structural information of the graph. The resulting compressed Hamiltonian contains fewer effective terms, leading to shallower QAOA circuits and lower computational cost while maintaining competitive community detection performance.

<p align="center">
  <img src="figures/compression_workflow.png" width="700">
</p>

The proposed approaches include:

- **Magnitude-based sparsification**: removes weak modularity couplings whose magnitude falls below a predefined threshold, reducing the number of ZZ interactions while preserving the strongest structural relationships.

- **Top-K filtering**: retains only the K most significant modularity couplings, providing direct control over the Hamiltonian size and circuit complexity.

- **Energy-based sparsification**: preserves only the interactions that contribute most to the overall energy of the modularity matrix, aiming to maximize information retention under a reduced interaction budget.

- **Low-rank spectral projection**: approximates the modularity matrix using a small number of dominant eigencomponents, yielding a compressed Hamiltonian that captures the main spectral structure of the graph.

- **Penalty-augmented modularity formulations**: incorporate additional penalty terms to encourage balanced community assignments and improve optimization behaviour without modifying the original graph structure.

The methods are evaluated against:

- Classical Louvain community detection
- Full modularity Hamiltonian encoding (QAOA baseline)

The evalaution is carried out by using multiple graph quality metrics, runtime measurements, scalability experiments, and noisy simulations.

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

