---
cover: ../.gitbook/assets/hoodminer-cover.png
coverY: 0
---

# 📜 The Hood Contract

Two contracts run the entire game: the **$HOOD token** and the **mine**. This page is the single source of truth for both addresses — check everything against it.

## Official addresses

| | |
| --- | --- |
| **Network** | Robinhood Chain (Ethereum L2) |
| **$HOOD token** | `TBA — published here at launch` |
| **Mine contract** | `TBA — published here at launch` |
| **Team wallet** (fees & buybacks) | `TBA — published here at launch` |
| **Explorer** | `TBA — Robinhood Chain explorer link` |
| **Source code** | Verified on the explorer at deployment |

{% hint style="danger" %}
Until an address appears in this table, **nothing exists** — no token, no presale, no contract. Any address circulating before then — or any address that differs from this page by even one character — is a scam. Always compare against this page, character by character, before buying or approving anything.
{% endhint %}

## What the contracts guarantee

* **Fixed-supply token.** $HOOD is minted once by the pons.family factory at launch — a standard, non-custodial ERC-20. No mint function, no owner powers, no tax switches. Burns only shrink the supply.
* **Immutable mine.** No upgradeability, no proxy, no owner-only functions that touch player funds. Once deployed, nobody — including the team — can change the rules, pause claims, or move the pool.
* **Self-custodial pool.** All deposited $HOOD sits in the mine contract itself, not in a team wallet. Claims are paid by the contract directly, with no human approval step anywhere in the flow.
* **Everything on-chain.** Hood recruitment, Loot accrual, claim decay, buyback top-ups — every mechanic described in this GitBook is enforced by contract code or visible wallet flows, not by a backend we run.
* **Verified source.** The full source code is verified on the block explorer at deployment, so every claim in [The Algorithm](../product-guides/algorithm.md) can be independently audited by anyone who reads Solidity.

## Token approvals — read this carefully

Depositing into the mine requires a standard ERC-20 approval of $HOOD. The rule is simple:

* Approve **only** the mine contract address in the table above, and only from the official dApp.
* The dApp will never ask you to approve any other token, any other spender, or an "unlimited migration/verification/sync" of anything.
* Any site, bot, or DM asking for an approval that doesn't match this page **is a drainer.** No exceptions.

## What the contracts do NOT do

* No "verification deposit," "wallet sync," or "migration." One token and one mine, forever.
* No admin claim function. If someone claims support can "recover" or "boost" your Hoods, they are a scammer.
* No hidden taxes on transfers. $HOOD moves like any standard ERC-20; game fees exist only inside the mine (5% in/out), and trading fees only on the curve/DEX.

## Interacting safely

1. Use only the dApp linked in [Official Links](official-links.md) — bookmark it.
2. Before your first buy or deposit, check both addresses the dApp uses against this page.
3. Team members will **never** DM you first. Anyone who does is impersonating us.
