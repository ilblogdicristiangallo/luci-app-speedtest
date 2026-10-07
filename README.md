# 🚀 LuCI App SpeedTest (Premium Edition)

The ultimate, highly accurate, and visually stunning speed test application for OpenWrt LuCI. 
Powered by the Cloudflare Edge Network, this app features **Ookla-style algorithms**, real-time SVG animations, and a modern Neon Dark UI.

---

## 📸 Screenshots

<p align="center">
  <img src="https://github.com/ilblogdicristiangallo/luci-app-speedtest/blob/main/Screenshot/Screenshot.png?raw=true" width="48%">
  <img src="https://github.com/ilblogdicristiangallo/luci-app-speedtest/blob/main/Screenshot/Screenshot2.png?raw=true" width="48%">
</p>
<p align="center">
  <img src="https://github.com/ilblogdicristiangallo/luci-app-speedtest/blob/main/Screenshot/Screenshot3.png?raw=true" width="48%">
  <img src="https://github.com/ilblogdicristiangallo/luci-app-speedtest/blob/main/Screenshot/Screenshot4.png?raw=true" width="48%">
</p>
<p align="center">
  <img src="https://github.com/ilblogdicristiangallo/luci-app-speedtest/blob/main/Screenshot/Screenshot5.png?raw=true" width="98%">
</p>

---

## ✨ Key Features

This application is engineered to provide the most accurate network diagnostics directly from your router:

*   🎯 **Ookla-Style Accuracy:** Implements intelligent algorithms to prevent browser queue saturation and hardware bottlenecks.
*   ⏱️ **10-Second Smart Ping:** Measures idle latency over a 10-second period, trimming the top 20% of spikes (TLS handshakes/anomalies) to find your true stable ping.
*   📉 **RFC3550 Jitter Calculation:** Calculates real-time jitter during the download phase using standard network variation math, avoiding false 1000ms+ spikes.
*   🚀 **TCP Slow-Start Bypass:** Automatically discards the first 1.5 seconds of the bandwidth test (warm-up phase) to ensure the measured speed is your actual peak throughput.
*   📊 **Dual Metrics:** Displays speeds in both **Mbps** (Megabits) and **MB/s** (Megabytes) simultaneously.
*   🎨 **Neon Dark UI & SVG Gauge:** A beautiful, responsive speedometer that scales perfectly on Desktop (2x2 Grid) and Mobile (Vertical 1-column).
*   💾 **Local History:** Saves your last 10 speed test results directly on the router's memory, complete with a UI button to clear the log.

---

## 🔄 Package Compatibility

Pre-compiled packages are available in the [Releases](https://github.com/ilblogdicristiangallo/luci-app-speedtest/releases) section for two different OpenWrt generations:

*   📦 **OpenWrt 25.x and Newer (`.apk`):** For OpenWrt versions using the new Alpine-based `apk` package manager.
*   📦 **OpenWrt 24.x and Older (`.ipk`):** For legacy OpenWrt versions using the traditional `opkg` package manager.

---

## ℹ️ Technical Note: Client-Side Testing & Wi-Fi Bottlenecks

### ❓ Why does the speed test measure performance from my client device?

`luci-app-speedtest` is a **Client-Side Web Application** executed directly by your web browser (Smartphone, PC, or Tablet) via the LuCI interface.

#### 🔄 Complete Data Pipeline:
`Internet (Cloudflare)` ➔ `Router WAN / Modem` ➔ `Wi-Fi or LAN Cable` ➔ `Client Device Browser`

---

### 📌 Key Considerations for Accurate Results:

* 📶 **Wi-Fi Limitations:** If you run the test from a smartphone connected over Wi-Fi (especially on 2.4 GHz or distant 5 GHz connections), the result will reflect the maximum throughput of your **Wi-Fi link and phone hardware**, which may be lower than your router's actual WAN/Cellular speed.
* 🔌 **Testing True WAN Capacity:** To measure the absolute maximum speed of your modem/WAN connection without wireless bottlenecks, always run the speed test from a **PC connected via a Gigabit Ethernet (LAN) cable**.
* ⚡ **Why Client-Side Execution is Superior for Routers:** Running speed tests directly on a router's CPU (Server-Side CLI tools) can easily saturate low-power embedded SoCs (causing 100% CPU load) because CPU-bound tests bypass **Hardware Flow Offloading**. By running the test Client-Side, your router’s hardware acceleration handles the packet forwarding effortlessly, ensuring accurate high-speed measurement without overloading the router's CPU.


## 🛠️ Installation Guide

### Option 1: Direct Installation via SSH (Using `wget`)

Connect to your router via SSH (e.g., using PuTTY or Terminal) and execute the commands matching your OpenWrt version:

#### 🟢 For OpenWrt 25.x and newer (`.apk` package):
```bash
cd /tmp
wget https://github.com/ilblogdicristiangallo/luci-app-speedtest/releases/download/speedtest%2Capk%2Cipk%2Copenwrt%2Cluci%2C/luci-app-speedtest-1.0.0-r1.apk
apk add --allow-untrusted luci-app-speedtest_1.0.0-r1_all.apk
