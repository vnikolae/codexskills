---
name: "cost-of-equity-estimator"
description: "Estimate cost of equity for a public company using both historical beta and peer bottom-up beta. Use when Codex needs to: (1) propose a peer set, (2) prepare a gated review packet with total and operating leverage, (3) ask for user confirmation on peers and leverage treatment, (4) finalize historical and bottom-up cost of equity calculations, or (5) generate a cost-of-equity report and dashboard with beta standard error."
---

# Cost Of Equity Estimator

## Overview

Use this skill after cost of debt is available or in parallel when debt work is independent. The skill is gated: it must propose a peer set, show total versus operating leverage, ask for user confirmation, and only then finalize the equity calculations and dashboard.

Read [references/workflow.md](references/workflow.md) for the review/finalization sequence. Read [references/methodology.md](references/methodology.md) for leverage treatment, beta handling, and dashboard requirements.

## Workflow

1. Work in `C:\Users\vnikolae\Dropbox\Data\WAAC estimation\YahooBeta`.
2. Prepare the review packet first:
   - use `prepare_equity_review.py`
   - write `../outputs-waac/<ticker>/equity_review.json`
3. Present the review packet to the user before finalizing:
   - proposed peer group
   - total debt leverage
   - operating-only leverage
   - flags for finance arms, non-operating debt, or questionable peers
4. Do not finalize until the user confirms the peer set and leverage treatment.
5. Finalize with `finalize_cost_of_equity.py` only after approval.
6. Save:
   - `cost_of_equity_<ticker>.md`
   - `beta_summary.json`
   - `peer_beta_table.csv`
   - `regression_diagnostics.csv`
   - dashboard HTML

## Required Outputs

- Historical beta
- Historical beta standard error
- Historical cost of equity
- Peer median unlevered beta
- Bottom-up peer-based relevered beta
- Bottom-up cost of equity

## Operating Rules

- Treat historical beta and bottom-up beta as separate outputs, not substitutes.
- Always show both total debt and proposed operating debt in the review packet.
- If a peer's leverage treatment is unclear, ask the user before finalizing.
- Excluding a questionable peer is better than silently keeping a distorted one.
- Keep company-specific leverage overrides explicit in review artifacts, not hidden in code.
