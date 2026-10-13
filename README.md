# alert-server

Push alerts for BHub: when XAUUSD closes an M1 / M5 / M15 / H1 bar with a
Bull or Bear Accelerator (Order Flow indicator), users who chose that
timeframe and signal get a push through OneSignal.

- `signals/` — the indicator's accelerator rule in Dart (the same code as
  the BHub app), compiled to JavaScript for the Worker.
- `worker/` — Cloudflare Worker: runs every minute, checks closed bars,
  sends pushes, and stores each user's alert settings.

Secrets (OneSignal REST API key, OANDA token) live only in Cloudflare
(`wrangler secret put …`), never in this repo.
