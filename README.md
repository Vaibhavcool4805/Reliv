<div align="center">

# RELiV

### Healthcare, now closer to you.

**A smart preventive healthcare kiosk bringing health screening, digital wellness insights, reports, and medicine dispensing into one accessible experience.**

<br/>

[![Status](https://img.shields.io/badge/status-prototype-orange?style=for-the-badge)](https://github.com/Vaibhavcool4805/Reliv)
[![Platform](https://img.shields.io/badge/platform-Raspberry%20Pi%20%2B%20ESP32-black?style=for-the-badge)](https://github.com/Vaibhavcool4805/Reliv)
[![Theme](https://img.shields.io/badge/theme-HealthTech-orange?style=for-the-badge)](https://github.com/Vaibhavcool4805/Reliv)
[![SIH](https://img.shields.io/badge/Smart%20India%20Hackathon-2026-black?style=for-the-badge)](https://sih.gov.in/)

<br/>

<a href="https://relivkiosk.vercel.app/"><strong>🌐 Explore RELiV</strong></a>
&nbsp;&nbsp;•&nbsp;&nbsp;
<a href="#-product-demo"><strong>🎥 Product Demo</strong></a>
&nbsp;&nbsp;•&nbsp;&nbsp;
<a href="#-documentation"><strong>📚 Documentation</strong></a>

</div>

---

## 🧡 The idea

Healthcare should be available where people already are.

**RELiV** is a student-led preventive healthcare kiosk designed to make routine health screening and essential healthcare services more accessible in everyday locations such as campuses, workplaces, gyms, and community spaces.

The current prototype combines a physical kiosk, local computing, sensor integration, a web interface, wellness-report generation, digital payments, and a medicine-dispensing workflow.

> **You matter. RELiV cares.**

> **Prototype status:** approximately 60% complete. Integration, device validation, end-to-end payment testing, and pilot reliability work remain in progress.

---

## 🎥 Product Demo

The strongest proof of RELiV is the physical machine itself.

**Demo video:** the repository is ready for the real machine walkthrough to be added as `assets/demo/reliv-machine-demo.mp4`.

A short 10–20 second loop can also be added as `assets/demo/reliv-demo.gif` for a visual README preview.

---

## ✨ What RELiV brings together

| 🩺 Health Screening | 🤖 Wellness Intelligence | 📄 Digital Reports | 💊 Essential Dispensing |
|---|---|---|---|
| BP, pulse, SpO₂, temperature and body metrics workflow | Plain-language wellness insights and trend-oriented summaries | QR/email-ready digital report experience | Payment-verified purchase and dispensing workflow |

### Designed around a simple journey

```text
                    ┌───────────────────────┐
                    │       PATIENT         │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     RELiV KIOSK       │
                    │   Touchscreen UI      │
                    └───────────┬───────────┘
                                │
                    ┌───────────┴───────────┐
                    ▼                       ▼
             ┌─────────────┐        ┌─────────────┐
             │ Health Scan │        │ Kit Purchase│
             └──────┬──────┘        └──────┬──────┘
                    │                      │
                    ▼                      ▼
             ┌─────────────┐        ┌─────────────┐
             │ Wellness    │        │ Verified    │
             │ Report      │        │ Payment     │
             └──────┬──────┘        └──────┬──────┘
                    │                      │
                    ▼                      ▼
             ┌─────────────┐        ┌─────────────┐
             │ QR / Digital│        │ Dispense +  │
             │ Delivery    │        │ Receipt     │
             └─────────────┘        └─────────────┘
```

---

## 🖥️ See the product

### 🌐 Live Website

**[Open the RELiV web experience →](https://relivkiosk.vercel.app/)**

### 🖼️ Product Poster

![RELiV — Now Live](assets/posters/reliv-now-live.jpg)

---

## 📸 Product Gallery

The repository is intended to use real RELiV assets rather than generated mockups.

| Physical Prototype | Health Report | Digital Receipt |
|---|---|---|
| ![RELiV prototype](assets/posters/reliv-now-live.jpg) | [Explore report](docs/reports/health-report.md) | [Explore receipt](docs/reports/receipt.md) |

---

## 🧠 Health report experience

RELiV's sample report is designed as a multi-section wellness experience rather than a single measurement screen. It includes:

- Vital signs overview
- Body-composition metrics
- Integrated analysis cards
- Current health-status tables
- Weekly consistency confidence
- A 7-day progress journey
- QR-based report access

The supplied sample report is a product/demo artifact and should not be interpreted as a medical diagnosis or clinical validation.

**[Read the report documentation →](docs/reports/health-report.md)**

---

## 💳 Payment & dispensing experience

The purchase workflow is designed around a **session-bound, verified transaction**:

```text
Customer
   │
   ▼
Select item
   │
   ▼
Online payment
   │
   ▼
Server verification
   │
   ▼
Signed one-use authorization
   │
   ▼
Kiosk verification
   │
   ├───────────────┐
   ▼               ▼
Dispense         Receipt
```

The target architecture uses a signed authorization bound to the kiosk session, service, amount and expiry, with replay protection before a paid report or dispensing action is released.

---

## ⚙️ Technical Architecture

RELiV follows an **offline-first kiosk + phone bridge** concept.

```text
                         RELiV KIOSK
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   Touch UI          Raspberry Pi 5           SQLite          │
│   React       ───►  Local API / Logic  ───►  Local Data     │
│                          │                                   │
│             ┌────────────┴────────────┐                      │
│             ▼                         ▼                      │
│       ESP32-S3 / Sensors        ESP32 / Dispenser           │
│       BLE • UART                MQTT / Local messaging      │
│                                                              │
└──────────────────────────┬───────────────────────────────────┘
                           │ Local Wi-Fi
                           ▼
                    CUSTOMER PHONE
                           │
                  Mobile Internet Bridge
                           │
             ┌─────────────┴─────────────┐
             ▼                           ▼
       Payment Verification        Deferred Delivery
             │                           │
             ▼                           ▼
          Razorpay                  Report / QR flow
```

### Core technology

| Layer | Technology / Approach |
|---|---|
| Kiosk controller | Raspberry Pi 5 (4 GB) |
| Microcontrollers | ESP32 / ESP32-S3 |
| Frontend | React |
| Backend | Node.js + Express |
| Device processing | Python |
| Database | SQLite |
| Device communication | BLE · UART · MQTT |
| Payment | Razorpay verification flow |
| Deployment | Local kiosk + web/cloud components |

---

## 🔐 Security & reliability principles

RELiV's target payment architecture is deliberately designed around failure cases, not just the happy path.

- Session-bound authorization
- Signed payment responses
- One-use authorization consumption
- Expiry validation
- Replay protection
- Durable local logs
- Retry-safe fulfillment
- No secrets committed to the repository
- Local operation for core kiosk functions

> **Important:** these are engineering targets for the prototype architecture. End-to-end validation and failure testing are still part of the remaining development work.

---

## 🏗️ Current development status

| Area | Status |
|---|---|
| Physical kiosk | 🟢 Prototype assembled |
| Touch UI | 🟢 Demonstrated |
| Local backend | 🟢 Demonstrated |
| Health screening workflow | 🟢 Prototype workflow |
| Digital health report | 🟢 Demonstrated |
| Local inventory/admin concept | 🟢 Implemented concept |
| Secure payment + dispensing flow | 🟡 Integration / validation |
| Sensor calibration & reference testing | 🟡 In progress |
| Full failure-path testing | 🟡 In progress |
| Campus pilot | 🔵 Next gate |
| Commercial deployment | ⚪ Future |

**Current prototype estimate: ~60% complete.**

---

## 🎯 Where RELiV can fit

### 🎓 Campuses
Routine wellness checks for students and staff without requiring a separate clinic visit for every basic measurement.

### 🏢 Workplaces
Accessible wellness stations in offices and institutional environments.

### 🏋️ Gyms & fitness spaces
Convenient measurements and wellness tracking alongside regular fitness activity.

### 🏘️ Community locations
A modular platform that can be developed for broader preventive-health access.

---

## 🏆 Recognition

**1st Runner-Up — Investopia, Bengal E-Summit 2026**

The project presentation records the recognition at IEM Gurukul, Kolkata, on 29–30 August 2026.

RELiV is also being developed under the **Student Innovation / Hardware** framing for Smart India Hackathon 2026.

---

## 📚 Documentation

| Resource | Description |
|---|---|
| [SIH Presentation Hub](docs/presentation/README.md) | Full project presentation and technical/business context |
| [Sample Health Report](docs/reports/health-report.md) | Demonstration wellness report |
| [Sample Receipt](docs/reports/receipt.md) | Demonstration digital purchase receipt |
| [System Architecture](docs/architecture/system-architecture.md) | Architecture and data-flow notes |
| [Product Workflow](docs/architecture/product-workflow.md) | Patient and dispensing journeys |

---

## 🗂️ Repository Structure

```text
Reliv/
├── README.md
├── LICENSE
├── SECURITY.md
├── CONTRIBUTING.md
├── CHANGELOG.md
│
├── assets/
│   ├── demo/
│   ├── gallery/
│   ├── posters/
│   └── screenshots/
│
├── docs/
│   ├── architecture/
│   ├── presentation/
│   ├── reports/
│   └── product/
│
├── frontend/
├── backend/
├── hardware/
├── ai-engine/
└── firmware/
```

Folders are intentionally separated so the repository can grow from prototype documentation into the actual product codebase without becoming a dump of unrelated files.

---

## 🚀 Getting Started

The public repository currently focuses on the **product, prototype evidence and architecture**. Implementation modules can be added under their respective directories as they are finalized.

### Planned module conventions

```text
frontend/     → patient/admin web interfaces
backend/      → APIs and session/business logic
hardware/     → Raspberry Pi kiosk integration
firmware/     → ESP32 sensor and dispenser firmware
ai-engine/    → wellness/report processing
```

Do not commit API keys, payment secrets, private patient information, production credentials, or device passwords.

---

## 🗺️ Roadmap

### Phase 1 — Prototype foundation
- [x] Physical kiosk enclosure
- [x] Touchscreen interface
- [x] Local processing foundation
- [x] Digital report concept
- [x] Product website

### Phase 2 — Integration
- [ ] Complete sensor integration
- [ ] Validate measurements against reference devices
- [ ] Complete secure payment-to-dispense flow
- [ ] Harden offline/phone-bridge behavior
- [ ] Complete failure-path testing

### Phase 3 — Pilot
- [ ] Supervised campus pilot
- [ ] Measure usability and session time
- [ ] Measure reading consistency
- [ ] Measure report delivery reliability
- [ ] Measure stock and downtime behavior

### Phase 4 — Scale
- [ ] Modular hardware refinement
- [ ] Institutional deployment model
- [ ] Maintenance and replenishment workflow
- [ ] Multi-location operations

---

## ⚠️ Responsible Use

RELiV is a **prototype preventive-health and wellness platform**. Screening outputs and generated summaries are not a substitute for professional medical diagnosis, treatment, or emergency care.

Clinical validation, calibration, regulatory/permission requirements, privacy controls, safe medicine-handling procedures, and supervised operational testing must be completed before broader real-world deployment.

Sample documents in this repository are demonstration artifacts. Any personal identifiers should be removed or anonymized before public distribution.

---

## 🤝 Contributing

Ideas, technical improvements, hardware integration work, UX feedback, testing strategies and documentation improvements are welcome.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the contribution workflow.

---

## 📜 License

See [LICENSE](LICENSE).

---

<div align="center">

### RELiV

**You matter. RELiV cares.**

[🌐 Website](https://relivkiosk.vercel.app/) · [💻 GitHub](https://github.com/Vaibhavcool4805/Reliv)

</div>
