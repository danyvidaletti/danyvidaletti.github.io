---
title: "Two Brazils Inside One"
date: 2026-05-15
draft: false
summary: "Brazil's national HDI of 0.660 looks balanced. What does that one number actually hide?"
tags: ["Python", "EDA", "Regression", "Public Data", "Storytelling"]
---

<section class="scene reveal">
  <p class="scene-q">The question</p>
  <h2 class="scene-a">How unequal is human development across Brazil's 5,564 municipalities?</h2>
  <div class="stat-tile">
    <p class="stat-num">0.660</p>
    <p class="stat-label">National HDI for Brazil in 2010. Looks balanced. It isn't.</p>
  </div>
</section>

<section class="scene reveal">
  <p class="scene-q">What does the average hide?</p>
  <h2 class="scene-a">A 0.444-point gap, the distance between a developing and a developed nation. Inside one country.</h2>
  <img src="/projects/hdi-brazil-2010/01-distribution.png" alt="Distribution of MHDI across 5,564 Brazilian municipalities">
  <p class="scene-note">The lowest municipality scores 0.418 (UN <em>Low</em>). The highest, 0.862 (<em>Very High</em>). Mean and median match, but only because the distribution is centred. Equality and symmetry are not the same thing.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Where does the gap live?</p>
  <h2 class="scene-a">Three regions above the national mean. Two clearly below.</h2>
  <img src="/projects/hdi-brazil-2010/02-regions.png" alt="Mean Municipal HDI by Brazilian macro-region, with internal range">
  <p class="scene-note">The Northeast has the lowest mean <em>and</em> the widest internal spread. Profoundly unequal, with islands of high development scattered through it.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">What actually drives it?</p>
  <h2 class="scene-a">Education explains 67% of the variation in municipal income.</h2>
  <img src="/projects/hdi-brazil-2010/03-education-income.png" alt="Education vs Income scatter with linear regression">
  <p class="scene-note">Longevity is the weakest driver: federal health policy (SUS, vaccination) reaches everywhere, so life expectancy is roughly equalised. Education is not. It depends on local infrastructure, and that is where the gap reproduces itself across generations.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Who is left behind?</p>
  <h2 class="scene-a">32 Low-HDI municipalities. Every single one in the North or Northeast.</h2>
  <img src="/projects/hdi-brazil-2010/04-low-hdi.png" alt="All 32 Low-HDI municipalities sit in the North or Northeast">
</section>

<section class="scene reveal">
  <p class="scene-q">Why those 32?</p>
  <h2 class="scene-a">Longevity remains strong. Education falls behind.</h2>
  <img src="/projects/hdi-brazil-2010/05-pillars.png" alt="Pillar comparison: national mean vs Low-HDI municipalities">
  <p class="scene-note">In every one of the 32 lowest cities, education is the weakest pillar. Without exception.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">So what?</p>
  <h2 class="scene-a">Three takeaways for anyone using this number to make decisions.</h2>
  <ol class="takeaways">
    <li>
      <p class="tk-num">01</p>
      <p class="tk-text">The national average hides everything. Programmes designed for the "average" Brazilian municipality fit almost none of them.</p>
    </li>
    <li>
      <p class="tk-num">02</p>
      <p class="tk-text">Education is the lever. It explains two thirds of the variation in income and collapses fastest where development is lowest.</p>
    </li>
    <li>
      <p class="tk-num">03</p>
      <p class="tk-text">The geography of deprivation is fixed. Every Low-HDI city is in the North or Northeast. A structural pattern, not noise.</p>
    </li>
  </ol>
</section>

<aside class="deep-dive reveal">
  <h2>Deep dive</h2>

  <h3>Data & method</h3>
  <ul>
    <li><strong>Source:</strong> Atlas of Human Development in Brazil (UNDP · IPEA · FJP), built on the 2010 IBGE Demographic Census.</li>
    <li><strong>Coverage:</strong> 5,564 municipalities × 237 indicators.</li>
    <li><strong>Stack:</strong> Python (pandas, scikit-learn, matplotlib), reproducible Jupyter workflow.</li>
    <li><strong>Pipeline:</strong> column standardisation → state-to-region mapping (27 → 5) → descriptive stats → distribution → correlation → linear regression (Education → Income).</li>
  </ul>

  <h3>Honest limitations</h3>
  <ul>
    <li>Cross-sectional, not longitudinal: a 2010 snapshot, not a trajectory.</li>
    <li>Pre-pandemic, pre-political-shift: the decade that followed reshaped much of the picture.</li>
    <li>Only three indicators: MHDI excludes environmental dimensions like deforestation or carbon emissions.</li>
  </ul>

  <h3>Next steps</h3>
  <ul>
    <li>Replicate with the 2022 Census to measure change over a decade.</li>
    <li>Add environmental indicators for a modern, multi-dimensional view.</li>
    <li>Choropleth maps for sharper geographic storytelling.</li>
  </ul>

  <p style="margin-top:24px;"><em>Completed as part of the Diploma in Data Analytics at Atlantic Technological University.</em></p>
</aside>
