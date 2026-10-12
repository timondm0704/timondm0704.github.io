---
layout: default
title: "BifurcatoR: Detecting Variance Heterogeneity"
section: Genomic Research
---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

## BifurcatoR: Detecting Variance Heterogeneity
*Variance Heterogeneity · Phenotypic Noise · Variability*


### Skills Demonstrated

Simulation Study Design · Statistical Power and False Positive Rate Analysis · Mean/Variance/Bimodality Tests · Mixture Models · High-Performance Computing · R · Data Visualization

---

### Overview

Patients with the same diagnosis often respond very differently to the same treatment, yet most biomedical research focuses on average effects and treats the remaining variation as statistical noise. This variation, known as variance heterogeneity (VH), can take the form of uneven spread, skewness, or multiple peaks, and it can reveal hidden patient subgroups that differ in prognosis or treatment response. Although statistical methods for detecting VH exist, they are scattered across different software packages, many assume normally distributed data that real biological measurements rarely follow, and most require programming expertise. Researchers also lack clear guidance on which method to choose and how large a study needs to be.

BifurcatoR was developed as an open-source framework, in collaboration with the Van Andel Institute and MaineHealth Institute for Research, that brings VH detection, study design, and data analysis into a single platform. It is available as an R package and as an interactive web application, so researchers without programming experience can estimate statistical power, plan sample sizes, and test their own data for variance differences and bimodality.

My work focused on the simulation study evaluating how well statistical methods perform. Thousands of datasets were simulated across a range of distributions, differences in group means and variances, subgroup proportions, and sample sizes. Under each scenario, variance tests, mixture models, and bimodality tests were compared on their statistical power and false positive rates. Power was defined as the proportion of simulated datasets in which a method detected a true difference, and the false positive rate as the proportion of simulated null datasets, with no true difference, in which it wrongly detected one. To handle the computational scale, the full set of simulations was run on Northeastern's high-performance computing cluster. The results showed that method performance is highly context-dependent, with no single approach performing best across all conditions, and these findings now inform the method recommendations built into BifurcatoR.

When applied to real data, BifurcatoR found two hidden groups of patients among children with a common type of leukemia, based on EVI1 gene expression, and those with higher EVI1 expression had worse survival. Among identical twins, it revealed two distinct immune-related patterns in fat tissue, suggesting that obesity may come in different forms even among people with the same genes.

---

### Figures

<iframe src="https://rstudio-pubs-static.s3.amazonaws.com/1149896_41dda4119cf9454096514ad35d6945d2.html"
        width="100%" style="height: 90vh; border: 1px solid #ddd; border-radius: 8px;"
        loading="lazy" title="BifurcatoR simulation study"></iframe>
<br><small><em>Figure 1. Interactive visualization of the BifurcatoR simulation study. <a href="https://rpubs.com/mding_mhir/add_LNmixR" target="_blank">Open full report on RPubs ↗</a></em></small>

---

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})
