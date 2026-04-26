# 📈 Pairs Trading & Statistical Arbitrage
 
A Python-based implementation of a **pairs trading strategy** using cointegration analysis on UK banking stocks. This project identifies statistically cointegrated stock pairs, computes z-score signals, and simulates a mean-reversion trading strategy.
 
---
 
## 🧠 What Is Pairs Trading?
 
Pairs trading is a **market-neutral strategy** that matches a long position in one stock with a short position in another highly correlated stock. When the price spread between two cointegrated stocks deviates significantly from its historical mean, a trade is triggered with the expectation that the spread will revert.
 
---
 
## 📂 Project Structure
 
```
pairs-trading/
│
├── pairs_trading.ipynb        # Main Jupyter notebook
├── README.md
└── requirements.txt           # Dependencies
```
 
---
 
## 🔍 Key Concepts Covered
 
| Concept | Description |
|---|---|
| **Stationarity** | Augmented Dickey-Fuller (ADF) test to check if a time series is stationary |
| **Cointegration** | Engle-Granger cointegration test to find long-run equilibrium pairs |
| **Spread / Ratio** | Price spread and ratio computed between cointegrated pairs |
| **Z-Score** | Rolling z-score used to generate buy/sell signals |
| **Backtesting** | Simulated P&L on test data using signal-based entry/exit logic |
 
---
 
## 📊 Dataset
 
- **Tickers**: `BARC.L`, `HSBA.L`, `LLOY.L`, `MTRO.L`, `NWG`, `STAN.L`, `VMUK.L`
- **Source**: Yahoo Finance via `yfinance`
- **Period**: January 2020 – September 2022
- **Focus Pair**: `BARC.L` (Barclays) & `VMUK.L` (Virgin Money UK)
---
 
## ⚙️ Strategy Logic
 
1. **Find Cointegrated Pairs** — scan all stock combinations using the Engle-Granger test
2. **Compute Price Ratio** — `ratio = S1 / S2`
3. **Rolling Z-Score** — using 10-day and 60-day moving averages
4. **Trading Signals**:
   - `z-score < -1` → **BUY** the ratio (buy S1, sell S2)
   - `z-score > +1` → **SELL** the ratio (sell S1, buy S2)
   - `|z-score| < 0.75` → **EXIT** all positions
5. **Simulate P&L** on the test set (last 30% of data)
---
 
## 📉 Results
 
- Cointegrated pairs found: `BARC.L/VMUK.L`, `MTRO.L/NWG`, `MTRO.L/VMUK.L`
- Starting capital: **£550**
- Final portfolio value: **~£3,837**
- Strategy profit: **~£3,287**
> ⚠️ *Past performance is not indicative of future results. This is for educational purposes only.*
 
---
 
## 🛠️ Installation
 
```bash
git clone https://github.com/Ak28071999/pairs-trading.git
cd pairs-trading
pip install -r requirements.txt
```
 
### Requirements
 
```
numpy
pandas
matplotlib
seaborn
statsmodels
yfinance
pandas-datareader
```
 
Or install directly:
 
```bash
pip install numpy pandas matplotlib seaborn statsmodels yfinance pandas-datareader
```
 
---
 
## 🚀 Usage
 
Open the notebook and run all cells:
 
```bash
jupyter notebook pairs_trading.ipynb
```
 
To test with different stocks or time periods, update the `tickers` list and `start`/`end` dates:
 
```python
tickers = ['BARC.L', 'HSBA.L', 'LLOY.L', 'MTRO.L', 'NWG', 'STAN.L', 'VMUK.L']
start = datetime.datetime(2020, 1, 1)
end   = datetime.datetime(2022, 9, 13)
```
 
---
 
## 📌 Visualisations
 
The notebook generates the following plots:
 
- Stationary vs. Non-Stationary series comparison
- Cointegration heatmap across all stock pairs
- Price ratio and spread over time
- Rolling z-score with buy/sell signal markers
- Individual stock price charts with entry/exit annotations
---
 
## 📚 References
 
- [Quantopian Lecture Series – Pairs Trading](https://www.quantopian.com/lectures)
- Engle, R. F., & Granger, C. W. J. (1987). *Co-integration and Error Correction*
- [statsmodels documentation](https://www.statsmodels.org/)
- [yfinance documentation](https://pypi.org/project/yfinance/)
---
 
## 👤 Author
 
**Ak28071999**  
GitHub: [@Ak28071999](https://github.com/Ak28071999)
 
---
 
## 📄 License
 
This project is open source and available under the [MIT License](LICENSE).
 
