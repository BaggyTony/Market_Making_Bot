# Market Making Bot

A simple Market Maker Bot for trading on the Phemex exchange using the `ccxt` Python library. The bot places limit buy and sell orders around the current market price and tries to earn the spread.

## Features:
- **Adjustable Desired Spread**
- **Dynamic Spread Adjustment** based on market volatility
- **Position Exposure Check**
- **API request rate limiting**
- **Kill switch** under certain conditions (excessive API errors, high volatility, profit/loss threshold breach)
- **Automatic order adjustment**

## Prerequisites:
- `ccxt` library
- `numpy`
- Python3

## Setup:
1. Create a `config.ini` file in the same directory as your script with the following content:

[DEFAULT]

desired_spread_percentage = YOUR_PREFERRED_SPREAD

amount = YOUR_TRADING_AMOUNT

symbol = YOUR_SYMBOL (e.g. AVAX/USDT)

trading_fee = YOUR_TRADING_FEE

MAX_POSITION = YOUR_MAX_POSITION

KILL_SWITCH = False (or True if you want to start with the kill switch on)

volatility_threshold = YOUR_VOLATILITY_THRESHOLD

2. Update `API_KEY` and `API_SECRET` with your Phemex API credentials.

## How to Run:
$ python3 your_script_name.py


## Bot Logic:

- Fetches the average price of a trading pair and adjusts orders based on current market conditions.
- Determines if current market volatility is too high and activates a kill switch if needed.
- Adjusts spread based on current market volatility.
- Checks open positions to ensure they don't exceed a certain threshold.
- Respects rate limits set by the exchange.
- Places buy and sell orders ensuring they are profitable and don't overlap.
- Adjusts orders that are either too far from the current market or too old.
- Monitors and logs its activities continuously.

## Notes:

- The script does not have any error-handling or retries for API request failures. Consider implementing these features for a more robust, production-ready bot.
- Exercise caution when using this bot with real funds. Always test your strategies with a paper trading account or smaller amounts first.

## Disclaimer:

- Use this bot at your own risk. The developer is not responsible for any financial losses or other damages caused by the bot.
