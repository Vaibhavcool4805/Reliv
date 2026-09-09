# RELiV Product Workflow

```mermaid
flowchart TB
    P[Patient] --> K[Start RELiV Session]
    K --> S[Health Screening]
    S --> M[Capture Measurements]
    M --> W[Wellness Analysis]
    W --> R[Generate Digital Report]
    R --> Q[QR / Digital Delivery]

    K --> C[Select Essential Item]
    C --> Pay[Online Payment]
    Pay --> V[Payment Verification]
    V --> A[Signed One-Use Authorization]
    A --> KV[Kiosk Verification]
    KV --> D[Dispense]
    D --> Rec[Digital Receipt]
```

## End-to-end experience

**Screen → Understand → Pay → Verify → Dispense → Receive**

The screening and dispensing journeys remain distinct while sharing the same guided kiosk experience.
