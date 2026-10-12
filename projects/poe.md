---
layout: default
title: "Parent-of-Origin Effects on Obesity"
section: Genomic Research
---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

## Parent-of-Origin Effects on Obesity


### Skills Demonstrated

R · Visualization · Statistical Genetics · QTL Analysis (mQTL, vQTL, eQTL) · Parent-of-origin Analysis  · Genotype QC and Imputation Filtering · LD and Haplotype Block Analysis (PLINK) · Multi-omics Integration (GTEx) · Large Cohort Data (FHS)

### Overview

The FTO gene is the most significant and widely replicated obesity finding from genome-wide association studies (GWAS). Its obesity-associated variants sit in non-coding regions (introns 1–3) and act as regulators, changing the expression of the neighboring genes IRX3 and IRX5 and shifting how fat cells store or burn energy. Earlier studies in humans and mice suggest that some of these effects depend on parental origin, known as parent-of-origin effects (POE): a variant inherited from the mother can act differently than the same variant inherited from the father. However, previous work examined only a handful of variants, focused almost entirely on BMI, was rarely replicated across cohorts, and only evaluated whether variants shift the mean. Variance effects, which describe the spread of a trait's distribution, remain understudied, yet they are important for understanding why people with the same variant can have different outcomes.

In this project, I systematically tested POE across FTO introns 1–3 using data from the Framingham Heart Study (FHS), where available parental genotypes allow each allele to be traced to the mother or the father. After quality control filtering, 398 SNPs grouped into 38 haplotype blocks were tested in 4,403 individuals for both mean (mQTL) and variance (vQTL) effects, comparing maternally and paternally inherited alleles. The analysis was then extended beyond BMI to five more obesity traits that capture body fatness and fat distribution. Blood expression of FTO, IRX3, and IRX5 was also examined to see whether these SNPs affect gene expression (eQTL) and whether that effect differs by parental origin (POE eQTL), followed by a GTEx lookup of tissue-specific eQTLs for comparison.

Preliminary results suggest that most variants with parent-of-origin signals have stronger maternal effects on both the mean and the variance of obesity traits. They partially replicate findings from the Sorbs and German Trios cohorts and point to a candidate region where BMI, blood expression, and skeletal muscle expression signals overlap. These findings indicate that parental origin is an often-overlooked layer of genetic influence on obesity, one that may contribute to the missing heritability of complex traits.

---

### Figures

![POE analysis workflow]({{ "/images/poe_workflow.png" | relative_url }})
<br><small><em>Figure 1. Analysis workflow: 398 FTO SNPs across 38 haplotype blocks, tested for mean and variance effects on obesity for parent-of-origin effects, blood eQTLs (FTO, IRX3, IRX5), and tissue-specific GTEx eQTLs.</em></small>

<br>

![Integrated association heatmap]({{ "/images/fto_integrated_heatmap.png" | relative_url }})
<br><small><em>Figure 2. Integrated view of association signals across FTO haplotype blocks, combining mean and variance effects on obesity traits, parent-of-origin effects, blood gene expression, and tissue-specific expression from GTEx.</em></small>

---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

<!-- After publication: add the paper link here, and replace demo figures with real results. -->
