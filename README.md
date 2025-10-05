Гано2, [05.10.2025 21:00]
# Telegram
TELEGRAM_BOT_TOKEN=YOUR_TELEGRAM_BOT_TOKEN
CHAT_ID=@your_channel_or_numeric_id

# Расписание (в минутах)
POLL_INTERVAL_MIN=5

# Источники (через запятую). Можно RSS/JSON API/твиттер-ленты через прокси.
NEWS_SOURCES=https://news.site1/rss,https://news.site2/rss

# Фильтры (опционально, через запятую)
TICKERS=BTC,ETH,EURUSD,USDJPY

# Настройки
DEDUP_WINDOW_HOURS=24
LOG_LEVEL=INFO

Гано2, [05.10.2025 21:00]
# рекомендуется Python 3.11+
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python bot.py

Гано2, [05.10.2025 21:00]
docker build -t crypto-fx-news-bot .
docker run --env-file .env --name newsbot --restart unless-stopped crypto-fx-news-bot

Гано2, [05.10.2025 21:01]
# docker-compose.yml
services:
  bot:
    build: .
    env_file: .env
    restart: unless-stopped

Гано2, [05.10.2025 21:01]
docker compose up -d --build

Гано2, [05.10.2025 21:02]
.
├── bot.py                 # Точка входа
├── news_fetcher.py        # Загрузка/парсинг источников (RSS/JSON)
├── filters.py             # Фильтрация по тикерам, дедуп
├── sender.py              # Отправка в Telegram
├── storage/               # Кэш/БД (sqlite/json) для дедупликации
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── README.md

Гано2, [05.10.2025 21:02]
python-telegram-bot>=21.0
feedparser>=6.0
httpx>=0.27
python-dotenv>=1.0
orjson>=3.10

Гано2, [05.10.2025 21:03]
# Линт (если используете ruff/flake8)
ruff check .
# Запуск в тестовом чате
export CHAT_ID=@test_channel && python bot.py
