# 🎬 Streaming-Lab — Resilient RTMP → HLS Pipeline with Automatic Failover

## 🚀 Overview
Streaming-Lab is a full DevOps-grade media pipeline designed to demonstrate live-stream resilience.  
It receives RTMP input, converts it to HLS through dual origins, and performs automatic failover with metrics and dashboards.

![Dashboard Grafana](docs/grafana_dashboard.png)

---

## 🧠 Architecture


Publisher (FFmpeg) → MediaMTX (RTMP ingest) → FFmpeg Packagers → Nginx Origins → FastAPI Switcher → Prometheus → Grafana


---

## ⚙️ Stack
| Layer | Technology | Role |
|-------|-------------|------|
| Ingest | **MediaMTX** | RTMP server |
| Transcoding | **FFmpeg** | RTMP → HLS packager |
| Origins | **Nginx** | Serve HLS playlists |
| Control | **FastAPI + Uvicorn** | Health monitor and switch logic |
| Metrics | **Prometheus** | Scrapes `/metrics` endpoint |
| Dashboard | **Grafana** | Visual analytics |
| Infrastructure | **Docker Compose** | Full orchestration |

---

## 🔁 Features
- RTMP ingest with **MediaMTX**
- **Automatic failover** between primary and backup origins
- **FastAPI switcher** with Prometheus metrics (`segment_age_seconds`, `failovers_total`, `switcher_active_origin`)
- Real-time visualization on **Grafana**
- Self-healing publisher generating continuous test stream
- Fully containerized with **Docker Compose**

---

## 🧪 How to Run
```bash
git clone https://github.com/phantasmagorie/streaming-lab.git
cd streaming-lab
docker compose up -d
Then open:

Primary HLS → http://localhost:8081/hls/index.m3u8Then open:

