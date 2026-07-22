# 📱💡 Smart Light Control Using Tasker + Home Assistant + Shelly

> *"Simple idea. Powerful automation. Total control."*

[![IoT](https://img.shields.io/badge/IoT-Smart%20Home-blue?style=flat-square)](https://github.com/Ab40D)
[![Tasker](https://img.shields.io/badge/Tasker-Automation-orange?style=flat-square)](https://tasker.joaoapps.com/)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-REST%20API-41BDF5?style=flat-square)](https://www.home-assistant.io/)
[![Shelly](https://img.shields.io/badge/Shelly-Relay-4CAF50?style=flat-square)](https://www.shelly.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

---

## 📖 Overview

This project automates your room light based on your **phone screen state** (ON/OFF). When you turn your phone screen ON, the light turns ON automatically — and when the screen turns OFF, the light turns OFF too.

No cloud. No internet required. **100% local, fast, and reliable.**

---

## 🏗️ Architecture

```
Phone Screen ON / OFF
        │
        ▼
    [Tasker]
  Detects Screen Event
        │
        ▼
  HTTP POST Request
  POST /api/services/...
        │
        ▼
 [Home Assistant]
 REST API (Local Network)
        │
        ▼
  [Shelly Relay]
 Receives ON/OFF Command
        │
        ▼
   💡 Light ON / OFF
```

> All communication happens over **local Wi-Fi** — no cloud dependency.

---

## ⚙️ Tech Stack

| Component | Role |
|---|---|
| 📱 **Tasker** | Detects phone screen events & sends HTTP POST |
| 🌐 **Home Assistant REST API** | Receives request & executes service |
| 💡 **Shelly Relay** | Physical relay that switches the light |
| 📶 **Wi-Fi (Local Network)** | Communication backbone |

---

## ✅ Key Features

- 🔄 **Automatic light control** based on phone screen state
- 🏠 **100% Local** — works without internet
- ⚡ **Fast & Lightweight** — no latency
- 🔧 **Easy to extend** — add conditions, schedules, or sensors
- 🔌 **Works with any Shelly device**

---

## 🚀 Setup Guide

### Prerequisites

- Android phone with **Tasker** installed
- **Home Assistant** running on local network
- **Shelly relay** integrated with Home Assistant
- Both phone and HA server on the **same Wi-Fi network**

---

### Step 1 — Home Assistant Setup

1. Make sure your Shelly device is integrated in Home Assistant.
2. Note the **entity ID** of your light (e.g., `light.room_light` or `switch.shelly_relay`).
3. Enable **Long-Lived Access Token** in your HA profile.
4. Note your HA local IP (e.g., `http://192.168.1.100:8123`).

Optionally, use the provided automation YAML:
👉 See [`home-assistant/automation.yaml`](home-assistant/automation.yaml)

---

### Step 2 — Tasker Setup

1. Import the Tasker profile from [`tasker/ScreenLightControl.prf.xml`](tasker/ScreenLightControl.prf.xml).
2. Edit the HTTP POST task and update:
   - `YOUR_HA_IP` → your Home Assistant local IP
   - `YOUR_HA_TOKEN` → your Long-Lived Access Token
   - `YOUR_ENTITY_ID` → your light/switch entity ID
3. Enable the profile.

---

### Step 3 — Test It

- Turn your phone screen **ON** → Light should turn **ON**
- Turn your phone screen **OFF** → Light should turn **OFF**

---

## 📂 Project Structure

```
📁 Smart-Light-Control-Using-Tasker-and-Home-Assistant
├── 📄 README.md
├── 📁 tasker/
│   └── ScreenLightControl.prf.xml    # Tasker profile (importable)
├── 📁 home-assistant/
│   └── automation.yaml               # Optional HA automation
├── 📁 screenshots/
│   └── architecture.jpg              # Add your architecture diagram here
└── 📄 LICENSE
```

---

## 💼 Use Cases

- 🌙 **Night mode lighting** — screen off = lights off automatically
- 💡 **Automatic room light** for better experience
- 🔋 **Energy saving** — no more forgotten lights
- 🏢 **Smart Building / BMS** demonstrations

---

## 👤 Author

**Abdelkhalek Mammeri**  
Electronics Engineer | IoT & Smart Systems Developer  
🌐 [Portfolio](https://se7en-web.vercel.app/) | 🐙 [GitHub](https://github.com/Ab40D)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
