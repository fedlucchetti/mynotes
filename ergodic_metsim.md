# Ergodic hypothesis — theory and a careful cross-sectional MRSI analogue

This page uses **inline** math with `$...$` and **display** math with `$$...$$` so it should render well in most Markdown environments that support LaTeX.

---

## 1. The big idea (plain language)

The **ergodic hypothesis** says:

> If you track one system for long enough, the average of what it does over time matches the average you would get by looking at many identical copies of the system at a single time.

It’s a way to justify replacing hard-to-measure **time behavior** with easier-to-compute **population (ensemble) behavior**.

---

## 2. The classic physics formulation

Let $X(t)$ be some quantity describing the system’s state over time.

### Time average (one system over a long time)

$$
\overline{X}^{\text{time}}
==========================

\lim_{T \to \infty}
\frac{1}{T}
\int_{0}^{T} X(t), dt
$$

### Ensemble average (many identical systems at one time)

$$
\langle X \rangle^{\text{ens}}
==============================

\int X , d\mu(X)
$$

where $\mu$ is an invariant (equilibrium) distribution over states.

### Ergodic hypothesis (informal)

$$
\overline{X}^{\text{time}}
\approx
\langle X \rangle^{\text{ens}}
$$

---

## 3. Why this *does not strictly apply* to cross-sectional MRSI

In typical MRSI datasets you have:

* **one snapshot per subject**
* **no individual time trajectory** $X_s(t)$

So you **cannot claim or test** classical time ergodicity at the subject level.

There is no meaningful way to say that a single subject’s snapshot “explores all states over time” because time is not observed.

---

## 4. The correct cross-sectional analogue

What you *can* assume is a standard statistical model:

### Exchangeability / ensemble sampling

$$
X_s \sim P(X), \quad s = 1,\dots,N
$$

Interpretation:

* each subject is a realization drawn from a shared population distribution $P(X)$
* after controlling for covariates, subjects are treated as **exchangeable** (often approximated as i.i.d.)

### Group mean estimates the population expectation

$$
\widehat{\mathbb{E}}[X]
=======================

\frac{1}{N}
\sum_{s=1}^{N} X_s
;\approx;
\mathbb{E}[X]
$$

This is **ensemble logic**, not time ergodicity.

---

## 5. Applying this to MRSI metabolic similarity matrices (MSMs)

Assume each subject yields a subject-specific metabolic similarity matrix:

$$
\text{MSM}_s \in \mathbb{R}^{R \times R}
$$

where $R$ is the number of regions.

### Group-average MSM

$$
\text{MSM}_{\text{group}}
=========================

\frac{1}{N}
\sum_{s=1}^{N} \text{MSM}_s
$$

Under exchangeability,

$$
\text{MSM}_{\text{group}}
;\approx;
\mathbb{E}[\text{MSM}_s]
$$

This is the clean mathematical justification for building a group-level metabolic connectome from cross-sectional subjects.

---

## 6. Your original intuition — refined

You suggested:

> one subject’s MRSI would explore all possible states that the collection of other subjects explores

A safer cross-sectional version is:

> **In the absence of longitudinal sampling, inter-subject variability provides an ensemble of realizations of the underlying metabolic organization.**

This avoids implying time exploration.

---

## 7. When the ensemble assumption can fail

If your dataset is a mixture of distinct regimes (biological or technical), then:

$$
P(X)
====

\sum_{k=1}^{K}
\pi_k , P_k(X)
$$

Consequences:

* a single group-average may describe **no subgroup well**
* “one subject represents the ensemble” becomes a poor intuition
* gradients / principal curves may shift across subpopulations

---

## 8. Practical checks to support the assumption

### Subject bootstrap stability

Resample subjects with replacement and recompute:

$$
\text{MSM}_{\text{group}}^{(b)}
===============================

\frac{1}{N}
\sum_{s \in \mathcal{B}_b}
\text{MSM}_s
$$

Then verify stability of:

* edge weights
* gradient structure
* principal-curve / path metrics
* rich-club / modular architecture

### Stratified robustness

Repeat analyses across:

* age bins
* sex
* site/scanner
* clinical strata / medication status

Look for conserved topology and consistent path/gradient geometry.

---

## 9. Recommended wording for a paper

### Methods (short)

> Because our dataset is cross-sectional, we do not assess time ergodicity. Instead, we treat subjects as exchangeable realizations of an underlying metabolic architecture and estimate group-level features via ensemble averaging.

### Limitations (short)

> This approach assumes within-cohort exchangeability after controlling for key covariates; unmodeled subgroup structure could bias group-average topology and derived gradients.

---

## 10. The one-line takeaway

**You’re not using time ergodicity.**
You’re using a **cross-sectional ensemble approximation**:

$$
X_s \sim P(X)
\quad \Rightarrow \quad
\frac{1}{N}\sum_{s=1}^{N} X_s \approx \mathbb{E}[X].
$$

That is the precise, defensible bridge from your single-snapshot-per-subject MRSI data to a meaningful group-level metabolic connectome.
