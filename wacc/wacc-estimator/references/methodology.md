# Methodology

## Inputs

- after-tax cost of debt from the debt report
- historical cost of equity from the equity report / beta summary
- bottom-up cost of equity from the equity report / beta summary
- market-value capital weights from the approved equity workflow

## WACC Variants

Historical-beta WACC:

```text
WACC_historical = Ke_historical * E/(D+E) + Kd_after_tax * D/(D+E)
```

Bottom-up-beta WACC:

```text
WACC_bottom_up = Ke_bottom_up * E/(D+E) + Kd_after_tax * D/(D+E)
```

## Reporting

Always report:

- both WACC variants
- the historical beta standard error
- the debt and equity weights
- the paths to the source reports
