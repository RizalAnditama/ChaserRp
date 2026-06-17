# AGENTS

| Agent Name | Language Matrix | Core Responsibilities | Input/Output Interfaces |
|---|---|---|---|
| Data Scraper Agent | JavaScript (Node.js, Puppeteer, `puppeteer-extra-plugin-stealth`) | Scrape Threads, X, and Facebook text with anti-bot evasion, infinite scrolling to 3000px (configured minimum depth to force lazy-loading consistently), proxy/user-agent rotation, and unified normalization. | **Input:** platform URLs, selectors, scraping config. **Output:** `raw_social_data.json` (`[{"text": "...", "timestamp": "...", "platform": "..."}]`). |
| Quantitative Engine Agent | Python (`yfinance`, `pandas`) | Download IDX ticker market data with mandatory `.JK` suffix for `1d`, `5m`, and `15m` intervals; normalize and persist structured OHLCV datasets. | **Input:** ticker list, interval/window config. **Output:** `idx_market_data.csv` and cleaned dataframes. |
| NLP Analysis Agent | Python (Hugging Face Transformers, IndoBERT) | Process Indonesian retail trading text, apply slang-aware weighting, and produce date-grouped sentiment means in `[-1.0, 1.0]`. | **Input:** `raw_social_data.json`, slang lexicon map. **Output:** `daily_sentiment_score` by date. |
| Execution Risk Agent | C++ / Java | Evaluate short-term execution risk, stop-loss thresholds, and trigger decisions with low-latency order-book/volume logic. | **Input:** model signal + live market microstructure feed. **Output:** risk-adjusted trade triggers and stop-loss metadata. |
