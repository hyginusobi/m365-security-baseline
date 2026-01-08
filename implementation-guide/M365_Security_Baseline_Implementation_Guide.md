# Microsoft 365 Security Baseline – Step-by-Step Implementation Guide

## Purpose
This guide provides a repeatable approach to implementing a **baseline security configuration for Microsoft 365**, aligned with:
- Cyber Essentials principles
- NCSC CAF-style thinking (governance, protection, detection, response)
- Audit and assurance expectations in regulated environments

This is written as a **reference implementation / lab guide** and avoids tenant-specific or sensitive information.

---

## Prerequisites
Before starting, ensure you have:

- A Microsoft 365 tenant (Business Premium or E3/E5 recommended)
- A Global Administrator account (for initial setup only)
- A test standard user account
- At least one admin account (separate from daily-use accounts)
- Access to Microsoft Entra ID (Azure AD)
- Access to Microsoft Defender and Microsoft Purview portals

> **Operational note:** In production, apply least privilege and use privileged identity management (where available).

---

## Baseline Scope
This baseline covers:

1. Identity and access management
2. Multi-factor authentication (MFA)
3. Conditional Access
4. Email security (Defender for Office 365 concepts)
5. Endpoint protection (baseline-level assurance)
6. Audit logging and monitoring

---

# Step 1 – Identity and Access Baseline

## 1.1 Review and reduce admin roles
**Where:** Microsoft Entra admin center → **Roles & administrators**

**Actions**
- Identify all Global Administrators
- Reduce Global Admins to the minimum needed
- Allocate least-privileged roles where appropriate (e.g., Security Admin, Exchange Admin)

**Why this matters**
- Reduces the blast radius if an admin account is compromised
- Supports least privilege and separation of duties

**Evidence to capture**
- Redacted screenshot or export showing admin role assignments
- A short “Admin Roles Review” note describing changes and rationale

---

## 1.2 Create and protect break-glass accounts
**Goal:** Ensure emergency access without creating an unmanaged risk.

**Actions**
- Create 1–2 emergency access accounts (break-glass)
- Exclude break-glass accounts from Conditional Access policies
- Protect with compensating controls:
  - very strong passwords stored securely
  - restricted sign-in locations (where possible)
  - enhanced monitoring / alerting
- Document account purpose and ownership

**Why this matters**
- Prevents tenant lockout during Conditional Access or MFA issues
- Supports resilience and business continuity

**Evidence to capture**
- A redacted screenshot showing accounts exist (no identifiers)
- A short “Break-glass controls” note describing protections and monitoring approach

---

# Step 2 – Multi-Factor Authentication (MFA)

## 2.1 Configure authentication methods
**Where:** Microsoft Entra admin center → **Protection** → **Authentication methods**

**Actions**
- Enable preferred methods (e.g., Microsoft Authenticator, FIDO2 if available)
- Encourage strong MFA methods (avoid weak options where possible)
- Ensure users can register MFA securely

**Why this matters**
- Mitigates credential theft and password spray attacks
- Supports Cyber Essentials access control expectations

**Evidence to capture**
- Authentication methods configuration screenshot (redacted)
- A short note outlining enabled methods and rationale

---

## 2.2 Enforce MFA for administrators (minimum standard)
**Where:** Microsoft Entra admin center → **Conditional Access**

**Policy (example)**
- Users: directory roles / administrators
- Cloud apps: all cloud apps
- Grant: require MFA
- Session: sign-in frequency (optional)

**Why this matters**
- Admin accounts are high-value targets and require stronger controls

**Evidence to capture**
- Conditional Access policy screenshot (redacted)
- Policy name, scope, and grant controls summary

---

# Step 3 – Conditional Access (Core Policies)

## 3.1 Block legacy authentication
**Policy**
- Users: all users (exclude break-glass)
- Conditions: client apps → **legacy authentication**
- Access controls: **block access**

**Why this matters**
- Legacy auth can bypass MFA and is a common attack path

**Evidence to capture**
- Policy configuration screenshot (redacted)
- Testing notes (what you tested before enabling)

---

## 3.2 Require MFA for all users
**Policy**
- Users: all users (exclude break-glass)
- Cloud apps: all cloud apps
- Grant: require MFA

**Why this matters**
- Establishes a consistent identity protection baseline across users

**Evidence to capture**
- Policy configuration screenshot (redacted)
- User communication / rollout notes (if applicable)

---

## 3.3 Require compliant device (optional, if using Intune)
If your environment uses Intune:
- Require compliant device for access to key apps
- Use this to enforce posture-based access

**Why this matters**
- Strengthens protection by ensuring only compliant endpoints can access services

**Evidence to capture**
- Conditional Access policy (redacted)
- Compliance policy reference (link to Intune project if applicable)

---

# Step 4 – Email Security Baseline

> Availability depends on licensing. Document what you can implement in your tenant.

## 4.1 Configure anti-phishing and anti-spam protection
**Where:** Microsoft 365 Defender → Email & collaboration

**Actions**
- Review / configure anti-phishing policy
- Review / configure anti-spam policy
- Enable impersonation protection (where available)

**Why this matters**
- Email is a common initial access vector in healthcare and public sector

**Evidence to capture**
- Policy summaries (redacted)
- A short note describing protection goals and scope

---

## 4.2 Safe Links / Safe Attachments (where available)
**Actions**
- Enable Safe Links protection
- Enable Safe Attachments detonation (where available)
- Document settings and exceptions

**Why this matters**
- Helps reduce risk from malicious links and attachments

**Evidence to capture**
- Policy summaries (redacted)
- Testing notes (pilot group validation)

---

# Step 5 – Mail Flow Controls (Baseline)

## 5.1 External sender tagging
**Where:** Exchange admin center → Mail flow rules

**Actions**
- Apply a warning/tag to emails from external senders
- Document scope and exclusions

**Why this matters**
- Reduces phishing risk by providing user context

---

## 5.2 Block risky attachments (baseline control)
**Actions**
- Block or quarantine executable attachments based on policy
- Document allowed exceptions (if any)

**Why this matters**
- Reduces malware delivery risk through email

**Evidence to capture**
- Mail flow rule summaries (redacted)
- A short change note outlining the rule purpose

---

# Step 6 – Endpoint Security (Baseline Assurance)

> Detailed endpoint configuration lives in the Intune project. This section focuses on baseline assurance.

**Actions**
- Confirm Microsoft Defender Antivirus is enabled on endpoints
- Confirm real-time protection and cloud-delivered protection are enabled
- Confirm tamper protection (where available)

**Why this matters**
- Supports the malware protection expectation in Cyber Essentials

**Evidence to capture**
- A redacted screenshot showing Defender protection status
- A short note describing baseline endpoint protection posture

---

# Step 7 – Audit Logging and Monitoring

## 7.1 Enable and verify unified audit logging
**Where:** Microsoft Purview → Audit

**Actions**
- Confirm audit logging is enabled
- Confirm retention settings (based on licensing)
- Document what is retained and for how long

**Why this matters**
- Supports investigations, accountability, and assurance activities

**Evidence to capture**
- Confirmation of audit logging enabled (redacted)
- A short “Audit logging verification” note

---

## 7.2 Review sign-in and audit logs
**Actions**
- Review Entra sign-in logs for risky patterns
- Review audit logs for key admin actions
- Document the process and escalation path

**Why this matters**
- Enables detection and supports incident response readiness

**Evidence to capture**
- Redacted example log review
- A short note describing how logs are reviewed and when issues are escalated

---

# Validation Checklist (Baseline Complete)
Use this to confirm baseline completion:

- [ ] Admin roles reviewed and reduced where appropriate
- [ ] Break-glass accounts created, excluded, and monitored
- [ ] MFA configured and enforced (admins at minimum, ideally all users)
- [ ] Legacy authentication blocked
- [ ] Conditional Access baseline policies enabled
- [ ] Email protection policies configured (where licensing allows)
- [ ] Mail flow rules in place for basic controls
- [ ] Endpoint protection verified at baseline level
- [ ] Audit logging enabled and verified
- [ ] Evidence captured safely and documented

---

# Common Mistakes
- Enforcing MFA without break-glass accounts
- Blocking legacy auth without testing impacts
- Too many Global Admins
- Implementing policies without documentation and evidence capture
- No validation checklist or review process

---

# How to Use This in a Portfolio
This guide demonstrates:
- Implementation thinking
- Audit readiness and evidence handling
- CAF-aligned structure (governance, protection, detection, response)
- Practical operational awareness (validation, common mistakes, escalation)

For the overall portfolio, see: https://github.com/hyginusobi
