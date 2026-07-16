---
cover: ../.gitbook/assets/hoodminer-cover.png
coverY: 0
---

# 🪙 The $HOOD Token

## One token. One address. Nothing else.

$HOOD is the only asset HoodMiner will ever issue, and its address is published in exactly one place: [The Hood Contract](../use-cases/hood-contract.md).

{% hint style="danger" %}
**There is exactly one $HOOD token** — the address on that page, character for character. There is no presale, no "early allocation," no second token, no v2. Anything else carrying our name — on a DEX, in a Telegram group, in your DMs — is a **scam**, without exception.
{% endhint %}

## How it launches

* **Fair launch on [pons.family](https://pons.family)** — the leading launchpad on Robinhood Chain. Everyone buys on the same public bonding curve, starting from zero.
* **Fixed supply.** The pons factory mints the entire supply at launch. No mint function, no inflation, ever. Burns only shrink it.
* **No team allocation.** The team buys at launch on the open curve like everyone else, from a wallet published in [The Hood Contract](../use-cases/hood-contract.md).
* **Graduation.** When the curve completes, liquidity migrates to the DEX per pons's standard, non-custodial process — not controlled by us.

## The economy runs on $HOOD

HoodMiner is a **mine denominated in its own token**:

* You **deposit $HOOD** to recruit Hoods.
* Hoods generate **Loot** — an internal accounting unit inside the mine contract, not a transferable token. Loot cannot be sent, sold or listed; it exists only as your balance inside the mine.
* You **claim $HOOD** when you sell Loot back to the contract — paid from the mine's pool, instantly.

One asset, one pool, one set of rules. Because the game and the market share the same token, there is nothing to arbitrage between them — the only way value leaves the mine is a claim, and claims are paced by [the algorithm](algorithm.md).

## Where the money flows

**Every deposit** into the mine splits two ways:

| Destination | Share | Purpose |
| --- | --- | --- |
| **The pool** (mine contract balance) | 95% | Backs all Loot claims — this is what miners withdraw from |
| **Protocol fee** | 5% | Development, marketing, and keeping the lights on |

On the way out, a **5% protocol fee** applies to claims. Compounding is always free.

**Every trade** of $HOOD — curve or DEX — pays a creator fee to the project. It is split at the wallet level, verifiably on-chain:

| Destination | Share | Purpose |
| --- | --- | --- |
| **Buyback** | 50% | Market-buys $HOOD: half of every buyback is **burned**, half is **deposited into the pool** |
| **Treasury** | 50% | Development, marketing, and operations |

## The flywheel

The buyback split is what makes HoodMiner more than a shared pot:

```
volume (curve/DEX) → creator fees → buy $HOOD → 50% burned  (fixed supply shrinks)
                                              → 50% to pool (miners get paid)
          miners deposit → supply locked in the mine → thinner float
```

Speculators who never touch the mine still pay the miners. Miners who never sell still tighten the float. Neither side needs to believe in the other — the contract routes the value anyway.

## Sustainability, stated honestly

HoodMiner does not print yield from nowhere, and we won't pretend it does. Two separate layers of risk, in plain words:

* **The pool.** Mining rewards are paid from the mine's $HOOD balance, which grows through deposits, compounds and buyback top-ups, and shrinks through claims. The mechanics — TVL-based Hood pricing, claim decay, fee-free compounding, the accrual cap — all exist to push the pool toward growth and slow its drain. The mine is sustainable as long as its inflows are, and no one can promise you inflows.
* **The price.** Your yield is denominated in $HOOD. What a claimed token is *worth* is decided by the open market, minute by minute — not by the algorithm, and not by us. The buyback engine adds permanent, volume-funded buy pressure; it does not repeal supply and demand.

Anyone who tells you otherwise is selling something.
