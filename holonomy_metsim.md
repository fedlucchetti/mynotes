# Cycle / Holonomy Curvature for MRSI Metabolic Similarity

*(with a clear definition of edge transport and what (H) means)*

This procedure turns your regional metabolite profiles into a **curvature-like** signal on a graph by checking whether **local alignments are globally consistent around small cycles** (triangles).

---

## 1) Data and notation

You have a brain graph (G=(V,E)) (e.g., built from MeSiM or anatomical adjacency).
Each node (i \in V) has a metabolic feature vector:

$$
\mathbf{m}_i \in \mathbb{R}^K
$$

where (K) is the number of metabolites included in the regional profile.

A common preprocessing choice is to standardize or harmonize (\mathbf{m}_i) across regions and/or subjects.

---

## 2) Normalize node “directions”

We interpret each (\mathbf{m}_i) as a **direction** in metabolite space:

$$
\hat{\mathbf{m}}_i = \frac{\mathbf{m}_i}{\lVert \mathbf{m}_i \rVert}
$$

This removes absolute magnitude so we focus on **profile shape/orientation**.

---

## 3) Define the **edge transport** (R_{ij})

**Edge transport** is the *local alignment operator* that maps the direction at node (i) to the direction at node (j).

Formally, for adjacent nodes ((i,j) \in E), we define:

$$
R_{ij} \in \mathbb{R}^{K \times K}
$$

as an orthogonal (rotation-like) matrix such that:

$$
R_{ij},\hat{\mathbf{m}}_i \approx \hat{\mathbf{m}}_j
$$

### A concrete, minimal-rotation choice

Let:

$$
u = \hat{\mathbf{m}}_i, \quad v = \hat{\mathbf{m}}_j
$$

Define the **skew-symmetric** matrix:

$$
A = v u^\top - u v^\top
$$

> Important implementation note:
> (vu^\top) and (uv^\top) are **outer products**, not elementwise products.

Let:

$$
\alpha = u^\top v
$$

When (\alpha \neq -1), the **minimal rotation** that maps (u) toward (v) is:

$$
R_{ij} = I + A + \frac{A^2}{1+\alpha}
$$

Properties:

* If (u = v), then (A=0) and (R_{ij}=I).
* If (u) and (v) are close, (R_{ij}) is a small rotation.
* The special case (\alpha \approx -1) (nearly opposite vectors) needs a separate fallback.

---

## 4) Define triangle **holonomy** (H_{ijk})

A triangle is a 3-cycle ((i,j,k)) where all three edges exist:

$$
(i,j), (j,k), (k,i) \in E
$$

We transport the direction around the loop:

$$
i \to j \to k \to i
$$

The **holonomy** is the composed transport:

$$
H_{ijk} = R_{ki},R_{jk},R_{ij}
$$

---

## 5) What does (H_{ijk}) *mean*?

(H_{ijk}) measures **loop consistency** of your local metabolite orientations.

### Interpretation

* **If the local structure is “flat / integrable-like”:**

$$
H_{ijk} \approx I
$$

This means:

> The alignment you infer from (i) to (j), (j) to (k), and (k) back to (i) is globally consistent.
> The triangle does not accumulate a net “twist.”

* **If there is a local “twist / incompatibility”:**

$$
H_{ijk} \not\approx I
$$

This indicates:

> A mismatch between local metabolic directions across the triangle.
> This is the **discrete analogue of curvature** (or non-integrability).

This is the graph version of your analogy:

> same space, but transporting orientation around a loop changes the orientation.

---

## 6) Define a scalar triangle curvature

A simple curvature magnitude:

$$
c_{ijk} = \lVert H_{ijk} - I \rVert_F
$$

where (\lVert \cdot \rVert_F) is the Frobenius norm.

---

## 7) Aggregate to edges and nodes (optional)

**Edge curvature** from triangles incident to edge ((i,j)):

$$
c_{ij} = \mathrm{mean}{ c_{ijk} : (i,j,k) \text{ is a triangle}}
$$

**Node curvature** from incident edges:

$$
c_i = \mathrm{mean}{ c_{ij} : j \in \mathcal{N}(i)}
$$

---

## 8) Algorithm summary

1. Build your graph (G) (MeSiM thresholded network or anatomical adjacency).
2. Assign node feature vectors (\mathbf{m}_i).
3. Normalize to (\hat{\mathbf{m}}_i).
4. For each edge ((i,j)), compute transport (R_{ij}).
5. Enumerate triangles ((i,j,k)).
6. Compute holonomy (H_{ijk}).
7. Convert to curvature (c_{ijk}).
8. Aggregate to edges/nodes.
9. Compare curvature maps across cohorts, conditions, or harmonization choices.

---

## 9) Why this is useful for your MRSI metabolic similarity

This gives you a **higher-order marker** beyond pairwise similarity:

* Pairwise edges tell you “who is similar to whom.”
* Triangle holonomy tells you:

  > “Are these local similarities mutually coherent, or do they conflict when you close the loop?”

That can highlight:

* boundaries between biochemical territories,
* hub-like transition regions,
* disease-related reconfiguration,
* or preprocessing/normalization instability.

---

## 10) Minimal implementation reminder

When you code:

* **Correct**

  ```python
  A = np.outer(v, u) - np.outer(u, v)
  ```

* **Incorrect (will give zero)**

  ```python
  A = v*u - u*v
  ```

---

## One sentence you can reuse in a Methods section

We define an edge transport (R_{ij}) as the minimal rotation in metabolite space that aligns the normalized metabolic profile at region (i) to that at region (j); the holonomy (H_{ijk}=R_{ki}R_{jk}R_{ij}) around triangles quantifies loop inconsistency, with deviations from identity providing a discrete curvature-like measure of local non-integrability in metabolic organization.

---

If you want, I can also give you a compact, numerically safe Python function for (R_{ij}) (including the (\alpha \approx -1) case) and a triangle-enumeration routine optimized for your NetworkX pipeline.
