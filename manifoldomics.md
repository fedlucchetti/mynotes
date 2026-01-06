# From Connectomics to Manifoldomics: A Geometric Reframing of Functional and Metabolic Organization

---

## Mathematical motivation: correlations as geometric objects in Hilbert space

Pairwise correlations between brain regions are often interpreted operationally as “connections.”  
However, mathematically, a correlation is not an edge but a **geometric relation**.

Let $X_i \in \mathbb{R}^T$ denote a regional signal (functional time series or metabolic profile), mean-centered and variance-normalized. The Pearson correlation between regions $i$ and $j$ is

$
\rho_{ij} = \frac{\langle X_i, X_j \rangle}{\|X_i\|\|X_j\|}
$

This is a **normalized inner product**, equivalent to a cosine similarity. Therefore:

- Each region corresponds to a point (or vector) in a Hilbert space
- The full correlation matrix is a **Gram matrix**
- The matrix encodes angles and relative orientations, not physical couplings

Although correlation itself is not a metric (it violates the triangle inequality), it can be transformed into a valid distance, e.g.:

$
d_{ij} = \sqrt{2(1 - \rho_{ij})}, \quad d_{ij} = \arccos(\rho_{ij})
$

Once this transformation is applied, the data naturally live in a **metric space**, and—under mild regularity assumptions—can be interpreted as samples from a **low-dimensional manifold embedded in a high-dimensional feature space**.

Thus, correlation matrices do not primarily describe networks of connections, but rather the **intrinsic geometry of a statistical product space**. Manifold learning methods (diffusion maps, Laplacian eigenmaps, UMAP, t-SNE) are not heuristic projections, but principled tools for recovering this latent geometry.

---

## 1. The conceptual move

The core conceptual move is the following:

> For functional and metabolic data, the primitive object is not a graph but a statistical manifold.  
> Graphs are a discretization choice, not a generative principle.

In this view, regions are not nodes exchanging signals, but coordinates on a latent manifold shaped by shared constraints. Pairwise similarities approximate local geometry, and global organization emerges from how these local neighborhoods stitch together.

This reframing does not discard connectomics; it **subsumes it** as a special, coarse representation of a deeper geometric structure.

---

## 2. Why “connectomics” becomes conceptually misleading

Connectomics implicitly assumes that:

- Edges correspond to interactions, transfers, or couplings
- Network topology reflects communication pathways or routing efficiency

In contrast, functional and metabolic correlations often arise from:

- Shared modulation by latent variables
- Common energetic or biochemical constraints
- Global homeostatic regulation
- Co-embedding in a restricted state space

In these contexts, no signal transmission is required for strong correlation.  
Thus, the language of “connections,” “hubs,” or “information flow” becomes ontologically ambiguous.

What is actually observed is **proximity in state space**, not wiring in physical space.

---

## 3. Proposing a new family of “-omics” terms

To reflect this shift, we propose geometry-first vocabularies that treat manifolds—not graphs—as the primary object:

- **Manifoldomics** – latent low-dimensional brain organization
- **Geometromics** – geometry-driven description of brain data
- **Statomorphomics** – shape of statistical variation
- **Energeomics** – organization shaped by energetic constraints
- **Metabologeomics** – geometry of metabolic similarity spaces
- **Diffusiomics** – structure revealed via diffusion operators
- **Entropomics** – entropy-structured brain state spaces
- **Spectromics** – organization in Laplacian eigenmodes

Within this framework, connectomics becomes one projection among many, rather than the foundational description.

---

## 4. From networks to manifolds: metrics compared

| Classical network metrics | Geometric / manifold counterparts |
|---------------------------|-----------------------------------|
| Node degree               | Local volume element / density |
| Strength (weighted degree)| Local entropy or participation ratio |
| Clustering coefficient    | Local curvature (Ricci / sectional) |
| Shortest path length      | Geodesic distance |
| Betweenness centrality    | Geodesic flow concentration |
| Hubs                      | Low-curvature or high-stability regions |
| Communities / modules     | Coordinate charts / manifold patches |
| Modularity                | Curvature heterogeneity |
| Small-worldness           | Scale-dependent dimensionality |
| Eigenvector centrality    | Dominant Laplacian eigenmodes |
| Rich club                 | High-dimensional attractor regions |

In this table, network metrics appear as **discrete summaries** of continuous geometric properties.

---

## 6. A unifying generative hypothesis

A central theoretical question follows naturally:

> What generates the functional manifold, and is it the same principle that generates the metabolic manifold?

We propose the following hypothesis:

> Functional and metabolic manifolds emerge from a shared set of biological constraints—energetic cost, biochemical availability, and homeostatic regulation—applied to different observable variables. These manifolds are therefore not identical, but are topologically aligned projections of a common constraint system.

In this view:
- Metabolism reflects constraints on available biochemical states
- Function reflects dynamical trajectories within those constraints
- Both carve structured geometry into state space

Differences between manifolds encode modality-specific expression; similarities reveal shared generative principles.

---

## 7. Reframing multimodal neuroscience

This geometric perspective reframes multimodal integration:

Instead of asking  
**“Are functional and metabolic networks connected?”**

we ask  
**“Do functional and metabolic manifolds share geometry?”**

Concrete questions become:
- Do they share low-dimensional embeddings?
- Are their Laplacian eigenmodes aligned?
- Do geodesic paths correspond across modalities?
- Is curvature conserved or redistributed?
- Do entropy gradients co-localize?

Multimodal neuroscience thus becomes a problem of **manifold alignment**, not network overlap.

---

## Closing perspective

Correlation-based brain organization is more naturally understood as geometry rather than connectivity.  
Graphs summarize; manifolds explain.

This shift moves the field from descriptive topology toward generative principles grounded in differential geometry, statistical physics, and biological constraint.
