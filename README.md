[![Downloads](https://static.pepy.tech/badge/microcrypta)](https://pepy.tech/project/microcrypta)
# microcrypta

`microcrypta` is a Python package for cryptocurrency technical analysis. It provides tools for fetching market data, performing technical analysis, and backtesting trading strategies.

## Installation

To install the package, run:

```sh
pip install microcrypta
```

## Usage

Here is an example of how to use the `microcrypta` package:

```python
# example_usage.py

from microcrypta.coin import Coin
from microcrypta.account import correlation_matrix, Account
from microcrypta.coinmarket import CoinMarket
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from microcrypta.bsh import BSH
from microcrypta.backtest import Backtest
import microcrypta.config as config

# Initialize coins
corr_coins = ['BTC', 'ETH','SHIB','ADA']
correlation_matrix(corr_coins,time_frame='4h')# Create a market object
market = CoinMarket(btc, usdt, "1h")

coin = Coin('REQ')
usd = Coin('BTC')
coin_usd = CoinMarket(coin,usd,time_frame = "1h")
bshs = BSH(coin_usd)

# Create an account object
account = Account(1000, 1)

# Generate buy/sell/hold signals using the moving average strategy
signal = bsh.moving_average()

# Backtest the strategy
backtest = Backtest(market, signal, "Moving Average")
position_size, coin_count, percent_gain = backtest.backtest(plot=True)

print(f"Position Size: {position_size}")
print(f"Coin Count: {coin_count}")
print(f"Percent Gain: {percent_gain:.2f}%")
```

## Features

- Fetch market data from various cryptocurrency exchanges using `ccxt`.
- Perform technical analysis with indicators like Moving Averages, RSI, MACD, Bollinger Bands, etc.
  ![Visualization of Aaron Oscillator](imgs/corr_mat.png)
- Backtest trading strategies based on technical indicators.
  ![Visualization of backtesting](imgs/signal.png)
- Visualize data and analysis results using `matplotlib`.
  ![Visualization of Aaron Oscillator](imgs/aaron.png)

## Dependencies

- `ccxt`
- `pandas`
- `numpy`
- `matplotlib`
- `mplfinance`
- `seaborn`
- `tqdm`

## License

This project is licensed under the MIT License.

## Acknowledgements

Special thanks to the developers of `ccxt`, `pandas`, `numpy`, `matplotlib`, `mplfinance`, `seaborn`, and `tqdm`.

## Project Structure

```console
microcrypta/
│
├── microcrypta/
│ ├── init.py
│ ├── config.py
│ ├── coin.py
│ ├── coinmarket.py
│ ├── account.py
│ ├── bsh.py
│ └── backtest.py
│
├── setup.py
├── README.md
└── LICENSE
```
