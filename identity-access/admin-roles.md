# Microsoft 365 Admin Role Management

## Overview
This document outlines a secure approach to managing administrative roles within Microsoft 365 using Azure AD (Entra ID). The objective is to reduce risk by enforcing least-privilege access, minimising the number of highly privileged accounts, and aligning with Cyber Essentials and enterprise security best practices.

---

## Why Admin Role Management Matters
Administrative accounts represent a high-value target for attackers. Excessive or poorly controlled admin privileges significantly increase the impact of account compromise, misconfiguration, or insider threat.

Proper role management helps to:
- Reduce the attack surface
- Limit the impact of credential compromise
- Improve audit and compliance readiness
- Support safe and controlled system changes

---

## Secure Admin Role Principles Applied

### 1. Minimise Global Administrators
- The number of Global Administrator accounts is kept to the minimum required for business continuity.
- Day-to-day administration is performed using lower-privilege roles where possible.
- Global Administrator access is reserved for break-glass or escalation scenarios.

### 2. Role-Based Administration
Administrative permissions are assigned using built-in Azure AD roles, such as:
- User Administrator
- Exchange Administrator
- SharePoint Administrator
- Security Administrator

This ensures administrators only have access relevant to their responsibilities.

### 3. Separation of Admin and User Accounts
- Administrative roles are assigned to dedicated admin accounts rather than standard user accounts.
- This reduces the risk of privilege misuse during normal user activity such as email access or web browsing.

### 4. Justification and Review
- Admin role assignments are documented and justified.
- Regular reviews are conducted to ensure roles remain appropriate and are removed when no longer required.

---

## Alignment with Cyber Essentials
This approach supports Cyber Essentials requirements by:
- Enforcing least-privilege access
- Reducing the risk of unauthorised system changes
- Improving accountability and traceability of administrative actions

---

## Notes
All configurations described are based on lab environments and best-practice guidance. No production credentials or sensitive information are included.
