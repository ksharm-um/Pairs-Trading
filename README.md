# Pairs Trading Analysis & Back‑Testing

A self‑contained Python project that discovers **cointegrated equity pairs**, visualises their statistical relationship, and simulates a simple z‑score–based long/short strategy.  
All logic lives in a single script, `karan_sharma_pairstrading.py`.

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| **Automated data pull** | Downloads daily *Close* prices for any ticker list via **yfinance**. |
| **Cointegration scan** | Applies the Engle–Granger test to every pair, returns those with *p* ≤ 0.05 and shows a heat‑map. |
| **Spread & ratio plots** | Plots the price spread, raw ratio and ±1 σ z‑score bands to visualise mean‑reversion. |
| **Trading signals** | Generates long/short entries when z‑score crosses ±1 and exits when it returns inside ±0.75. |
| **Quick back‑tester** | `trade()` function simulates the strategy and prints cumulative PnL. |

## 🗂️ Repository Layout

```text
.
├── karan_sharma_pairstrading.py   # Main analysis & back‑test script
└── README.md                      # You're here
```

## 🚀 Getting Started

1. **Clone & create a virtual environment**

   ```bash
   git clone https://github.com/<your‑user>/<repo>.git
   cd <repo>
   python -m venv .venv
   # Linux/macOS
   source .venv/bin/activate
   # Windows
   .venv\Scripts\activate
   ```

2. **Install requirements**

   ```bash
   pip install numpy pandas statsmodels matplotlib seaborn yfinance pandas_datareader
   ```

3. **Run the analysis**

   ```bash
   python karan_sharma_pairstrading.py
   ```

   You will see:

   * a cointegration heat‑map,
   * spread, ratio and z‑score charts,
   * console output listing cointegrated pairs and sample PnL.

## ⚙️ Configuration

| Item | Location in script | Default |
|------|-------------------|---------|
| **Ticker universe** | `tickers = [...]` | 10 US construction‑industry stocks |
| **Date range** | `start` / `end` variables | 2022‑01‑01 → 2025‑01‑01 |
| **Entry / exit z‑scores** | `ENTRY_Z`, `EXIT_Z` | +1 / −1 entry, ±0.75 exit |
| **Back‑test windows** | Arguments to `trade()` | `window1=34`, `window2=5` |

## 📈 Methodology Overview

1. **Cointegration testing** – Use Engle–Granger to find statistically cointegrated pairs.  
2. **Visual sanity check** – Confirm stationarity via charts.  
3. **Signal generation** – Trade the spread when z‑score diverges and converges.  
4. **Back‑test** – Simple pair‑neutral allocation, no fees or slippage.

> **Note:** This is an educational prototype, not production‑ready trading software.

## 🤝 Contributing

Pull requests are welcome! Please:

* Fork the repo and create a feature branch.
* Explain changes in the PR description.
* Attach visuals or logs that demonstrate impact.

## 📜 Licence

Released under the MIT License. See [`LICENSE`](LICENSE) for details.

---

Happy trading 📊
