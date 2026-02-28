Agent 13 — Market Intelligence & Realtime Market Microstructure Engine
Agent 13 is a full‑stack, real‑time market analytics system designed to fuse live market data, price‑action structure, on‑chain / project momentum, and market microstructure signals into a unified, operator‑friendly dashboard.
It combines exchange websocket ingestion, structured signal generation, NBBO analytics, and observability into a single deployable package.
This repository contains the v1.5 full‑stack release, including:

Real-time crypto + equity data ingestion
TimescaleDB storage optimized for high‑frequency market data
Multi‑channel websocket ingestion (Binance + Polygon “AM/T/Q”)
Event‑driven signal generation (Stage 2 / Stage 4 / Neutral)
Momentum scoring via AIXBT project metadata
NBBO spark + mini trade tape for equities
Streamlit dashboard with a clean, minimal operator UI
Prometheus + Alertmanager + Grafana observability stack


✨ Features
🔌 Multi‑Exchange Real‑Time Ingestion

Crypto (Binance WebSocket): 1‑minute candlesticks (kline_1m)
Equities (Polygon WebSocket):

AM.* aggregate minute bars
T.* trades
Q.* quotes — powering NBBO metrics


Automatic reconnect logic, per‑stream health checks, and ingestion stall detection.

📊 Structured Market Signals
A background signal worker builds a rolling model for each symbol:

OBV & Accumulation/Distribution slopes
Rolling relative volume
Short‑term price structure breakouts/down
Stage labeling:

Stage 2 — upward momentum / structural breakout
Stage 4 — distribution / breakdown
Neutral



Signals are stored in TimescaleDB and exposed through the API for the UI.
🔥 AIXBT Momentum Overlay
Optionally enrich symbol confidence using AIXBT project momentum:

Auto‑maps tickers to project pages
Extracts momentum scores and trend series
Blends into the platform’s confidence model

📈 Dashboard (Streamlit)
A fast operator‑view tuned for clarity:

Stage arrows overlay directly on the last price bar
Momentum badge (Rising / Stable / Fading)
NBBO sparkline with metric selector (Spread bps / Midprice)
Mini tape (latest prints) for equities
Recent signals feed
Shareable stateful link (symbol + theme + NBBO metric)
Dark/light mode supported

🛰 Observability Built‑In
Production‑grade monitoring stack:

Prometheus scrapes API + Pushgateway
Alertmanager with email/Telegram/Teams routing
Alerts included out‑of‑the-box:

No WS messages (2m)
IngestStallByStream (5m)
NoSignalsGenerated (10m)


Grafana dashboards auto‑provisioned (no manual import)

WS health (messages/sec/min by stream)
DB & system overviews
