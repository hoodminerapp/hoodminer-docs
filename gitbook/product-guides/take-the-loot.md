---
cover: ../.gitbook/assets/hoodminer-cover.png
coverY: 0
---

# 💰 Take the Loot

Your Hoods generate **Loot** every second. This page explains the two things you can do with it — and why the timing of your choice decides how much you earn.

## Your two options

### 1. Claim — take the Loot

Claiming sells your accumulated Loot back to the contract for **$HOOD**, paid directly to your wallet in the same transaction. There is no waiting period, no manual approval, no middleman — the contract executes it instantly. What you do with claimed $HOOD is up to you: hold it, redeposit it, or sell it on the market.

Claiming does **not** touch your Hoods. They stay recruited and keep working the moment the transaction confirms.

### 2. Compound — recruit more Hoods

Compounding spends your accumulated Loot on **new Hoods** instead of cashing out. Your daily Loot output grows immediately, and because compounding is an internal contract operation, it costs **nothing but gas** — and gas on Robinhood Chain is measured in cents.

## The anti-whale mechanism

HoodMiner deliberately punishes greed and rewards patience:

* Every claim applies a **cooldown decay** to your personal daily rate.
* Claim occasionally, and the decay is negligible — you stay near the top of the 8–12%/day range.
* Claim continuously, and your rate collapses. A player who smashes the claim button several times a day will watch their daily percentage sink far below the cap.

This protects the pool for everyone — and because the **only** way $HOOD leaves the mine is a claim, the same decay that protects the pool also paces sell pressure on the market. Whales cannot drain the contract at full rate, and steady players are never diluted by someone else's exit.

{% hint style="warning" %}
**Straight talk on the decay:** the rate decay is tracked per wallet. Someone determined enough to split a stake across many wallets and rotate their claims can sidestep the per-wallet penalty — that's true of any per-address throttle on a public chain, and we'd rather say it than pretend otherwise. The decay is a pacing incentive for normal play, not what keeps the pool solvent: solvency comes from the payout math itself, which can only ever pay a fraction of what the pool holds, no matter how many wallets claim at once.
{% endhint %}

## The recommended strategy: 6 + 1

The math favors one simple routine:

> **Compound six days a week. Claim on the seventh.**

* Six compounds grow your Hood count all week, raising every future day's output.
* One weekly claim keeps your rate decay minimal.
* Played this way, most players recover their initial deposit in roughly **two weeks**, and everything after that is profit riding on a bigger stack of Hoods than they started with — in $HOOD terms; the market decides what each token is worth on the day you claim.

You are free to play differently — the contract enforces no schedule. But the 6 + 1 rhythm is the efficiency sweet spot the algorithm was tuned around.

## Fees

| Action | Fee |
| --- | --- |
| Deposit $HOOD (recruit Hoods) | **5%** protocol fee |
| Claim (withdraw $HOOD) | **5%** protocol fee |
| Compound | **Free** — gas only |

The 5% fee applies once on the way in and once on the way out. Compounding is never taxed — deliberately, so the optimal strategy is also the cheapest one. Where fees go is covered in [The $HOOD Token](token-economics.md).

{% hint style="info" %}
**Practical tip:** compound at roughly the same time each day. Loot accrues per second, so nothing is lost by being a few hours late — but a consistent rhythm makes your weekly claim day easy to track.

**One hard limit to know:** your Loot tank holds **12.5 days** of production. After that, accrual pauses until you compound or claim. Hours late costs nothing; weeks of inactivity does.
{% endhint %}
