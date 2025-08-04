---
title: Liquidity Pools - The Core of DeFi as we know it
date: 2025-07-27
author: jstEagle
tags:
  - DeFi
  - Blockchain
  - Educational
---
A lot of Decentralized finance (DeFi) protocols or infrastructure can seem very futuristic and most of all **very** complicated. On the one hand this is because they are often a fusion of traditional finance principles along with math and computer science. But on the other hand, it's also easier to get people to invest into your coin when you call it an *"Algorithmic Stablecoin with Seigniorage-Based Elastic Supply"* instead of *"When price go up, we make more coins. When price go down, we destroy more coins."*

This article is meant to build intuition and build up the understanding to help demystify Automatic Market Makers (AMMs) also known as Liquidity Pools (LPs), the building block of DeFi as we know it. To do that we will cover the following:
- [Market Makers](#Market%20Makers)
- [Automatic Market Makers](#Automatic%20Market%20Makers)
- [How do modern AMMs work?](Liquidity%20Pools%20-%20The%20Core%20of%20DeFi%20as%20we%20know%20it.md#Modern%20AMMs)
- [Impermanent Loss](#Impermanent%20Loss)
- 
______
### Market Makers
In traditional finance (TradFi) there are 2 main ways in which assets get traded. Over the Counter (OTC) or through an Order Book. OTC orders are pretty self explanatory. Someone makes an offer to either buy or sell and *usually* anyone can accept that offer and provide the other side of the trade.

Order books are where it gets interesting. An order book is just a record of all the [limit orders|Limit orders are buy or sell orders set to execute at a specific price or better] that are open. A trader that puts in an order on either side is called a **maker** and a trader that trades against that order is called a **taker**.

![](orderbooksimple.svg)
Above is a simplified example of what a theoretical order book for Solana (SOL) might look like. Note that the *real* price of SOL at this time would be somewhere between 150 and 151. This is because an order book has no indication of what the actual price of SOL is, it only contains a list of orders to execute if the price is at the limit or [better|In this context "better" means that for buy side orders, the price is at or lower than the limit. And for sell side orders the price is at or above the limit].

A Market Maker is a trader that places both buy and sell side limit orders within a small range of where the *real* price is. This range is called the [spread|Spread is defined as the highest bid price and the lowest ask price in an order book also called the cost of immediate execution]. This spread is what makes traditional market making profitable. Any trader who wants to sell SOL [spot|A Spot or Market Order is just an instruction to execute a trade for some amount of money at the best price immediately] will lose a small amount of money by not selling at the *real* price due to the spread of the market maker. This is called **slippage**.

![](orderbookhorizontal.svg)
In our simple orderbook example, we can think of the price of SOL as this imaginary line that goes from 0 to $\infty$. And limit orders as buckets of [liquidity|Simply put: The amount of buy and sell volume available through limit orders at a time (I will elaborate on this more soon)] placed along the way. As these buckets of liquidity get emptied, takers (the active buyers or sellers) need to move further up and down the line to get their orders filled. Of course in reality market makers constantly replenish their offers to always give takers an offer while maintaining their spread. And so as price moves up and down depending on the supply and demand of either side, so does the order book.

![](orderbookhorizontal2.svg)

______
### Automatic Market Makers
With the rise of DeFi and blockchain technology the first Decentralised Exchanges (DEXs) started to appear. But they had some key issues with their order books:
1. **High gas fees** for orders
2. **Slow execution** due to Ethereum block times
3. **Front-Running risks** because pending orders were visible in the [mempool|This isn't important to the article, it just means that pending orders were visible to everyone else]
As a result DEX trading was clunky, expensive, and illiquid.

So in 2018 a breakthrough was made by the [Uniswap](https://app.uniswap.org/) team.

> Instead of matching buyers and sellers, **let traders interact with a pool of assets using a pricing formula**

This is genius because it removes the need for *active* makers to support price, allows anyone to *passively* contribute to an asset pairs liquidity and it was fully on-chain and gas-efficient.

![](constantproductammdiagram.svg)

Above is a visualisation for what a simple **constant product AMM** looks like. Don't worry, it looks *mathy* but it's really not that bad. A **constant product AMM** is simply a [pool|Pools are represented on-chain in various different fashions but that isn't relevant to the scope of this article] that keeps one simple rule. The amount of token $X$ multiplied by the amount of token $Y$ is always a constant $K$. This just means that when a swap happens, the amount of the opposite token a user gets out of the swap is determined by this simple rule $X\times Y = K$. This constant $K$ is just a measure of how much liquidity there is in the pool. So as more tokens get added, the amount the price changes by the same amount of tokens swapped changes.

This is why you often hear that you should be aware of tokens with low liquidity. As this means that a trade of 100 tokens for example, will affect a token with low liquidity much more than a token with a lot of liquidity

> *Note: the amount that the price of the tokens changes is only affected by the amount of tokens traded, not by the dollar value. So a trade of 1000 SOL for example might have the same proportional affect as the trade of 1000 USDC if you had two pools with the same liquidity and ratio of tokens*

Another key difference between this kind of AMM and a traditional order book is that an AMM has **a set value of what the real price is at any ratio of tokens**. However, we also have a problem... how are liquidity providers (the market makers) making their money? Having your money locked up in a liquidity pool can incur both [opportunity cost|The theoretical value of the next best investment you give up when making a choice] and [impermanent loss|The temporary loss in value an LP experiences when the price of tokens in a liquidity pool diverges from their original price due to market movements. (This will be explained further)]. The answer, trading fees. Every trade made through a pool is charged a percentage fee. Usually in equal parts of the two tokens provided in the pool. *Now most pools have very low fees. Usually less than `0.5%`. Some more modern liquidity pool providers also allow for automatic adjusting of fees. So during periods of high volume or high volatility, fees can increase to offset the additional impermanent loss that may be incurred.*

![](Untitled-2025-04-27-1540.svg)
_____
### Modern AMMs
The original Uniswap model was revolutionary and completely changed the DeFi landscape. But since 2018, some improvements have been made.

> **Note:** When exploring Liquidity pools, we usually refer to the two tokens present in a pool as the base token and the quote token. The base token priced in the quote token. i.e. SOL (base token) is priced at 150 USDC (quote token).

##### DLMMs and CLMMs
These are some terms you might have seen if you frequent Solana DeFi on platforms like [Jupiter](https://jup.ag/), [Meteora](https://www.meteora.ag/), [Orca](https://www.orca.so/) or pretty much any other platform that revolves around trading tokens.

**CLMM** stands for **Concentrated Liquidity Market Maker**. Again, sounds very complicated. But isn't actually. Before, we were thinking about the price of SOL moving up and down an infinite range. CLMMs think of prices the same way. However, instead of depositing liquidity into the entire range, it is deposited into buckets called [ticks|A tick is the smallest increment that the price can move in the liquidity pool. This may vary for different pools and providers]. Each tick to the left of the price in a pool would be filled with quote tokens and each tick to the right with base tokens.

![](firstlpsimplediagram.svg)

As shown above, the _real price_ corresponds to the active tick—the one that currently holds a mix of both tokens. This helps explain why ticks on either side contain only one type of token. To the right of the active tick, the price is higher, so these ticks hold only base tokens; buyers must deposit quote tokens to purchase base tokens, pushing the price up. Conversely, to the left, the price is lower, and these ticks hold only quote tokens, as selling base tokens for quote pushes the price down.

**DLMM** stands for **Dynamic Liquidity Market Maker**. It is very similar to **CLMMs** but have some more fancy math and calculations built in to increase efficiency to both reduce fees and increase profits of makers. Below is a simple diagram to try communicate what liquidity might look like in a **DLMM**. The shape of the liquidity may change depending on the characteristics that are desired. If it is a [stable pair|A liquidity pool that contains two different stable coins tracking the same thing. i.e. USDC-USDT] or a memecoin pool all affect how the equations controlling the liquidity might be set up.

![](DLMMdiagram.svg)

**DLMMs** may also change how liquidity acts inside ticks. Instead of behaving like a simple constant product AMM inside each tick, DLMMs can use other formulas that better fit the token pair’s nature (e.g. stableswap curves for stablecoins).
_______
### Impermanent Loss
Earlier defined as
> The temporary loss in value an LP experiences when the price of tokens in a liquidity pool diverges from their original price due to market movements.

This is one of the more difficult concepts to understand so don't feel discouraged if you have to read this section a couple of times to fully grasp it.

Let's ease into this explanation with an analogy. Meet **Ray**. He loves trading Solana (SOL). However, Ray has learned that if you don't take profits on the way up, you might not have any profits to take when price comes back down. So here is what Ray does. He invests **100 USDC** into **SOL** when it is at **100 USDC per SOL** and every time **SOL** goes up 10 dollars or **10 USDC** he sells **0.1 SOL**..
![](solchartdiagram.svg)

Here is a table of what that would look like

| Price of SOL | Amount of SOL held | Amount of USDC held |
| ------------ | ------------------ | ------------------- |
| 100          | 1                  | 0                   |
| 110          | 0.9                | 11                  |
| 120          | 0.8                | 23                  |
| 130          | 0.7                | 36                  |


*Note: If Ray had just held 1 SOL, then at 130 his portfolio would be worth 130 USDC. But instead his portfolio is worth $130 \times 0.7 + 36 = 127$ USDC.*

Looking at Rays strategy we can see that he does not make as much profit as he could have made if he had just HODLed his **SOL** until **130 USDC**. Impermanent Loss in liquidity pools works in a similar way. If Ray had deposited **100 USDC** worth of **SOL** into a liquidity pool, then his **SOL** would have been converted into **USDC** incrementally as the price increased. Each tick his position had filled with **SOL** now contains **USDC** meaning that while he might still be in profit, he is not in as much profit as he *could* have been.... and that's just no fun. However, if the price of **SOL** goes back down to **100 USDC** then all those *impermanently* converted tokens get turned back into **SOL** and he has **1 SOL** again. This phenomenon is what we call **Impermanent Loss**.

> "Then why would anyone want to hold their SOL in a liquidity pool?" - Roy (Ray's friend who buys index funds instead of crypto).

Now, while Roy might just be trying to heckle Rays investing strategies, it is a fair question. As mentioned earlier, anyone who deposits tokens to be used as liquidity in these pools gets to share in the fees earned by these pools. A lot of the time, these fees offset the impermanent loss. But they might not. That's the risk.

For more advanced traders a normal and balanced liquidity position would be called "shorting volatility" as the most money is made when the price stays close to the start price of the position while making fees. There are also other cool trading strategies and opportunities that are created by the characteristics of Liquidity Pools but that will have to wait for a different post...