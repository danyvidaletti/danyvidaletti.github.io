---
title: "Catching Detractors Before They Speak"
date: 2026-05-15
draft: false
summary: "An e-commerce dataset of 2,500 customers. One question: can we predict who will become a detractor before the NPS survey is even sent?"
tags: ["Python", "Random Forest", "Classification", "EDA", "Storytelling"]
---

<section class="scene reveal">
  <p class="scene-q">The question</p>
  <h2 class="scene-a">Can we predict who will become a detractor before the survey is even sent?</h2>
  <div class="stat-tile">
    <p class="stat-num">2,500</p>
    <p class="stat-label">E-commerce customers across 19 behavioural and operational signals. One target: will this customer give us an NPS score of 6 or lower?</p>
  </div>
</section>

<section class="scene reveal">
  <p class="scene-q">What does the data look like?</p>
  <h2 class="scene-a">Most customers are detractors. The middle of the scale is almost empty.</h2>
  <img src="/projects/nps-predictive/01-distribution.png" alt="Distribution of NPS scores by band">
  <p class="scene-note">Customers either love the experience or hate it. The "passive" middle is the smallest of the three groups, which means polarising operational issues are doing most of the work.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">What kills NPS?</p>
  <h2 class="scene-a">Delivery delay is the single strongest negative driver. Complaints come next.</h2>
  <img src="/projects/nps-predictive/02-drivers.png" alt="Top negative and positive correlations with NPS">
  <p class="scene-note">Five operational red flags pull NPS down (delivery delay, complaints, service contacts, resolution time, delivery attempts). Five behavioural signals lift it back up (repeat purchase, internal CSAT, order value, tenure, age).</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Is there a breaking point?</p>
  <h2 class="scene-a">Above 3 days late, customers tip into detractor territory.</h2>
  <img src="/projects/nps-predictive/03-breaking-point.png" alt="Detractor rate as a function of delivery delay in days">
  <p class="scene-note">The relationship is not linear. There is a clean threshold. Operationally that translates into one number: a strict 3-day SLA on delivery delay.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">What rescues NPS?</p>
  <h2 class="scene-a">Loyalty signals are visible long before the survey arrives.</h2>
  <img src="/projects/nps-predictive/04-positive-signals.png" alt="Repeat-purchase rate and internal CSAT by NPS band">
  <p class="scene-note">Promoters repurchase within 30 days at a much higher rate, and their internal CSAT is roughly double that of detractors. Both signals are observable before any survey is sent.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Can we predict it?</p>
  <h2 class="scene-a">A Random Forest classifier separates detractors with AUC 0.88.</h2>
  <img src="/projects/nps-predictive/05-roc.png" alt="ROC curve for the Random Forest classifier">
  <div class="stat-tile" style="margin-top:36px;">
    <p class="stat-num">87%</p>
    <p class="stat-label">Test-set accuracy on a held-out 25%. AUC 0.88. Enough to act on, weeks before the next NPS pulse.</p>
  </div>
</section>

<section class="scene reveal">
  <p class="scene-q">What does the model actually look at?</p>
  <h2 class="scene-a">Complaints, delivery delay, and order value lead the feature importance.</h2>
  <img src="/projects/nps-predictive/06-feature-importance.png" alt="Top 10 features ranked by Random Forest importance">
  <p class="scene-note">The model agrees with the correlation analysis: the strongest predictors are operational, not demographic. Which means the levers to pull are operational too.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">So what?</p>
  <h2 class="scene-a">Three things the business can do tomorrow.</h2>
  <ol class="takeaways">
    <li>
      <p class="tk-num">01</p>
      <p class="tk-text">Treat a 3-day delivery delay as a hard SLA. Past that point, customers become detractors at a rate close to 9 in 10.</p>
    </li>
    <li>
      <p class="tk-num">02</p>
      <p class="tk-text">Escalate proactively on complaints. Each additional complaint moves the customer measurably toward detraction.</p>
    </li>
    <li>
      <p class="tk-num">03</p>
      <p class="tk-text">Use the model to flag at-risk customers between surveys, so retention actions land before damage is locked in.</p>
    </li>
  </ol>
</section>

<aside class="deep-dive reveal">
  <h2>Deep dive</h2>

  <h3>Data & method</h3>
  <ul>
    <li><strong>Source:</strong> Tech Challenge Phase 1 dataset, FIAP postgrad in AI Scientist.</li>
    <li><strong>Coverage:</strong> 2,500 e-commerce customers × 19 features (operational, behavioural, demographic).</li>
    <li><strong>Target:</strong> binary classification — detractor (NPS ≤ 6) vs non-detractor.</li>
    <li><strong>Stack:</strong> Python (pandas, scikit-learn, matplotlib).</li>
    <li><strong>Pipeline:</strong> EDA → correlation analysis → train/test split (75/25, stratified) → Random Forest (300 trees) → evaluation on ROC AUC and accuracy.</li>
  </ul>

  <h3>Honest limitations</h3>
  <ul>
    <li>Synthetic teaching dataset: patterns are cleaner than they would be in production.</li>
    <li>Cross-sectional snapshot, no time component — no way to model how the same customer evolves.</li>
    <li>No causal claim. Correlations and feature importance suggest leverage points; A/B tests would confirm them.</li>
  </ul>

  <h3>Next steps</h3>
  <ul>
    <li>Re-run on a larger, real-world dataset to test generalisation.</li>
    <li>Add a probability threshold sweep to tune precision/recall for the actual cost of false alarms.</li>
    <li>Explore a gradient-boosted alternative (XGBoost / LightGBM) for comparison.</li>
  </ul>

  <p style="margin-top:24px;"><em>Group project completed as part of the Postgraduate Diploma in Machine Learning and AI at FIAP.</em></p>
</aside>
