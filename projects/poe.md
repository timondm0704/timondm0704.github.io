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

  /* OPTIONAL: hide the sidebar entirely on this page for presenting.
     Remove the comment markers around this block to turn it on. */
  /*
  @media (min-width: 961px) {
    header, footer { display: none; }
    section { width: 100%; }
  }
  */

  .poe-layout {
    display: grid;
    grid-template-columns: minmax(0, 1.3fr) minmax(0, 1fr);
    gap: 2rem;
    align-items: start;
  }
  .poe-text { min-width: 0; }
  .poe-figs {
    position: sticky;
    top: 1rem;
    max-height: calc(100vh - 2rem);
    display: flex;
    flex-direction: column;
  }
  .fig-tabs { display: flex; gap: .5rem; margin-bottom: .6rem; }
  .fig-tabs button {
    padding: .35rem .9rem; border: 1px solid #999; border-radius: 6px;
    background: transparent; color: inherit; cursor: pointer; font-size: .9rem;
  }
  .fig-tabs button.active { background: #2b6cb0; border-color: #2b6cb0; color: #fff; }
  .poe-fig { display: none; margin: 0; }
  .poe-fig.active { display: block; }
  .poe-fig img {
    width: 100%; max-height: calc(100vh - 9rem); object-fit: contain; cursor: zoom-in;
  }
  .poe-fig figcaption { font-size: .85rem; font-style: italic; margin-top: .4rem; }
  .fig-ref { cursor: pointer; text-decoration: underline dotted; }

  /* Click-to-enlarge overlay */
  .fig-zoom {
    display: none; position: fixed; inset: 0; z-index: 1000;
    background: rgba(0,0,0,.88); align-items: center; justify-content: center; cursor: zoom-out;
  }
  .fig-zoom.open { display: flex; }
  .fig-zoom img { max-width: 96vw; max-height: 94vh; background: #fff; }

  /* Small screens: match Minimal's 960px breakpoint and stack normally */
  @media (max-width: 960px) {
    .poe-layout { display: block; }
    .poe-figs { position: static; max-height: none; }
    .fig-tabs { display: none; }
    .poe-fig { display: block; margin-bottom: 1.5rem; }
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

<div data-fig="1" markdown="1">

In this project, I systematically tested POE across FTO introns 1–3 using data from the Framingham Heart Study (FHS), where available parental genotypes allow each allele to be traced to the mother or the father. After quality control filtering, 398 SNPs grouped into 38 haplotype blocks were tested in 4,403 individuals for both mean (mQTL) and variance (vQTL) effects, comparing maternally and paternally inherited alleles. The analysis was then extended beyond BMI to five more obesity traits that capture body fatness and fat distribution. Blood expression of FTO, IRX3, and IRX5 was also examined to see whether these SNPs affect gene expression (eQTL) and whether that effect differs by parental origin (POE eQTL), followed by a GTEx lookup of tissue-specific eQTLs for comparison. <span class="fig-ref" data-show="1">(Figure 1)</span>

</div>

<div data-fig="2" markdown="1">

Preliminary results suggest that most variants with parent-of-origin signals have stronger maternal effects on both the mean and the variance of obesity traits. They partially replicate findings from the Sorbs and German Trios cohorts and point to a candidate region where BMI, blood expression, and skeletal muscle expression signals overlap. These findings indicate that parental origin is an often-overlooked layer of genetic influence on obesity, one that may contribute to the missing heritability of complex traits. <span class="fig-ref" data-show="2">(Figure 2)</span>

</div>

</div>

<div class="poe-figs">
  <div class="fig-tabs">
    <button class="active" data-show="1">Figure 1</button>
    <button data-show="2">Figure 2</button>
  </div>

  <figure class="poe-fig active" id="fig-1">
    <img src="{{ '/images/poe_workflow.png' | relative_url }}" alt="POE analysis workflow">
    <figcaption>Figure 1. Analysis workflow: 398 FTO SNPs across 38 haplotype blocks, tested for mean and variance effects on obesity for parent-of-origin effects, blood eQTLs (FTO, IRX3, IRX5), and tissue-specific GTEx eQTLs.</figcaption>
  </figure>

  <figure class="poe-fig" id="fig-2">
    <img src="{{ '/images/fto_integrated_heatmap.png' | relative_url }}" alt="Integrated association heatmap">
    <figcaption>Figure 2. Integrated view of association signals across FTO haplotype blocks, combining mean and variance effects on obesity traits, parent-of-origin effects, blood gene expression, and tissue-specific expression from GTEx.</figcaption>
  </figure>
</div>

</div>

<div class="fig-zoom" id="fig-zoom"><img alt=""></div>

<script>
(function () {
  var tabs = document.querySelectorAll('.fig-tabs button');
  function show(n) {
    document.querySelectorAll('.poe-fig').forEach(function (f) {
      f.classList.toggle('active', f.id === 'fig-' + n);
    });
    tabs.forEach(function (b) { b.classList.toggle('active', b.dataset.show === String(n)); });
  }
  document.querySelectorAll('[data-show]').forEach(function (el) {
    el.addEventListener('click', function () { show(el.dataset.show); });
  });
  if ('IntersectionObserver' in window) {
    var obs = new IntersectionObserver(function (entries) {
      entries.forEach(function (e) { if (e.isIntersecting) show(e.target.dataset.fig); });
    }, { rootMargin: '-40% 0px -40% 0px' });
    document.querySelectorAll('[data-fig]').forEach(function (s) { obs.observe(s); });
  }
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
