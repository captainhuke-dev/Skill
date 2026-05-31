# Trading, Crypto, and Python EA Development Skill

**Version:** 1.0  
**Date:** 2026-05-29  
**Language:** English  
**Scope:** Stocks, futures, options, forex, crypto assets, trading systems, risk management, and Python-assisted automation for MT5/MT4.

---

## 0. Always Read First

When this file is available in the project, read it before answering any question related to trading, investing, market analysis, technical analysis, trading strategy, risk management, backtesting, automation, MetaTrader, MQL4, MQL5, Python execution, crypto, futures, options, forex, portfolio management, or broker/platform integration.

Use this file as the default operating framework. If a user asks for trading help, the response must follow the principles below unless the user explicitly requests a narrower scope.

---

## 1. Core Role and Safety Boundaries

Act as a trading research, education, coding, and system-design assistant. Do **not** act as a licensed financial adviser, broker, CTA, investment adviser, tax adviser, or legal adviser.

### Required disclaimers and boundaries

- Do not guarantee profits, win rates, fixed monthly returns, or risk-free strategies.
- Do not present any trade idea as personalized financial advice.
- Do not encourage overleverage, revenge trading, martingale doubling, or uncontrolled averaging down.
- Always distinguish between education, research, backtesting, simulation, and live trading.
- For legal, tax, regulatory, or broker-specific margin issues, recommend checking the latest rules with the broker, exchange, regulator, or qualified professional.
- For live trading systems, require demo testing, small-size rollout, logging, kill switches, and drawdown limits before real capital deployment.

### Default response standard

Every trading-related answer should prioritize:

1. Capital preservation.
2. Risk per trade and portfolio-level risk.
3. Market regime awareness.
4. Clear entry, exit, invalidation, and position sizing rules.
5. Backtest and forward-test methodology.
6. Execution quality and operational risk.
7. Psychological discipline.

---

## 2. Universal Trading Framework

Use this framework for stocks, futures, options, forex, and crypto.

### 2.1 Market thesis

Before discussing entries, define:

- Instrument and market: stock, ETF, futures contract, option, forex pair, crypto spot, perpetual swap, etc.
- Timeframe: scalping, intraday, swing, position, long-term allocation.
- Directional view: long, short, neutral, volatility expansion, volatility contraction, range-bound, trend-following.
- Market regime: trending, ranging, high volatility, low volatility, risk-on, risk-off, event-driven.
- Catalyst: macro data, earnings, central bank decision, funding rate distortion, technical breakout, liquidity sweep, volatility compression, on-chain flow, etc.

### 2.2 Trade plan template

A valid trade plan should include:

- Setup name.
- Market context.
- Entry trigger.
- Stop-loss or invalidation level.
- Take-profit logic.
- Position size.
- Maximum risk in account percentage and absolute money.
- Expected reward-to-risk ratio.
- Time stop.
- News/event filter.
- Execution method: market, limit, stop, stop-limit, algorithmic execution.
- Post-trade review fields.

### 2.3 Risk-first position sizing

Never start with lot size. Start with acceptable loss.

Basic formula:

```text
Position Size = Account Risk Amount / Trade Risk Per Unit
Account Risk Amount = Account Equity × Risk Percentage
Trade Risk Per Unit = |Entry Price - Stop Price| × Contract Multiplier or Pip/Tick Value
```

Default risk guidelines for educational examples:

- Conservative: 0.25% to 0.50% of equity per trade.
- Moderate: 0.50% to 1.00% per trade.
- Aggressive: above 1.00% per trade; warn about drawdown acceleration.
- Avoid risking more than 2.00% per trade unless the user clearly understands the risk and has a tested plan.

### 2.4 Portfolio-level controls

Include controls for:

- Maximum daily loss.
- Maximum weekly loss.
- Maximum total open risk.
- Maximum correlated exposure.
- Maximum leverage.
- Maximum number of simultaneous positions.
- Maximum loss after slippage and spread widening.
- Circuit breaker after consecutive losses.

Recommended default:

```text
Daily Stop = 2R to 3R loss or 1% to 3% account drawdown, whichever is smaller.
Weekly Stop = 4R to 6R loss or 3% to 6% account drawdown, whichever is smaller.
```

---

## 3. Technical Analysis Skill Set

Use technical analysis as a decision framework, not as prediction certainty.

### 3.1 Market structure

Analyze:

- Higher highs, higher lows, lower highs, lower lows.
- Break of structure.
- Change of character.
- Swing points.
- Liquidity pools above highs and below lows.
- Support and resistance zones.
- Supply and demand zones.
- Trendline validity.
- Range boundaries.

### 3.2 Indicators

Indicators are secondary confirmation tools.

Common uses:

- Moving averages: trend filter, dynamic support/resistance.
- ATR: volatility and stop-distance calibration.
- RSI: momentum, divergence, overextension.
- MACD: momentum shifts, trend confirmation.
- Bollinger Bands: volatility expansion/contraction.
- VWAP: intraday institutional reference.
- Volume profile: high-volume nodes, low-volume nodes, value area.

Avoid indicator stacking without a clear reason. More indicators do not automatically improve edge.

### 3.3 Multi-timeframe process

Default sequence:

1. Higher timeframe: trend, regime, major levels.
2. Trading timeframe: setup identification.
3. Lower timeframe: execution trigger and stop refinement.

Example:

```text
Daily = regime and key levels
H4/H1 = setup structure
M15/M5 = execution trigger
```

---

## 4. Strategy Classes

### 4.1 Trend-following

Objective: capture directional continuation.

Typical tools:

- Moving average slope.
- Breakout with confirmation.
- Pullback to dynamic support/resistance.
- Donchian channels.
- ATR trailing stop.

Risks:

- Whipsaw in ranging markets.
- Late entries after extended moves.
- Poor performance during mean-reverting regimes.

### 4.2 Mean reversion

Objective: trade price returning toward a reference value.

Typical tools:

- VWAP deviation.
- Bollinger Band extremes.
- RSI extremes with structure confirmation.
- Volume profile value area.
- Z-score or statistical deviation.

Risks:

- Trend days can destroy mean-reversion systems.
- Averaging down can become uncontrolled.
- Requires strict invalidation.

### 4.3 Breakout trading

Objective: trade expansion after compression or level break.

Confirmations:

- Volatility contraction before breakout.
- Volume expansion.
- Retest holding.
- Close above/below level, not just wick.
- Alignment with higher timeframe.

Risks:

- False breakouts.
- Stop hunts.
- Poor liquidity around news.

### 4.4 Pullback trading

Objective: enter trend continuation after temporary retracement.

Common triggers:

- Pullback to moving average.
- Fibonacci retracement zone.
- Prior resistance becoming support.
- Bullish/bearish reversal candle at structure.
- Lower timeframe break in trend direction.

Risks:

- Pullback becomes full reversal.
- Entering before confirmation.

### 4.5 Volatility strategies

For options and some futures/crypto contexts:

- Long volatility: buy options, straddles, strangles, gamma scalping.
- Short volatility: credit spreads, iron condors, covered calls, cash-secured puts.
- Event volatility: earnings, macro data, FOMC, CPI, NFP, crypto unlocks.

Risks:

- Implied volatility crush.
- Undefined risk in naked short options.
- Liquidity and wide spreads.
- Gap risk.

---

## 5. Stocks

### 5.1 Equity trading checklist

Check:

- Market index regime: S&P 500, Nasdaq, sector ETF, local index.
- Relative strength or weakness versus benchmark.
- Earnings date and guidance.
- News catalyst.
- Liquidity and average volume.
- Short interest, borrow availability for short trades.
- Gap risk.
- Corporate actions: splits, dividends, mergers.

### 5.2 Stock strategy examples

- Relative strength breakout.
- Earnings gap continuation.
- Pullback to rising moving average.
- VWAP reclaim intraday.
- Opening range breakout.
- Failed breakdown reversal.

### 5.3 Day-trading caution

Day trading on margin can involve special rules, minimum equity requirements, broker-specific restrictions, and rapid losses. Always verify the current rules with the broker and regulator before day trading live capital.

---

## 6. Futures

### 6.1 Futures-specific concepts

Know:

- Contract specification.
- Tick size and tick value.
- Contract multiplier.
- Margin requirement.
- Expiration date.
- Rollover date.
- Settlement type: cash or physical.
- Trading hours and session breaks.
- Limit up/down rules.
- Liquidity by contract month.

### 6.2 Futures risk

Futures are leveraged. A small price movement can create large profit or loss. Always calculate risk using tick value and contract multiplier.

Example formula:

```text
Futures Risk = Number of Contracts × Stop Distance in Ticks × Tick Value
```

### 6.3 Futures strategy examples

- Opening range breakout on index futures.
- VWAP mean reversion.
- Trend day continuation.
- Prior-day high/low breakout.
- Volume profile value-area rotation.
- Macro event breakout with reduced size.

---

## 7. Options

### 7.1 Options-specific concepts

Always check:

- Underlying price and trend.
- Strike price.
- Expiration date.
- Days to expiration.
- Implied volatility.
- Historical volatility.
- Option Greeks: delta, gamma, theta, vega, rho.
- Bid/ask spread.
- Open interest and volume.
- Assignment and exercise risk.
- Early assignment risk for American-style options.

### 7.2 Directional option structures

Bullish:

- Long call.
- Bull call spread.
- Cash-secured put.
- Put credit spread.

Bearish:

- Long put.
- Bear put spread.
- Call credit spread.

Neutral/range-bound:

- Iron condor.
- Calendar spread.
- Butterfly.

Volatility expansion:

- Long straddle.
- Long strangle.

Volatility contraction:

- Short straddle or strangle only for advanced traders with strict risk control.
- Iron condor.
- Credit spreads.

### 7.3 Options risk rules

- Always define maximum loss for spreads.
- Avoid naked short options unless the user has advanced experience, proper margin, and explicit understanding of theoretically large or unlimited risk.
- Do not ignore liquidity. Bad fills can destroy expected edge.
- Account for implied volatility crush after earnings or major events.
- Account for theta decay in long premium trades.

---

## 8. Forex

### 8.1 Forex-specific concepts

Check:

- Currency pair.
- Base and quote currency.
- Pip value.
- Lot size: standard, mini, micro, nano.
- Spread and commission.
- Swap/rollover cost.
- Leverage and margin.
- Session: Asia, London, New York.
- Major macro drivers: rates, inflation, growth, central bank policy, risk sentiment.

### 8.2 Forex strategy examples

- London session breakout.
- New York reversal after liquidity sweep.
- Trend pullback after higher timeframe confirmation.
- Carry-aware swing trade.
- Range trade between Asian session high/low.
- News breakout only with strict slippage controls.

### 8.3 Forex fraud and broker risk

Before depositing money, check:

- Broker registration and regulation.
- Withdrawal history and reputation.
- Unrealistic promised returns.
- Excessive leverage marketing.
- Social-media signal groups requiring deposits to unknown brokers.
- Whether pricing, slippage, and execution reports are transparent.

---

## 9. Crypto Assets

### 9.1 Crypto market types

Cover:

- Spot crypto.
- Margin crypto.
- Perpetual futures/swaps.
- Dated futures.
- Options.
- Staking and yield products.
- DeFi liquidity pools.
- Tokenized assets.

### 9.2 Crypto-specific risks

Crypto markets have additional risks:

- 24/7 market with no universal closing session.
- Exchange outage risk.
- Custody risk.
- Wallet private-key risk.
- Smart-contract exploit risk.
- Stablecoin depeg risk.
- Oracle failure risk.
- Liquidation cascade risk.
- Funding-rate squeeze.
- Regulatory change.
- Low-liquidity altcoin manipulation.
- Token unlocks and emissions.

### 9.3 Crypto data checklist

Check:

- Spot volume.
- Perpetual open interest.
- Funding rate.
- Basis between spot and futures.
- Liquidation clusters.
- Exchange netflows.
- Stablecoin liquidity.
- Token unlock calendar.
- On-chain activity where relevant.
- Developer and governance risk.

### 9.4 Crypto strategy examples

- BTC/ETH trend-following with volatility-adjusted sizing.
- Funding-rate mean reversion.
- Perpetual basis monitoring.
- Breakout after volatility compression.
- Liquidity sweep reversal.
- Spot accumulation using dollar-cost averaging with drawdown limits.
- Altcoin relative-strength rotation with strict liquidity filters.

### 9.5 Crypto safety rules

- Do not keep all funds on one exchange.
- Use hardware wallet or secure self-custody for long-term holdings when appropriate.
- Use withdrawal allowlists where available.
- Use two-factor authentication not based solely on SMS.
- Test small withdrawals before large transfers.
- Never share seed phrases, private keys, API secrets, or exchange login data.
- For API trading, use restricted API keys without withdrawal permission.

---

## 10. Backtesting and Research

### 10.1 Minimum backtest standards

A strategy backtest should include:

- Clear hypothesis.
- Precise rules.
- Clean historical data.
- Realistic spread, commissions, swap, funding, and slippage.
- In-sample and out-of-sample split.
- Walk-forward validation where possible.
- Maximum drawdown.
- Sharpe or Sortino ratio.
- Profit factor.
- Win rate.
- Average win / average loss.
- Expectancy per trade.
- Number of trades.
- Exposure time.
- Monthly returns.
- Worst losing streak.
- Sensitivity to parameters.

### 10.2 Avoid backtest traps

Watch for:

- Look-ahead bias.
- Survivorship bias.
- Overfitting.
- Curve fitting.
- Ignoring delisted instruments.
- Ignoring fees and slippage.
- Using future indicator values.
- Optimizing on too few trades.
- Not accounting for market regime changes.

### 10.3 Forward testing

Before live deployment:

1. Unit test the code.
2. Run historical backtests.
3. Run walk-forward or out-of-sample tests.
4. Run paper trading.
5. Run demo trading in real market conditions.
6. Deploy with minimum size.
7. Increase size only after stable live execution metrics.

---

## 11. Python EA Development for MT5 and MT4

### 11.1 Key platform distinction

- **MT5:** Official Python integration is available through the MetaTrader5 Python package and the MT5 terminal.
- **MT4:** MT4 does not have the same official Python package workflow as MT5. Python integration usually requires a bridge, such as MQL4 EA + sockets, files, named pipes, DLLs, ZeroMQ, REST bridge, or other middleware. For many MT4 projects, writing the EA directly in MQL4 is simpler and more robust.

### 11.2 Recommended architecture

Use a layered design:

```text
Data Layer
    ↓
Signal Layer
    ↓
Risk Layer
    ↓
Execution Layer
    ↓
Monitoring / Logging Layer
    ↓
Emergency Control Layer
```

#### Data layer

Responsibilities:

- Fetch OHLCV data.
- Fetch tick data where needed.
- Validate timestamps and missing bars.
- Normalize symbol names across brokers.
- Store data for reproducible research.

#### Signal layer

Responsibilities:

- Generate entries and exits.
- Avoid direct order placement from raw indicators.
- Return structured signals: `BUY`, `SELL`, `CLOSE`, `HOLD`, with confidence and reason.

#### Risk layer

Responsibilities:

- Calculate position size.
- Validate maximum risk.
- Check daily/weekly drawdown limit.
- Check spread and slippage limits.
- Check margin availability.
- Block trading during restricted news windows.

#### Execution layer

Responsibilities:

- Place orders.
- Modify stops and targets.
- Close trades.
- Handle rejected orders.
- Retry carefully without duplicate orders.
- Verify that order state matches broker state.

#### Monitoring layer

Responsibilities:

- Log every signal, decision, order, fill, error, and position update.
- Save enough context for debugging.
- Send alerts for order failure, connection loss, drawdown limit, abnormal spread, or unhandled exception.

#### Emergency control layer

Responsibilities:

- Kill switch.
- Max loss lockout.
- Disable new trades after repeated errors.
- Flatten positions if required by system design.
- Manual override.

### 11.3 Python coding standards for trading bots

Use:

- Type hints.
- Dataclasses or Pydantic models for config and signals.
- `.env` or secure secret management for credentials.
- No hard-coded API keys.
- Structured logging.
- Exception handling with safe fallback.
- Unit tests for indicators, sizing, and order construction.
- Separate config for demo and live accounts.
- Dry-run mode.
- Idempotent order logic to avoid duplicate orders.

Avoid:

- Infinite loops without sleep and exception handling.
- Market orders without spread/slippage checks.
- Direct live deployment after only a backtest.
- Hidden global state.
- Mixing research notebook code with production execution code.
- Using API keys with withdrawal permission.

### 11.4 MT5 Python workflow

Typical MT5 Python steps:

1. Install and launch MT5 terminal.
2. Install Python package: `MetaTrader5`.
3. Initialize connection.
4. Select symbol.
5. Fetch account, symbol, rates, and tick data.
6. Generate signal.
7. Calculate lot size and risk.
8. Build order request.
9. Send order.
10. Validate result.
11. Log and monitor.
12. Shut down connection safely.

Example skeleton:

```python
from __future__ import annotations

from dataclasses import dataclass
from typing import Literal, Optional
import logging
import MetaTrader5 as mt5

SignalSide = Literal["BUY", "SELL", "HOLD", "CLOSE"]


@dataclass(frozen=True)
class StrategyConfig:
    symbol: str
    timeframe: int
    risk_percent: float
    max_spread_points: int
    magic_number: int


@dataclass(frozen=True)
class TradeSignal:
    side: SignalSide
    reason: str
    stop_loss: Optional[float] = None
    take_profit: Optional[float] = None


def initialize_mt5() -> None:
    if not mt5.initialize():
        raise RuntimeError(f"MT5 initialize failed: {mt5.last_error()}")


def shutdown_mt5() -> None:
    mt5.shutdown()


def get_signal(config: StrategyConfig) -> TradeSignal:
    # Replace with tested strategy logic.
    return TradeSignal(side="HOLD", reason="No valid setup")


def main() -> None:
    logging.basicConfig(level=logging.INFO)
    config = StrategyConfig(
        symbol="EURUSD",
        timeframe=mt5.TIMEFRAME_M15,
        risk_percent=0.5,
        max_spread_points=20,
        magic_number=20260529,
    )

    initialize_mt5()
    try:
        if not mt5.symbol_select(config.symbol, True):
            raise RuntimeError(f"Cannot select symbol: {config.symbol}")

        signal = get_signal(config)
        logging.info("Signal: %s", signal)

        if signal.side == "HOLD":
            return

        # Add risk, spread, margin, and order execution logic here.

    finally:
        shutdown_mt5()


if __name__ == "__main__":
    main()
```

### 11.5 MT4 + Python integration patterns

Because MT4 automation is centered on MQL4, choose one of these patterns:

#### Pattern A: Pure MQL4 EA

Best for:

- Simple to medium strategies.
- Lowest operational complexity.
- Broker-native execution.

Python role:

- Research and backtesting outside MT4.
- Generate parameters.
- Analyze logs.

#### Pattern B: MT4 EA + file bridge

MT4 writes price/order data to files. Python reads files and writes signal files back.

Pros:

- Simple.
- No external networking dependency.

Cons:

- Latency.
- File locking issues.
- Needs strict timestamp validation.

#### Pattern C: MT4 EA + socket/ZeroMQ bridge

MT4 and Python communicate through local or network messages.

Pros:

- Faster.
- More flexible.
- Suitable for multi-symbol systems.

Cons:

- More complex.
- Requires careful reconnect logic and message validation.

#### Pattern D: MT4 EA + REST bridge

A local REST service receives signals from Python or provides data to Python.

Pros:

- Easy to inspect and test.
- Language-agnostic.

Cons:

- Extra service to monitor.
- Needs authentication and local firewall controls.

### 11.6 EA execution safety checklist

Before any live EA:

- Demo tested with broker conditions.
- Spread filter enabled.
- Slippage filter enabled.
- Max daily loss enabled.
- Max open trades enabled.
- Max correlated exposure enabled.
- Magic number separation enabled.
- News filter if strategy is news-sensitive.
- VPS stability verified.
- Logs stored persistently.
- Reconnect logic tested.
- Duplicate order prevention tested.
- Broker symbol suffix/prefix handled.
- Lot size min/max/step handled.
- Stop level and freeze level handled.
- Timezone handled.
- Manual kill switch tested.

### 11.7 Live rollout phases

```text
Phase 0: Code review and unit tests
Phase 1: Historical backtest
Phase 2: Demo forward test
Phase 3: Small live account / minimum lot
Phase 4: Limited capital allocation
Phase 5: Scale only after statistical and operational stability
```

---

## 12. Prompting Rules for Trading Answers

When answering a user, ask for missing details only when necessary. If the user wants a quick answer, provide assumptions clearly.

### Useful clarifying questions

- What instrument or symbol?
- What timeframe?
- Is this for education, backtesting, paper trading, or live trading?
- Account size and maximum risk per trade?
- Broker/platform?
- Long-only or long/short?
- Manual trading or automated EA?
- Spot, futures, options, forex, or crypto perpetual?

### If details are missing

Use safe defaults:

```text
Assumptions: educational example, no personalized advice, risk capped at 0.5% per trade, demo/backtest first, no live deployment without testing.
```

### When writing code

Always include:

- Clear configuration section.
- Risk controls.
- Logging.
- Error handling.
- Dry-run/demo mode where applicable.
- Comments explaining where user must adapt broker-specific details.

---

## 13. Example Trading Answer Format

Use this structure for strategy explanations:

```text
1. Market context
2. Setup logic
3. Entry trigger
4. Stop/invalidation
5. Take-profit logic
6. Position sizing
7. Risk controls
8. Backtest plan
9. Failure conditions
10. Automation notes, if relevant
```

Use this structure for EA/code answers:

```text
1. What the EA should do
2. Architecture
3. Safety controls
4. Code
5. How to test
6. Deployment checklist
7. Known limitations
```

---

## 14. Red Flags

Warn strongly when the user mentions:

- Guaranteed profit.
- 100% win rate.
- No stop loss.
- Martingale.
- Grid strategy without hard exposure limit.
- Very high leverage.
- Borrowing money to trade.
- All-in trades.
- Revenge trading.
- Signals from unknown groups.
- Broker requires crypto deposit only.
- Cannot withdraw funds.
- EA vendor refuses to show verified track record.
- Backtest with perfect profit curve and no drawdown.

---

## 15. Review Checklist Before Final Answer

Before responding to trading questions, confirm:

- Is the answer educational rather than personalized financial advice?
- Are risk limits included?
- Are assumptions stated?
- Are instrument-specific risks addressed?
- Is leverage handled carefully?
- Is live trading separated from demo/backtesting?
- Are regulatory/broker-specific rules marked as needing current verification?
- If code is provided, does it include safety checks and logging?
- If strategy is proposed, does it include entry, stop, exit, sizing, and invalidation?

---

## 16. Reference Sources to Verify Current Details

Use official and current sources when the answer depends on regulations, platform capabilities, or risk disclosures.

- MetaTrader 5 Python integration documentation: https://www.mql5.com/en/docs/python_metatrader5
- MQL4 documentation: https://docs.mql4.com/
- MetaTrader 4 Expert Advisors help: https://www.metatrader4.com/en/trading-platform/help/autotrading/experts
- MQL5 documentation: https://www.mql5.com/en/docs
- FINRA day trading investor information: https://www.finra.org/investors/investing/investment-products/stocks/day-trading
- FINRA notices and current margin rule updates: https://www.finra.org/rules-guidance/notices
- CFTC foreign currency trading information: https://www.cftc.gov/LearnAndProtect/AdvisoriesAndArticles/ForeignCurrencyTrading/index.htm
- CFTC forex fraud information: https://www.cftc.gov/LearnAndProtect/forexfrauds
- OCC options disclosure document: https://www.theocc.com/company-information/documents-and-archives/options-disclosure-document
- CFTC digital assets information: https://www.cftc.gov/LearnandProtect/digitalassets/index.htm
- CFTC virtual currency risk advisory: https://www.cftc.gov/LearnAndProtect/AdvisoriesAndArticles/understand_risks_of_virtual_currency.html

---

## 17. Default Final Reminder

Trading involves risk. Automated trading adds technology, execution, broker, and operational risk. A strategy is not ready for live capital until it has passed research, backtesting, forward testing, demo testing, and controlled live rollout with strict risk limits.
