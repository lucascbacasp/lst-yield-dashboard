# Meta Pool — LST Yield Explorer

> Live utility dashboard showing DeFi yield opportunities for Meta Pool's Liquid Staking Tokens across NEAR, Ethereum, Solana, ICP, and Story Protocol.

![Meta Pool LST Dashboard](https://img.shields.io/badge/status-live-brightgreen) ![Chains](https://img.shields.io/badge/chains-5-blue) ![License](https://img.shields.io/badge/license-MIT-purple)

---

## The Problem

Meta Pool issues liquid staking tokens (LSTs) across 5 chains — stNEAR, mpETH, mSOL, mpICP, and mpSTORY. Once users stake and receive their LST, they face a fragmented experience:

- **No single place** to see where each LST can be deployed in DeFi
- **APYs, TVL, and reliability** are scattered across protocol docs and Discord
- **Multichain users** can't compare opportunities across ecosystems
- The existing ecosystem page is **static documentation**, not a live signal

## The Solution

A real-time dashboard that answers one question: **"I hold this LST — where should it go right now?"**

For each token Meta Pool issues, the dashboard shows:
- Active DeFi integrations ranked by yield
- Total APY (base staking + DeFi yield)
- TVL depth and reliability scoring per integration
- One-line strategy descriptions for each opportunity

This turns passive documentation into an active **retention tool** — the staking yield is the floor, the DeFi yield on top is the moat.

---

## Features

| Feature | Description |
|---------|-------------|
| **Multichain View** | Filter by All / NEAR / Ethereum / Solana / ICP / Story Protocol |
| **Live Yield Ranking** | Integrations sorted by APY, TVL, or reliability |
| **Reliability Scoring** | Visual depth bars (green/orange/red) to judge liquidity risk |
| **Strategy Tags** | Quick one-liner per integration explaining the play |
| **Best Yield Badge** | Auto-highlights the top opportunity per LST |
| **Responsive Design** | Mobile, tablet, and desktop layouts |
| **Real-time Feeds** | Status indicator with last-update timestamp |

---

## Supported Tokens & Chains

| Token | Chain | Base APY | Active Integrations |
|-------|-------|----------|---------------------|
| stNEAR | NEAR | 5.1% | 8 (Ref Finance, Burrow, Jumbo, Pembrock, Trisolaris, Bastion, Aurigami, WannaSwap) |
| spETH | Ethereum | 3.8% | 5 (QiDAO, Lynex, Velodrome, TENET, Linea) |
| mpSOL | Solana | 10.2% | 2 (Jupiter, Coinstore Web3) |
| stICP | ICP | 7.2% | 3 (ICPSwap, Sonic, Helix) |
| stIP | Story Protocol | 8.5% | 2 (Story Swap, IP-Fi Lending) |

> **Note:** mpETH was rebranded to **spETH** (Staking Pool ETH). mSOL is Marinade Finance's token — Meta Pool's Solana LST is **mpSOL**. ICP and Story tokens use **stICP** and **stIP** naming.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML5, CSS3, JavaScript (ES6+) |
| Styling | CSS Custom Properties (design tokens), CSS Grid, Flexbox |
| Typography | [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts |
| Hosting | [Railway](https://railway.app) with `serve` static server |
| Version Control | Git + GitHub |

### Why vanilla HTML/CSS/JS?

This is a **mockup/prototype** designed for speed and zero dependencies. The architecture is intentionally simple:
- Single `index.html` — no build step, no bundler, no framework overhead
- All data is mock — ready to swap with real API calls
- CSS variables for consistent theming
- Modular JS rendering function for easy migration to React/Vue/Svelte

---

## Project Structure

```
lst-yield-dashboard/
├── index.html          # Main application (HTML + CSS + JS)
├── package.json        # Node.js config for Railway deployment
├── .gitignore          # Git ignore rules
├── LICENSE             # MIT License
├── CONTRIBUTING.md     # Contribution guidelines
└── README.md           # This file
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+ (only needed for local server)
- A modern browser (Chrome, Firefox, Safari, Edge)

### Run Locally

```bash
# Clone the repository
git clone https://github.com/lucascbacasp/lst-yield-dashboard.git
cd lst-yield-dashboard

# Option 1: Open directly in browser
open index.html

# Option 2: Run with a local server
npx serve -s . -l 3000
# → http://localhost:3000
```

### Deploy to Railway

1. Fork or connect this repo on [railway.app/new](https://railway.app/new)
2. Railway auto-detects the `package.json` start script
3. Go to **Settings → Networking → Generate Domain**
4. Done — your dashboard is live

---

## Architecture Decisions

### Data Layer (Current: Mock Data)

The `TOKENS` array in `index.html` contains the full mock dataset. Each token object follows this schema:

```javascript
{
  symbol: 'stNEAR',           // LST ticker
  chain: 'near',              // Chain identifier for filtering
  chainLabel: 'NEAR',         // Display name
  color: '#00c08b',           // Brand color
  gradient: 'linear-gradient(...)', // Card gradient
  baseApy: 5.1,               // Base staking APY %
  totalStaked: '$48.2M',      // Total value staked
  integrations: [             // DeFi integrations array
    {
      protocol: 'Ref Finance', // Protocol name
      type: 'DEX / Farm',      // Integration category
      apy: 11.8,               // Total APY (base + DeFi)
      tvl: 12400000,           // TVL in USD (raw number)
      reliability: 92,         // 0-100 reliability score
      logo: 'RF',              // Logo initials
      logoColor: '#00c08b',    // Logo background
      strategy: '...'          // One-line strategy description
    }
  ]
}
```

### Reliability Score

The reliability metric (0-100) represents liquidity depth and protocol maturity:

| Score | Level | Meaning |
|-------|-------|---------|
| 80-100 | High (green) | Deep liquidity, established protocol, low slippage |
| 60-79 | Medium (orange) | Moderate depth, check slippage for large positions |
| 0-59 | Low (red) | Shallow liquidity, early-stage, higher risk |

### Rendering Pipeline

```
filterChain() / sortIntegrations()
        ↓
    render()
        ↓
  For each token matching filter:
        ↓
  Sort integrations by selected criteria
        ↓
  Generate HTML via template literals
        ↓
  Inject into #tokenSections
```

---

## Roadmap to Production

This mockup is designed to evolve. Key milestones for a production version:

- [ ] **Real data feeds** — Connect to on-chain data via protocol APIs (DeFiLlama, subgraphs, RPC nodes)
- [ ] **Wallet integration** — Show user's actual LST balances and personalized yield recommendations
- [ ] **Auto-refresh** — WebSocket or polling for live APY/TVL updates
- [ ] **One-click actions** — Deep links to deposit/supply directly on each protocol
- [ ] **Historical APY charts** — Sparklines showing 7d/30d yield trends
- [ ] **Risk scoring model** — Factor in audit status, TVL stability, impermanent loss
- [ ] **Notifications** — Alert when a new integration goes live or yields spike
- [ ] **Framework migration** — Move to Next.js/Nuxt for SSR, routing, and component architecture

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [Meta Pool](https://metapool.app) — Multichain liquid staking protocol
- Built as a prototype to demonstrate how a live LST utility dashboard could improve user retention and DeFi discovery across Meta Pool's ecosystem
