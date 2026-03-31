# 📈 ma-crossover-strategy

A beginner-friendly quantitative trading strategy built in Python. Uses a **Moving Average Crossover** signal on historical stock data to simulate a long-only trading strategy — with real performance metrics and charts.

Built as a quant hackathon project.

---

## What it does

- Downloads real stock price data via `yfinance`
- Generates **buy/sell signals** when a fast SMA crosses a slow SMA
- Simulates a backtest with commission costs
- Outputs key performance metrics and a results chart

---

## Strategy logic

| Signal | Condition |
|--------|-----------|
| **BUY** | 20-day SMA crosses **above** 50-day SMA |
| **SELL** | 20-day SMA crosses **below** 50-day SMA |

Between signals the strategy holds cash (long-only, no shorting).

---

## Quickstart

**Option A — Google Colab (recommended)**

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

1. Upload `ma_strategy.py` to a new Colab notebook
2. Run the cell — `yfinance` installs automatically

**Option B — local**

```bash
git clone https://github.com/YOUR_USERNAME/ma-crossover-strategy
cd ma-crossover-strategy
pip install yfinance pandas numpy matplotlib
python ma_strategy.py
```

---

## Configuration

Edit the constants at the top of `ma_strategy.py`:

```python
TICKER     = "AAPL"        # any valid Yahoo Finance ticker
START      = "2020-01-01"
END        = "2024-12-31"
SHORT_WIN  = 20            # fast MA window (days)
LONG_WIN   = 50            # slow MA window (days)
CAPITAL    = 10_000        # starting cash ($)
COMMISSION = 0.001         # 0.1% per trade
```

---

## Output

The script prints a performance summary and saves `ma_strategy_results.png`:

```
Strategy Return :  78.2%
Buy & Hold      : 339.0%
Sharpe Ratio    :   0.62
Max Drawdown    : -25.5%
Total Trades    :     29
```

The chart shows:
- Price with SMA lines and buy/sell markers
- Strategy portfolio value vs. buy-and-hold benchmark (indexed to 100)

---

## Limitations

- **Lagging** — MAs react to price moves, never anticipate them
- **Whipsawing** — generates false signals in sideways/choppy markets
- **Long-only** — cannot profit from falling prices
- **Single asset** — no diversification
- Past backtest results do not guarantee future performance

---

## Stack

`Python` · `pandas` · `numpy` · `matplotlib` · `yfinance`

---

## License

MIT
