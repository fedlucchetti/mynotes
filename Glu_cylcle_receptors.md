# Introduction
Molecular neuroimaging modalities provide complementary but fundamentally distinct views of brain chemistry. Proton magnetic resonance spectroscopic imaging (¹H-MRSI) quantifies regional concentrations of neurochemicals, reflecting large intracellular and extracellular metabolic pools that support neuronal and glial function. In contrast, positron emission tomography (PET) with receptor-specific radioligands indexes the spatial distribution of molecular targets such as neurotransmitter receptors or synaptic proteins, reflecting the capacity for signaling rather than metabolite abundance. Because these modalities probe different biochemical compartments and operate on different spatial and temporal scales, direct voxelwise correspondence between metabolite concentrations and receptor binding is neither expected nor biologically well defined.

Rather than testing for local biochemical equivalence, an alternative perspective is to ask whether different imaging modalities reveal a shared organizational structure of brain chemistry. Brain regions are not independent entities; instead, they are embedded in coordinated systems shaped by development, cellular composition, and long-term functional specialization. As a result, biological organization is often expressed more robustly in the pattern of relationships between regions than in absolute regional values. This principle underlies widely used approaches such as structural covariance analysis, gene co-expression networks, and functional connectivity, where inter-regional similarity captures meaningful systems-level organization even when direct voxelwise correspondence is absent.

Building on this framework, we test whether regions that are metabolically similar with respect to the glutamate cycle—as quantified by multimetabolite MRSI—are also similar in their receptor architecture as indexed by PET imaging of glutamatergic targets. This network-level hypothesis does not imply a direct biochemical coupling between glutamate concentration and receptor binding. Instead, it asks whether both modalities encode a common macroscale organization of glutamatergic systems across the cortex. By comparing inter-regional similarity matrices derived independently from MRSI and PET data, we assess shared topological structure while remaining agnostic to modality-specific units, scaling, and noise.

This relational approach provides a principled framework for integrating MRSI and PET, allowing multimodal comparison at the level of systems organization rather than local concentration matching. In doing so, it leverages the strengths of each modality while avoiding assumptions that are incompatible with their underlying biology.


## 1) What voxelwise comparison assumes (and why it’s often ill-posed)

A voxelwise (or regionwise) comparison typically assumes there is a direct mapping between modality values:

Let  
- \(x_i\) = MRSI-derived value in region \(i\) (e.g., Glu concentration)  
- \(y_i\) = PET-derived value in region \(i\) (e.g., mGluR5 binding, \(BP_{ND}\))

Voxelwise correspondence implicitly tests a relationship like:

\[
y_i \approx f(x_i)
\]

Most commonly, one assumes a linear model:

\[
y_i = a x_i + b + \varepsilon_i
\]

This implies that the two modalities measure **the same underlying quantity** up to scaling/offset (plus noise).
For MRSI vs PET, that assumption is usually biologically inappropriate:
- MRSI: largely metabolic pools (mostly intracellular + extracellular tissue pools)
- PET: receptor/target availability (membrane protein architecture, often long-timescale)

So a pointwise relation \(y_i \approx f(x_i)\) is not expected to hold.

---

## 2) What a similarity matrix comparison asks instead

Rather than matching values, we compare **relationships between regions**.

Let \(\mathcal{R} = \{1,\dots,N\}\) be the set of brain regions/parcels.

### MRSI: represent each region by a feature vector
For MRSI, each region \(i\) can be represented as a vector of metabolites:

\[
\mathbf{m}_i \in \mathbb{R}^p
\]

Example: \(\mathbf{m}_i = (\text{Glu}_i,\text{Gln}_i,\text{GSH}_i)\).

Define an inter-regional distance:

\[
d_M(i,j) = \|\mathbf{m}_i - \mathbf{m}_j\|
\]

(or any other sensible distance / dissimilarity)

### PET: represent each region by a scalar
For a single PET tracer map (one scalar per region):

\[
x_i \in \mathbb{R}
\]

Define a distance:

\[
d_P(i,j) = |x_i - x_j|
\]

### Convert distances to similarities (optional but common)
Using a Gaussian/RBF kernel:

\[
S_{ij} = \exp\!\left(-\frac{d(i,j)^2}{2\sigma^2}\right)
\]

This yields:
- \(S^M\) from MRSI distances \(d_M\)
- \(S^P\) from PET distances \(d_P\)

---

## 3) The network-level hypothesis (precise statement)

The hypothesis is **not** “PET values equal MRSI values”.
Instead, it is:

> The **distance geometry** (or similarity geometry) of regions induced by MRSI resembles that induced by PET.

Formally, you test whether:

\[
d_M(i,j) \approx g\!\big(d_P(i,j)\big)
\]

for some monotonic function \(g\) (often you don’t need to model \(g\) explicitly).

A practical test is to compare the two distance (or similarity) matrices:

\[
\text{corr}\Big(\{d_M(i,j)\}_{i<j},\; \{d_P(i,j)\}_{i<j}\Big) > 0
\]

or equivalently

\[
\text{corr}\Big(\{S^M_{ij}\}_{i<j},\; \{S^P_{ij}\}_{i<j}\Big) > 0
\]

This asks:

> Do pairs of regions that are metabolically similar also tend to be receptor-architecturally similar?

This is a **relational / network-level** correspondence, not a voxelwise biochemical coupling.

---

## 4) Why this can succeed even when voxelwise matching fails

### (a) You are matching *shape*, not *coordinates*
Voxelwise comparison tries to match values \(x_i\) and \(y_i\) directly.

Similarity comparison matches the **pairwise structure**:
- who is close to whom,
- which clusters form,
- what gradients or manifolds appear.

It’s the difference between comparing two coordinate systems vs comparing the geometry they induce.

### (b) Invariance to scaling and offsets (robustness)
If PET values undergo a linear transform:

\[
x_i' = a x_i + b
\]

then distances scale but preserve ordering:

\[
|x_i' - x_j'| = |a|\,|x_i - x_j|
\]

If you use a rank-based distance (or compare ranks of distances), you gain invariance even to monotonic transforms:

\[
x_i' = h(x_i) \quad \text{(monotonic }h\text{)}
\]

Voxelwise regression is not invariant in this way.

### (c) Modalities can encode the same *systems organization* via different mechanisms
Different biological processes can be constrained by the same macroscale axes (development, cytoarchitecture, myelination, hierarchical gradients).
Thus MRSI metabolism and PET receptor architecture can share a similar topology even without pointwise coupling.

---

## 5) Kernel / embedding viewpoint (optional intuition)

When you define a similarity kernel \(S\), you implicitly embed regions into a (possibly high-dimensional) space where inner products reproduce similarities (RKHS intuition).

Comparing \(S^M\) and \(S^P\) is equivalent to asking:

> Do the two modalities induce similar embeddings / neighborhood structures of the same set of regions?

This is closely related to:
- kernel alignment
- Mantel tests (matrix correlation)
- Procrustes / embedding alignment
- diffusion map / gradient alignment

---

## 6) Manifold viewpoint (why this is “systems-level”)

Suppose regions lie on (or near) a low-dimensional manifold that encodes cortical organization.
Different modalities provide different “charts” of the same manifold:

- MRSI provides coordinates via metabolite features \(\mathbf{m}_i\)
- PET provides coordinates via receptor density \(x_i\) (or vectors across tracers)

Similarity matrices approximate the manifold’s intrinsic geometry.
So the comparison asks whether both modalities recover a **shared low-dimensional organization**.

---

## 7) Take-home summary (one line)

**Voxelwise analysis asks whether two functions are equal.  
Similarity-matrix analysis asks whether two functions induce the same geometry (shape) over regions.**
