# Equinox

A Fair and Inclusive Order Book-Based Multi-Collateral DeFi Lending Protocol Native to Sui Blockchain

---

## Table of Contents

- [Problem Statement](#problem-statement)
- [Solution](#solution)
- [Key Advantages](#key-advantages)
- [Core Features](#core-features)
- [Target Market](#target-market)
- [Concept and Mechanism](#concept-and-mechanism)
  - [How It Works](#how-it-works)
  - [Multi-Collateral System](#multi-collateral-system)
  - [Hidden Position Privacy](#hidden-position-privacy)
  - [Lender Journey](#lender-journey)
  - [Borrower Journey](#borrower-journey)
  - [Matching Engine](#matching-engine)
  - [Vesting Integration](#vesting-integration)
  - [Aggregator Vault (Nautilus-driven Yield Router)](#aggregator-vault-nautilus-driven-yield-router)
- [Technical Architecture](#technical-architecture)
- [Deployed Contracts](#deployed-contracts)
- [Quick Start](#quick-start)
- [Why Sui Blockchain](#why-sui-blockchain)
- [Links](#links)

---

## Problem Statement

Current DeFi lending protocols on Sui and other blockchains face significant limitations:

1. **Fragmented Liquidity** - Pooled lending models create isolated liquidity pools, leading to inefficient capital allocation and inconsistent rates across similar assets.

2. **Inflexible Interest Rates** - Users cannot customize their lending or borrowing terms. Rates are algorithmically determined by pool utilization, offering no personalization.

3. **Cold-Start Problem** - New or emerging assets struggle to bootstrap liquidity, as pooled models require critical mass before becoming useful.

4. **Vesting Pressure on Ecosystem** - Large vesting schedules from early investors and team allocations create sustained selling pressure, destabilizing token prices and ecosystem health.

5. **Inequity Between Retail and Institutional Users** - Institutional players with larger capital have inherent advantages in current systems, while retail users lack privacy options and face higher relative costs.

6. **Front-Running and Order Manipulation** - Transparent order books allow malicious actors to front-run trades and manipulate pricing.

7. **Whale Position Exposure** - Large lenders face privacy risks as their position sizes and strategies become visible to the market, enabling targeted manipulation.

---

## Solution

Equinox introduces an order book-based multi-collateral lending protocol that addresses these fundamental issues through core innovations:

1. **Multi-Collateral Lending System** - Support for multiple asset types (USDC, SUI, ETH) as both lending assets and collateral. Users can diversify their collateral portfolio and access better rates through flexible collateral composition.

2. **Dynamic Order Book Matching** - Users place custom limit or market orders specifying their exact terms (interest rate, LTV ratio, term duration, collateral preferences). Orders are matched dynamically based on compatibility, enabling true price discovery and capital efficiency.

3. **Zero-Knowledge Privacy Orders with Hidden Positions** - Order details and position sizes remain hidden using native Sui zero-knowledge proofs until a match is achieved. Pending orders display no position details, protecting whale lenders from targeted attacks and front-running.

4. **AI-Verifiable Fair Matching via Nautilus** - Off-chain AI compute through Sui's Nautilus ensures fairness in matching by prioritizing retail users, diversifying counterparty risk, and maintaining inclusive access. All computations are verifiable on-chain.

5. **Vesting-Integrated Collateral Vault** - Holders of vested tokens can lock their assets as collateral with ZK proofs of vesting status, earning yield while reducing ecosystem selling pressure.

---

## Key Advantages

| Advantage                | Description                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
| Multi-Collateral Support | Accept multiple asset types (USDC, SUI, ETH) as collateral with flexible composition |
| Capital Efficiency       | Order book model eliminates idle liquidity common in pooled systems                  |
| Customizable Terms       | Users define their own rates, LTV, and duration instead of accepting pool rates      |
| Privacy Protection       | ZK-hidden orders and positions prevent information leakage and front-running         |
| Whale Privacy            | Pending order positions are hidden to protect large lenders from targeted attacks    |
| Algorithmic Fairness     | AI-verified matching ensures retail users receive priority access                    |
| Ecosystem Stability      | Vesting vault mechanism reduces token selling pressure                               |
| Fast Finality            | Sui's Mysticeti consensus provides sub-second transaction confirmation               |
| Frictionless Onboarding  | zkLogin enables access via existing Google, email, or social accounts                |
| Low Transaction Costs    | Sui's efficient execution allows frequent order adjustments without prohibitive fees |

---

## Core Features

### 1. Multi-Collateral Lending System

Equinox supports multiple asset types for both lending and collateral:

- USDC, SUI, and ETH as accepted collateral types
- Flexible collateral composition for improved capital efficiency
- Cross-asset lending and borrowing opportunities
- Dynamic collateral ratio calculations based on asset volatility
- Seamless integration with DeepBook for liquidation routing

### 2. Dynamic Order Book Matching

Place limit and market orders with fully customizable parameters:

- Minimum or maximum interest rate
- Loan-to-Value (LTV) ratio preferences
- Term duration (fixed or flexible)
- Collateral asset preferences and requirements

Orders are matched when lender and borrower terms align, creating efficient two-sided markets.

### 3. ZK-Privacy Orders with Hidden Position Details

Order details are encrypted using zero-knowledge proofs native to Sui blockchain:

- Order parameters remain hidden until matched
- Pending orders show no position size or value details for whale privacy
- Prevents front-running and sandwich attacks
- Provides institutional-grade privacy for all users
- No information leakage during order placement

### 4. AI-Verifiable Fair Matching

Nautilus enables off-chain AI computation with on-chain verification:

- Fairness scoring prioritizes smaller retail orders
- Risk diversification algorithms prevent concentration
- Inclusive matching boosts for underserved user segments
- Fully verifiable and auditable matching logic

### 5. Vesting-Integrated Collateral Vault

Designed specifically for Sui ecosystem stability:

- Lock vested tokens as collateral with ZK proof of vesting status
- Earn subsidy APR for contributing to liquidity stability
- Receive priority matching as a reward for lock-up commitment
- Reduces circulating supply pressure from vesting unlocks

### 6. Gamified and Inclusive User Experience

Engagement-focused design with practical benefits:

- Fairness badges for consistent participation
- Sponsored transactions for small retail orders
- Referral revenue sharing via DeepBook integration
- Interactive dashboard with real-time metrics

---

## Target Market

### Primary Users

**Retail and Emerging Market Users**

- First-time DeFi users seeking simple onboarding via zkLogin
- Users in regions with limited banking infrastructure
- Small-scale lenders and borrowers seeking fair rates

**Institutional and High-Net-Worth Users**

- Traders requiring privacy for large positions
- Whale lenders seeking hidden order details to prevent targeted attacks
- Funds needing customizable lending terms with multi-collateral support
- Market makers seeking efficient capital deployment

**Vested Token Holders**

- Early investors with locked Sui or partner tokens
- Team members with vesting schedules
- Ecosystem participants seeking yield on illiquid positions

**Developers and Builders**

- Protocols seeking composable lending primitives
- Applications requiring programmable loan objects
- Builders extending the Sui DeFi ecosystem

---

## Concept and Mechanism

### How It Works

Equinox operates as a two-sided order book where lenders and borrowers place orders with specific terms. The matching engine finds compatible counterparties, creates on-chain loan objects, and manages the lifecycle from origination to repayment or liquidation.

### Multi-Collateral System

The multi-collateral system enables flexible asset management:

1. **Asset Registration** - USDC, SUI, and ETH are registered as supported assets in the protocol
2. **Collateral Deposit** - Users can deposit multiple asset types as collateral
3. **Weighted Valuation** - Collateral value is calculated based on oracle prices with asset-specific risk weights
4. **Cross-Asset Loans** - Borrow one asset while providing different assets as collateral
5. **Liquidation Routing** - DeepBook integration enables efficient liquidation across all supported pairs

### Hidden Position Privacy

Position privacy is designed to protect whale lenders:

1. **Pending Order Masking** - When orders are pending (not yet matched), position details are hidden from public view
2. **ZK Proof Verification** - Cryptographic proofs verify order validity without revealing amounts
3. **Match Revelation** - Position details only become visible after successful order matching
4. **Anti-Front-Running** - Hidden positions prevent targeted manipulation of large orders
5. **Dashboard Privacy Mode** - Users can toggle visibility of their own position details

### Lender Journey

1. **Authentication** - Connect via zkLogin using Google, email, or social account
2. **Deposit** - Transfer assets to the Equinox vault (USDC, SUI, or ETH)
3. **Order Placement** - Create a hidden limit lend order specifying minimum rate, maximum LTV, term, size, and accepted collateral types
4. **AI Fairness Check** - Order enters the matching queue with fairness scoring
5. **Match Execution** - When a compatible borrower order exists, a loan object is created
6. **Monitoring** - Track yield accrual and earn fairness badges through the dashboard (position details hidden until matched)

### Borrower Journey

1. **Authentication** - Connect via zkLogin
2. **Collateral Deposit** - Provide multi-asset collateral including vested assets if applicable
3. **Order Placement** - Create a borrow order with maximum acceptable rate, minimum LTV, and term
4. **Matching with Boost** - Retail users receive priority in fair matching algorithm
5. **Loan Execution** - Receive borrowed assets upon successful match
6. **Repayment** - Pay back principal plus interest, with sponsored transactions for small amounts

### Matching Engine

The matching engine runs client-side as a deterministic ranker and falls back to a pure on-chain entry when the off-chain enclave is unavailable.

**Phase 1: Client-side Ranking (`lib/matching/ranker.ts`)**

- Filter pairs that pass the protocol rules: borrower rate ≥ lender minimum rate, lender duration ≥ borrower duration, asset and collateral types align, amount delta within tolerance.
- Score the surviving pairs with a composite signal:
  - **Size fit (45%)** — closer amounts settle more reliably on-chain.
  - **Duration fit (25%)** — terms that match avoid early-recall friction.
  - **Rate spread (20%)** — wider gap → more economic surplus to share.
  - **Age priority (10%)** — older orders (price-time priority).
- Surface the breakdown to the user in a preview modal before signing.

**Phase 2: Settlement**

The user picks one of two paths from the preview modal:

- `match_orders` — Nautilus enclave signs the (lend_id, borrow_id, score) tuple. The Move contract verifies the Ed25519 signature against a registered enclave before settling.
- `match_best_offer` — pure on-chain entry, no Nautilus dependency. Anyone can call it; the Move contract enforces the same rule set deterministically. Used automatically as fallback when the enclave call fails or is unconfigured.

Both paths converge on the same loan creation logic: midpoint rate, lender receives the `Loan<Asset, Collateral>` object, borrower receives the principal, collateral locks inside the loan object until repayment or liquidation. Mysticeti finality lands matches in ~400 ms.

### Vesting Integration

Vested token holders follow a specialized flow:

1. **Proof Generation** - Upload ZK proof of vesting status and schedule
2. **Vault Lock** - Lock vested assets in the specialized vesting vault
3. **Yield Earning** - Receive subsidy APR for liquidity contribution
4. **Priority Matching** - Gain matching priority as collateral provider
5. **Ecosystem Impact** - Contribute to reduced selling pressure and improved token stability

### Aggregator Vault (Nautilus-driven Yield Router)

A separate path for users who want passive yield without managing individual orders. The vault holds a single asset and routes capital across multiple markets according to plans signed by the Nautilus enclave.

**Flow**

1. **Deposit** - User calls `vault::deposit` and receives shares 1:1 with the underlying asset.
2. **Plan Request** - The keeper asks the enclave for an allocation plan: a list of `(market, amount, rate, duration)` legs.
3. **Plan Signing** - The enclave signs each leg as `vault_id || nonce || market_id || amount || rate || duration` (all u64 little-endian).
4. **Execution** - The keeper submits each leg via `vault::execute_allocation_leg`. The Move contract verifies the Ed25519 signature against the registered enclave key before splitting the deposit and placing a lend order on the target market.
5. **Withdraw** - Idle balance can be withdrawn at any time via `vault::withdraw` (subject to capital not currently deployed).

This is where the verifiable off-chain compute story actually pays off: the enclave's recommendation is non-trivial (multi-market yield optimization) and the on-chain check is cheap (one signature verification per leg).

---

## Technical Architecture

### Smart Contracts (Move Language)

- **Market Module** - Multi-collateral order book management with support for USDC, SUI, and ETH. Provides two settlement entries: `match_orders` (Nautilus-signed fairness proof) and `match_best_offer` (deterministic price-time priority, no enclave required as fallback).
- **Loan Module** - Creates independent objects for each loan position. `repay` and `liquidate_defaulted_loan` refund overpayment to the caller and pay the lender principal + interest.
- **Registry Module** - Asset registry for supported collateral types and configurations (max LTV, liquidation threshold, liquidation bonus, DeepBook pool routing).
- **Vesting Module** - Manages lock-up mechanics with Groth16 BN254 ZK proof verification, subsidy distribution, and collateralization hooks. Vested borrow orders require an authenticated `&VestingPosition` reference to claim the priority boost.
- **Vault Module** - `AggregatorVault<T>` Nautilus-driven yield router. Users deposit a single asset; the off-chain enclave designs an allocation plan and signs each leg; the vault verifies signatures on-chain before routing capital across markets.

### Off-Chain Infrastructure

- **Nautilus** - Verifiable off-chain compute. Two integration paths:
  - Fairness scoring for order matching (optional, with deterministic fallback).
  - Allocation planner for the aggregator vault (signs `vault‖nonce‖market‖amount‖rate‖duration` per leg).
- **Walrus** - Decentralized storage for vesting proofs and historical order data.

### Frontend Application

- **Framework** - Next.js 16 with React 19.
- **Matching engine** - Pure deterministic ranker (`lib/matching/ranker.ts`) ranks all viable (lend, borrow) pairs by composite score: size fit, duration fit, rate spread, age priority. Top match drives the on-chain settlement.
- **Authentication** - Sui zkLogin SDK + Enoki API for custom OAuth client IDs.
- **Interface** - Gamified dashboard with real-time fairness metrics, match preview modal, position privacy controls.
- **Tests** - `npm test` runs vitest. Unit + 100-order simulation for the ranker.

### External Integrations

- **DeepBook V3** - Liquidation routing via `swap_exact_quantity`; lender is paid first, liquidator keeps the swap surplus.
- **Price Oracles** - Pyth Network for accurate collateral valuation.
- **Mysticeti** - Sui's consensus mechanism for sub-second finality.

---

## Deployed Contracts

The following contracts are deployed on Sui Testnet.

### Core Package and Shared Objects

| Component               | Address                                                              |
| ----------------------- | -------------------------------------------------------------------- |
| Package ID              | `0xb4131de782309ff0f9abf46f9eebe92984b2b62dc0edc67917241937b222c373` |
| Registry                | `0xd2387d19331d4e1a791fd4345d1d8b695228beecfae9f8497b5f8483531c5419` |
| Registry AdminCap       | `0x184078a57b62fedaf01f361558c352cfafc84a49d8977405ba3389a656477bf6` |
| Legacy Vesting Vault    | `0x2490fbec70b7a49037a64589dc67fd8a834a5b422aabac0977e050462fd9a4cf` |

### Markets

| Pair (Asset / Collateral) | Market ID                                                            |
| ------------------------- | -------------------------------------------------------------------- |
| USDC / SUI                | `0x9f75f8a3eecfbaa128475d85b9d0482644c5cfa501f09a9c1ea0c14d71f976d2` |
| SUI / USDC                | `0xb2318f3f519aca72ad575a4cffdd74d34564d2c12082fdc56a3af6baa4869862` |

### Aggregator Vault (Nautilus-driven yield router)

| Component                   | Address                                                              |
| --------------------------- | -------------------------------------------------------------------- |
| AggregatorVault<MOCK_USDC>  | `0x55ffa907ec596c1f495d485dc735e82f6d62cdfb470cfe9f3e37d6f61b416ff9` |

### Nautilus Enclave

| Component         | Address                                                              |
| ----------------- | -------------------------------------------------------------------- |
| EnclaveConfig     | `0x444fdef3865dbe58b1d9e3e44e2d13587a1453ac5bd4926c48380bcb4b86c479` |
| RegisteredEnclave | `0x31f7b357bf062d6d298b3844f988bc3017b9110669d69a03643afe5e17bed161` |

### Faucet Capabilities (shared, public mint)

| Asset          | Admin Cap ID                                                         |
| -------------- | -------------------------------------------------------------------- |
| USDC Admin Cap | `0x09c36d6877c00fe9ac1eaa49e367e2ffc47a1f8d2d156ca488ece2ab2c31371f` |
| ETH Admin Cap  | `0x530478a6bb66575f95a913f815771ce42df0196bbbde59494c79cbf1c6b9193f` |

### Registry Configuration

| Asset | Role                | Max LTV | Liquidation Threshold | Liquidation Bonus |
| ----- | ------------------- | ------- | --------------------- | ----------------- |
| SUI   | Asset + Collateral  | 75%     | 85%                   | 5%                |
| USDC  | Asset + Collateral  | 80%     | 85%                   | 3%                |
| ETH   | Asset + Collateral  | 70%     | 80%                   | 5%                |

Interest rate band per asset: 1% — 50% APR.

### Network Configuration

- **Network**: Sui Testnet
- **RPC URL**: https://fullnode.testnet.sui.io:443
- **Deployment Date**: 2026-05-05
- **Deployer**: `0x8c4551885e339c4b2cd88cb96f0fe34186a5a1dd03667957187c257c02e88776`

---

## Quick Start

### Frontend

```bash
cd equinox-interface
cp .env.example .env.local   # already populated with deployed object IDs in this repo
npm install
npm run dev                   # http://localhost:3000
npm test                      # vitest — ranker unit + 100-order simulation
```

### Move contracts

```bash
cd contracts/equinox
sui move build                # compile
sui move test                 # 12 unit tests including match_best_offer settlement
```

### Bootstrap a fresh deployment

If you republish the package, repeat these on-chain steps in order (the deployer must hold the registry `AdminCap`):

1. `registry::add_collateral<T>` for SUI, USDC, ETH (max LTV / liq threshold / liq bonus).
2. `registry::add_asset<T>` for SUI, USDC, ETH (min / max interest rate basis points).
3. `market::create_market_standalone<Asset, Collateral>` for each pair you want to expose.
4. `vault::create_vault<T>` to spin up an aggregator vault for the chosen asset.
5. `market::register_enclave_config` then `market::register_enclave` with the Ed25519 public key derived from `NEXT_PUBLIC_NAUTILUS_DEV_PRIVATE_KEY`.
6. Update `equinox-interface/.env.local` with the new object IDs.

---

## Why Sui Blockchain

Equinox leverages Sui's unique capabilities that make this design possible:

| Sui Feature          | Equinox Application                                              |
| -------------------- | ---------------------------------------------------------------- |
| Mysticeti Consensus  | Sub-second finality enables real-time dynamic matching           |
| Object-Centric Model | Each loan is an independent object for parallel processing       |
| Parallel Execution   | High throughput without congestion during peak demand            |
| Native ZK Support    | Efficient zero-knowledge proof verification for hidden positions |
| Nautilus Stack       | Verifiable off-chain compute exclusive to Sui                    |
| Walrus Storage       | Trusted decentralized storage for sensitive data                 |
| zkLogin              | Frictionless onboarding without wallet complexity                |
| Low Fees             | Frequent order updates remain economically viable                |

---

## Links

| Resource          | Link                                                  |
| ----------------- | ----------------------------------------------------- |
| Live Application  | [Launch App](https://equinox-fi.vercel.app)           |
| GitHub Repository | [View Code](https://github.com/yeheskieltame/Equinox) |

---

Built for HackMoney x Sui 2026
