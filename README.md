# 📈 MT5 Trading Bot with Technical Indicators  

## 🔹 Project Overview  
This project is an **automated trading bot for MetaTrader 5 (MT5)** that allows traders to backtest and automate strategies using **technical indicators** (MA, RSI, MACD, etc.).  

The bot connects directly to the **MetaTrader 5 terminal**, retrieves historical OHLCV data, applies indicator-based strategies, simulates backtests with performance metrics, and can optionally execute trades in real-time.  

---

## 🔹 Features  
✔️ Connects to **MetaTrader 5 (MT5)** terminal  
✔️ Fetches **historical OHLCV data** for any symbol & timeframe  
✔️ Implements **indicators**: Moving Averages, RSI, MACD  
✔️ **Signal generation logic** for buy/sell  
✔️ **Backtesting engine** with:  
- Initial & Final Capital  
- Profit % and PnL  
- Total Trades & Win Rate  
- Maximum Drawdown  
✔️ **Visualization**: Profit Curve & Candlestick charts  
✔️ Supports both **paper trading & live trading**  

---

## 🔹 Requirements  

### 1. Install Python Libraries  
```bash
# Required packages
pip install MetaTrader5
pip install --upgrade MetaTrader5
pip install TA-Lib
pip install pandas matplotlib pytz
```

⚠️ **TA-Lib installation note**:  
- **Windows**: download from [TA-Lib binaries](https://technical-analysis-library-in-python.readthedocs.io/en/latest/) and install with pip.  
- **Linux/Mac**:  
```bash
sudo apt-get install -y build-essential
sudo apt-get install -y libta-lib0 libta-lib0-dev
pip install ta-lib
```

---

### 2. Install MetaTrader 5 Terminal  
To run this bot, you **must install the MT5 terminal** on your system:  
👉 [Download MetaTrader 5](https://www.metatrader5.com/en/download)  

---

### 3. MT5 Login Credentials  
You need a **broker account** that provides MT5 access.  
- Sign up with a Forex broker (e.g., Exness, ICMarkets, Pepperstone, etc.)  
- Log into the MT5 terminal with:  
  - **Login (Account ID)**  
  - **Password**  
  - **Server**  

These credentials are required in `config.py` (or inside the notebook).  

⚠️ **Never commit your real credentials to GitHub!** Use environment variables or `.env` files.  

---

## 🔹 Handling Large Historical Data  

When fetching historical OHLCV data from MT5, requesting a very long date range in a single call can cause **performance issues or incomplete data**. To handle this efficiently, this bot uses the following logic:

### 1. `split_by_month`  
- **Purpose**: Splits a large date range into **monthly chunks**.  
- **Why**: MT5 API can fail or return incomplete data if too many candles are requested at once. By fetching data month by month, we ensure reliability and avoid API limits.  

### 2. `get_candle_ranges`  
- **Purpose**: Determines the number of candles for a given date range and timeframe.  
- **Why**: If the number of candles exceeds MT5 limits, this function helps split the request into smaller, manageable chunks. This ensures **complete historical data retrieval** without errors.

---

## 🔹 Installation  

1. **Clone the repository**  
```bash
git clone https://github.com/your-username/mt5-trading-bot.git
cd mt5-trading-bot
```

2. **Install dependencies**  
```bash
pip install -r requirements.txt
```

3. **Set MT5 credentials** in `config.py` or as environment variables.  

---

## 🔹 Usage  

### Run Backtest  
```bash
python run.py
```

This will:  
- Connect to MT5  
- Fetch OHLCV data  
- Apply indicators  
- Generate signals  
- Run backtest  
- Print performance metrics  

### Example Output  
```
===== Strategy Performance =====
Initial Capital : 100000.00
Final Capital   : 134268.31
Total Profit    : 34268.31 (34.27%)
Total Trades    : 886
Winning Trades  : 815
Win Rate        : 91.99%
```

✅ A profit curve graph and candlestick chart with buy/sell signals will also be displayed.  

---

## 🔹 Future Improvements  
- Add advanced indicators (ATR, Bollinger Bands, SuperTrend)  
- Risk management with stop-loss & take-profit  
- Live order execution via MT5 API  
- Streamlit dashboard for real-time monitoring  

---

## 🔹 License  
This project is licensed under the **MIT License**.  

---

⚠️ Note: This bot is for **educational & research purposes**. Trading involves financial risk — use responsibly.  
