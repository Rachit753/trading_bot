# Binance Futures Testnet Trading Bot

A lightweight Python CLI trading bot for placing MARKET and LIMIT orders on the Binance Futures Testnet.

---

## Overview

This project is a command-line trading bot built in Python that interacts with the **Binance Futures Testnet (USDT-M)**. It allows users to place basic trading orders directly from the terminal while demonstrating how to structure a small but maintainable Python project.

The project focuses on clean separation of responsibilities, input validation, and logging so that the application can be easily extended in the future.

---

## Features

* Place **MARKET orders**
* Place **LIMIT orders**
* Supports both **BUY** and **SELL** sides
* Command-line interface using `argparse`
* Input validation for symbol, order type, quantity, and price
* Logging for API requests, responses, and errors
* Modular and reusable project structure

---

## Project Structure

```
trading_bot/
│
├── bot/
│   ├── client.py           # Binance client setup
│   ├── orders.py           # Order execution logic
│   ├── validators.py       # Input validation
│   └── logging_config.py   # Logging configuration
│
├── logs/
│   └── trading_bot.log     # Application logs
│
├── cli.py                  # CLI entry point
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Setup

### 1. Clone the repository

```
git clone <your-repo-url>
cd trading_bot
```

### 2. Create a virtual environment

```
python -m venv venv
```

Activate the environment.

**Windows**

```
venv\Scripts\activate
```

### 3. Install dependencies

```
pip install -r requirements.txt
```

---

## API Configuration

Create a `.env` file in the project root and add your Binance Testnet API credentials:

```
BINANCE_API_KEY=your_api_key
BINANCE_SECRET_KEY=your_secret_key
```

You can generate API keys from:

```
https://testnet.binancefuture.com
```

---

## Usage

### MARKET Order

```
python cli.py --symbol BTCUSDT --side BUY --type MARKET --qty 0.002
```

### LIMIT Order

```
python cli.py --symbol BTCUSDT --side SELL --type LIMIT --qty 0.002 --price 90000
```

---

## Example Output

```
Order Request
-------------
Symbol: BTCUSDT
Side: BUY
Type: MARKET
Quantity: 0.002

Order Response
--------------
Order ID: 123456789
Status: FILLED
Executed Qty: 0.002
Avg Price: 61234.50

SUCCESS: Order executed successfully
```

---

## Logging

All API requests, responses, and errors are written to:

```
logs/trading_bot.log
```

Example log entry:

```
INFO Sending MARKET order | BTCUSDT BUY qty=0.002
INFO Order response: {...}
```

Logging helps track order activity and makes debugging easier when interacting with external APIs.

---

## Requirements

Dependencies used in this project:

* python-binance
* python-dotenv

Install them with:

```
pip install -r requirements.txt
```

---

## Notes

* Binance Futures Testnet requires a **minimum notional value of 100 USDT** per order.
* LIMIT orders may remain in `NEW` status if the price is far from the current market price.
* The project runs on the **Binance Testnet environment**, meaning no real funds are used.

---

## Disclaimer

This project is for **learning and demonstration purposes**. It should not be used for real trading without implementing proper strategy and risk management.
