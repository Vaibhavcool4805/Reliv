# RELiV System Overview

```mermaid
flowchart LR
    U[Patient] --> K[RELiV Kiosk]

    K --> UI[Touchscreen UI]
    K --> PI[Raspberry Pi 5]
    PI --> DB[(SQLite)]
    PI --> API[Local Application Logic]

    API --> S[ESP32 / ESP32-S3]
    S --> H[Health Sensors]
    S --> D[Dispenser]

    API --> R[Wellness Report]
    R --> QR[QR / Digital Delivery]

    K --> P[Payment Flow]
    P --> V[Server Verification]
    V --> A[Signed One-Use Authorization]
    A --> D
    D --> RC[Digital Receipt]

    K -. Local Wi-Fi .-> PH[Customer Phone]
    PH --> NET[Mobile Internet]
```

## Architecture principles

- **Local-first:** core kiosk workflows are designed to remain operational locally.
- **Modular:** hardware, device communication, application logic and reporting are separated into clear layers.
- **Verified fulfillment:** payment verification precedes dispensing.
- **Digital delivery:** reports and receipts are designed for QR/digital access.
