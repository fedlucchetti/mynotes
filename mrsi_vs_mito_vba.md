# Metabolic Weighting Results and Mitochondrial Alignment

## 1. Weighting Results

The optimal linear combination of MRSI-derived metabolite maps that maximized alignment with the mitochondrial reference yielded the following weights:

| Metabolite | Weight |
|-----------|--------|
| Glu | **+1.0024** |
| Cho | **+0.4257** |
| NAA | **+0.3036** |
| Gln | **+0.1654** |
| tCr | **−0.9820** |
| GABA | **−0.7176** |
| NAAG | ~0 |
| Ins | ~0 |
| GSH | ~0 |

Zero or near-zero weights indicate metabolites whose variance did not contribute additional explanatory power after conditioning on the others.

---

## 2. Structure of the Discovered Metabolic Mode

The learned metabolic mode can be expressed schematically as:

$
\text{Mitochondrial Alignment} \;\approx\;
(\text{Glu} + \text{Cho} + \text{NAA} + \text{Gln})
\;-\;
(\text{CrPCr} + \text{GABA})
$

This representation highlights that mitochondrial correspondence is governed by a **contrastive metabolic axis**, rather than by absolute levels of any single metabolite.

---

## 3. Interpretation of Positive Contributions

### Glutamate (Glu)
Glu emerged as the dominant positive contributor, indicating that mitochondrial spatial organization is primarily associated with regions of high glutamatergic metabolic throughput. This reflects strong coupling between excitatory neurotransmission and oxidative metabolism via the tricarboxylic acid cycle.

### Choline-containing Compounds (GPC + PCh)
The positive contribution of GPC+PCh suggests an association between mitochondrial alignment and membrane turnover or structural maintenance, including myelin and axonal membrane synthesis, processes that are energetically demanding and mitochondria-dependent.

### N-acetylaspartate (NAA)
NAA contributed positively but with a lower weight than Glu, consistent with its role as a marker of neuronal mitochondrial integrity and acetyl-CoA–dependent metabolism. Its moderate weight indicates that structural mitochondrial specificity adds explanatory value beyond glutamatergic metabolic demand.

### Glutamine (Gln)
The positive Gln weight reflects astrocytic metabolic support and ATP-dependent glutamate–glutamine cycling, indicating that mitochondrial alignment encompasses neuron–astrocyte metabolic coupling.

---

## 4. Interpretation of Negative Contributions

### Creatine + Phosphocreatine (Cr + PCr)
Cr+PCr showed a strong negative weight, indicating that generic energy buffering and nonspecific energetic background variance do not explain mitochondrial spatial organization. Subtracting this component isolates sustained oxidative energy consumption rather than storage capacity.

### GABA
The negative GABA weight suggests that, after accounting for glutamatergic metabolism, inhibitory neurotransmitter pool size does not contribute additional explanatory power. This implies that mitochondrial alignment in the present data is biased toward excitatory rather than inhibitory metabolic organization.

---

## 5. Metabolites with Minimal Contribution

NAAG, myo-inositol (Ins), and glutathione (GSH) exhibited near-zero weights, indicating that variance associated with peptide neurotransmission, glial osmotic regulation, and redox balance, respectively, does not significantly contribute to mitochondrial alignment once other metabolites are considered.

---

## 6. Conceptual Summary

These results indicate that mitochondrial spatial organization in the brain is best captured by a metabolic mode dominated by **glutamatergic oxidative demand and membrane maintenance**, while subtracting **nonspecific energy buffering and inhibitory pool storage**. Rather than reflecting mitochondrial density per se, this axis represents the **deployment of mitochondrial support required to sustain excitatory neurotransmission and neuron–astrocyte metabolic coupling**.

---

## 7. One-sentence Synthesis

**Mitochondria align with regions of sustained excitatory oxidative economy, not with generic energy storage or inhibitory neurotransmitter pools.**
