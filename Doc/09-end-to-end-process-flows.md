# 9. End-to-End Process Flows (Visual Index)

> **Purpose:** One page to see how everything connects. Use this to explain the model to new team members, auditors, and business leaders. Each flow links to the document where the detail lives.

---

## 9.1 Master Flow: How Every Ticket Travels

```mermaid
flowchart TD
    A[User or monitoring raises a ticket] --> B[Service Desk logs, classifies, prioritises]
    B --> C{What is it?}
    C -- Something broken --> INC[Incident Management]
    C -- Something needed --> REQ[Service Request Management]
    C -- Risky technical modification --> CHG[Change Enablement]
    C -- Employee joins, moves, leaves --> JML[JML and Access]
    INC --> I1{P1 or P2?}
    I1 -- Yes --> I2[Major Incident process and communications]
    I1 -- No --> I3[Normal support queue]
    I2 --> I4[Resolve, PIR, Problem record]
    I3 --> I5[Resolve and close]
    I4 --> PM[Problem Management]
    PM --> CHG
    REQ --> R1{Approval needed?}
    R1 -- Yes --> R2[Approval workflow]
    R1 -- No --> R3[Fulfil]
    R2 --> R3
    R3 --> R4{Purchase needed?}
    R4 -- Yes --> PRO[Procurement and Vendor Onboarding]
    R4 -- No --> R5{Change needed?}
    PRO --> R5
    R5 -- Yes --> CHG
    R5 -- No --> R6[Deliver and close]
    CHG --> C1[Assess, approve, schedule, implement]
    C1 --> R6
    JML --> R3
    I4 --> KB[Knowledge Management]
    I5 --> KB
    R6 --> KB
    KB --> GOV[Governance, KPIs, Continual Improvement]
    GOV -.-> B
```

---

## 9.2 Request to Purchase to Deployment (Hardware or Software)

```mermaid
flowchart LR
    A[Request raised] --> B[Approval]
    B --> C{In catalogue or stock?}
    C -- Yes --> D[Deploy]
    C -- No --> E[Quotes per tier]
    E --> F[Vendor onboarding if new]
    F --> G[Final approval and PO]
    G --> H[Receive and register]
    H --> D
    D --> I[User confirms and closes]
```

See: [01 Service Request](01-service-request-management.md), [02 Procurement](02-procurement-and-vendor-onboarding.md)

## 9.3 Incident to Problem to Change to Knowledge

```mermaid
flowchart LR
    A[Incident] --> B[Resolved with fix or workaround]
    B --> C[Problem record if P1, repeat or unknown cause]
    C --> D[Root cause analysis]
    D --> E[Change to fix permanently]
    E --> F[Knowledge article and monitoring update]
    F --> G[Fewer repeat incidents]
```

See: [03 Incident](03-incident-management.md), [05 Problem](05-problem-and-knowledge-management.md), [04 Change](04-change-enablement.md)

## 9.4 Employee Lifecycle

```mermaid
flowchart LR
    A[Joiner: accounts, laptop, role access] --> B[Working: requests and incidents]
    B --> C{Role change?}
    C -- Yes --> D[Mover: remove old, add new access]
    D --> B
    C -- No --> E{Leaving?}
    E -- No --> B
    E -- Yes --> F[Leaver: disable, recover assets, archive data]
```

See: [06 JML and Access](06-joiner-mover-leaver-and-access.md)

---

## 9.5 Flowchart Index

| Process | Flowcharts Included | Where |
|---------|--------------------|-------|
| **Service Requests** | Request flow, request vs incident vs change, approval workflow, priority and SLA, new hardware, new software | [01](01-service-request-management.md) |
| **Procurement** | Purchase flow, quote rule decision, quote evaluation, single source, goods receipt and payment, vendor onboarding, contract renewal, asset lifecycle | [02](02-procurement-and-vendor-onboarding.md) |
| **Incident** | Standard flow, priority setting, P1 detailed flow, escalation timeline, communication sequence, security incident, PIR | [03](03-incident-management.md) |
| **Change** | Change type decision, standard, normal, emergency, CAB meeting, failed change and rollback | [04](04-change-enablement.md) |
| **Problem and Knowledge** | Problem trigger, root cause flow, knowledge article lifecycle | [05](05-problem-and-knowledge-management.md) |
| **JML and Access** | Joiner, mover, leaver, access request, access review | [06](06-joiner-mover-leaver-and-access.md) |
| **Communication** | Channel selection, maintenance comms, vendor SLA breach | [07](07-communication-and-escalation.md) |
| **Governance** | Monthly review, improvement loop, review cadence | [08](08-governance-roles-and-kpis.md) |
