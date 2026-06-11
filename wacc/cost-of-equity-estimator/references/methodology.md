# Methodology

## Historical Beta

- Estimate raw beta from return regression.
- Report the standard error of the beta estimate.
- Historical cost of equity:

```text
Ke_historical = Rf + beta_historical * ERP
```

## Bottom-Up Beta

- Unlever peer betas using reviewed operating leverage.
- Aggregate peer unlevered beta using the approved method, typically median.
- Relever to the focal company's approved operating leverage.

```text
beta_unlevered = beta_levered / (1 + (1 - t) * D/E)
beta_bottom_up = beta_unlevered_peer * (1 + (1 - t) * D/E_focal)
```

- Bottom-up cost of equity:

```text
Ke_bottom_up = Rf + beta_bottom_up * ERP
```

## Leverage Views

Always distinguish:

- total debt leverage
- operating-only leverage

If those differ materially, force user review before finalization.

## Dashboard

The dashboard must show:

- historical beta
- historical beta standard error
- historical cost of equity
- peer median unlevered beta
- bottom-up relevered beta
- bottom-up cost of equity
- leverage comparison across peers
