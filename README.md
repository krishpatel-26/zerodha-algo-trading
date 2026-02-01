# Multi-Asset Algo Trading System (BTC • Gold • Silver)

This project implements a Python-based **systematic swing trading strategy** across multiple high-volatility assets:

- Bitcoin (BTC-USD)
- Gold Futures (GC=F)
- Silver Futures (SI=F)

The system uses technical momentum + pullback logic with strict risk management and exports full trade logs to CSV for analysis in Excel.

---

## Strategy Overview

The strategy is designed for **swing trading on daily data** and follows a professional trend-following structure.

### Indicators

- EMA 50 → Trend filter  
- EMA 20 → Pullback entry  
- ATR(14) → Stop loss & target sizing  

---

## Entry Logic (Long Only)

A trade is entered when:

1. Price is above EMA50 (bullish trend)
2. Previous candle closes below EMA20 (pullback)
3. Current candle closes back above EMA20 (continuation)

---

## Risk Management

- Fixed risk per trade: **2% of equity**
- Stop Loss: **1.5 × ATR**
- Target: **3 × ATR (2R reward)**
- Position sizing calculated dynamically based on stop distance.

---

## Backtest Parameters

- Timeframe: Daily
- Lookback: 5 Years
- Data Source: Yahoo Finance (via yfinance)

---

## Output

After running the script, the following files are generated:

- `BTC_trades.csv`
- `GOLD_trades.csv`
- `SILVER_trades.csv`

Each CSV contains:

- Entry Time  
- Exit Time  
- Entry Price  
- Exit Price  
- Profit / Loss  
- Equity Curve  

These files can be opened directly in Excel for further analysis.

---

## Example Results (5-Year Backtest)

| Asset | Return |
|------|--------|
| BTC | ~0.6% |
| Gold | ~46.8% |
| Silver | ~23.1% |

*(Results depend on market regime and are for educational purposes only.)*

---

## Installation

Create virtual environment (optional):

```bash
python -m venv venv
venv\Scripts\activate
