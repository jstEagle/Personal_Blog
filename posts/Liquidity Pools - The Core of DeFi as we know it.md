---
title: Liquidity Pools - The Core of DeFi as we know it
date: 2025-07-27
author: jstEagle
tags:
  - DeFi
  - Blockchain
  - Educational
---
A lot of Decentralized finance (DeFi) protocols or infrastructure can seem very futuristic and most of all **very** complicated. On the one hand this is because they are often a fusion of traditional finance principles along with math and computer science. But on the other hand, it's also easier to get people to invest into your coin when you call it a *"Algorithmic Stablecoin with Seigniorage-Based Elastic Supply"* instead of *"When price go up, we make more coins. When price go down, we destroy more coins."*

This article is meant to build intuition and build up the understanding to help demystify Automatic Market Makers (AMMs) also known as Liquidity Pools (LPs), the building block of DeFi as we know it. To do that we will cover the following:
- What is a Market Maker?
- What is a LP?
- What makes LPs better than a traditional Market Maker?
- What are some different kinds of LPs and how do they work?
	- Standard LP
	- Concentrated LP (CLMM)
	- Dynamic LP (Constant Product AMM)

### Market Makers
In traditional finance (TradFi) there are 2 main ways in which assets get traded. Over the Counter (OTC) or through an Order Book. OTC orders are pretty self explanatory. Someone makes an offer to either buy or sell and *usually* anyone can accept that offer and provide the other side of the trade.

Order books are where it gets interesting. An order book is just a record of all the [limit orders|Limit orders are buy or sell orders set to execute at a specific price or better] that are open. A trader that puts in an order on either side is called a **maker** and a trader that trades against that order is called a **taker**.

![](orderbooksimple.svg)
Above is a simplified example of what a theoretical order book for Solana (SOL) might look like. Note that the *real* price of SOL at this time would be somewhere between \$150 and \$151. This is because an order book has no indication of what the actual price of SOL is, it only contains a list of orders to execute if the price is at the limit or [better| In this context "better" means that for **buy** side orders, the price is at or lower than the limit. And for **sell** side orders the price is at or above the limit].

A Market Maker is a trader that places both buy and sell side limit orders within a small range of where the *real* price is. This range is called the [spread|Spread is defined as the **highest bid price** and the **lowest ask price** in an order book
$$\text{Spread} = \text{Ask Price} - \text{Bid Price}$$also called the **cost of immediate execution**]
