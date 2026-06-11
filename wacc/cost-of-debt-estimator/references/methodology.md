# Methodology

## Market-Yield Method

Use current bond yield data from traded straight debt.

Preferred process:

1. Identify major outstanding bonds.
2. Collect current yield to maturity or yield to worst.
3. Use either:
   - a weighted average across material issues, or
   - a representative intermediate/long-term issue
4. State whether the estimate is point-based or weighted.

Source preference:

1. Primary bond-market platforms / institutional feeds
2. Direct market-trade sources
3. Aggregators such as TradingView or bond websites as fallback

If the bonds are thinly traded or odd-lot heavy, say so and avoid false precision.

Formula:

```text
Pre-tax Kd = current bond yield
After-tax Kd = current bond yield * (1 - tax rate)
```

## Rating-Based Method

Use:

```text
Pre-tax Kd = risk-free rate + rating spread
After-tax Kd = Pre-tax Kd * (1 - tax rate)
```

Requirements:

- cite the actual issuer rating
- cite the spread table or spread source
- cite the risk-free-rate source/date
- identify whether the rating source is primary, secondary, or fallback
- if the exact rating bucket is unavailable in the spread table, explain the approximation and its likely direction of bias

## Synthetic-Rating Method

Compute interest coverage:

```text
Interest coverage = EBIT / Interest expense
```

Then map coverage to a synthetic rating and spread using a table such as Damodaran's ratings/coverage table.

Then:

```text
Pre-tax Kd = risk-free rate + synthetic spread
After-tax Kd = Pre-tax Kd * (1 - tax rate)
```

Be explicit about whether the numerator is:

- EBIT, or
- operating income

Do not label operating income as EBIT.

## Recommendation Logic

- Use market yield as primary if the debt trades actively and the yield data is current.
- Use rating-based as a cross-check when the issuer has an actual rating.
- Use synthetic rating as fallback or triangulation when bond-yield data is thin.
- If the methods cluster tightly, recommend a midpoint or the market-yield figure.
- If the methods diverge, explain why and choose the method with the strongest data quality.

## Verification Checklist

- Confirm bond yield is current YTM / yield-to-worst, not coupon.
- Confirm the exact bond issue(s) used and their dates/maturities.
- Confirm the rating date and source.
- Confirm the spread-table date.
- Confirm the risk-free-rate date.
- Confirm EBIT vs operating income labeling.
- If any method is approximate, present the result as approximate.
