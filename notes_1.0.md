
# 06-05-2024
• Invariant network metrics in structural connectome attain invariance if
streamline number is above 10e6
[REF](https://eur03.safelinks.protection.outlook.com/GetUrlReputation)
• Metabolic changes in MRS alzheimer
[REF] (https://eur03.safelinks.protection.outlook.com/GetUrlReputation)
• High NAA leads to OS
[REF] (https://www.tandfonline.com/doi/full/10.3109/00207454.2011.558225)
• N-Acetylaspartate as a reservoir for glutamate
[REF] (https://www.sciencedirect.com/science/article/pii/S0306987706001927)
• Homophily (from Ancient Greek ὁμός (homós) 'same, common', and φιλία
(philía) 'friendship, love') is a concept in sociology describing the tendency of
individuals to associate and bond with similar others, as in the proverb "birds
of a feather flock together".[1]

# 06-05-2024
• Tractography Fail: S006-V1 S058-V2
• Yasser call:
  - Use dipyfodf then normalize then input to tckgen "sfwm_fod_norm"
  - Tckgen: angle 45, trials 30
  - Add thalamaic, bs nuclei and transform before tractography
  - Tckgen –see_image use whitze matter mask
  - Convert tck to trk and view with trackvis: check yasser mail
  - Use in 5ttgen derivatives/freesurfer/Sub_XX-ses_YY/mri/aparcroseg.mgz instead of 55t
  -> convert from "freesurfer space" use:
    - cmd_bashargs = ['mri_vol2vol', '--mov', out_vol, '--targ', raw_vol,
    - '--regheader', '--o', out_vol, '--no-save-reg', '--interp', 'nearest']
    - Where:
      - out_vol = aparc+aseg.mgz
      - out_vol2 = aparc+aseg.nii.gz
      - raw_vol = 'mri', 'rawavg.mgz'
      - 
# 23-05-2024
- Check number of automorphisms and relate to symetry and redundancy
- Check book "Introduction to Algebraic Graph Theory" and in particular how the
spectrum of a Laplacaian graph reveals internal structures and isomophisms
28-05-2024
- The Bianconi–Barabási model is a model in network science that explains the growth of
complex evolving networks. This model can explain that nodes with different
characteristics acquire links at different rates. It predicts that a node's growth depends
on its fitness and can calculate the degree distribution. The Bianconi–Barabási model [1][2]
is named after its inventors Ginestra Bianconi and Albert-László Barabási. This model is a variant of the Barabási–
Albert model. The model can be mapped to a Bose gas and this mapping can predict a topological phase transition
between a "rich-get-richer" phase and a "winner-takes-all" phase.[2]
- Network robustness: Scale-free networks do not have a critical thresh-old for disintegration —
they are amazingly robust against accidental failures: even if 80% of randomly selected
nodes fail, the remaining 20% still form a compact cluster with a path connecting any two
nodes. This is because random failure affects mainly the numerous small degree nodes,
the absence of which doesn’t disrupt the network’s integrity71 . This reliance on hubs, on
the other hand, induces a so-called attack vulnerability the removal of a few key hubs
splinters the system into small isolated node clusters71
- Party hubvs are active, date hubs are non expressive

# 11-06-2024
- In addition to the model networks described above, we also examined model networks
that were created from points in 3-space [17, 18]. Our motivation for studying this class
of spatially embedded networks [25] lies in the fact that in many real-world systems,
geometric constraints can govern network structure.
https://academic.oup.com/comnet/article/5/2/245/2555362?login=true


# 13-06-2024
• Region and tissue differences of metabolites in normally
aged brain using multislice 1H magnetic resonance
spectroscopic imaging
https://pubmed.ncbi.nlm.nih.gov/11323817/


# 14-06-2024
- Yes, the clustering of brain parcels based on their metabolic composition can indeed be
seen as a result of self-organization. Self-organization refers to the process by which a
system naturally develops a structured pattern or organization without external direction,
driven by internal interactions and dynamics.
Self-Organization in Biological Systems:
1. Emergence of Patterns:
• In self-organization, complex structures and patterns emerge from simple
interactions between components of the system. This is observed in many biological
systems, such as the formation of cellular structures, neural networks, and ecological
systems.
1. Neuronal Development:
• During brain development, neurons and glial cells undergo self-organization to
form functional circuits and networks. This process is influenced by genetic
factors, chemical gradients, and neural activity.
1. Homeostasis and Adaptation:
• Self-organizing systems often exhibit homeostasis and adaptability. In the
brain, this could mean that metabolic demands and supplies are balanced
dynamically, leading to the observed metabotopic organization.
Metabotopic Organization as Self-Organization:
2. Metabolic Efficiency:
• Brain regions may self-organize based on metabolic needs to maximize
efficiency. Regions with similar metabolic demands and compositions cluster
together to optimize energy use and resource distribution.
1. Local Interactions:
• Local interactions between neurons, glial cells, and blood vessels could
drive the clustering of metabolically similar regions. For example, regions
with high metabolic activity may attract more blood supply, reinforcing
their metabolic characteristics.
1. Functional Integration:
• Metabotopic organization might facilitate the integration of
functionally related areas, promoting coordinated activity and
efficient information processing.
Examples in the Brain:
2. Cortical Columns:
• Cortical columns are an example of self-organization where neurons within
a column respond to similar types of stimuli and exhibit similar metabolic
activity.
1. Neuronal Assemblies:
• Neuronal assemblies, groups of neurons that fire together and form
functional units, often exhibit metabolic and structural coherence,
reflecting self-organized patterns.
Conclusion:
The concept of metabotopic organization as a result of self-organization
highlights how complex brain structures and functions can arise from simple,
local interactions and intrinsic dynamics. This perspective can provide valuable
insights into the development, function, and adaptation of neural systems, as
well as their responses to changes in metabolic demands and environmental
conditions.

• Include WM to GM segmentation to homotopy
https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.1910390107


# 7/26/24
• Metabolic homotopy: inter and intra cluster segementation:
- automorpgic equivalence AE: clusters are maximally non-AE, intracluster nodes are
maximally AE.
WM maturation, reference for WM segementation , frontal lobe gradient:
https://pubmed.ncbi.nlm.nih.gov/29305910/
https://pubmed.ncbi.nlm.nih.gov/18295509/

