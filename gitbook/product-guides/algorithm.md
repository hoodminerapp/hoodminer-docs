---
cover: ../.gitbook/assets/hoodminer-cover.png
coverY: 0
---

# ⚙️ The Algorithm

This page explains how the HoodMiner contract actually prices Hoods and pays Loot. No hand-waving — this is the machine under the hood.

## The core loop

```
$HOOD in  →  Hoods recruited  →  Loot accrues per second  →  your choice:
                                                             ├─ Compound → more Hoods → more Loot/day
                                                             └─ Claim    → $HOOD out (rate decay applies)
```

## Hood pricing

Hoods are priced by a bonding-curve-style formula against the contract's state:

```
Hoods received = deposit / (deposit + contract balance) × Loot market size
```

What this means in practice:

* **Early deposits buy more.** When the mine's pool is small, the same $HOOD recruits significantly more Hoods. Being early is a real, mathematical advantage — not a marketing line.
* **Your deposit size self-adjusts.** A whale-sized deposit raises the denominator against itself, so it cannot buy Hoods at the same unit price a small player pays. Everyone gets the fair marginal price for the size they bring.
* **Nobody gets diluted retroactively.** Hoods you already own are yours at the price you paid. Later deposits recruit at *their* market conditions, not yours.

Because Hood pricing and the market share the same unit — $HOOD — there is no internal "exchange rate" to arbitrage against the DEX. The mine has one entrance (deposit) and one exit (claim), both denominated in the token.

## The daily rate

The contract targets an emission of up to **12% of your position in Loot per day**, modified per-player:

* **Compound streaks** push your effective rate toward the 12% cap — sustained compounders live at the top of the range.
* **Claims** apply a decay to your personal rate that recovers over time. One claim a week is barely felt; claiming daily craters your rate.
* **Pool conditions** matter: emission is a function of contract state, so a growing pool supports the high end of the range and a shrinking one compresses it.

The published figures — up to 12% peak, 8–10% realistic average — describe the algorithm's targets, **not a promise**. The rate you experience is determined entirely by contract state and your own behavior.

## Why the design holds together

Each mechanism plugs a hole that killed earlier miner games on other chains:

| Mechanism | Problem it solves |
| --- | --- |
| TVL-based Hood pricing | Late whales buying at early-bird prices |
| Claim-rate decay | Bank-run drains by impatient sellers |
| Fee-free compounding | Optimal play being too expensive to execute |
| 5% in/out fee | Zero-cost wash cycling through the contract |
| 12.5-day accrual cap | Dormant wallets building unbounded claims against the pool |
| Buyback pool top-ups | Yield depending on new deposits alone |
| Single asset ($HOOD everywhere) | Internal/external price gaps for bots to arbitrage |

## The honest paragraph

Claims are possible **for as long as the mine holds $HOOD** — that is the whole guarantee, and the only one. The algorithm is built to make the pool grow faster than it drains under normal play, and every parameter above exists to serve that goal. On top of the pool sits a second, separate risk: the market price of $HOOD itself, which no algorithm controls. A miner game is a shared pot with rules, not a yield source with revenue. Play with money you can afford to lose, front-load your compounding while the pool is young, and treat every claim after breakeven as the win it is.

## Verify it yourself

Both contracts are **immutable** — no owner functions, no pause switch, no parameter changes after deployment. Everything on this page can be checked against the verified source code linked in [The Hood Contract](../use-cases/hood-contract.md). Don't trust the docs; read the code.
