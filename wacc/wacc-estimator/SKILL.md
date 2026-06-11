---
name: "wacc-estimator"
description: "Compute WACC for a public company using completed cost-of-debt and cost-of-equity outputs. Use when Codex needs to: (1) verify whether debt and equity reports already exist, (2) instruct the user to run missing prerequisite skills, or (3) compute and save WACC using both historical-beta and peer bottom-up-beta versions of cost of equity."
---

# WACC Estimator

## Overview

Use this skill after the cost-of-debt and cost-of-equity steps are complete. The WACC step should use their saved reports rather than redoing the upstream work unless those reports are missing.

Read [references/workflow.md](references/workflow.md) for the dependency logic and [references/methodology.md](references/methodology.md) for the exact WACC calculations.

## Workflow

1. Check whether these prerequisites exist:
   - `../outputs-waac/<ticker>/cost_of_debt_<ticker>.md`
   - `../outputs-waac/<ticker>/cost_of_equity_<ticker>.md`
   - `../outputs-waac/<ticker>/beta_summary.json`
2. If prerequisites are missing, stop and instruct the user to run the missing skills first.
3. If prerequisites exist, run `compute_wacc.py`.
4. Save a WACC report that includes:
   - WACC using historical beta
   - WACC using peer bottom-up beta
   - the historical beta standard error for context

## Operating Rules

- Do not recompute debt or equity silently if their reports are missing.
- Use the saved approved reports as the source of truth.
- Present both WACC variants explicitly:
  - historical-beta WACC
  - bottom-up-beta WACC
