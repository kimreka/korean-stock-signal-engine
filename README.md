# korean-stock-signal-engine

## About
This is a signal parsing and technical analysis engine for Korean stock market (KRX) scalping strategies.
It collects trading signals from Telegram channels, validates them through multi-channel cross-checking, and combines them with real-time technical analysis to identify short-term entry opportunities.

## Key Features
- **Telegram Signal Parsing** — Extracts stock tickers and entry/stop-loss levels from Korean-language Telegram messages using regex, hashtag mapping, and a KRX-based ticker dictionary (2,800+ stocks)
- **Multi-Channel Validation** — Cross-validates signals across multiple channels with weighted reliability scores; filters out copy-paste duplicates using Jaccard similarity
- **Technical Analysis Engine** — Volume spike detection, EMA alignment (5/20/60), RSI filtering, and 10-minute high breakout confirmation
- **Signal Type Classification** — 8 signal types (disclosure, explicit stop-loss, closing bet, momentum, OCR-estimated, TA-only, etc.) with per-type stop-loss and time-cut rules
- **Risk Management** — Daily P&L limits, consecutive loss circuit breaker, sector concentration limits, market halt detection (VI, circuit breaker, sidecar)
- **Ticker Alias Map** — 230+ Korean stock nicknames and abbreviations mapped to official KRX codes (e.g. 삼전 → 삼성전자 / 005930)

## Usage
1. Clone the repository
```bash
git clone https://github.com/kimreka/korean-stock-signal-engine.git
cd korean-stock-signal-engine
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Run the signal parser
```bash
python tg_signal_parser.py
```

4. Run the TA scanner
```bash
python scalping_engine.py
```

> **Note:** Broker API integration (KIS Open API) and Telegram collector credentials are not included in this repository. This repo covers the signal logic and analysis layer only.

## Project Structure
```
├── tg_signal_parser.py     # Telegram signal extraction and validation
├── scalping_engine.py      # TA-based entry/exit logic
├── ticker_map.py           # Korean stock alias dictionary
├── ticker_resolver.py      # Ticker name-to-code resolution
├── rate_limiter.py         # Sliding window rate limiter
└── README.md
```

## License
MIT License
## Disclaimer
This project is for educational and personal use only.
The author is not responsible for any financial losses resulting from the use of this software.
