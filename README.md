## Systematic Strategy on the FTSE: Risk Reduction and Return Enhancement

This systematic strategy trades the FTSE index with a focus on reducing volatility and drawdowns while maximizing risk-adjusted returns. In backtests, it has demonstrated:

- A **significantly higher CAGR** than the index.
- **Markedly lower volatility and drawdown**.
- A **Sharpe ratio 6x higher** than that of the index.

The strategy combines macro risk signals with a mean-reversion model tailored to the FTSE’s behavioral characteristics.

---

### 1. Portfolio Exposure: Baseline and Dynamic Adjustments

- The strategy maintains a **baseline exposure of 1.0 (fully invested)** in the FTSE index.
- When macro risk increases (as detected via credit spreads), it shifts to **risk-off mode**, setting exposure to **0**.
- In all other periods, the portfolio remains fully allocated, and may **increase exposure above 1.0** using tactical overlays based on a mean-reversion signal.

---

### 2. Risk Management Layer: Credit Spread Signal

The strategy switches to **risk-off mode** when a rise in the credit spread (the differential between high-yield corporate bonds and Treasuries) is detected.

#### Fundamental Rationale:

- Credit spreads are a leading indicator of systemic risk: wider spreads imply growing concerns about corporate creditworthiness and market liquidity.
- This reflects **risk aversion** and potential stress in the financial system, often preceding equity downturns.
- By fully exiting the market during such times (setting exposure to 0), the strategy **avoids drawdowns** and **preserves capital**.

---

### 3. Tactical Layer: Mean Reversion via Z-Score

The FTSE index tends to **mean revert** over short- to medium-term horizons. The strategy takes advantage of this by using a **multi-timeframe z-score signal** (e.g., combining 5, 10, and 20-day z-scores) to enhance robustness and reduce noise.

#### Entry Logic (Tenor-Based Overlay):

- When the **z-score drops below -1**, a long signal is triggered.
- Each day that the signal remains active:
  - A **fixed portion of additional exposure** (e.g., +10%) is added.
  - This increased exposure is **held for a fixed number of days** (e.g., 5), regardless of the signal's status afterward.
- This creates a **tenor ladder**, where multiple overlapping tranches of extra exposure may coexist.

#### Example:

- On day 1: z-score < -1 → add +10%, exposure = 1.10  
- On day 2: z-score still < -1 → add another +10%, exposure = 1.20  
- And so on, up to a predefined maximum (if applicable).

#### Benefits:

- **Reduces timing risk** by spreading entry over multiple days.
- Capitalizes on short-term dislocations and rebounds in the FTSE.
- Enhances returns by leveraging selectively during oversold conditions.

---

### 4. Strategy Coordination: Credit Spread Overrides Mean-Reversion

The two layers interact as follows:

- When the **credit spread signal is risk-off**, the entire position is closed (exposure = 0). No z-score signals are acted upon during this time.
- When in **risk-on mode**, the **baseline exposure is 1.0**, and the **mean-reversion overlays increase exposure dynamically** via the tenor-based logic.

This blend allows the strategy to **protect capital during macro stress** and **enhance returns during local dislocations**, resulting in a smoother and higher-performing equity curve.

---
