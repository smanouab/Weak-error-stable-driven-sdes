# Weak Convergence of Euler Schemes for Stable-Driven SDEs

### A Kolmogorov Equation Approach with Lévy–Itô Truncation

<p align="center">
  <img src="https://img.shields.io/badge/Mathematical%20Analysis-Stochastic%20Numerics-blue" alt="Mathematical Analysis">
  <img src="https://img.shields.io/badge/Stable%20Processes-%CE%B1%20%3C%202-purple" alt="Stable Processes">
  <img src="https://img.shields.io/badge/Method-Euler--Maruyama-green" alt="Euler Maruyama">
</p>

<p align="center">
  <strong>Solym M. Manou-Abi</strong><sup>1,2,*</sup> ·
  <strong>Ronald R. Moussitou</strong><sup>3</sup>
</p>

---

## Overview

This repository contains the theoretical and numerical developments associated with the study of the **weak convergence of Euler–Maruyama schemes** for one-dimensional stochastic differential equations driven by strictly α-stable Lévy processes.

We consider stochastic differential equations of the form

$$
dX_t=f(X_t)\,dt+\phi(X_{t-})\,dZ_t,
\qquad X_0=x,
$$

where $Z=(Z_t)_{t\geq 0}$ is a strictly α-stable Lévy process, with stability index $\alpha\in(0,2)$, possibly asymmetric.

The main objective is to establish weak error estimates for the Euler–Maruyama approximation when the increments of the driving stable process are **exactly simulated**.

Our approach relies on three main ingredients:

- The backward Kolmogorov equation.
- A scaling identity for the generators.
- A Lévy–Itô decomposition with a suitable truncation level.

The analysis provides two complementary approaches to weak error estimation, leading to explicit convergence rates under appropriate regularity assumptions.

---

## Main Contributions

### 1. Weak error estimates with a fixed truncation level

For a fixed truncation level $R>0$, Dynkin's formula yields a first-order weak error estimate:

$$
\boxed{
\left|
\mathbb{E}[g(X_T)]-\mathbb{E}[g(X_T^h)]
\right|
\leq Ch.
}
$$

The estimate holds with an explicit constant for every $\alpha\in(0,2)$, provided that the solution of the backward Kolmogorov equation belongs to $C_b^{1,4}$.

This result applies to:

- **Additive noise:** for every $\alpha\in(0,2)$.
- **Non-degenerate multiplicative noise:** when $\alpha\in(1,2)$.

### 2. Weak error estimates with the natural truncation scale

A second approach consists in choosing the truncation level according to the natural scale of the stable increments:

$$
\boxed{R=h^{1/\alpha}.}
$$

This choice provides sharp estimates for the truncated moments of the increments.

For $\alpha\in(1,2)$, assuming that the Kolmogorov solution has Hölder regularity $\alpha+\beta$, we obtain the following weak convergence rates:

| Regularity regime | Weak error rate |
|:---:|:---:|
| $\beta<\alpha$ | $O(h^{\beta/\alpha})$ |
| $\beta=\alpha$ | $O(h(1+|\log h|))$ |
| $\beta>\alpha$ | $O(h)$ |

More precisely,

$$
\boxed{
\left|
\mathbb{E}[g(X_T)]-\mathbb{E}[g(X_T^h)]
\right|
\leq C
\begin{cases}
h^{\beta/\alpha}, & \beta<\alpha,\\[2mm]
h(1+|\log h|), & \beta=\alpha,\\[2mm]
h, & \beta>\alpha.
\end{cases}
}
$$

These estimates highlight the role of the regularity of the Kolmogorov equation in determining the weak convergence rate.

---

## Mathematical Framework

The theoretical analysis is built around the following components:

| Component | Description |
|:---|:---|
| **Stable-driven SDEs** | Existence, uniqueness and well-posedness under suitable assumptions on the drift coefficient $f$ and diffusion coefficient $\phi$. |
| **Backward Kolmogorov equation** | Regularity estimates for the associated integro-differential equation. |
| **Generator scaling identity** | Representation of the generators in terms of the generator of the driving stable process. |
| **Lévy–Itô truncation** | Decomposition of the stable process into compensated small jumps and large jumps. |
| **Euler–Maruyama approximation** | Exact representation of the weak error through the difference between the generator of the solution and the frozen generator of the scheme. |

### Weak error representation

The central idea is to express the weak error through the difference between the infinitesimal generator of the original stochastic dynamics and the frozen generator associated with the Euler scheme.

This representation allows us to combine the regularity properties of the backward Kolmogorov equation with suitable estimates for the truncated stable increments.

---

## Numerical Experiments

The numerical experiments illustrate the theoretical convergence results and include two exactly solvable benchmarks of Ornstein–Uhlenbeck type.

### 1. Stable Ornstein–Uhlenbeck model

An Ornstein–Uhlenbeck process driven by a strictly α-stable Lévy process is considered to investigate the weak error of the Euler approximation.

### 2. Cauchy-driven Ornstein–Uhlenbeck model

A Cauchy-driven Ornstein–Uhlenbeck process provides an additional benchmark corresponding to the stability index

$$
\alpha=1.
$$

### 3. Empirical weak convergence rates

The numerical experiments investigate the behavior of the weak error as the time discretization step decreases.

The results illustrate the first-order weak convergence behavior in the benchmark examples.

---

## Repository Structure

The repository is organized as follows:

```text
stable-sde-weak-convergence/
│
├── README.md
│
├── manuscript/
│   └── manuscript.pdf
│
├── src/
│   ├── stable_process/
│   ├── euler_scheme/
│   └── auxiliary_functions/
│
├── experiments/
│   ├── stable_ou/
│   ├── cauchy_ou/
│   └── convergence_rates/
│
├── figures/
│
├── results/
│
├── requirements.txt
│
├── LICENSE
│
└── CITATION.cff
```

The structure is indicative and can be adapted to the actual implementation.

---

## Reproducibility

The numerical experiments are designed to illustrate the theoretical results and can be reproduced using the scripts provided in this repository.

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/stable-sde-weak-convergence.git

cd stable-sde-weak-convergence
```

### 2. Install the dependencies

If the implementation uses Python:

```bash
pip install -r requirements.txt
```

### 3. Run the numerical experiments

```bash
python experiments/stable_ou/main.py

python experiments/cauchy_ou/main.py
```

The execution commands and dependencies will be updated to match the released implementation.

---

## Scientific Reference

If you use this repository in your research, please cite the associated work:

**Solym M. Manou-Abi and Ronald R. Moussitou.**

*Weak Convergence of Euler Schemes for Stable-Driven SDEs: A Kolmogorov Equation Approach with Lévy–Itô Truncation.*

Manuscript.

---

## Authors and Affiliations

**Solym M. Manou-Abi**<sup>1,2,*</sup>

- Laboratoire de Mathématiques et Applications, UMR CNRS 7348, Université de Poitiers, Poitiers, France.
- School of Engineering ENSAR, Université de Poitiers, Poitiers, France.
- Corresponding author: [solym.manou.abi@univ-poitiers.fr](mailto:solym.manou.abi@univ-poitiers.fr)

**Ronald R. Moussitou**<sup>3</sup>

- School of Engineering 3iL Ingénieurs, Campus de Rodez, Rodez, France.

---

## Keywords

`Euler–Maruyama scheme` · `Weak convergence` · `Stable-driven SDEs` · `Strictly α-stable Lévy processes` · `Backward Kolmogorov equation` · `Lévy–Itô decomposition` · `Weak error analysis`

---

## License

The licensing terms for the source code and associated materials will be specified in the repository.

---

## Acknowledgements

We acknowledge the contributions of the mathematical and scientific communities working on stochastic numerical methods, Lévy processes and the analysis of stochastic differential equations.
