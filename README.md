# Microsoft Entra ID Privileged Identity Management Lab

![Platform](https://img.shields.io/badge/Platform-Microsoft%20Entra%20ID-0078D4)
![Identity](https://img.shields.io/badge/Identity-IAM-5C2D91)
![Security](https://img.shields.io/badge/Security-Privileged%20Identity%20Management-0078D4)
![Access](https://img.shields.io/badge/Access-Just--in--Time-success)
![Authentication](https://img.shields.io/badge/Authentication-MFA-orange)
![Governance](https://img.shields.io/badge/Governance-RBAC-blue)
![Workflow](https://img.shields.io/badge/Workflow-Approval-purple)
![Monitoring](https://img.shields.io/badge/Monitoring-Audit%20Logs-green)
![Project](https://img.shields.io/badge/Project-Completed-brightgreen)

<p align="center">
  <img src="Docs/PIM%20cover.png" alt="Nzweme Identity Security Lab - Microsoft Entra PIM" width="850">
</p>

---

## 🎥 Project Demo

A complete walkthrough of the Microsoft Entra Privileged Identity Management
implementation is available below.

The demonstration covers:

- PIM role configuration
- Global Administrator eligibility
- Just-in-Time role activation
- MFA and justification requirements
- Approval workflow
- Privileged role activation
- PIM audit verification
- Manual deactivation
- Verification that role eligibility is retained

### ▶️ Watch the Full Demo

[![Microsoft Entra PIM Project Demo](https://img.youtube.com/vi/aH3IwJUI_NY/maxresdefault.jpg)](https://youtu.be/aH3IwJUI_NY)

**YouTube:** [Microsoft Entra Privileged Identity Management Project Demo](https://youtu.be/aH3IwJUI_NY)

---

## 📌 Project Overview

This project demonstrates the design, configuration, and testing of
**Microsoft Entra Privileged Identity Management (PIM)** in the
**Nzweme Identity Security Lab**.

The goal was to implement a secure privileged-access model that reduces
standing administrative privileges by allowing an administrator to become
eligible for a privileged role and activate that role only when it is needed.

Instead of maintaining permanent active Global Administrator privileges,
the administrator must complete a controlled activation workflow.

The implemented workflow is:

**Eligible → Request → MFA → Justification → Approval → Activate → Audit → Deactivate**

This project demonstrates practical implementation of:

- Privileged Identity Management (PIM)
- Just-in-Time (JIT) privileged access
- Least privilege
- Role-Based Access Control (RBAC)
- Multi-Factor Authentication (MFA)
- Approval-based privilege elevation
- Time-bound administrative access
- Separation of duties
- Privileged access auditing
- Identity governance

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|---|---|
| **Microsoft Entra ID** | Cloud identity and access management platform |
| **Microsoft Entra PIM** | Privileged role governance and JIT access |
| **Microsoft Entra Admin Center** | Administration and configuration |
| **Azure MFA** | Strong authentication during privileged activation |
| **Microsoft Entra RBAC** | Administrative role assignment |
| **PIM Approval Workflow** | Independent approval before elevation |
| **PIM Resource Audit** | Privileged activity monitoring and evidence |
| **Global Administrator Role** | Privileged role used for the lab |

---

## 🏗️ Lab Environment

| Component | Configuration |
|---|---|
| Environment | Nzweme Identity Security Lab |
| Platform | Microsoft Entra ID |
| Tenant Domain | `nzwemeidentitylab.onmicrosoft.com` |
| Privileged Access | Microsoft Entra PIM |
| Privileged Role | Global Administrator |
| Maximum Activation | 1 Hour |
| MFA | Required |
| Justification | Required |
| Approval | Required |
| Audit Logging | Enabled through PIM |

### Lab Identities

Three identities were used to demonstrate separation of responsibilities.

| Identity | Responsibility |
|---|---|
| **Lab Admin** | PIM configuration and role governance |
| **Elie Admin** | Eligible privileged administrator |
| **PIM Approver** | Independent privileged-access approver |

This separation prevents the privileged administrator from controlling the
entire privileged-access lifecycle.

---

# 🔐 Security Problem

Traditional administrative environments may provide administrators with
privileged roles that remain active continuously.

This creates **standing privileged access**.

If such an account is compromised, the attacker may immediately inherit the
account's administrative permissions.

Microsoft Entra PIM provides an alternative model where privileged roles can
remain **eligible but inactive** until access is required.

<p align="center">
  <img src="Docs/JIT%20vs%20Standing%20access.png"
       alt="Standing Access vs Just-in-Time Access"
       width="850">
</p>

### Standing Access

```text
Administrator
     │
     ▼
Global Administrator
     │
     ▼
Privilege continuously active
