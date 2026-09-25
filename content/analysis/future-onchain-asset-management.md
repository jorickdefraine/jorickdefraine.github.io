+++
title = "Stablecoins Were the First Floor: Where On-Chain Asset Management Is Heading"
date = "2026-09-25"
description = "Tokenized fund shares used as collateral, vaults as the standard form of delegated management, 24/7 stock tokens, and the one question that will decide it all: which rails."
tags = [
    "defi",
    "vaults",
    "curators",
    "rwa",
    "tokenization",
    "regulation",
]
+++

Stablecoins took the dollar on-chain. Around $306 billion of them now circulate, and their reserves are large enough to matter for the US T-bill market. That story is well covered. The next one is less so: what is being tokenized today is no longer just the unit of account, but the fund share itself, and with it the whole value chain of asset management.

<!--more-->

This piece started as the closing section of an academic manuscript on crypto-asset markets. It didn't make the final cut, so here it is in a freer form, with the numbers as of 24 September 2026.

**Disclosure:** I used to work at Morpho, and several examples below run on Morpho. I analyze vault risk independently today, including for vaults curated by the firms named here.

---

## From tokenization to composability

Excluding stablecoins, **$38.7 billion** of real-world assets are held in tokenized form, spread across 212 platforms and about 4.7 million holders. Of that, **$14.9 billion** sits in money market funds and short-term government debt, and **$8.0 billion** in private credit ([RWA.xyz](https://app.rwa.xyz)).

A quick warning on that dataset: RWA.xyz also reports a "represented value" of around $358 billion. It includes registries that are recorded on-chain but never distributed as tokens (one HELOC ledger alone accounts for $23 billion). The two numbers should never be added together.

Tokenization on its own is not the interesting part. A fund share on a private ledger is still just a fund share. What changes things is what the share can *do* once it lives on a public network.

### The SAFO case: a whole fund value chain, rebuilt on public rails

The clearest example to date happens to be French.

- **SAFO** (Spiko Amundi Overnight Swap Fund) is an overnight fund launched in March 2026 by Amundi and Spiko, a firm licensed as an investment firm by the ACPR.
- Since **22 July 2026**, SAFO shares have been accepted as collateral on **Morpho**, in a market curated by **Steakhouse Financial** ([Spiko](https://www.spiko.io/blog/borrow-stablecoins-against-your-safo-shares)).
- Holders borrow **EUR CoinVertible** against them, a MiCA-compliant euro stablecoin issued by **SG-FORGE**.
- The fund's net asset value (NAV) is published on-chain by the fund administrator, CACEIS, through a Chainlink oracle. If the collateral runs short, part of it is sold automatically.

Put together, that is the full value chain of a regulated fund (management, custody, valuation, distribution, and financing leverage against it) reassembled on public infrastructure. Spiko pitches it as retail access to Lombard credit, and that is a fair description.

### The other side of composability

Composability works in both directions. Shares of **ACRED**, the tokenized Apollo credit fund issued with Securitize, yield 7 to 9%. On Morpho they are **levered two to three times** through a Gauntlet-optimized vault, and the collateral underneath is illiquid first-lien corporate credit maturing in **seven to ten years**.

That is a liquidity mismatch of the same kind people worry about with stablecoins, except that it sits on private credit. The good news is that, unlike in traditional finance, it can be measured in public data:

- the **gap between the token price and the NAV** reported by the oracle;
- the **depth and frequency of liquidation cascades** when that gap opens.

If I had to pick one on-chain risk signal to watch for tokenized credit, it would be the first one.

---

## Vaults: the standard form of delegated management

This is where most of the action is.

### The scale

DefiLlama now tracks two categories dedicated to delegated management: **Risk Curators** (86 entities, $9.6 billion) and **Onchain Capital Allocators** (79 entities, $9.2 billion). Together, that is close to **$19 billion allocated under predefined mandates** by 165 managers ([DefiLlama](https://defillama.com)).

The trajectory matters more than the level:

| | Sept 2024 / Nov 2024 | Sept 2025 | Sept 2026 |
|---|---|---|---|
| Steakhouse Financial (curator) | $93M (Nov) | $1.30B | $2.58B |
| Morpho Blue | $0.98B | $7.19B | $10.80B |
| Aave V3 | $11.46B | $39.60B | $18.04B |

TVL is price-sensitive, so absolute numbers mean little in a market that is down about 52% from its October 2025 peak. But over the same year Aave V3 was **divided by 2.2** while the leading curator **doubled**. That relative gap is not a price effect: **delegation is gaining share**.

Traditional managers are moving in too. **Bitwise**, with more than $15 billion of client assets, became a non-custodial vault curator on Morpho on 26 January 2026, targeting 6% on stablecoins ([announcement](https://www.prnewswire.com/news-releases/bitwise-expands-onchain-solutions-with-introduction-of-non-custodial-vault-curation-on-morpho-302670308.html)).

Why vaults, rather than direct lending? Because lending markets are getting more expressive. [Morpho Midnight](https://www.theblock.co/post/409062/morpho-midnight-fixed-rate-lending-protocol-base-onchain-credit-markets), launched on Base on 21 July 2026, adds fixed rates, fixed maturities and more than 120 collateral types. More choice for the lender also means more positions to track and maintain. A vault turns that complexity into a set of predetermined rules that allocate across many markets at once.

### "Vault" means very different things

The problem is that the same word now covers very different custody models, permissions and guarantees.

Paul Frambot, co-founder and CEO of Morpho, published *The Next Phase of Vaults* on 24 September 2026, the day of the Singapore Vault Summit. He proposes to separate two families:

- **Non-custodial vaults.** The curator cannot increase risk or take control of funds without users being able to leave first. In practice: a mandatory timelock on any risk-increasing change, an exit window during that timelock, a Guardian/Sentinel role that can cancel the change on users' behalf, role-based access control, in-kind redemptions (exiting into the underlying market positions instead of relying on the manager to unwind), and immutable contracts.
- **Discretionary vaults.** The manager has much more room on allocation and strategy (market making, leverage, multi-chain deployment), and depositors are trusting the manager's judgment and risk management.

His operational test is the most useful line in the piece: **what happens if the operator is hacked, disappears, or acts in bad faith?** If users can exit within a reasonable delay without depending on the curator, the vault is non-custodial.

That taxonomy should be read for what it is: a position from an industry participant, which also serves Morpho's interest in having non-custodial vaults recognized as a distinct regulatory category. What makes it more than marketing is that a regulator is drawing the same line.

### The SEC is drawing the same spectrum

On 22 July 2026, SEC Commissioner Hester Peirce published [*Headstands and Summervaults*](https://www.sec.gov/newsroom/speeches-statements/peirce-statement-crypto-vaults-lending-strategies-072226), a statement on crypto vaults and lending strategies. Her key points:

- putting an activity on-chain does not take it out of the scope of federal securities law;
- vaults sit on a spectrum "from programmatic allocations determined solely by immutable smart contracts, to allocations at the sole discretion of another person or group of persons";
- a vault can be a common enterprise whose profits come from "the vault deployer's and curator's entrepreneurial or managerial efforts";
- depending on structure, some look like unit investment trusts, some like management investment companies, others like separately managed accounts.

It is an individual statement, not a position of the Commission. But the underlying question is exactly the one Frambot's test answers: does the depositor's expected return rest on the curator's managerial efforts, or on code?

### Why this matters beyond regulation

For anyone who analyzes managers, this setup offers something traditional vehicles never could: **a complete panel of delegated portfolios where every allocation, fee and risk parameter is observable at block frequency**. No quarterly disclosures, no self-reported numbers.

And there is something genuinely new here. In traditional delegated management, the agency problem is handled **ex post, by law**: you sue the manager. In a non-custodial vault, it is handled **ex ante, by code**: a timelock plus a right to exit. That is directly testable:

- Do depositors actually use their exit window before a risk increase goes live?
- Does the non-custodial vs. discretionary classification predict returns, fees, and losses in a shock?
- Do curators herd, piling into the same collateral at the same time?
- Do fee structures create measurable conflicts of interest (for example, chasing yield by adding riskier markets)?

These are the questions I think vault risk analysis should answer, and they can be answered with public data.

---

## Distribution is going on-chain too

Tokenized equities are still small: **$3.1 billion**. But they already have **3.9 million holders**, up 72% in 30 days ([RWA.xyz](https://app.rwa.xyz/stocks)). Distribution is running ahead of assets under management.

- On **1 July 2026**, Robinhood, with about 28 million clients, launched the mainnet of its own network, [Robinhood Chain](https://robinhood.com/us/en/newsroom/robinhood-accelerates-global-expansion-robinhood-chain-mainnet-stock-tokens-agentic-trading/), offering stock tokens that trade 24/7 in more than 120 countries (outside the US).
- Coinbase has offered tokenized US equities on Base since 24 August 2026.
- Steakhouse already curates vaults on Robinhood Chain. In other words, a retail broker is outsourcing the risk management of its lending markets to an on-chain curator. That is the vault story from the previous section, arriving through the front door of retail.

A security that trades continuously on-chain and six and a half hours a day on the NYSE also raises a clean market-structure question: **where does price discovery happen** when one venue is open and the other is closed, and what does the on-chain price tell you on Monday morning?

---

## The real question: which rails

Whether all this consolidates depends on the rails it is allowed to run on, and the signals point in two directions.

**Opening up, in the US and Europe:**

- On **17 September 2026**, the SEC granted a [conditional five-year exemption](https://www.sec.gov/newsroom/press-releases/2026-90-sec-issues-innovation-exemption-facilitate-trading-tokenized-nms-stock-request-comment) allowing tokenized listed shares to trade through permissioned automated market makers on public blockchains (Release No. 34-106402).
- The **Clarity Act** passed the House in July 2025 but is still awaiting a Senate vote.
- In Europe, **MiCA** is under review, alongside a proposed overhaul of the DLT Pilot Regime for market infrastructure (ESMA reported on it in March 2026; the reform is expected to run through 2027).

**Pushing back:**

- The Bank for International Settlements, in its [2026 Annual Economic Report](https://www.bis.org/publ/arpdf/ar2026e3.htm), considers permissionless networks structurally ill-suited to carrying the financial system, and advocates a **unified ledger on permissioned networks**: central bank reserves, commercial bank money and tokenized assets on one interoperable, closed ledger.

So the open question is not *whether* asset management moves on-chain. It is **on which rails**: public and composable, or permissioned and compartmentalized.

That choice matters for more than efficiency. Everything described above (the NAV discount on tokenized credit, liquidation cascades, curator herding, depositors' exit behavior, cross-venue price discovery) is visible today because it happens on public ledgers. On permissioned rails, the same risks would still exist. We would simply lose the ability to see them.

---

## Sources

Data as of 24 September 2026.

- RWA.xyz, [tokenized real-world assets](https://app.rwa.xyz), [tokenized stocks](https://app.rwa.xyz/stocks). Distributed value only; not to be added to represented value.
- DefiLlama, *Risk Curators* and *Onchain Capital Allocator* categories, protocol series for Steakhouse Financial, Morpho Blue and Aave V3 ([API](https://api.llama.fi/protocols)).
- Spiko (2026), [Borrow Stablecoins Against Your SAFO Shares](https://www.spiko.io/blog/borrow-stablecoins-against-your-safo-shares), 22 July 2026.
- CoinDesk (2025), *Tokenized Apollo Credit Fund Makes DeFi Debut With Levered Yield Strategy*, 30 April 2025.
- Bitwise (2026), [Bitwise Introduces Non-Custodial Vault Curation on Morpho](https://www.prnewswire.com/news-releases/bitwise-expands-onchain-solutions-with-introduction-of-non-custodial-vault-curation-on-morpho-302670308.html), 26 January 2026.
- The Block (2026), [Morpho Midnight](https://www.theblock.co/post/409062/morpho-midnight-fixed-rate-lending-protocol-base-onchain-credit-markets).
- Frambot, P. (2026), *The Next Phase of Vaults*, 24 September 2026. See also [Stablecoins Upgraded Money, Vaults Will Upgrade Asset Management](https://morpho.org/blog/stablecoins-upgraded-money-vaults-will-upgrade-asset-management), 21 October 2025.
- Peirce, H. M. (2026), [Headstands and Summervaults: A Statement on Crypto Vaults and Lending Strategies](https://www.sec.gov/newsroom/speeches-statements/peirce-statement-crypto-vaults-lending-strategies-072226), SEC, 22 July 2026. Individual statement.
- Robinhood (2026), [Robinhood Chain Mainnet and Stock Tokens](https://robinhood.com/us/en/newsroom/robinhood-accelerates-global-expansion-robinhood-chain-mainnet-stock-tokens-agentic-trading/), 1 July 2026.
- SEC (2026), [Order Granting Conditional Exemptive Relief to Tokenized Securities Venues](https://www.sec.gov/newsroom/press-releases/2026-90-sec-issues-innovation-exemption-facilitate-trading-tokenized-nms-stock-request-comment), Release No. 34-106402, 17 September 2026.
- ESMA (2026), *Report on the Functioning and Review of the DLT Pilot Regime* (Art. 14 DLTR).
- BIS (2026), [Anchoring Trust in Money: Innovation Beyond Stablecoins](https://www.bis.org/publ/arpdf/ar2026e3.htm), Annual Economic Report, Chapter III, 23 June 2026.
