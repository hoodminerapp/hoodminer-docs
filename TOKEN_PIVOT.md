# HoodMiner Token Pivot — Spec & Launch Plan

*Decision 2026-07-15: HoodMiner pivots from an ETH-denominated mine (no token) to a $HOOD-denominated mine. $HOOD fair-launches on pons.family. Referral system deleted; headline yield becomes "up to 12%/day". Docs in `gitbook/` already rewritten to this spec (committed, NOT pushed until launch is coordinated).*

## Architecture

- **$HOOD** — fixed-supply ERC-20, fair launch on pons.family bonding curve, graduates to DEX per pons rules. No presale, no team allocation; team dev-buys on the open curve from the published team wallet.
- **The Mine** — fork of the audited ETH contract, re-denominated in $HOOD. One entrance (deposit), one exit (claim), both in $HOOD → no internal/external price spread to arb, and the claim decay throttles sell pressure upstream of the DEX.

## Mechanics changes vs the audited ETH contract

| Item | Old (ETH) | New ($HOOD) |
| --- | --- | --- |
| Denomination | native ETH (`payable`) | ERC-20 $HOOD (`approve` + `transferFrom`; pay via `transfer`) |
| Deposit split | 83% pool / 12% referrer / 5% fee | **95% pool / 5% fee** |
| Referral system | 12% single-tier, instant | **DELETED** (no referrer param, no ReferralPaid event, no eligibility logic) |
| Base emission | 8%/day base, ~12% peak via streaks | **12%/day cap**; decay pulls below, streaks restore toward cap; realistic avg 8–10% |
| Claim decay / recovery / floor | -2000bps per claim, +250bps/day recovery, floor 2500 | unchanged |
| Compound streak bonus | +500bps ≥20h apart | keep, but cap total at 12% (streaks restore toward cap, never exceed) |
| Accrual cap | 12.5 days | unchanged |
| Fees | 5% in / 5% out, fee wallet immutable | unchanged (paid in $HOOD) |
| Hood pricing | `deposit/(deposit+balance) × marketLoot` | unchanged (all terms now in $HOOD) |
| Seed | ≥ MIN_SEED 0.005 ETH, marketLoot scales | same pattern, denominated in $HOOD (pick seed after launch price discovery) |
| takeLootTo(address) | escape hatch | unchanged |

**New contract requirements:**
- Use received-amount accounting (`balanceOf` before/after `transferFrom`) even though pons tokens should be tax-free on transfer — cheap insurance, verify token has no transfer tax before mainnet.
- Donations: plain $HOOD transfers into the mine raise the pool without minting Hoods — this is the buyback top-up path. Verify accrual math reads `balanceOf(this)` so top-ups flow through automatically.
- Re-run all 37 Foundry tests adapted to ERC-20 + re-audit pass (the math core is unchanged; the money-movement layer is new).
- Re-run sims: 12% cap + 95% intake + buyback top-ups (breakeven ~2 weeks; whale extraction bounds).

## Fee revenue model (the "what we earn" answer)

| Stream | Asset | Split |
| --- | --- | --- |
| pons creator fee on every trade (set on launch form, target ~2%; **confirm exact % and creator share on the pons launch form**) | WETH | 50% treasury / 50% buyback engine |
| Buyback engine output | $HOOD | 50% burned / 50% transferred into the mine pool |
| Game fees 5% in + 5% out | $HOOD | 100% treasury (fee wallet, immutable) |

Buyback engine = BURNSEM-style loop (claim fees → swap WETH→$HOOD → split burn/pool), run from the team wallet on a timer. Port `burnsem` engine pattern; adapt flapper tooling (`app/flapper/`) from flap.sh to pons for launch + fee claiming.

## dApp changes (`app/site/`)

- Deposit flow: add ERC-20 approve step (exact-amount default), balances/inputs in $HOOD, remove ETH bridge-first framing → add "Buy $HOOD on pons" button (curve link pre-graduation, DEX after).
- Remove referral dashboard, ?ref capture, ReferralPaid reads.
- Stats: add burned-to-date, pool top-ups to date (from buyback wallet events), $HOOD price.
- `deployments.json`: add token address + pons/DEX links alongside mine address.
- **Scrub list (public "no token" statements — must flip BEFORE launch):**
  - `app/site/app.js:471` prelaunch banner: "…there is NO token…" → "the token and mine launch soon; the only real addresses will appear in the docs"
  - X bio / pinned posts, Telegram pin (if the old "no token" copy was used anywhere)
  - First-post drafts that say "no token"

## Launch sequence

1. Contract fork + tests + audit pass + sims (above).
2. Rewire dApp against devnet (anvil rehearsal with mock $HOOD).
3. Scrub list executed; docs pushed live (gitbook commit is ready and waiting).
4. Launch $HOOD on pons (team wallet), dev-buy, record addresses.
5. Fill addresses in `hood-contract.md` + `official-links.md` + `deployments.json`; deploy mine with seed; verify source; redeploy site off prelaunch mode.
6. Start buyback engine timer. Announce on X + Telegram.

## Open items (user decisions)

- Exact pons creator-fee % (read the launch form; docs deliberately avoid hard numbers on this).
- Dev-buy size + seed size.
- Ticker confirm: $HOOD (check collisions on pons before launch day).
