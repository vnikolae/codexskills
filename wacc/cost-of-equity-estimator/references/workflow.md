# Workflow

## Prepare

Run:

```powershell
python prepare_equity_review.py --config <config.json>
```

This writes:

```text
../outputs-waac/<ticker>/equity_review.json
```

The packet must include:

- focal company
- proposed peers
- total debt
- proposed operating debt
- debt/equity ratios under both views
- peer inclusion flags
- questions for the user

## User Confirmation

Do not finalize until:

```json
"approval": {
  "user_confirmed": true
}
```

is set in `equity_review.json`.

## Finalize

Run:

```powershell
python finalize_cost_of_equity.py <ticker>
```

This should:

- run the beta pipeline with approved leverage treatment
- generate the dashboard
- write `cost_of_equity_<ticker>.md`

## Review Standard

The final answer should state:

- approved peer set
- leverage treatment used
- historical beta and standard error
- bottom-up beta
- historical and bottom-up costs of equity
