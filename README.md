# Sthenos Cloud

**AI Backbone for Next-Gen C2 Systems**

Sthenos is a behavioral early-warning capability that converts movement data into detection of coordination, instability, and regime shifts — giving decision-makers earlier warning and reduced uncertainty in contested multi-agent environments.

## Platform Overview

Sthenos transforms incomplete operational datasets (raw movement traces, geometry) into actionable simulation environments for defense AI.

### Core Problem

Activision Caldera OpenUSD provides geometry + breadcrumbs but explicitly excludes logic, intent, and tactical semantics. A semantic reconstruction layer is mandatory.

### Solution

Sthenos acts as the semantic enrichment layer between raw breadcrumbs and simulation-ready entities, enabling:
- Tactical scenario reconstruction
- AI-assisted decision support
- Synthetic operational data generation
- Edge + cloud inference integration

## Architecture

Sthenos is built on a 7-layer defense AI platform:

```
L7: Strategic AI / Multi-agent Simulation
L6: Decision Support & Scenario Evaluation
L5: Synthetic Data Generation Engine
L4: Behavioral & Tactical Modeling Layer
L3: Semantic Enrichment Layer ← MVP Core
L2: Data Normalization (USD / JSON / Streams)
L1: Raw Inputs (Caldera / Sensors / IoT / Edge)
```

**Key principle:** Layer N cannot import Layer N+1. This preserves modularity.

## Technology Stack

- **Python Core:** Simulation, data pipelines, AI/ML integration, OpenUSD bindings
- **Libraries:** pxr (USD), numpy, pandas, networkx, fastapi
- **Local LLM Ready:** LM Studio integration (DeepSeek-Coder, Gemma)

## Getting Started

### Prerequisites

- Node.js 18+
- npm or pnpm

### Installation

```bash
# Clone the repository
git clone https://github.com/sthenoscloud/sthenos.presentation.git
cd sthenos.presentation

# Install dependencies
npm install

# Start development server
npm run dev
```

### Build

```bash
npm run build
npm run preview
```

## Project Structure

```
sthenos.presentation/
├── src/
│   ├── pages/
│   │   └── index.astro       # Main landing page
│   ├── layouts/
│   │   └── Layout.astro      # Base layout component
│   └── components/           # Reusable components
├── public/
│   └── favicon.svg           # Site favicon
├── astro.config.mjs          # Astro configuration
├── package.json
└── README.md
```

## Deployment

This site is configured for Vercel deployment. Connect your Vercel project to this repository for automatic deployments.

### Domain Setup (GoDaddy)

1. In GoDaddy, navigate to DNS Management
2. Add an A record pointing to Vercel's deployment IP
3. Or add a CNAME record pointing to `cname.vercel-dns.com`
4. Configure custom domain in Vercel project settings

## Features

- **Observe:** Raw movement data converted to dynamic interaction graphs
- **Understand:** Behavioral intelligence with coordination and instability detection
- **Anticipate:** Regime transition detection for early warning
- **Cloud Modernization:** Seamless ISR pipeline integration
- **Quantum-Ready:** Architecture designed for future quantum workloads

## License

UNCLASSIFIED // FOR OFFICIAL USE ONLY

---

Built with [Astro](https://astro.build)