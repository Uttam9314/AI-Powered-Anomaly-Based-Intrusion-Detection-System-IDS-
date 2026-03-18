# AI-Powered Anomaly-Based Intrusion Detection System (IDS)

> Built using Raspberry Pi 4, this project is a **plug-and-play, lightweight, and real-time IDS** designed for detecting and mitigating cyber-attacks such as DDoS, brute-force, and port scans. It features automated IP blocking, real-time system monitoring, and a live Flask-based dashboard.

![Python](https://img.shields.io/badge/Python-3.11-blue)
![XGBoost](https://img.shields.io/badge/ML-XGBoost-orange)
![Flask](https://img.shields.io/badge/Dashboard-Flask-green)
![Raspberry Pi](https://img.shields.io/badge/Device-Raspberry%20Pi%204-red)
![Accuracy](https://img.shields.io/badge/Accuracy-98.6%25-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## Table of Contents

- [Project Summary](#project-summary)
- [Target Audience](#target-audience)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Key Features](#key-features)
- [Machine Learning Details](#machine-learning-details)
- [Model Training (Colab)](#model-training-google-colab)
- [Live Dashboard](#live-dashboard)
- [Installation & Usage](#installation--usage)
- [Testing Tools](#testing-tools)
- [Product Launch Strategy](#product-launch-strategy)
- [Future Impact](#future-impact)
- [Known Limitations](#known-limitations)
- [Why This Project Stands Out](#why-this-project-stands-out)
- [Team Members](#team-members)

---

## Project Summary

This AI-Powered IDS is a **cost-effective, real-time network defense tool** intended for homes, schools, and small organizations. It monitors incoming network traffic, detects threats using trained ML models, auto-blocks malicious IPs via `iptables`, and displays everything on a clean Flask dashboard.

The system is **plugged in between the router and switch** for seamless traffic analysis, designed to work even in offline environments — ideal for remote and rural deployments.

---

## Target Audience

- Educational Institutes and Labs
- Smart Homes and IoT Networks
- Small & Medium Enterprises (SMEs)
- Defense and Government Organizations
- Research Labs and Cybersecurity Students

---

## Tech Stack

| Component | Tool / Library |
|-----------|---------------|
| Device | Raspberry Pi 4 (4 GB RAM) |
| OS | Raspberry Pi OS (Debian-based) |
| Programming | Python 3.11 |
| ML Model | XGBoost / Random Forest |
| Data Source | MQTT-Based Intrusion Dataset |
| Dashboard | Flask + HTML + Chart.js + AJAX |
| Monitoring | psutil, netstat |
| Security | iptables, RSA |
| Alerts | Twilio (SMS), smtplib (Email) |
| Testing Tools | hping3, hydra, netcat, Wireshark |

---

## System Architecture
```
          [Internet]
               |
           [Router]
               |
   ┌───────────────────────┐
   │   Raspberry Pi IDS    │
   │  ─ ML Prediction      │
   │  ─ Real-time Blocking │
   │  ─ Dashboard View     │
   └───────────────────────┘
               |
            [Switch]
               |
      [All Connected Devices]
```

> Plug-and-play model: Just insert the Raspberry Pi between your **router and switch** — the IDS starts passively monitoring and defending immediately.

---

## Key Features

- Real-time detection of DDoS, brute-force, and port scan attacks
- Auto-blocks malicious IPs using `iptables`
- Flask-based live dashboard with charts and logs
- AI model trained on real-world MQTT intrusion dataset
- Sends SMS and Email alerts upon threat detection
- RSA signature verification for request authenticity
- Works fully offline — perfect for remote and rural areas
- Prediction time under 0.5 seconds on Raspberry Pi 4

---

## Machine Learning Details

- **Dataset:** MQTT-Based Intrusion Detection Dataset
- **Model:** XGBoost Classifier (fallback: Random Forest)
- **Accuracy:** ~98.6% on test set
- **Prediction Time:** < 0.5 sec on Raspberry Pi 4

**Top 10 Features Used:**

| # | Feature |
|---|---------|
| 1 | Duration |
| 2 | Bytes Sent |
| 3 | Packets |
| 4 | Source Port |
| 5 | Destination Port |
| 6 | Protocol |
| 7 | ACK Flags |
| 8 | Packet Size Variance |
| 9 | Flow Rate |
| 10 | Latency |

---

## Model Training (Google Colab)

Train or test the ML model directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1y0vSX56S7ObC94boj3f7vqQOSScpUTS7)

The notebook includes:
- Data preprocessing and feature selection
- Training using XGBoost / Random Forest
- Evaluation metrics (accuracy, precision, recall, F1)
- Model export for deployment on Raspberry Pi or Flask app

---

## Live Dashboard

The Flask web dashboard provides:

- Real-time CPU, RAM, and latency monitoring
- Attack detection logs with timestamps
- Auto-blocked IP list
- Network traffic statistics
- Live graphs powered by Chart.js
```
Access via: http://192.168.59.36:5000
```

---

## Installation & Usage

### Step 1 — Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/ai-ids-raspberry-pi.git
cd ai-ids-raspberry-pi
```

### Step 2 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 3 — Train or load the model
```bash
python train_model.py
# OR load pre-trained model from /models folder
```

### Step 4 — Start the IDS
```bash
python ids_main.py
```

### Step 5 — Launch the dashboard
```bash
python dashboard/app.py
# Open: http://localhost:5000
```

### Step 6 — Configure alerts (optional)
```bash
# Edit config.py with your Twilio and SMTP credentials
TWILIO_SID = "your_sid"
TWILIO_TOKEN = "your_token"
ALERT_EMAIL = "your@email.com"
```

---

## Testing Tools

All tests conducted in a **controlled, isolated environment** using virtual machines and routers.

| Tool | Use Case | Example Command |
|------|----------|----------------|
| **hping3** | Simulate DDoS / SYN Flood | `hping3 -S -p 80 --flood <target-IP>` |
| **hydra** | SSH Brute Force | `hydra -l root -P passwords.txt ssh://<target-IP>` |
| **nmap** | Port Scan | `nmap -sS -p 1-65535 -T4 <target-IP>` |
| **netcat** | Open fake ports | `nc -lvp 9999` |
| **Wireshark** | Packet capture analysis | Real-time monitoring GUI |
| **scapy** | Custom packet crafting | Test zero-day signatures |

---

## Product Launch Strategy

This project is designed to be **production-ready** with minimal setup, enabling even non-technical users to protect their networks.

### Go-to-Market Plan
- Package as a **pre-configured Raspberry Pi device** with everything preloaded
- **No-code dashboard** that boots up instantly on power-on
- Plug-and-play hardware placed **between router and switch**

### Product Package Includes
- Raspberry Pi with IDS pre-installed
- SD card pre-flashed with software and OS
- Access credentials for the dashboard
- Setup manual and quick start guide
- Alert configuration instructions for SMS / Email

### Initial Launch Focus
- 1,000+ Schools and Colleges across India
- MSMEs with limited cybersecurity infrastructure
- NGOs and Government offices in Tier-2 / Tier-3 cities

---

## Future Impact

| Area | Vision |
|------|--------|
| Rural & Remote Protection | No internet required — works offline. Ideal for defense installations and rural labs |
| Cybersecurity for Education | Training tool for students — implements cybersecurity literacy at grassroots level |
| Federated Threat Intelligence | Multiple devices forming a decentralized learning network sharing anonymized attack patterns |
| Adaptive Threat Response | Self-healing system with reinforcement learning and zero-trust architecture |

---

## Known Limitations

| Limitation | Current Status |
|------------|---------------|
| No Deep Packet Inspection (DPI) | Kept light for Raspberry Pi performance |
| No HTTPS Packet Decryption | Legal and ethical restrictions |
| IPv6 Not Fully Supported | Currently optimized for IPv4 only |
| Not Yet Dockerized | Docker packaging planned for next release |
| Static ML Model | Does not auto-learn from new threats (work in progress) |

---

## Why This Project Stands Out

| Feature | Benefit |
|---------|---------|
| Edge AI Integration | Smart detection directly on Raspberry Pi — no cloud needed |
| Plug-and-Play Setup | Zero configuration needed post-boot |
| Live Web Dashboard | Monitor threats, resources, and logs in real time |
| AI-Based Classification | Trained ML model with 98.6% accuracy |
| Automated IP Blocking | Instantly blocks attack sources via iptables |
| Real-Time Alerts | SMS and Email notifications on threat detection |
| Offline Capability | Fully functional without internet access |
| Cost-Effective | Ideal for rural, defense, and SME deployment across India |

---

## Team Members

| Name | Role | Contributions |
|------|------|---------------|
| **Amit Kumar Behera** | Project Lead, ML & IoT Developer | Model training, firewall integration, system architecture |
| **Shashi Ranjan Kumar** | Frontend & Dashboard Developer | Flask app, real-time chart integration |
| **Uttam Kumar** | Dataset Preprocessing & Feature Selection | Cleaned dataset, extracted top 10 features |
| **Santosh Kumar** | Penetration Testing & QA | hping3, hydra attack simulation, stress testing |

---

## License

MIT License — free to use, modify, and distribute.

---

*Built with Raspberry Pi 4 + XGBoost + Flask | Dataset: MQTT-Based Intrusion Detection Dataset | Real-time Edge AI IDS*
