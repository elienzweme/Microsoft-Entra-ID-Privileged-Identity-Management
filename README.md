# 🔐 Microsoft Entra ID Privileged Identity Management Lab

![Platform](https://img.shields.io/badge/Platform-Microsoft%20Entra%20ID-0078D4)
![Identity](https://img.shields.io/badge/Identity-IAM-5C2D91)
![Security](https://img.shields.io/badge/Security-PIM-0078D4)
![Access](https://img.shields.io/badge/Access-Just--in--Time-success)
![Authentication](https://img.shields.io/badge/Authentication-MFA-orange)
![Governance](https://img.shields.io/badge/Governance-RBAC-blue)
![Workflow](https://img.shields.io/badge/Workflow-Approval-purple)
![Monitoring](https://img.shields.io/badge/Monitoring-Audit%20Logs-green)
![Project](https://img.shields.io/badge/Project-Completed-brightgreen)

<p align="center">
  <img src="Docs/PIM%20cover.png"
       alt="Nzweme Identity Security Lab - Microsoft Entra PIM"
       width="850">
</p>

<p align="center">
  <b>Microsoft Entra ID • Privileged Identity Management • Just-in-Time Access • Identity Governance</b>
</p>

---

# 🎥 Project Demo

This video demonstrates the complete Microsoft Entra Privileged Identity
Management implementation performed in the **Nzweme Identity Security Lab**.

The demonstration includes:

- PIM role configuration
- Global Administrator eligibility
- Just-in-Time privileged access
- MFA enforcement
- Activation justification
- Independent approval workflow
- Temporary Global Administrator activation
- PIM Resource Audit verification
- Manual privileged-role deactivation
- Verification that eligibility remains after deactivation

## ▶️ Watch the Full Demo

<p align="center">
  <a href="https://youtu.be/aH3IwJUI_NY">
    <img src="https://img.youtube.com/vi/aH3IwJUI_NY/maxresdefault.jpg"
         alt="Microsoft Entra PIM Project Demo"
         width="850">
  </a>
</p>

<p align="center">
  <b>
    <a href="https://youtu.be/aH3IwJUI_NY">
      ▶ Watch the Microsoft Entra PIM Lab Demo on YouTube
    </a>
  </b>
</p>

---

# 📌 Project Overview

This project demonstrates the design, configuration, testing, and validation of
**Microsoft Entra Privileged Identity Management (PIM)** in the
**Nzweme Identity Security Lab**.

The goal of the project was to implement a controlled privileged-access model
that reduces **standing administrative privileges**.

Instead of maintaining a permanently active Global Administrator account,
Microsoft Entra PIM was used to make an administrator **eligible** for the role.

When privileged access is required, the administrator must complete a
controlled activation workflow.

### Privileged Access Lifecycle

**Eligible → Request → MFA → Justification → Approval → Activate → Audit → Deactivate**

The project demonstrates practical implementation of:

- Privileged Identity Management (PIM)
- Privileged Access Management (PAM) concepts
- Just-in-Time (JIT) privileged access
- Least privilege
- Role-Based Access Control (RBAC)
- Multi-Factor Authentication (MFA)
- Approval-based privilege elevation
- Time-bound administrative access
- Separation of duties
- Privileged-access auditing
- Identity governance
- Administrative role lifecycle management

---

# 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| **Microsoft Entra ID** | Cloud Identity and Access Management platform |
| **Microsoft Entra PIM** | Privileged role governance and Just-in-Time access |
| **Microsoft Entra Admin Center** | Identity and privileged-access administration |
| **Azure MFA** | Strong authentication during privileged activation |
| **Microsoft Entra RBAC** | Administrative role assignment and authorization |
| **PIM Approval Workflow** | Independent approval before privilege elevation |
| **PIM Resource Audit** | Privileged activity monitoring and audit evidence |
| **Global Administrator Role** | Privileged administrative role used for testing |

---

# 🏗️ Lab Environment

| Component | Configuration |
|---|---|
| **Environment** | Nzweme Identity Security Lab |
| **Platform** | Microsoft Entra ID |
| **Tenant Domain** | `nzwemeidentitylab.onmicrosoft.com` |
| **Privileged Access** | Microsoft Entra PIM |
| **Privileged Role** | Global Administrator |
| **Maximum Activation** | 1 Hour |
| **MFA** | Required |
| **Justification** | Required |
| **Approval** | Required |
| **Audit Logging** | Microsoft Entra PIM Resource Audit |

---

# 👥 Administrative Identities

Three identities were used to demonstrate separation of responsibilities.

| Identity | Responsibility |
|---|---|
| **Lab Admin (`labadmin`)** | PIM configuration, eligible assignments, and governance |
| **Elie Admin (`elie.admin`)** | Eligible administrator requesting temporary Global Administrator access |
| **PIM Approver (`pim.approver`)** | Independent reviewer and approver of privileged-access requests |

This separation demonstrates **separation of duties**.

The account requesting privileged access does not control the entire
privileged-access lifecycle.

---

# 🔐 The Security Problem

Traditional administrative environments may provide administrators with
privileged roles that remain active continuously.

This creates **standing privileged access**.

If an administrative identity with permanently active privileges is
compromised, those privileges may immediately become available to an attacker.

Microsoft Entra Privileged Identity Management provides a different approach.

Administrators can remain **eligible but inactive** until privileged access is
actually required.

<p align="center">
  <img src="Docs/JIT%20vs%20Standing%20access.png"
       alt="Standing Access vs Just-in-Time Access"
       width="850">
</p>

## Standing Privileged Access

```text
Administrator
      │
      ▼
Global Administrator
      │
      ▼
Privilege Continuously Active
```

## Just-in-Time Privileged Access

```text
Eligible Administrator
        │
        ▼
Request Activation
        │
        ▼
MFA + Justification
        │
        ▼
Approval
        │
        ▼
Temporary Privilege
        │
        ▼
Deactivation / Expiration
```

The Just-in-Time model reduces the amount of time privileged permissions remain
active.

---

# 🔄 PIM Privileged Access Workflow

The lab implemented the following end-to-end privileged-access lifecycle:

```text
┌─────────────────────────────┐
│          LAB ADMIN          │
│                             │
│ Configure PIM Role Policy   │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│         ELIE ADMIN          │
│                             │
│ Eligible for Global Admin   │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ Request Role Activation     │
│                             │
│ + Business Justification    │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│             MFA             │
│                             │
│ Identity Verification       │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│        PIM APPROVER         │
│                             │
│ Review Activation Request   │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│     GLOBAL ADMINISTRATOR    │
│                             │
│ Activated Temporarily       │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│       RESOURCE AUDIT        │
│                             │
│ Privileged Events Recorded  │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│        DEACTIVATION         │
│                             │
│ Active Privilege Removed    │
└──────────────┬──────────────┘
               │
               ▼
        REMAINS ELIGIBLE
```

---

# ⚙️ Implementation

## 1️⃣ Configure Privileged Identity Management

Microsoft Entra Privileged Identity Management was configured for the
**Global Administrator** role.

The activation policy was configured to require additional controls before
privileged access could become active.

### PIM Configuration

| Setting | Configuration |
|---|---|
| **Role** | Global Administrator |
| **Maximum activation duration** | 1 hour |
| **Require Azure MFA** | Enabled |
| **Require justification** | Enabled |
| **Require approval** | Enabled |
| **Approver** | PIM Approver |
| **Ticket information** | Not required |

These controls prevent the eligible administrator from immediately obtaining
privileged access without completing the configured activation requirements.

---

## 2️⃣ Assign Global Administrator Eligibility

The **Elie Admin** identity was assigned the Global Administrator role as an
**eligible assignment**.

```text
Elie Admin
     │
     └── Global Administrator
              │
              └── Eligible
```

Eligibility does **not** mean that Global Administrator privileges are
continuously active.

Instead, the account is authorized to request temporary activation when
administrative privileges are required.

This reduces standing administrative privilege.

---

## 3️⃣ Request Privileged Role Activation

The eligible administrator navigated to:

**Privileged Identity Management → My roles → Microsoft Entra roles**

The Global Administrator role appeared under:

**Eligible assignments**

The administrator selected:

**Activate**

The activation request required a justification describing why privileged
administrative access was needed.

### Activation Justification Used During Testing

> Authorized IAM lab administration to validate Microsoft Entra Privileged
> Identity Management, just-in-time Global Administrator activation, MFA
> enforcement, and privileged access audit logging.

The requested activation duration was limited to **one hour**.

---

## 4️⃣ Multi-Factor Authentication

The PIM activation policy required **Azure MFA**.

MFA adds an additional identity-verification requirement before privileged
administrative access can be activated.

```text
Username + Password
        │
        ▼
       MFA
        │
        ▼
PIM Security Controls
        │
        ▼
Privileged Access
```

This provides additional protection against credential compromise.

---

## 5️⃣ Independent Approval Workflow

The activation request was routed to the dedicated **PIM Approver**.

The approver reviewed information including:

- Requester
- Requested role
- Resource
- Activation duration
- Business justification

The request was then approved.

This demonstrates **separation of duties** because the identity requesting
privileged access is separate from the identity approving the elevation.

```text
Elie Admin
    │
    │ Requests Access
    ▼
PIM Workflow
    │
    │ Requires Approval
    ▼
PIM Approver
    │
    │ Approves
    ▼
Temporary Global Administrator
```

---

## 6️⃣ Just-in-Time Global Administrator Activation

After approval, the Global Administrator role became active for
**Elie Admin**.

The role appeared under:

**My roles → Active assignments**

The assignment displayed:

- Global Administrator
- Activated state
- Activation expiration
- Deactivate option

The privilege existed only for the approved activation window.

This demonstrates the difference between:

### Eligibility

The administrator is authorized to **request** privileged access.

### Activation

The administrator temporarily receives the privileged permissions after
satisfying the required security controls.

---

# 📊 Audit & Monitoring

Microsoft Entra PIM **Resource Audit** was used to verify the
privileged-access lifecycle.

The audit trail recorded the major events associated with the activation.

```text
Activation Requested
        │
        ▼
Approval Requested
        │
        ▼
Request Approved
        │
        ▼
Role Activation Completed
```

During testing, the audit trail showed the following sequence:

| Event | Actor |
|---|---|
| **Activation requested** | Elie Admin |
| **Approval requested** | Elie Admin / PIM workflow |
| **Activation approved** | PIM Approver |
| **Activation completed** | Microsoft Entra PIM |

The completed audit event included information such as:

- Requester
- Approver
- Target role
- Resource
- Subject
- Timestamp
- Activation reason
- Status
- Expiration
- Correlation ID

This provides traceability for privileged administrative activity.

Audit evidence can support:

- Security investigations
- Privileged-access reviews
- Identity governance
- Compliance evidence
- Administrative accountability

---

# ⏹️ Privileged Role Deactivation

The Global Administrator role was manually deactivated before the maximum
activation period expired.

The deactivation workflow completed successfully.

After refreshing Microsoft Entra PIM:

## Active Assignments

```text
Global Administrator
Status: No Active Assignment
```

## Eligible Assignments

```text
Global Administrator
Status: Eligible
Action: Activate
```

This confirmed an important PIM behavior:

> **Deactivation removes the active privileged role without removing the
> administrator's eligibility.**

A future privileged administrative session therefore requires a new PIM
activation workflow.

---

# 🔎 PIM Lifecycle Demonstrated

```text
┌─────────────┐
│  ELIGIBLE   │
└──────┬──────┘
       ▼
┌─────────────┐
│   REQUEST   │
└──────┬──────┘
       ▼
┌─────────────┐
│     MFA     │
└──────┬──────┘
       ▼
┌─────────────┐
│ JUSTIFY     │
└──────┬──────┘
       ▼
┌─────────────┐
│  APPROVAL   │
└──────┬──────┘
       ▼
┌─────────────┐
│  ACTIVATE   │
└──────┬──────┘
       ▼
┌─────────────┐
│    AUDIT    │
└──────┬──────┘
       ▼
┌─────────────┐
│ DEACTIVATE  │
└──────┬──────┘
       ▼
┌─────────────┐
│  ELIGIBLE   │
└─────────────┘
```

---

# ✅ Validation Results

| Security Control | Status |
|---|---|
| Global Administrator eligible assignment | ✅ Verified |
| No continuous active GA privilege | ✅ Verified |
| Just-in-Time activation | ✅ Verified |
| MFA activation requirement | ✅ Verified |
| Activation justification | ✅ Verified |
| Independent approval | ✅ Verified |
| One-hour activation window | ✅ Verified |
| Temporary Global Administrator activation | ✅ Verified |
| PIM Resource Audit logging | ✅ Verified |
| Manual deactivation | ✅ Verified |
| Active privilege removed after deactivation | ✅ Verified |
| Global Administrator eligibility retained | ✅ Verified |

---

# 🔑 Security Principles Demonstrated

## 🛡️ Least Privilege

Privileged permissions are activated only when required instead of remaining
continuously available.

---

## ⏱️ Just-in-Time Access

Global Administrator privileges are temporarily activated for a defined
administrative task and time period.

---

## 👥 Separation of Duties

The privileged administrator and privileged-access approver are separate
identities.

This prevents the requester from independently controlling the entire
privileged-access lifecycle.

---

## 🔐 Strong Authentication

MFA provides an additional identity-verification requirement before privileged
role elevation.

---

## 📝 Accountability

Activation requests require a documented justification explaining why the
privileged access is required.

---

## 🔎 Auditability

Microsoft Entra PIM maintains records of privileged-access requests,
approvals, activations, and deactivations.

---

## 🎯 Reduced Standing Privilege

The administrator remains eligible for Global Administrator but does not need
to maintain continuously active Global Administrator permissions.

---

# 🧠 Skills Demonstrated

This project demonstrates hands-on experience with:

### Identity & Access Management

- Microsoft Entra ID
- Identity and Access Management (IAM)
- Microsoft Entra RBAC
- Administrative role management
- Identity governance concepts

### Privileged Access

- Privileged Identity Management (PIM)
- Privileged Access Management (PAM) concepts
- Just-in-Time privileged access
- Time-bound privilege elevation
- Least privilege
- Privileged role lifecycle management

### Authentication & Authorization

- Azure MFA
- Role eligibility
- Role activation
- Approval workflows
- Separation of duties

### Security Operations & Governance

- Privileged-access auditing
- PIM Resource Audit
- Security control validation
- Administrative accountability
- Audit evidence analysis

---

# 📚 Project Documentation

The complete technical project report is available in this repository.

### 📄 [View the Microsoft Entra PIM Project Report](Docs/Nzweme_Entra_PIM_Project.pdf)

The report contains additional details about:

- Project objectives
- Lab architecture
- PIM configuration
- Eligible role assignment
- Activation workflow
- Approval workflow
- Audit evidence
- Deactivation testing
- Validation results
- Security lessons learned

---

# 🎥 Video Demonstration

The complete project demonstration is available on YouTube.

<p align="center">
  <a href="https://youtu.be/aH3IwJUI_NY">
    <img src="https://img.youtube.com/vi/aH3IwJUI_NY/maxresdefault.jpg"
         alt="Microsoft Entra PIM Project Demo"
         width="750">
  </a>
</p>

<p align="center">
  <b>
    <a href="https://youtu.be/aH3IwJUI_NY">
      ▶ Watch Full Microsoft Entra PIM Project Demo
    </a>
  </b>
</p>

The video demonstrates the complete privileged-access lifecycle:

**Eligibility → Activation Request → MFA → Justification → Approval → Activation → Audit → Deactivation**

---

# 💡 Key Takeaways

This project demonstrates that privileged access should be managed as a
**security lifecycle**, rather than simply assigning an administrator a
permanent privileged role.

Microsoft Entra PIM allows organizations to separate:

**Role eligibility**

from

**Active privileged access**

The administrator can remain authorized to request the role while the actual
privileges remain inactive until they are required.

Combining:

- Eligibility
- MFA
- Justification
- Approval
- Time limitations
- Auditing
- Deactivation

creates a more controlled approach to privileged administrative access.

---

# 🚀 Future Enhancements

Future phases of the Nzweme Identity Security Lab can extend this project with:

- Microsoft Entra Conditional Access
- Authentication Context
- PIM for Groups
- Privileged Access Groups
- Access Reviews
- Microsoft Entra Identity Governance
- Additional privileged administrative roles
- Microsoft Graph automation
- PowerShell automation
- SIEM integration
- Privileged-role alerting
- ITSM / ticket integration
- Automated privileged-access reporting
- Non-human identity governance

---

# 📂 Repository Structure

```text
Microsoft-Entra-ID-Privileged-Identity-Management/
│
├── README.md
│
└── Docs/
    │
    ├── PIM cover.png
    ├── JIT vs Standing access.png
    └── Nzweme_Entra_PIM_Project.pdf
```

---

# 👤 Author

## Elie Nzweme

**Cybersecurity | Identity & Access Management | Microsoft Entra ID**

This project is part of my hands-on cybersecurity and identity-security
portfolio focused on implementing and validating enterprise IAM,
privileged-access, and identity-governance technologies.

---

# ⚠️ Disclaimer

This project was completed in a dedicated lab environment for educational,
technical demonstration, and portfolio purposes.

The identities, configurations, administrative roles, and workflows shown in
this repository are part of the lab environment and are not production
credentials or production configurations.

---

<p align="center">
  <b>Nzweme Identity Security Lab</b>
</p>

<p align="center">
  Microsoft Entra ID • IAM • PIM • JIT • MFA • RBAC • Identity Governance
</p>
