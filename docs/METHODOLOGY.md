# Measurement methodology

## Research design

The public results are historical simulations checked against preserved report/summary artifacts. A new replay was not performed for this presentation. The evidence supports the reported historical arithmetic within its specified assumptions; it does not establish future profitability, exact executable fills or an operational reliability guarantee.

## Metrics and units

| Measure | Definition | Important distinction |
|---|---|---|
| Net P&L | Sum of closed whole-position net outcomes after modeled costs | Not gross profit or a prospective income estimate |
| Closed positions | Number of completed simulated positions | Not the count of executions or partial legs |
| Win rate | Positive-net closed positions divided by all closed positions | A profitable partial leg cannot make a negative-net position a win |
| Profit factor | Sum of positive position net results divided by absolute sum of negative position net results | Undefined if there are no losses; never assumed infinite evidence of reliability |
| Mean net per position | Net P&L divided by closed-position count | A descriptive sample average, not a predicted payoff |
| End-of-day drawdown | Highest completed end-of-day equity minus a later end-of-day equity | Excludes the adverse intraday marks used by the headline measure |
| Headline drawdown | Highest prior completed end-of-day equity minus adverse intraday marked equity, maximized over the replay | Does not use the highest intraday equity |

Win rate and profit factor appear only where the published evidence supports them. Listing a definition does not imply a missing metric has been measured.

For position net outcomes `p`, the descriptive arithmetic is:

```text
net P&L            = sum(p)
win rate           = count(p > 0) / number of closed positions
profit factor      = sum(p where p > 0) / abs(sum(p where p < 0))
mean net/position  = net P&L / number of closed positions
```

These are reporting definitions, not decision rules. Drawdown additionally requires an equity path; it cannot be reconstructed from final net P&L and a position count alone.

## Why final profit is insufficient

```mermaid
flowchart TD
    A[Same final aggregate profit] --> B[Possible equity path A]
    A --> C[Possible equity path B]
    B --> D[Different adverse marks]
    C --> D
    D --> E[Potentially different drawdown]
```

The diagram is conceptual. No synthetic path is presented as a measured equity curve. The public charts use only the verified aggregate values; no trade-level timing or reconstructed curve is published.

## Measurement and assumptions

- Net P&L is the sum of whole-position results after modeled transaction costs. A win requires positive whole-position net P&L; profitable partial executions alone do not constitute a win. Profit factor is total positive net P&L divided by the absolute sum of negative net P&L.
- **Maximum drawdown*** is the largest decline from the highest previously completed end-of-day equity to adverse intraday marked equity. It is not a drawdown measured from the highest intraday equity. The legacy replay also records end-of-day peak-to-trough drawdown of $1,310.20.
- Legacy replay costs: micro gold commission $1.92 per contract round trip with two ticks of modeled exit slippage; micro index commission $1.40 per contract round trip with zero modeled stop slippage. Costs in the preserved implementation differ from some configuration documentation; these are the effective replay assumptions.
- The causal-calendar sensitivity selects the micro index contract using the prior completed session rather than the current full day. The final row additionally applies micro index commission of $1.90 per contract round trip, two stop/market slippage ticks, one-tick entry trade-through, and session-end flattening at the open. Gold assumptions remain unchanged. This is a partial execution sensitivity, not a fully stressed portfolio.
- Minute bars do not establish intrabar event order, queue priority, latency or executable fills. The legacy row contains a known future-information issue in contract selection. The alternate rows address that calendar issue but do not remove all simulation limitations.
- Model selection used the inspected period. Preserved arithmetic is checked against the audit artifacts; a new market-data replay was not run for this showcase. No prospective paper or live performance is published.

## Scenario comparison rules

- Compare each alternate scenario with its matching version and research period.
- Report changes in both net P&L and drawdown; a lower final result does not imply a proportionally higher drawdown.
- Separate calendar changes from execution-cost changes where the preserved experiment does so.
- Keep independently reset annual runs separate. Do not combine them into a compounded return series.
- Treat inspected development periods as inspected, even if a later analysis freezes some definitions.
- Do not infer statistical significance from a difference in two aggregate values. No confidence interval is manufactured from these summaries.

## Reproducibility boundary

The public layer provides machine-readable aggregates, explicit definitions and labeled scenarios. It is not a complete public replication package: the implementation and detailed research inputs remain private. The showcase review checked consistency of preserved metrics and the presentation, rather than rerunning or certifying the entire underlying experiment.

## Evidence still needed

Tick-sequence and execution validation, broader independent data, prospective observations and integration parity require their own evidence. No paper/live track record, annualized return, Sharpe ratio or inferred equity curve is added here. Unpublished measurements should not be interpreted as zero or as favorable results.

[Overview](../README.md) · [Engineering](ENGINEERING.md) · [Results](RESULTS.md)
