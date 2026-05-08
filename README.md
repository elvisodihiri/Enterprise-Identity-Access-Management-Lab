# 🔐 Enterprise Identity & Access Management Lab
### Microsoft Entra ID + Hybrid Active Directory | SC-300 Aligned

---

## What I Built

I built a full enterprise IAM environment from scratch for a fictional organisation, **Northwind Data Systems** — covering everything from on-premises Active Directory through to cloud identity, Zero Trust, and identity governance.

This wasn't a guided click-through. I worked through 110 structured tasks across 12 phases, troubleshot real sync errors, misconfigured CA policies, and broke things (then fixed them). The goal was to build the kind of hands-on depth that doesn't show up in a cert alone.

---

## Lab Environment

| Component | Detail |
|---|---|
| Tenant | northwinddata.onmicrosoft.com |
| On-Prem Domain | northwind.local (DC1, DC2 Windows Server 2022) |
| Users | 40–50 hybrid and cloud-only users |
| Licence Tier | Microsoft Entra ID P2 |
| Clients | Windows 10/11 |
| Sync Tool | Azure AD Connect (Entra Connect) |

---

## 📸 Architecture Overview

> **SCREENSHOT TO ADD:** Full architecture diagram showing DC1 → Entra Connect → Entra ID tenant, with the 12 phases labelled. Draw this in draw.io or just use a clean screenshot of your Entra portal Overview page showing your tenant, synced users, and Connect health status.

---

## What I Covered (12 Phases)

### Phase 1 — Tenant Foundation
Custom domain, DNS verification, company branding, break-glass accounts, password protection policies.

> **SCREENSHOT:** Entra portal showing verified custom domain (northwinddata.com) + company branding on the sign-in page (open a private browser window to capture it)

---

### Phase 2 — Administrative Units & Scoped Delegation
Built department-based Administrative Units with dynamic membership rules. Delegated Helpdesk Admin, User Admin, and Authentication Admin roles scoped per-department — so HR admins can only touch HR users. Configured a Restricted Management AU to protect exec accounts from even Global Admins.

> **SCREENSHOT:** IT-AdminUnit showing dynamic membership rule `(user.department -eq "IT")` and the populated members list

---

### Phase 3 — Advanced Group Management
Created Microsoft 365 Groups, dynamic security groups with complex attribute rules, group nesting (cloud AGDLP model), group-based licensing, and group writeback to on-prem AD.

> **SCREENSHOT:** Dynamic group rule editor for one of the complex rules (e.g., DYN-SeniorLeadership using jobTitle contains "Manager" or "VP")

---

### Phase 4 — RBAC & Custom Roles
Audited existing role assignments, designed a least-privilege RBAC model, created a custom Entra ID role (`NWD-ServiceDesk-UserEditor`) with specific permissions granted and blocked, and configured PIM-eligible role assignments.

> **SCREENSHOT:** Custom role permissions page showing the specific permissions added (basic/read, standard/read, basic/update) with password reset explicitly absent

---

### Phase 5 — Authentication & Passwordless
Configured Microsoft Authenticator with number matching (MFA fatigue prevention), SSPR with on-prem writeback, Temporary Access Pass for new hire onboarding, FIDO2 security key policy, and passwordless phone sign-in.

> **SCREENSHOT:** Authentication Methods policy showing Authenticator enabled with number matching turned on — and the SSPR configuration page showing methods enabled

---

### Phase 6 — Conditional Access (Zero Trust)
Built a full CA policy stack: baseline MFA for all users, legacy auth block, location-based policies for Finance, compliant device requirements, risk-based MFA, high-risk user block, Terms of Use enforcement, and session controls. Used Report-Only mode and the What If tool before enabling each policy.

> **SCREENSHOT:** CA policy list showing all policies (CA001–CA010) with their enabled/report-only status — and one policy open showing the full configuration (e.g., CA001 with MFA grant and break-glass exclusions)

---

### Phase 7 — Identity Protection
Configured risk-based policies, investigated risky sign-ins, remediated a simulated credential breach, set up real-time SOC notifications, and tested detection using Tor Browser to trigger anonymous IP risk signals.

> **SCREENSHOT:** Identity Protection dashboard showing Risky users and/or Risky sign-ins — ideally with at least one test detection visible

---

### Phase 8 — Hybrid Identity
Installed and configured Azure AD Connect, enabled Password Hash Sync and Password Writeback, configured OU filtering to exclude servers and service account OUs, added attribute filtering to block personal data from syncing (GDPR), and verified Seamless SSO on domain-joined workstations.

> **SCREENSHOT:** Azure AD Connect sync status page showing last sync time + Entra Users page filtered to "On-premises sync enabled: Yes" showing synced users

---

### Phase 9 — Identity Governance
Built entitlement management catalogues and access packages with approval workflows. Configured quarterly access reviews with auto-apply. Built a Lifecycle Workflow to automate new hire onboarding (TAP generation, group assignment, welcome email) triggered by employeeHireDate.

> **SCREENSHOT:** Access package request flow — either the My Access portal showing the Finance-NewEmployee-Access package, or the access package assignments view showing a delivered assignment

---

### Phase 10 — B2B Guest Access
Configured external collaboration settings, invited B2B guests, set up cross-tenant access with MFA trust for a partner organisation, created an external-facing access package, and restricted guest directory enumeration permissions.

> **SCREENSHOT:** Cross-tenant access settings page showing inbound trust settings (MFA trust, compliant device trust) for a partner org

---

### Phase 11 — Enterprise Applications & SSO
Configured SAML 2.0 SSO, restricted app access to specific groups, set up SCIM automatic provisioning (Joiner/Mover/Leaver), created app roles (Finance.Viewer / Finance.Editor), and mapped roles as claims in the SAML token.

> **SCREENSHOT:** Enterprise app SSO configuration page showing SAML setup (Entity ID, ACS URL, certificate) — and the Provisioning logs showing successful user creation

---

### Phase 12 — Monitoring & Troubleshooting
Exported logs to Log Analytics, wrote KQL queries to detect sign-ins from outside the UK, MFA failures, stale accounts, and break-glass usage. Created alert rules for SOC notification and built an identity security workbook.

> **SCREENSHOT:** Log Analytics showing one of the KQL queries running with results — ideally the break-glass detection query or the sign-in anomaly query

---

## Troubleshooting Scenarios Worked Through

Real issues I diagnosed and resolved during the lab:

- User not appearing in Administrative Unit despite matching department attribute (attribute sync delay + smart quote corruption in dynamic rule)
- Dynamic group not updating after on-prem department change (forced delta sync, re-saved rule to trigger reprocessing)
- PIM role activation failing due to no MFA registered (issued TAP to bootstrap Authenticator setup)
- SSPR not completing for a user (group membership gap — traced through audit logs)
- CA policy locking out all users (recovered using break-glass account, used What If to diagnose the logic error)
- Sync export error due to duplicate proxyAddresses attribute (resolved with IdFix and PowerShell)

---

## Key Skills Demonstrated

`Microsoft Entra ID` · `Active Directory` · `Hybrid Identity` · `Azure AD Connect` · `Conditional Access` · `Zero Trust` · `PIM` · `RBAC` · `Identity Governance` · `SSPR` · `MFA` · `FIDO2` · `SAML SSO` · `SCIM Provisioning` · `KQL` · `Log Analytics` · `SC-300`

---

## Certification Alignment

This lab covers every major domain of the **SC-300: Microsoft Identity and Access Administrator** exam at mid-to-advanced level.

---


