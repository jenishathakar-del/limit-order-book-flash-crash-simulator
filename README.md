# limit-order-book-flash-crash-simulator
# Limit Order Book Liquidity & High-Frequency Trading (HFT) Flash Crash Simulator

## Academic Overview
This project simulates market microstructure dynamics within an electronic limit order book (LOB). By modeling synthetic discrete queues for bids (buy orders) and asks (sell orders) using an exponential distribution, the framework algorithmically executes a structural liquidity drain to observe systemic price cascades and evaluate the performance of automated volatility circuit breakers.

## The Economic & Philosophical Thesis
In classical Walrasian price theory, markets instantly settle at a continuous equilibrium price. However, modern high-frequency trading (HFT) environments operate on discrete millisecond queues where structural liquidity is highly ephemeral. 

This simulation tests the systemic vulnerability of market depth. By algorithmically purging 40% of institutional buy-side depth immediately prior to a large market-sell shock, the framework demonstrates how modern algorithmic market-making strategies can cause endogenous "Flash Crashes," exposing structural flaws in modern electronic trading architectures.

## Quantitative Methodology
The limit order book is constructed as a dual-array system initialized around a baseline fair value ($P_0$):

$$\text{Bids} = P_0 - X_{\text{bid}}, \quad X_{\text{bid}} \sim \text{Exp}(\lambda)$$
$$\text{Asks} = P_0 + X_{\text{ask}}, \quad X_{\text{ask}} \sim \text{Exp}(\lambda)$$

Where $\lambda = 1.5$ defines the spatial density of order distribution near the mid-market price. 

The algorithmic shock models an exogenous liquidity evaporation coefficient ($\alpha = 0.40$), recalculating the available bid depth vector before executing a large volume market sell order. The system calculates continuous price degradation ($\Delta P$) and applies a deterministic binary condition to model an automated exchange circuit breaker:

$$\Delta P = \frac{P_{\text{executed}} - P_0}{P_0}$$

If $|\Delta P| \ge 0.05$, a structural volatility halt is programmatically triggered.

## Empirical Results & Conclusion
* **Pre-Crash Top Bid Price:** $99.98
* **Post-Drain Cleared Market Price:** $94.61
* **Instantaneous Price Devaluation:** -5.37%
* **Exchange Safety Audit:** Volatility Halt Triggered (Circuit Breaker Activated)

## Strategic Market Microstructure Conclusion
The engine delivers mathematical proof that market resilience is determined by immediate queue depth rather than long-term asset fundamentals. By capturing the mechanics of an algorithmic cash cascade, this project highlights why advanced microstructure risk parameters are vital for systemic stability within quantitative asset management and market regulatory frameworks.
