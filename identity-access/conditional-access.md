# Conditional Access Policy Design

## Overview
This document describes a structured Conditional Access (CA) approach within Microsoft 365 using Azure AD (Entra ID). Conditional Access enables risk-based access control by evaluating sign-in conditions and enforcing security requirements such as MFA and device compliance.

---

## Why Conditional Access Is Important
Static security controls are insufficient in modern cloud environments. Conditional Access allows organisations to respond dynamically to risk by enforcing additional controls when access attempts are considered high risk.

Conditional Access helps to:
- Prevent unauthorised access from risky locations
- Enforce MFA and device trust requirements
- Reduce reliance on passwords alone
- Improve security without unnecessarily impacting user experience

---

## Conditional Access Design Principles

### 1. Role-Based Policies
- Administrative roles are subject to stricter Conditional Access policies.
- Admin access requires MFA at all times, regardless of location or device.
- Break-glass accounts are excluded and protected with alternative controls.

---

### 2. Location-Based Access
- Sign-ins from trusted locations are treated differently from unknown or high-risk locations.
- Access attempts from unfamiliar or high-risk geographies require additional verification or are blocked.

---

### 3. Device Compliance
- Access to Microsoft 365 services is restricted to compliant or hybrid-joined devices where appropriate.
- Unmanaged or non-compliant devices are limited or blocked from accessing sensitive resources.

---

### 4. Application-Specific Policies
- Conditional Access policies are scoped to specific applications such as Exchange Online, SharePoint and Teams.
- Higher-risk applications require stronger access controls.

---

## Policy Management and Review
- Policies are documented, tested and reviewed regularly.
- Changes follow controlled change management processes to reduce the risk of disruption.
- Monitoring and sign-in logs are used to validate policy effectiveness.

---

## Alignment with Cyber Essentials
This Conditional Access approach supports Cyber Essentials by:
- Enforcing secure access to cloud services
- Reducing the risk of unauthorised access
- Supporting controlled and auditable access management

---

## Notes
All examples are based on lab environments and Microsoft-recommended best practices. No production data or credentials are included.
 

