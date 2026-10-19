---
layout: default
title: "Variance Heterogeneity in Metabolic Traits: A Chromosome Substitution Strain (CSS) Mouse Study"
section: Genomic Research
---

{% include sticky-figs.html %}

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

<div class="poe-layout">

<div class="poe-text" markdown="1">

## Variance Heterogeneity in Metabolic Traits: A Chromosome Substitution Strain (CSS) Mouse Study

### Skills Demonstrated

*R · Permutation Testing · Nonparametric Statistics · Bootstrap Resampling · FDR Correction · Data Visualization · Correlation Networks*

---

### Overview

Differences between people in traits like body weight, blood sugar, and liver fat are usually explained by genes, environment, and their interactions. Yet even genetically identical animals raised under the same conditions can differ dramatically. This points to a neglected dimension of variation. Most genetic studies look only for variants that shift a trait’s average (mean QTLs, or mQTLs). Some genomic regions instead change how widely a trait is spread across individuals (variance QTLs, or vQTLs). This pattern is called variance heterogeneity, and standard analyses usually dismiss it as noise.

The project is a collaboration between Northeastern University, the MaineHealth Institute for Research, and the Van Andel Institute, funded by an NIH Transformative Research Award. It compares the two parent strains, C57BL/6J and A/J, with 22 chromosome substitution strains (CSSs). Each CSS is a B6 mouse carrying one chromosome from A/J. Mice were fed a high-fat, high-sugar diet or a control diet, and metabolic traits were measured over time, including body weight, glucose, insulin, cholesterol, and liver triglycerides etc.

To detect where and how strongly genetic background, diet, and sex change trait averages and variability, I implemented the analysis and visualizations in R:

- Permutation tests on mean ratios and median absolute deviation (MAD) ratios to detect mean and variance effects of strain, diet, and sex, summarized in heatmaps across the full CSS panel
- Paired within-mouse permutation tests to track changes over time
- Phenotypic effect calculations for each CSS relative to the two parent strains, with additivity tests using bootstrap confidence intervals
- Parallel coordinates plots of each mouse’s metabolic profile
- Spearman correlation networks showing how traits move together

By treating variability as a measurable trait in its own right, this study provides a framework for identifying genomic regions that control how much individuals differ in metabolic disease risk. Understanding these regulators could help explain why disease severity varies so widely and support more personalized approaches to prevention and treatment.

</div>

<div class="poe-figs">
  <figure class="poe-fig">
    <img src="{{ '/images/CSS_parallel_coordinates.png' | relative_url }}" alt="Parallel coordinates plot of metabolic traits">
    <figcaption>Figure 1. Parallel coordinates plot of 13 metabolic traits in C57BL/6J and A/J mice on HFHS and control diets</figcaption>
  </figure>

  <figure class="poe-fig">
    <img src="{{ '/images/CSS_correlation_network.png' | relative_url }}" alt="Spearman correlation networks of metabolic traits">
    <figcaption>Figure 2. Spearman correlation networks of 13 metabolic traits for each strain and diet combination.</figcaption>
  </figure>

  <figure class="poe-fig">
    <img src="{{ '/images/CSS_mean_variance.png' | relative_url }}" alt="Mean and variance effects across CSS strains">
    <figcaption>Figure 3. Mean and variance effects for 22 chromosome substitution strains compared with C57BL/6J across 13 metabolic traits.</figcaption>
  </figure>
</div>

</div>

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})
