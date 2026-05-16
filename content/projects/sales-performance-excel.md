---
title: "Decoding a Year of Sales"
date: 2026-05-15
draft: false
summary: "17,154 closed-won deals, six business questions, one Excel workbook. A Sales Operations dashboard that turns a year of bookings into a 30-second read."
tags: ["Excel", "Sales Operations", "Dashboards", "Pivot Tables", "Formulas"]
---

<section class="scene reveal">
  <p class="scene-q">The question</p>
  <h2 class="scene-a">Can leadership read a full year of sales in 30 seconds?</h2>
  <div class="stat-tile">
    <p class="stat-num" style="font-size:clamp(2.4rem,5.5vw,4rem);">$294.6M</p>
    <p class="stat-label">Closed-won bookings across 17,154 opportunities, 40 sales teams, and 4 regions, in FY 2017. The dashboard answers six business questions on one page.</p>
  </div>
  <p class="scene-note" style="margin-top:32px;">
    <a href="/projects/sales-performance-excel/Sales-Performance-Dashboard.xlsx" download style="display:inline-block;background:#2f4f3e;color:#faf7f2;text-decoration:none;padding:12px 22px;border-radius:8px;font-weight:600;">Download the workbook (.xlsx)</a>
  </p>
</section>

<section class="scene reveal">
  <p class="scene-q">Where does the money come from?</p>
  <h2 class="scene-a">The US generates over half of global bookings.</h2>
  <img src="/projects/sales-performance-excel/01-revenue-by-region.png" alt="Revenue by region">
  <p class="scene-note">Four regions, but the distribution is heavily skewed. The US carries the year; EMEA and APAC together roughly equal it; CAN is a small fraction.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">When does the money land?</p>
  <h2 class="scene-a">Q4 closes roughly three times the revenue of Q1.</h2>
  <img src="/projects/sales-performance-excel/02-quarterly.png" alt="Bookings by quarter">
  <p class="scene-note">The year is heavily back-loaded, classic enterprise SaaS pattern: renewals concentrate at fiscal-year end and pull the bookings curve sharply upward in Q4.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Where is revenue concentrated?</p>
  <h2 class="scene-a">Most of the heat lives in two cells: US Q4 and EMEA Q4.</h2>
  <img src="/projects/sales-performance-excel/03-region-quarter.png" alt="Region by quarter heatmap">
  <p class="scene-note">A 20-cell matrix tells the whole story. Two cells, US Q4 and EMEA Q4, together account for a disproportionate share of the year.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">What is the business actually selling?</p>
  <h2 class="scene-a">Renewals carry the year. New business is a smaller, faster-growing layer.</h2>
  <img src="/projects/sales-performance-excel/04-deal-type.png" alt="Deal type mix">
  <p class="scene-note">Eleven deal types collapse into two stories: a large renewal base that funds the year and a smaller new-business engine that defines next year's trajectory.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">Who wins the year?</p>
  <h2 class="scene-a">The top 10 teams produce a disproportionate share of bookings.</h2>
  <img src="/projects/sales-performance-excel/05-top-teams.png" alt="Top 10 teams by revenue">
  <p class="scene-note">A familiar Pareto: 25% of the teams generate more than 70% of revenue. The SMB engine in the US leads.</p>
</section>

<section class="scene reveal">
  <p class="scene-q">What if we move one lever?</p>
  <h2 class="scene-a">Adding $52k to every US West-SAE deal lifts global revenue by 9.07%.</h2>
  <div class="stat-tile">
    <p class="stat-num">+9.07%</p>
    <p class="stat-label">514 deals × $52,000 = $26.7M of uplift on a $294.6M base. The scenario is computed in the workbook with a single conditional formula — the Sales Ops version of "what does this cost / save us?"</p>
  </div>
</section>

<section class="scene reveal">
  <p class="scene-q">So what?</p>
  <h2 class="scene-a">Three things this dashboard surfaces in 30 seconds.</h2>
  <ol class="takeaways">
    <li>
      <p class="tk-num">01</p>
      <p class="tk-text">Geographic concentration is real. Forecast risk in the US matters far more than risk anywhere else.</p>
    </li>
    <li>
      <p class="tk-num">02</p>
      <p class="tk-text">Seasonality is severe. Q4 dependency means a missed quarter cannot be recovered the same year.</p>
    </li>
    <li>
      <p class="tk-num">03</p>
      <p class="tk-text">Renewals are the floor, new business is the ceiling. Two very different stories to manage with very different tools.</p>
    </li>
  </ol>
</section>

<aside class="deep-dive reveal">
  <h2>Deep dive</h2>

  <h3>Workbook structure</h3>
  <ul>
    <li><strong>Dashboard</strong> — KPI tiles, revenue-by-region bar chart, quarterly trend line, deal-type doughnut, top-10 teams table with banded rows.</li>
    <li><strong>Analysis</strong> — the six classic Sales Ops test questions, each answered with a single formula (MAXIFS, SUMIFS, AVERAGEIFS, conditional COUNTIFS).</li>
    <li><strong>Region × Quarter</strong> — pivot matrix with a colour scale showing where heat concentrates.</li>
    <li><strong>Team Performance</strong> — ranked table with a data bar on the revenue column.</li>
    <li><strong>Raw Data</strong> — the original 17,154-row dataset, enriched with parsed Close Date, Month, Quarter, and Geo Region columns.</li>
    <li><strong>Geo Map</strong> — Team → Geo Region lookup, the join key for everything else.</li>
  </ul>

  <h3>Techniques used</h3>
  <ul>
    <li>VLOOKUP-style joins between Team and Geo Region (replaced by a clean merge column in Raw Data).</li>
    <li>SUMIFS, MAXIFS, AVERAGEIFS, COUNTIFS for conditional aggregations.</li>
    <li>SUMPRODUCT with COUNTIF for distinct count.</li>
    <li>Pivot tables for region × quarter matrices and team rankings.</li>
    <li>Conditional formatting: colour scales and data bars to make heat readable at a glance.</li>
    <li>Native Excel charts (bar, line, doughnut) bound to the underlying tables, so any data refresh flows through.</li>
  </ul>

  <h3>Dataset</h3>
  <ul>
    <li><strong>Source:</strong> LinkedIn Sales Operations technical assessment dataset.</li>
    <li><strong>Scope:</strong> 17,154 closed-won opportunities, FY 2017, 40 sales teams, 4 regions, 11 deal types.</li>
    <li><strong>Note:</strong> data is anonymised; account and opportunity names are placeholders.</li>
  </ul>
</aside>
