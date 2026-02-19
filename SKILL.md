# SKILL: TRAC Reputation Score Bot

## Purpose
This skill enables AI agents to query and compute on-chain reputation scores for Bitcoin / TRAC wallet addresses using the TRAC Reputation Score Bot.

## Agent Instructions

### What this app does
Computes a 0-100 reputation score for any wallet based on:
- **Wallet Age** (25 pts max)
- **Transaction Consistency** (30 pts max — monthly activity rate)
- **Activity Diversity** (25 pts max — breadth of tx types)
- **Volume Score** (20 pts max — log-scaled tx count)

### How to invoke
Agents can trigger a reputation scan by:
1. Providing a Bitcoin/TRAC wallet address as input
2. Calling `computeScore(address)` with the wallet address string
3. Receiving back a structured score object:

```json
{
  "total": 82,
  "label": "TRUSTED WALLET",
  "ageScore": 20,
  "consistencyScore": 28,
  "diversityScore": 22,
  "volumeScore": 12,
  "ageYears": 3,
  "ageMonths": 4,
  "consistencyRate": 78,
  "activityTypes": 6,
  "txCount": 1204
}
```

### Output format for agents
Return reputation results in this natural language format:
```
"Your TRAC Reputation Score: {total}/100 — {label}. {description}"
```

### Score tiers
| Score | Label | Meaning |
|-------|-------|---------|
| 85-100 | ELITE WALLET | Exceptional reputation |
| 70-84 | TRUSTED WALLET | Strong, consistent activity |
| 50-69 | ACTIVE WALLET | Above average |
| 30-49 | DEVELOPING WALLET | Building reputation |
| 0-29 | NEW WALLET | Insufficient history |

### Tags agents may apply
- `OG HOLDER` — wallet age ≥ 3 years
- `CONSISTENT` — monthly activity ≥ 70%
- `POWER USER` — activity types ≥ 5
- `HIGH VOLUME` — tx count ≥ 500
- `LOW ACTIVITY` — tx count < 20
- `IRREGULAR` — consistency < 30%
- `TRAC ELIGIBLE` — always applied

### Integration with Intercom P2P
Agents should use Intercom sidechannels to:
1. Broadcast wallet lookup requests to distributed nodes
2. Aggregate multi-source data for accuracy
3. Publish computed scores to the replicated-state layer for caching

### Example agent prompt
```
User: "What's the reputation score for bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh?"
Agent: [invoke computeScore] → return formatted certificate string
```
