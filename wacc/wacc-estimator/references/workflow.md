# Workflow

## Prerequisites

Require:

- `../outputs-waac/<ticker>/cost_of_debt_<ticker>.md`
- `../outputs-waac/<ticker>/cost_of_equity_<ticker>.md`
- `../outputs-waac/<ticker>/beta_summary.json`

If any are missing, stop and say which artifacts are missing.

## Run

```powershell
python compute_wacc.py <ticker>
```

## Output

Write:

```text
../outputs-waac/<ticker>/wacc_<ticker>.md
```
