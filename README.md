# HoodMiner

Miner-style yield game on **Robinhood Chain** (Robinhood's Ethereum L2). Robin Hood theme: deposit ETH → recruit **Hoods** (miners) → they generate **Loot** per second → compound into more Hoods or claim as ETH.

Modeled on BananaMiner (Solana) but with internally consistent numbers and properly written docs.

## What's here

```
hoodminer/
├── .gitbook.yaml             ← GitBook config — MUST stay at repo root; points root to ./gitbook/
└── gitbook/                  ← GitBook docs, ready to sync
    ├── .gitbook/assets/      ← Images (hoodminer-banner.svg — replace with AI art anytime)
    ├── README.md             ← Landing page (Welcome to HoodMiner, BananaMiner-style layout)
    ├── SUMMARY.md            ← Table of contents / navigation
    ├── product-guides/
    │   ├── take-the-loot.md  ← Claim vs compound, anti-whale decay, 6+1 strategy
    │   ├── invite.md         ← 12% instant single-tier referral
    │   ├── token-economics.md← No token (by design), ETH flow split, scam warning
    │   └── algorithm.md      ← Hood pricing formula, rate mechanics, design rationale
    └── use-cases/
        ├── hood-contract.md  ← Contract address (TBA), immutability guarantees
        └── official-links.md ← Official channels (TBA placeholders)
```

## Game parameters (as documented)

| Parameter | Value |
| --- | --- |
| Chain / currency | Robinhood Chain / native ETH |
| Base daily rate | ~8% (target, variable) |
| Realistic average | 6–8%/day |
| Peak (compound streaks) | ~12%/day |
| Claim decay | Per-claim rate decay, recovers over time (anti-whale) |
| Recommended play | Compound 6 days, claim 1 day ("6+1") |
| Referral | 12% of referred deposits, instant, single-tier only |
| Fees | 5% on deposit + 5% on claim; compounding free |
| Deposit split | 83% pool / 12% referrer / 5% protocol (no-ref deposits: 12% → pool) |
| Token | **None** — Loot is internal accounting, not transferable |
| Hood pricing | `deposit / (deposit + contract balance) × Loot market` |

## Fixes vs the BananaMiner docs

Their GitBook contradicts itself (8% daily on one page, 12% on another; "no fee on claims" next to "5% fee on all withdrawals"). This version reconciles everything: 8% is the base target, 12% is the compound-streak ceiling, claim decay explains the spread, and the 5% fee applies once in / once out with compounding explicitly free. Also added: honest sustainability language, Robinhood Markets non-affiliation disclaimer, and anti-scam guidance throughout.

## Publishing to GitBook

1. The GitHub repo root must be this `hoodminer/` folder, so `.gitbook.yaml` sits at the **repo root** — GitBook only reads it there. If it's nested (or missing), GitBook ignores `SUMMARY.md` and auto-generates ugly pages from the folder tree.
2. In gitbook.com: New space → **Sync with GitHub (Git Sync)** → select the repo/branch. Do NOT use the zip/file import — import ignores `.gitbook.yaml` and `SUMMARY.md` entirely.
3. After changing `.gitbook.yaml` or `SUMMARY.md`, push a commit (or GitBook → space → Configure → force re-sync) to rebuild the structure.
4. Space name: **HoodMiner**. The URL will be `hoodminer.gitbook.io/hoodminer` (or a custom domain later).
5. Sidebar structure comes from `SUMMARY.md`: the `## Product Guides` / `## Use Cases` headings become the grouped sections, and the emoji in each entry title becomes the page icon — same look as the BananaMiner book.

## Still TBA (update docs at launch)

- [ ] Contract address + explorer link → `use-cases/hood-contract.md`
- [ ] dApp URL, Twitter/X → `use-cases/official-links.md` (no Telegram — X is the only social channel)
- [ ] Verify final contract parameters match the table above (rates, fees, decay curve)
- [ ] Bridge guide link in the Quick start section

## Not built yet

The contract and dApp. The docs define the full spec the contract must implement — pricing formula, decay, referral, fee split are all pinned down above.
