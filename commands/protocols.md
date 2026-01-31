---
description: Search DeFi protocol documentation specifically
---

# QMD Protocol Search

Quick search across all DeFi protocol skills.

## Usage

```
/qmd:protocols <query>
```

## What This Searches

The `protocols` collection indexes skills from:
- Aave V3/V4 - Lending, flash loans, eModes
- Balancer V3 - Vault, pools, hooks
- Uniswap V3/V4 - AMM, concentrated liquidity, hooks
- Aerodrome/Slipstream - ve(3,3), gauges, emissions
- Compound V3 Comet - Monolithic lending
- Euler - EVC, EVK, modular lending
- Resupply - CDP stablecoin, liquidations

## Execute Search

Use hybrid search for best results:

```
qmd_query(collection: "protocols", query: "<user query>", limit: 10)
```

Or CLI:

```bash
qmd query "<query>" --collection protocols --limit 10 --format markdown
```

## Example Queries

- "flash loan implementation" → Aave, Balancer flash loan docs
- "concentrated liquidity positions" → Uniswap V3, Slipstream docs
- "liquidation mechanism" → Cross-protocol liquidation patterns
- "hook system" → Uniswap V4, Balancer V3 hooks
- "ERC4626 vault" → Euler EVK, Aave StataToken

## If Collection Not Indexed

```bash
qmd index protocols --path ~/.claude/plugins --pattern "**/skills/**/*.md" --description "DeFi protocol technical documentation"
```

## Present Results

Group by protocol when relevant:

```
Found [N] results for "[query]":

**Aave V3**
- aave-v3-flash-loans: [excerpt]

**Balancer V3**
- balancer-v3-vault: [excerpt]

**Uniswap V4**
- uniswap-v4-hooks: [excerpt]
```
