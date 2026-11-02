# 6. Joiner, Mover, Leaver (JML) and Access Management

> **Purpose:** Give people what they need on day one, adjust it when their role changes, and remove it cleanly when they leave. This is one of the biggest security and cost controls in IT.

---

## 6.1 Joiner (New Employee)

```mermaid
flowchart TD
    A[HR confirms new joiner, start date, role, manager] --> B[Joiner ticket auto-created, at least 5 business days before start]
    B --> C[Manager confirms access and equipment needs]
    C --> D[IT prepares laptop and accessories from stock]
    D --> E[Create accounts: identity, email, MFA]
    E --> F[Role-based access applied as per template]
    F --> G{Extra access requested?}
    G -- Yes --> H[Approval per access matrix]
    G -- No --> I[Day 1 handover]
    H --> I
    I --> J[Security and policy briefing, user signs equipment acceptance]
    J --> K[Check in at Day 7 and Day 30]
```

**Rules**
- Role-based access templates (by department or job role) keep it simple and consistent.
- New joiners get the minimum access required, nothing more.
- MFA is set up on day one.
- Hardware shortage? Raise a purchase request early, not on the morning of day one.

## 6.2 Mover (Role or Department Change)

1. HR or the manager raises the mover ticket with the effective date.
2. IT **removes access no longer needed** (this is the step most companies forget).
3. New access is granted as per the new role and approvals.
4. Equipment and mailboxes reviewed.
5. Manager confirms in writing.

## 6.3 Leaver

```mermaid
flowchart TD
    A[HR notifies leaver and last working day] --> B[Leaver ticket raised]
    B --> C[Manager confirms data handover and mailbox needs]
    C --> D[Last day: disable accounts, revoke MFA, remove from groups]
    D --> E[Recover laptop, phone, badge, tokens]
    E --> F[Device wiped or re-imaged, asset register updated]
    F --> G[Mailbox and data retained or archived as per policy]
    G --> H[Licences reclaimed]
    H --> I[Close and record]
```

**Rules**
- Accounts are **disabled at the end of the last working day** (immediately for involuntary or high-risk exits).
- Never share a leaver's password. Use delegated access to mailbox if needed.
- Check for shared accounts, service accounts, and admin rights owned by the leaver.
- Leaver audit: compare HR leaver list with active directory every month.

---

## 6.4 Access Management Principles

| Principle | Meaning |
|-----------|---------|
| **Least privilege** | Only the access needed to do the job |
| **Need to know** | Sensitive data only for those with a reason |
| **Segregation of duties** | One person should not hold conflicting rights (e.g., create and approve payments) |
| **Time-bound privileged access** | Admin rights granted for a period, then removed |
| **Individual accounts** | No shared logins where avoidable |
| **MFA everywhere** | Especially remote, admin, and email |

### Periodic Access Review

| System Type | Review Frequency | Reviewer |
|-------------|------------------|----------|
| Privileged / admin accounts | Quarterly | IT Head plus Security |
| Finance, HR, and sensitive apps | Quarterly | Application Owner |
| General business apps | Every 6 months | Line Managers |
| Third-party / vendor accounts | Quarterly | Vendor owner |

Unused accounts (no login for **90 days**) are disabled after notice.

---

## 6.5 Additional Flowcharts

### A. Mover (Role or Department Change)

```mermaid
flowchart TD
    A[HR or manager notifies role change and effective date] --> B[Mover ticket raised]
    B --> C[IT lists current access and equipment]
    C --> D[Remove access not needed for new role]
    D --> E[Apply new role template]
    E --> F{Extra access requested?}
    F -- Yes --> G[Approval per access matrix]
    F -- No --> H[Review equipment and mailbox]
    G --> H
    H --> I[Manager confirms in writing]
    I --> J[Close ticket]
```

### B. Access Request

```mermaid
flowchart TD
    A[User requests access] --> B[Service Desk logs and identifies application]
    B --> C{Sensitive system? Finance, HR, production, customer data}
    C -- No --> D[Line Manager approval]
    D --> E[Application Owner approval]
    C -- Yes --> F[Line Manager approval]
    F --> G[Application Owner approval]
    G --> H[Security or Data Owner approval]
    E --> I{Admin or privileged?}
    H --> I
    I -- Yes --> J[IT Head approval, set end date for time-boxed access]
    I -- No --> K[Provision least-privilege access]
    J --> K
    K --> L[Notify user, record in ticket]
    L --> M[Include in next access review]
```

### C. Periodic Access Review

```mermaid
flowchart TD
    A[Review cycle starts: quarterly or half-yearly] --> B[Export user access lists per system]
    B --> C[Send to reviewers: managers or application owners]
    C --> D[Reviewer marks keep or remove for each user]
    D --> E{All reviews returned on time?}
    E -- No --> F[Reminder, then escalate to reviewer's manager]
    F --> D
    E -- Yes --> G[IT removes access marked for removal]
    G --> H[Check for accounts unused for 90 days]
    H --> I[Disable inactive accounts after notice]
    I --> J[Record evidence for audit]
```
