# MaLoPhyLAND

## Graph-Based Spectral Clustering for PSInSAR Time Series

Framework for landslide detection and structural deformation analysis using graph-based spectral clustering via Symmetric Nonnegative Matrix Factorization (SymNMF).

---

## 🌍 Scientific Context

Persistent Scatterer Interferometric SAR (PSInSAR) provides displacement time series for stable radar targets (Pixel-PS).  
Identifying coherent deformation patterns (e.g., landslides) requires clustering of time series without imposing geometric assumptions on cluster shape.

Here we use:

- Time series similarity computation via Dynamic Time Warping (DTW)
- Graph construction from similarity matrices
- Spectral clustering through Symmetric Nonnegative Matrix Factorization (SymNMF)
- Comparative analysis across orbital configurations (Ascending vs Descending)

---

## 🎯 Objectives

- Detect landslide bodies from stable surrounding terrain
- Compare clustering behaviour under:
  - Multiple distance metrics
  - Different orbital geometries (ASC / DESC)
  - Varying number of clusters
- Provide confidence-level assessment via soft clustering interpretation

---

## 🧠 Method Overview

Pipeline:

1. Load PSInSAR time series
2. Compute pairwise similarity matrix
3. Build weighted graph
4. Apply Symmetric NMF
5. Extract cluster assignments
6. Analyze ASC vs DESC behaviour

Graph partitioning is formulated as an optimization problem:

Minimize:

    || A - H Hᵀ ||_F²

subject to:

    H ≥ 0

Where:
- A is the similarity / adjacency / Laplacian matrix
- H encodes cluster membership
- Near-orthogonality of H enforces separation


The algorithm used for Symmetric NMF is based on 
"Moutier, F., Vandaele, A., & Gillis, N. (2021). Off-diagonal symmetric nonnegative matrix factorization. Numerical Algorithms, 88(2), 939-963. doi:10.1007/s11075 020 01063 9."
