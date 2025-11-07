+++
title = "How DeFi Lending Actually Works?"
date = "2022-09-28"
description = "A technical deep-dive into decentralized lending protocols, consensus mechanisms, and why over-collateralization matters."
tags = [
    "defi",
    "lending",
    "ethereum",
    "aave",
    "compound",
]
+++

Traditional finance runs on intermediaries. You want to borrow money? Go through a bank. Want to earn yield on your savings? Give it to a bank and hope they don't blow it up. DeFi promised to change this by replacing trusted intermediaries with code. But how does it actually work?

<!--more-->

## Understanding Blockchain Consensus: The Foundation

Before diving into lending protocols, we need to understand how transactions get validated on blockchains. This matters because different consensus mechanisms affect cost, speed, and decentralization—all critical for DeFi usability.

### Proof of Work: Bitcoin's Model

Bitcoin uses Proof of Work (PoW), where miners compete to solve complex computational puzzles. First one to solve it gets to add the next block and earns bitcoin rewards.

**The problem with PoW:**
- Energy consumption is massive
- Mining becomes centralized (whoever can afford the best hardware wins)
- Slow and not scalable
- As difficulty increases, only large mining operations survive

This is why Ethereum moved away from PoW on September 15, 2022.

### Proof of Stake: Ethereum's Evolution

Proof of Stake (PoS) replaced miners with validators who stake ETH as collateral. The more ETH you stake, the higher your chances of being selected to validate transactions. If you validate honestly, you earn rewards. If you try to cheat, you lose your stake (called "slashing").

**PoS advantages:**
- ~99.95% less energy consumption than PoW
- Much more scalable
- Faster transaction finality

**The tradeoff:**
PoS favors the wealthy. More tokens = more voting power = more validation opportunities = more rewards. This creates a rich-get-richer dynamic that somewhat contradicts the decentralization ethos.

**My take:** Perfect decentralization is impossible. PoS is a pragmatic compromise that makes Ethereum actually usable for DeFi applications. The scalability gains are worth the tradeoff.

---

## What is DeFi Actually Doing?

In traditional finance, you need trusted intermediaries—banks, brokerages, payment processors. They custody your assets, verify transactions, and theoretically keep everything fair.

DeFi replaces these intermediaries with smart contracts. Instead of trusting Bank of America to handle your money, you trust code that's publicly verifiable and automatically enforced by the blockchain.

**Smart contracts** are programs running on Ethereum (usually) that execute automatically when certain conditions are met. They're public, auditable, and can't be changed once deployed (in most cases).

This transparency is powerful. With a bank, you have no idea what they're doing with your deposits. With a DeFi protocol, anyone can read the code and verify exactly how it works.

---

## How DeFi Lending Protocols Work

Let me walk through how protocols like Aave and Compound actually function.

### The Basic Model

**Lenders (Suppliers):**
- Deposit tokens (ETH, USDC, DAI, etc.) into a liquidity pool
- Earn interest based on current utilization rates
- Can withdraw anytime (if there's liquidity available)

**Borrowers:**
- Provide collateral (must be worth more than what they borrow)
- Pay interest on borrowed assets
- Must maintain collateralization ratio or face liquidation

The interest paid by borrowers becomes the interest earned by lenders (minus protocol fees).

### Markets and Liquidity Pools

Protocols create separate markets for each asset. There's an ETH market, a USDC market, a DAI market, etc.

When you lend USDC, your tokens go into the USDC liquidity pool and become available for others to borrow. You start earning interest immediately based on the current borrow rate.

---

## The Over-Collateralization Question

Here's what confuses people: **almost all DeFi lending is over-collateralized.**

If you want to borrow $1,000 USDC, you might need to deposit $1,500 worth of ETH as collateral.

**Wait, what? Why would anyone do this?**

Good question. Here are the real use cases:

### 1. Tax Optimization
Selling assets triggers capital gains tax. Borrowing against them doesn't. If you're sitting on ETH that's up 5x but need cash, you can borrow stablecoins without realizing gains.

### 2. Maintaining Exposure
You believe ETH will keep going up, but you need liquidity now. Borrowing lets you access cash without selling your position.

### 3. Leverage
Borrow stablecoins against ETH → Buy more ETH → Repeat (carefully). This amplifies both gains and losses.

### 4. Yield Farming
Borrow Asset A at 5% APY → Lend it somewhere else at 8% APY → Pocket the spread (if you can maintain your collateral ratio).

**Reality check:** Most borrowing in DeFi during 2020-2021 was for leverage and yield farming, not practical needs. When markets crashed in 2022, over-leveraged positions got liquidated en masse.

---

## Collateralization Factors

The **collateralization factor** determines how much you can borrow relative to your collateral value.

On Compound, for example:
- ETH and DAI have a 75% collateral factor
- You deposit $1,000 of ETH → You can borrow up to $750 of other assets

Different assets have different factors based on their risk profile. More volatile assets have lower collateral factors because they're more likely to drop in value quickly.

### Liquidation: When Things Go Wrong

Your borrowed value must always stay below your collateral value × collateral factor.

**Example:**
- You deposit $1,000 ETH (75% collateral factor)
- You borrow $700 USDC
- ETH drops 30% → Your collateral is now worth $700
- $700 × 0.75 = $525 max borrow capacity
- But you've borrowed $700 → **You get liquidated**

When liquidation happens:
1. Liquidators (usually bots) repay part of your debt
2. They receive your collateral at a discount (typically 5-10%)
3. You lose your collateral but your debt is cleared

During market crashes, liquidation cascades can be brutal. I've seen this firsthand—when ETH dropped from $1,800 to $1,000 in June 2022, thousands of positions got liquidated in hours.

---

## Interest Rates: Supply and Demand

Interest rates in DeFi are algorithmically determined based on utilization:

**Utilization Rate = Total Borrowed / Total Supplied**

- Low utilization (lots of idle capital) → Lower interest rates
- High utilization (most capital borrowed) → Higher interest rates

This creates a natural equilibrium. When rates are high, more people want to lend (increasing supply) and fewer want to borrow (decreasing demand), which brings rates back down.

**The spread:**
Borrowers pay more than lenders earn. The difference goes to the protocol (and sometimes token holders).

Example:
- Borrow rate: 5% APY
- Supply rate: 3% APY
- Protocol takes 2% as revenue

---

## CeFi vs DeFi: The Key Differences

### CeFi (Centralized Finance)
Platforms like Binance, Celsius, BlockFi operate like traditional banks:
- They custody your assets
- They lend to institutional clients (market makers, hedge funds)
- You trust them to manage risk properly

**The problem:** We've seen what happens when this trust breaks. Celsius, Voyager, BlockFi—all collapsed in 2022, taking billions of user funds with them.

### DeFi (Decentralized Finance)
Protocols like Aave, Compound operate on smart contracts:
- You maintain custody of your assets (until you deposit them)
- Lending/borrowing happens peer-to-peer via smart contracts
- Everything is transparent and verifiable
- No permission needed—anyone can participate

**The tradeoff:** You're responsible for your own security. No customer support to call if you send tokens to the wrong address.

---

## Why This Matters

DeFi lending isn't perfect, but it's fundamentally different from traditional finance:

**Transparency:** Anyone can audit the code and verify reserves
**Accessibility:** No credit checks, no minimum balances, no geographic restrictions
**Composability:** Protocols can build on top of each other
**No counterparty risk:** Smart contracts can't run away with your money (in theory)

**But also:**
- Smart contract bugs can drain funds
- Over-collateralization limits use cases
- High gas fees can make small transactions uneconomical
- Liquidations during market crashes are brutal

---

## My Experience at Morpho

I wrote this during my internship at Morpho Labs in September 2022. Morpho was building a new model to optimize lending rates by matching lenders and borrowers peer-to-peer while using Aave and Compound as fallback liquidity.

Working there gave me a front-row seat to how these protocols actually function at the infrastructure level. The amount of complexity hidden behind "deposit and earn yield" is staggering—rate calculations, liquidation mechanics, oracle dependencies, gas optimization.

DeFi lending works, but it's still early. We're building the financial infrastructure of the future, but we're not there yet.

---

## What's Next?

In future posts, I'll dive into:
- How Morpho optimizes lending rates
- The oracle problem in DeFi
- Real yield vs ponzi yield
- Account abstraction and its impact on DeFi UX

---

*This article is based on my research and experience from September 2022. Protocol mechanics may have evolved since then.*

*Not financial advice. DeFi is risky. Only invest what you can afford to lose.*