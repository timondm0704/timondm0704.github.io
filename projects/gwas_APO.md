---
layout: default
title: "Pharmacogenetic GWAS of Bone Mineral Density"
section: Genomic Research
---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

## Pharmacogenetic GWAS of Bone Mineral Density

### Skills Demonstrated

*REGENIE · PLINK · Linkage Disequilibrium (LD) · LocusZoom Plot· Manhattan Plot · R · Bash · SLURM · High-Performance Computing (HPC)*

---

### Overview

Bone loss speeds up in women after menopause, yet most approved osteoporosis drugs are reserved for treating established disease rather than preventing it, partly because of rare but serious side effects. The Atenolol for the Prevention of Osteoporosis (APO) trial tested whether atenolol, a widely used and low-cost beta-blocker, can prevent bone loss in postmenopausal women. This multi-site, double-blind, randomized placebo-controlled trial enrolled 420 women at Mayo Clinic, Columbia University Irving Medical Center, and Maine Medical Center, measuring bone mineral density (BMD) by DXA and the bone resorption marker CTX at baseline and every six months for two years. Because people often respond differently to the same drug, a key question is whether genetic variation helps explain who benefits from atenolol.

In this project, I built a GWAS pipeline on a high-performance computing cluster to test SNP × treatment interactions genome-wide. Variants were quality-filtered with PLINK2, and association testing was performed with REGENIE, which accounts for each participant’s genetic background and ancestry while testing about 5.9 million variants. Outcomes were percent change from baseline in five BMD traits (total hip, femoral neck, lumbar spine, ulna, and whole body) and CTX across follow-up visits. Top signals were annotated using public resources (UCSC Genome Browser, GWAS Catalog, GTEx, GeneHancer) and compared with large published BMD GWAS from the Musculoskeletal Knowledge Portal.

Preliminary results identified several genome-wide significant SNP × treatment interactions for hip, femoral neck, and ulna BMD, and for CTX, emerging at different time points during the trial. Notably, one of the strongest bone-resorption signals lies near a gene previously shown in experimental studies to suppress the formation of bone-resorbing cells, offering a plausible biological explanation for the CTX finding. Several other signals were also nominally associated with BMD in much larger external studies. These findings suggest that genetic variation may influence how individuals respond to bone-protective treatment, an important step toward precision medicine in osteoporosis prevention.

---

### Figures

![APO GWAS analysis workflow]({{ "/images/apo_workflow.png" | relative_url }})
<br><small><em>Figure 1. Pharmacogenetic GWAS workflow in the APO trial</em></small>

![APO GWAS circular Manhattan plot]({{ "/images/APO_interaction_circular.jpg" | relative_url }})
<br><small><em>Figure 2. Circular Manhattan plot of genome-wide genotype by treatment interaction results for change in bone mineral density and the bone resorption marker CTX in the APO trial</em></small>

![LocusZoom plot of an interaction signal]({{ "/images/APO_Locuszoom.png" | relative_url }})
<br><small><em>Figure 3. LocusZoom plot of a genome-wide significant genotype by treatment interaction signal and nearby genes</em></small>

![Predicted percent change in CTX by genotype and treatment]({{ "/images/predicted_%change_CTX.png" | relative_url }})
<br><small><em>Figure 4. Predicted percent change in CTX by genotype and treatment at a top interaction variant</em></small>

---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

<!-- After publication: add the paper link here, and replace demo figures with real results. -->
