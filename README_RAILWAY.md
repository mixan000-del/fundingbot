# Binance Funding Bot — Railway

## Быстрый деплой
1) Форк/загрузите репозиторий.
2) На https://railway.app → New Project → Deploy from GitHub → выберите репозиторий.
3) В разделе Variables добавьте:
   - TG_TOKEN = 123456:AA...
   - TG_CHAT_ID = 123456789  (или -100... для канала/супергруппы)
   - STATE_FILE = /data/binance_funding_state.json
   - (опц.) POLL_SEC=30, THRESHOLD=-1.0, DOWN_STEP=0.25, REBOUND_STEP=0.05, REBOUND_START=-2.0, ONLY_USDT=1, SNAPSHOT_MODE=0
4) В разделе Volumes добавьте Persistent Volume и примонтируйте к `/data`.
5) Запустите Deploy. Логи должны показать "Binance monitor started...".
6) В Телеграме /status → «Проверить сейчас».

## Примечания
- Railway обычно не даёт 451 на Binance egress.
- Если нужен другой хостер: Render/Fly/Hetzner VPS — всё то же (Dockerfile + env), либо VPS + systemd.
