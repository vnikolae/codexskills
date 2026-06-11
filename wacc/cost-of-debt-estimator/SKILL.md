---
name: "cost-of-debt-estimator"
description: "Estimate pre-tax and after-tax cost of debt for a public company using current market bond yields, agency/rating-based spreads, and synthetic-rating methods. Use when Codex needs to calculate cost of debt for WACC or valuation work, compare at least two methods, document sources and assumptions, or save a debt-cost methodology report in the project folder."
---

# Cost Of Debt Estimator

## Overview

Use this skill first in the cost-of-capital workflow. Produce a defendable cost-of-debt estimate with at least two methods and a saved report. Favor current market yields when reliable bond data exists; otherwise use rating-based or synthetic-rating methods as structured fallbacks.

Read [references/methodology.md](references/methodology.md) before estimating debt cost. Read [references/report-template.md](references/report-template.md) when drafting the saved report.

## Workflow

1. Identify the focal company and confirm currency and market.
2. Attempt a market-yield estimate first:
   - find currently traded straight debt
   - collect representative bond yields or a weighted-average yield
   - avoid using coupons as a substitute for current yields
3. Independently estimate debt cost using at least one additional method:
   - agency/rating-based spread method, or
   - synthetic rating from interest coverage
4. If possible, calculate all three:
   - market yield
   - rating-based
   - synthetic rating
5. Convert each pre-tax cost of debt to after-tax cost of debt using the statutory tax rate.
6. Compare methods and recommend one primary estimate.
7. Save a markdown report in the project folder with methodology, sources, calculations, and verification notes.

## Required Methods

- Always compute at least two methods.
- Prefer one of them to be market yield when live bond data is available.
- If market-yield data is weak or fragmentary, say so explicitly and rely more heavily on rating-based or synthetic estimates.
- Use statutory tax rates for after-tax conversion unless the user directs otherwise.

## Method Rules

- Market-yield method:
  - use current YTM or yield-to-worst from representative straight debt
  - prefer a weighted average across material issues when practical
  - if using one representative issue, explain why it was chosen
- Rating-based method:
  - use a current risk-free rate plus a spread for the issuer's actual rating bucket
  - cite the rating and the spread source/date
- Synthetic-rating method:
  - compute interest coverage from EBIT and interest expense
  - map coverage to a synthetic rating and default spread
  - use a current risk-free rate plus that spread
- Always distinguish:
  - pre-tax cost of debt
  - after-tax cost of debt

## Source Hierarchy

- Bond yields:
  - prefer primary market-data sources or direct bond-market sources first
  - use aggregator pages such as TradingView only as secondary or fallback sources
- Ratings:
  - prefer primary rating-agency releases or company filings
  - use secondary news summaries only when primary sources are unavailable, and label them as fallback
- Financial inputs:
  - prefer SEC filings for EBIT, operating income, interest expense, and debt disclosures
  - use normalized API data only as a cross-check or convenience fallback
- Risk-free rate:
  - use a clearly named current Treasury source and state the date
- Synthetic spread tables:
  - use a named source such as Damodaran and state the table date

## Precision Rules

- Match output precision to source quality.
- If a method depends on:
  - stale sources
  - secondary summaries
  - approximate bucket mapping
  - thin bond trading
  then present the result as approximate, for example `~5.6%` or a range, not as an overly precise point estimate.
- If the exact rating bucket is unavailable in the chosen spread table:
  - state the nearest bucket used
  - state whether that likely biases the estimate up or down
  - prefer a range or explicitly approximate wording
- Do not present a fallback-source estimate as a definitive current market fact.

## Verification

- Cross-check that the market-yield estimate and spread-based estimate are directionally consistent.
- If they differ materially, explain likely reasons:
  - maturity mix
  - stale quotes
  - unusual capital structure
  - tiny interest expense distorting synthetic coverage
- Verify that the source date and exact instrument/rating are stated.
- Prefer primary or near-primary sources where available.
- Explicitly confirm:
  - bond yield vs coupon distinction
  - rating date and rating source quality
  - EBIT vs operating income distinction in the synthetic method
  - tax-rate source
  - why the recommended method is preferred over the alternatives

## Output

- Save a report in the active project folder, not in the skill folder.
- Default filename:
  - `cost_of_debt_<ticker>.md`
- The report must include:
  - company name and ticker
  - analysis date
  - tax rate used
  - each method with inputs and formula
  - sources with links
  - verification notes
  - recommended pre-tax and after-tax cost of debt
  - source-quality notes when any method relies on secondary or fallback data
  - a short limitations note when source quality or precision is weak
