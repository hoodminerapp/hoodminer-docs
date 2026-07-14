# 📜 The Hood Contract

One contract runs the entire game. This page is the single source of truth for its address — check everything against it.

## Contract address

| | |
| --- | --- |
| **Network** | Robinhood Chain (Ethereum L2) |
| **Contract** | `TBA — published here at launch` |
| **Explorer** | `TBA — Robinhood Chain explorer link` |
| **Source code** | Verified on the explorer at deployment |

{% hint style="danger" %}
Until an address appears in this table, **no HoodMiner contract exists**. Any address circulating before then — or any address that differs from this page by even one character — is a scam. Always compare against this page, character by character, before interacting.
{% endhint %}

## What the contract guarantees

* **Immutable.** No upgradeability, no proxy, no owner-only functions that touch player funds. Once deployed, nobody — including the team — can change the rules, pause withdrawals, or move the pool.
* **Self-custodial pool.** All deposited ETH sits in the contract itself, not in a team wallet. Claims are paid by the contract directly, with no human approval step anywhere in the flow.
* **Everything on-chain.** Hood recruitment, Loot accrual, claim decay, referral payouts — every mechanic described in this GitBook is enforced by contract code, not by a backend we run.
* **Verified source.** The full source code is verified on the block explorer at deployment, so every claim in [The Algorithm](../product-guides/algorithm.md) can be independently audited by anyone who reads Solidity.

## What the contract does NOT do

Just as important:

* It never asks for token approvals — the game uses native ETH only. Any site requesting an ERC-20 approval "for HoodMiner" is a drainer.
* It never requires a "verification deposit," "wallet sync," or "migration." There is one contract, forever.
* It has no admin claim function. If someone claims support can "recover" or "boost" your Hoods, they are a scammer.

## Interacting safely

1. Use only the dApp linked in [Official Links](official-links.md) — bookmark it.
2. Before your first deposit, check that the contract the dApp calls matches the address on this page.
3. Team members will **never** DM you first. Anyone who does is impersonating us.
