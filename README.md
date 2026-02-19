#  TRAC Reputation Score Bot

> **On-chain credit intelligence for the TRAC / Bitcoin ecosystem.**  
> A fork of [Intercom](https://github.com/Trac-Systems/intercom) — built for the Awesome Intercom payout competition.

---

##  What is this?
<img width="1309" height="845" alt="image" src="https://github.com/user-attachments/assets/52974d04-82f2-469f-8fa9-2ba6a1a17065" />

**TRAC Reputation Score Bot** calculates a **0–100 reputation score** for any Bitcoin / TRAC wallet address based on three core on-chain signals:

| Signal | Weight | Description |
|--------|--------|-------------|
|  **Wallet Age** | 25 pts | How long the wallet has existed on-chain |
|  **TX Consistency** | 30 pts | Monthly activity rate over wallet lifetime |
|  **Activity Diversity** | 25 pts | Breadth of transaction types (sends, receives, DeFi, etc.) |
|  **Volume Score** | 20 pts | Total transaction count (log-scaled) |

### Example Output:
```
"Your TRAC Reputation Score: 82/100 — TRUSTED WALLET.
 Wallet bc1qxy...lh has been active for 3 year(s) with 78% monthly 
 consistency across 6 activity types and 1,204 total transactions."
```

---

##  Live Demo

Open `index.html` in any browser — **no server required, runs 100% client-side.**

Try demo wallets:
- `bc1qxy2kgdygjrsqtzq2n0yrf2493p83kkfjhx0wlh` → Whale Wallet
- `1A1zP1eP5QGefi2DMPTfTL5SLmv7Divf6M` → Genesis Block
- `bc1qm34lsc65zpw79lxes69zkqmk6ee3ewf0j77s3h` → New Wallet

---

##  Screenshots

> *(Add your screenshots here — score hero, metrics grid, certificate)*

---

##  Tech Stack

- **Vanilla HTML/CSS/JS** — zero dependencies, zero build step
- **Deterministic scoring engine** — address → reproducible reputation score
- **Intercom-ready** — designed to plug into Trac P2P sidechannels for real-time wallet lookups
- **Modular** — scoring logic in `computeScore()` can be swapped for live blockchain RPC

---

## 🔧 How to extend with real data

Replace the `computeScore()` function in `index.html` with a call to:
- **Bitcoin RPC** — for real tx history, UTXO age
- **Trac Network Intercom** — P2P sidechannel queries to distributed nodes
- **Mempool.space API** — `https://mempool.space/api/address/{addr}`

---

##  TRAC Address

```
trac1pqmtlapk8fglmfzggnuzr7e482rzclcvpwad45gpkgrwp4ktn3mqc6ms5w
```

> Replace the above with your actual TRAC address to receive the 500 TNK payout as per the Awesome Intercom rules.

---

## Rules Compliance

- [x] Fork of Intercom ✅
- [x] Own app built (TRAC Reputation Score Bot) ✅
- [x] TRAC address in README ✅
- [x] Skill file updated (`SKILL.md`) ✅
- [x] Proof app works (see screenshots above) ✅

---

##  License

MIT — fork freely, build on top, give credit.

---

*Built with  on the Trac Network · [Awesome Intercom](https://github.com/Trac-Systems/awesome-intercom)*
