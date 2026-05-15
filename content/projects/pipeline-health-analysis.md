---
title: "Pipeline Health Analysis"
date: 2026-05-15
draft: false
summary: "How clean CRM data and a single executive dashboard surfaced the three deal-stage bottlenecks slowing a regional sales team."
tags: ["SQL", "Tableau", "Salesforce", "Sales Ops"]
---

> *Featured case study — illustrative example demonstrating the kind of analysis I run day-to-day. Specific numbers are representative, not from a confidential engagement.*

## The question

A regional sales team was missing quarterly targets. Leadership suspected the issue was rep performance — but the data told a different story. The real question was:

> **Where exactly do our deals lose momentum, and what does it cost us?**

## The data

- **Source:** Salesforce opportunity records over four quarters, plus activity logs (calls, emails, meetings).
- **Volume:** ~12k opportunities, ~180k activity events.
- **Data quality issues:** Inconsistent stage-progression timestamps, ~9% of opportunities missing close-date updates, free-text fields used inconsistently for product lines.

The first week was data cleansing: standardising stage transitions, reconciling closed-won/closed-lost timestamps, and building a clean lookup for product categorisation.

## The approach

1. **Cohort by quarter and segment** — so apparent trends weren't confounded by seasonality or product mix.
2. **Stage-duration analysis** — calculating average and median time-in-stage per cohort, with outlier handling for stalled deals.
3. **Conversion-rate funnel** — measuring stage-to-stage conversion, isolating where the funnel actually narrows.
4. **Activity correlation** — joining opportunity timelines with activity logs to test whether outreach intensity correlated with progression speed.

All in SQL for reproducibility, surfaced in a Tableau dashboard tuned for a 15-minute leadership review.

## The answer

Three bottlenecks accounted for **78% of pipeline slippage**:

1. **Discovery → Proposal** took 2.4× longer than benchmark for one product line — driven by missing pricing-approval workflow, not rep behaviour.
2. **Proposal → Negotiation** showed a 31% conversion drop in one segment, traceable to a competitor's incentive programme that hadn't been escalated.
3. **Negotiation → Close** was healthy on average but masked a 14-day tail of deals stuck waiting on procurement docs from prospect side — a process gap, not a sales gap.

The dashboard let leadership see all three at once, sorted by revenue impact.

## What changed

- Pricing-approval SLA tightened from 5 days to 48 hours.
- Competitive-intelligence loop added to weekly Sales Ops sync.
- Procurement-docs checklist embedded into the late-stage workflow.

By the next quarter, the bottlenecks reflected in stage-duration metrics had narrowed by roughly half.

## What I'd do next

- **Predictive stalling signal** — train a simple model on stage-duration + activity patterns to flag at-risk deals 2 weeks earlier.
- **Pipeline-quality scoring** — extend the dashboard with a single rep-level health score combining stage discipline, data completeness, and activity intensity.
- **Self-service exploration** — turn the static dashboard into a parameterised view so RVPs can drill in without needing analyst support.
