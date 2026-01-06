# Multi-Factor Authentication (MFA) Configuration

## Overview
This document outlines a secure approach to implementing Multi-Factor Authentication (MFA) within Microsoft 365 using Azure AD (Entra ID). MFA is a critical control for protecting user and administrative accounts against credential-based attacks and is a core requirement for Cyber Essentials and enterprise security standards.

---

## Why MFA Is Critical
Usernames and passwords alone are vulnerable to phishing, reuse and credential leakage. MFA significantly reduces the likelihood of unauthorised access by requiring an additional verification factor that attackers are unlikely to possess.

MFA helps to:
- Prevent account takeover
- Reduce the impact of phishing attacks
- Protect privileged administrative access
- Improve compliance and audit readiness

---

## MFA Enforcement Approach

### 1. MFA for Administrative Accounts
- MFA is enforced for all administrative roles without exception.
- Privileged accounts are required to authenticate using strong MFA methods such as authenticator applications or hardware tokens.
- Legacy authentication methods are disabled to prevent MFA bypass.

This ensures that high-impact accounts remain protected even if credentials are compromised.

---

### 2. MFA for Standard User Accounts
- MFA is enabled for all users accessing Microsoft 365 services.
- Conditional enforcement is applied to balance security and usability, particularly for trusted locations and compliant devices.
- Risk-based access decisions are preferred where supported.

---

### 3. MFA Configuration Method
MFA is implemented using Azure AD Conditional Access policies rather than per-user MFA to allow:
- Centralised policy management
- Granular control and exclusions
- Better visibility and reporting

Security Defaults may be used in smaller environments where Conditional Access licensing is unavailable.

---

## Alignment with Cyber Essentials
This MFA implementation supports Cyber Essentials requirements by:
- Protecting cloud services and remote access
- Securing administrative access
- Reducing the risk of unauthorised system access

---

## Notes
All configurations described are based on lab environments and Microsoft-recommended best practices. No production systems or credentials are referenced.


