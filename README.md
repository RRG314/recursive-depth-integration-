
# Recursive-Depth Integration 

A Depth-Weighted Measure and Integration Theory Based on the Recursive Division Tree (RDT)

**Author:** Steven Reid
**ORCID:** [https://orcid.org/0009-0003-9132-3410](https://orcid.org/0009-0003-9132-3410)

---

## Overview

This repository contains reference implementations and numerical experiments for Recursive Depth Integration (RDI). The theory defines a new measure on the integers using weights derived from the Recursive Division Tree (RDT) depth function.

For a decay parameter ( 0 < \rho < 1 ), the recursive-depth measure is

[
\mu_R(A) = \sum_{n \in A} \rho^{R(|n|)}.
]

The associated integral is

[
\int_{\mathbb{Z}} f(n), d\mu_R(n)
= \sum_{n\in\mathbb{Z}} f(n), \rho^{R(|n|)}.
]

The depth function ( R(n) ) comes from the RDT recurrence and measures how integers compress under recursive splitting. When combined with the weight ( \rho^{R(|n|)} ), this produces a well-defined integration theory on the integers that reflects recursive structure.

This repository reproduces the experiments and plots associated with the paper "Recursive-Depth Integration: A Depth-Weighted Measure on the Integers."

---

## Key Features

1. Exact implementation of the RDT depth recurrence:
   [
   R(1)=0, \quad
   R(n) = 1 + \min_{1 \le k < n} \frac{R(k)+R(n-k)}{\alpha}.
   ]

2. Construction of the recursive-depth measure ( \mu_R ).

3. General-purpose integrator for depth-weighted sums.

4. Numerical experiments validating theoretical results.

5. Visualization tools for depth functions, weighted kernels, and convergence behavior.

---

## Installation

Clone the repository:

```
git clone https://github.com/RRG314/recursive-depth-integration.git
cd recursive-depth-integration
```

Open `rdi_notebook.ipynb` in Jupyter or Colab to reproduce experiments.

---

## Quick Start

### Compute a depth table

```python
from rdi_core import compute_R_table

R = compute_R_table(500, alpha=1.5)
print(R[23])     # approximately 3.0 for alpha = 1.5
```

### Compute a recursive-depth integral

```python
from rdi_core import recursive_depth_integral

f = lambda n: 1 / (1 + n*n)
I = recursive_depth_integral(f, N=1000, R=R, rho=0.5)
print(I)
```

### Generate a convergence plot

```python
from rdi_plots import plot_integral_convergence
plot_integral_convergence()
```

---

## Mathematical Summary

### Depth Function

For ( \alpha > 1 ), the RDT depth satisfies

[
R(n) \to R^{*} = \frac{\alpha}{\alpha - 1}.
]

For ( \alpha = 1.5 ),

[
R(n) = 3 \text{ for all } n \ge 23.
]

This saturation arises directly from the recurrence and is verified computationally.

### Integrability Criterion

Since ( \rho^{R(n)} \to \rho^{R^{*}} > 0 ), a function is integrable if and only if

[
f \in \ell^{1}(\mathbb{Z}).
]

### Examples

* ( f(n)=1/(1+n^{2}) ) is integrable.
* ( f(n)=e^{-|n|} ) is integrable.
* ( f(n)=1/(1+|n|) ) is not integrable.

---

## Included Plots

The notebook generates the following figures:

1. RDT depth ( R(n) ) for a range of integers.
2. The decay kernel ( \rho^{R(n)} ).
3. Convergence of truncated integrals.
4. Comparison between weighted and unweighted sums.
5. Tail behavior and convergence rates.

All figures are fully reproducible from the code in this repository.

---

## Reproducibility

All numerical results in the associated paper come directly from the algorithms contained in this repository. The depth values, integrals, and convergence tables are produced deterministically by the RDT recurrence and weighted summation formulas.

Dependencies required:

* Python 3
* NumPy
* Matplotlib

---

## Citation

If this repository is used in research or academic work, please cite the following:

Reid, S. (2025). Recursive Division Tree: A Log-Log Algorithm for Integer Depth. Zenodo.

Reid, S. (2025). The Recursive-Adic Number Field: Construction, Analysis, and Recursive Depth Transforms. Zenodo.

Reid, S. (2025). Recursive-Depth Integration: A Depth-Weighted Measure on the Integers. Zenodo.

---

## Contact

Steven Reid
Independent Researcher
Email: [sreid1118@gmail.com](mailto:sreid1118@gmail.com)
ORCID: [https://orcid.org/0009-0003-9132-3410](https://orcid.org/0009-0003-9132-3410)

-
