# World Monitor 全球态势感知大屏系统架构与本地部署

## 一、系统定位与技术架构
World Monitor 是一套面向开源情报 (OSINT) 与全球宏观态势感知的开源实时监控平台（`koala73/worldmonitor`）：
* **前端渲染层**：基于 3D WebGL / Three.js 与 Vite SPA 构建，实现全球多维数据在三维地球上的高性能平滑渲染；
* **数据聚合层**：集成 60+ 实时多源数据流（地震/气象/冲突/军机航运/金融/大宗商品等）；
* **服务与代理层**：内置 Node.js API、Upstash Redis 兼容代理与 AIS Relay 实时船舶追踪服务。

## 二、本地化持久部署与局域网共享

### 1. 运行参数与网络拓扑
* **源码目录**：`/home/pengbo/onespace/github/worldmonitor`
* **启动方式**：通过 `hub` / `vite` 启动，全局监听 `0.0.0.0:3000`；
* **局域网访问地址**：
  * 有线 IP：`http://10.0.0.10:3000`
  * Wi-Fi IP：`http://10.0.0.108:3000`
  * 本地回环：`http://localhost:3000`

### 2. 数据源分级与凭据策略
* **🟢 免 Key 开箱即用**：地震、自然灾害、全球天气、难民流动、加密货币、海底光缆等；
* **🟡 可选增强 Key**：
  * AI 简报：`GROQ_API_KEY`（免费 14.4k 次/天）或 `OPENROUTER_API_KEY` 或 本地 Ollama；
  * 宏观金融：`FINNHUB_API_KEY`、`ALPHA_VANTAGE_API_KEY`、`FRED_API_KEY`；
  * 船舶追踪：`AISSTREAM_API_KEY`。
