---
layout: default
title: "Parent-of-Origin Effects on Obesity"
section: Genomic Research
---

<style>
  /* Use almost the full screen width on this page */
  @media (min-width: 961px) {
    .wrapper { width: 98vw; max-width: none; }
    header, footer { width: 200px; }
    section { width: calc(100% - 230px); }
  }

  /* Two columns: text (left) + both figures (right, sticky) */
  .poe-layout {
    display: grid;
    grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
    gap: 2rem;
    align-items: start;
  }
  .poe-text { min-width: 0; }

  .poe-figs {
    position: sticky;
    top: 1rem;
    max-height: calc(100vh - 2rem);
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .poe-fig { margin: 0; }
  .poe-fig img {
    width: 100%;
    max-height: calc(50vh - 4.5rem);
    object-fit: contain;
    cursor: zoom-in;
  }
  /* OPTIONAL: make Figure 1 smaller so Figure 2 (heatmap) gets more room.
     Remove the comment markers to turn it on. */
  /* .poe-fig:first-child img { max-height: 35vh; } */

  .poe-fig figcaption { font-size: .8rem; font-style: italic; margin-top: .3rem; }

  /* Click a figure to enlarge it full-screen; click or Esc to close */
  .fig-zoom {
    display: none; position: fixed; inset: 0; z-index: 1000;
    background: rgba(0,0,0,.88); align-items: center; justify-content: center; cursor: zoom-out;
  }
  .fig-zoom.open { display: flex; }
  .fig-zoom img { max-width: 96vw; max-height: 94vh; background: #fff; }

  /* Small screens: stack text and figures normally */
  @media (max-width: 960px) {
    .poe-layout { display: block; }
    .poe-figs { position: static; max-height: none; overflow: visible; }
    .poe-fig img { max-height: none; }
  }
</style>

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

<div class="poe-layout">

<div class="poe-text" markdown="1">

## Parent-of-Origin Effects on Obesity

### Skills Demonstrated

*R · Visualization · Statistical Genetics · QTL Analysis (mQTL, vQTL, eQTL) · Parent-of-origin Analysis · Genotype QC and Imputation Filtering · LD and Haplotype Block Analysis (PLINK) · Multi-omics Integration (GTEx) · Large Cohort Data (FHS)*

---

### Overview

The FTO gene is the most significant and widely replicated obesity finding from genome-wide association studies (GWAS). Its obesity-associated variants sit in non-coding regions (introns 1–3) and act as regulators, changing the expression of the neighboring genes IRX3 and IRX5 and shifting how fat cells store or burn energy. Earlier studies in humans and mice suggest that some of these effects depend on parental origin, known as parent-of-origin effects (POE): a variant inherited from the mother can act differently than the same variant inherited from the father. However, previous work examined only a handful of variants, focused almost entirely on BMI, was rarely replicated across cohorts, and only evaluated whether variants shift the mean. Variance effects, which describe the spread of a trait's distribution, remain understudied, yet they are important for understanding why people with the same variant can have different outcomes.

In this project, I systematically tested POE across FTO introns 1–3 using data from the Framingham Heart Study (FHS), where available parental genotypes allow each allele to be traced to the mother or the father. After quality control filtering, 398 SNPs grouped into 38 haplotype blocks were tested in 4,403 individuals for both mean (mQTL) and variance (vQTL) effects, comparing maternally and paternally inherited alleles. The analysis was then extended beyond BMI to five more obesity traits that capture body fatness and fat distribution. Blood expression of FTO, IRX3, and IRX5 was also examined to see whether these SNPs affect gene expression (eQTL) and whether that effect differs by parental origin (POE eQTL), followed by a GTEx lookup of tissue-specific eQTLs for comparison.

Preliminary results suggest that most variants with parent-of-origin signals have stronger maternal effects on both the mean and the variance of obesity traits. They partially replicate findings from the Sorbs and German Trios cohorts and point to a candidate region where BMI, blood expression, and skeletal muscle expression signals overlap. These findings indicate that parental origin is an often-overlooked layer of genetic influence on obesity, one that may contribute to the missing heritability of complex traits.

</div>

<div class="poe-figs">
  <figure class="poe-fig">
    <img src="{{ '/images/poe_workflow.png' | relative_url }}" alt="POE analysis workflow">
    <figcaption>Figure 1. Analysis workflow: 398 FTO SNPs across 38 haplotype blocks, tested for mean and variance effects on obesity for parent-of-origin effects, blood eQTLs (FTO, IRX3, IRX5), and tissue-specific GTEx eQTLs.</figcaption>
  </figure>

  <figure class="poe-fig">
    <img src="{{ '/images/fto_integrated_heatmap.png' | relative_url }}" alt="Integrated association heatmap">
    <figcaption>Figure 2. Integrated view of association signals across FTO haplotype blocks, combining mean and variance effects on obesity traits, parent-of-origin effects, blood gene expression, and tissue-specific expression from GTEx.</figcaption>
  </figure>
</div>

</div>

<div class="fig-zoom" id="fig-zoom"><img alt=""></div>

<script>
(function () {
  var zoom = document.getElementById('fig-zoom'), zimg = zoom.querySelector('img');
  document.querySelectorAll('.poe-fig img').forEach(function (img) {
    img.addEventListener('click', function () { zimg.src = img.src; zoom.classList.add('open'); });
  });
  zoom.addEventListener('click', function () { zoom.classList.remove('open'); });
  document.addEventListener('keydown', function (e) { if (e.key === 'Escape') zoom.classList.remove('open'); });
})();
</script>

[← Back to Genomic Research]({{ "/genomics/" | relative_url }})

<!-- After publication: add the paper link here, and replace demo figures with real results. -->
