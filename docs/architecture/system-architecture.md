# RELiV System Architecture

## Overview

RELiV is designed around an offline-first kiosk with a phone bridge for services that require external connectivity.

```mermaid
flowchart TD
    A[Patient] --> B[RELiV Touch UI]
    B --> C[Raspberry Pi 5]
    C --> D[Local API / Session Logic]
    C --> E[SQLite]
    C --> F[ESP32-S3 Sensors]
    C --> G[ESP32 Dispenser]
    F --> C
    G --> C
    C --> H[Local Wi-Fi]
    H --> I[Customer Phone]
    I --> J[Mobile Internet]
    J --> K[Payment Verification]
    K --> I
    I --> C
```

## Core components

- **Raspberry Pi 5:** local kiosk controller.
- **React:** touch-oriented user interface.
- **Node.js / Express:** local APIs and session/business logic.
- **Python:** measurement processing and device integration.
- **ESP32 / ESP32-S3:** sensor and dispensing interfaces.
- **SQLite:** local inventory, prices and application data.
- **BLE / UART / MQTT:** device communication paths.
- **Phone bridge:** provides mobile connectivity for payment and deferred delivery workflows.

## Payment authorization target

The intended flow is:

1. Create a kiosk session.
2. Bind the purchase request to the session, service and amount.
3. Verify payment through the server-side payment flow.
4. Return a signed, one-use authorization with an expiry.
5. Verify the authorization locally at the kiosk.
6. Reject expired or replayed authorizations.
7. Consume the authorization atomically before fulfillment.
8. Make dispensing and receipt generation retry-safe.

This is an architecture target. Complete end-to-end integration and failure testing remain part of the prototype roadmap.
