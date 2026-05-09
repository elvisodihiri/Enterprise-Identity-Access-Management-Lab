# 🔐 Enterprise Identity & Access Management Lab
### Microsoft Entra ID + Hybrid Active Directory | SC-300 Aligned

---

## What I Built

I built a full enterprise IAM environment from scratch for a fictional organisation, **Northwind Data Systems**  covering everything from on-premises Active Directory through to cloud identity, Zero Trust, and identity governance.

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

<img width="600" height="600" alt="northwind-iam-architecture" src="https://github.com/user-attachments/assets/09ef3452-09bd-45d8-bad7-3a48e75f3ab0" />
<br/>
<br/>

## What I Covered (12 Phases)

### Phase 1 — Tenant Foundation
Custom domain, DNS verification, company branding, break-glass accounts, password protection policies.


<img width="800" height="600" alt="login" src="https://github.com/user-attachments/assets/5aaa1db3-a466-4a14-b2b0-8833021df54c" />
<br/>
<br/>
---

### Phase 2 — Administrative Units & Scoped Delegation
Built department based Administrative Units with dynamic membership rules. Delegated Helpdesk Admin, User Admin, and Authentication Admin roles scoped per-department so HR admins can only touch HR users. Configured a Restricted Management AU to protect exec accounts from even Global Admins.


<img width="1000" height="600" alt="AdminUnit" src="https://github.com/user-attachments/assets/e2271fdc-23a5-4b47-afae-6cfdeccb0d38" />
<br/>
<br/>
<br/>

---

### Phase 3 — Advanced Group Management
Created Microsoft 365 Groups, dynamic security groups with complex attribute rules, group nesting (cloud AGDLP model), group-based licensing, and group writeback to on-prem AD.


<img width="1000" height="500" alt="DynamicGroups" src="https://github.com/user-attachments/assets/e44f6e75-0ff5-4c16-8970-b657c3e4472d" />
<img width="1000" height="600" alt="DynamicRules" src="https://github.com/user-attachments/assets/6014fe94-5660-4c06-b1b9-5ecb540e16c8" />
<br/>
<br/>
---

### Phase 4 — RBAC & Custom Roles
Audited existing role assignments, designed a least-privilege RBAC model, created a custom Entra ID role (`NWD-ServiceDesk-UserEditor`) with specific permissions granted and blocked, and configured PIM-eligible role assignments.
<img width="900" height="550" alt="CustomRole" src="https://github.com/user-attachments/assets/90d8b3a4-c256-4c59-aeef-15559e358a0a" />

<br/>
<br/>
---

### Phase 5 — Authentication & Passwordless
Configured Microsoft Authenticator with number matching (MFA fatigue prevention), SSPR with on-prem writeback, Temporary Access Pass for new hire onboarding, FIDO2 security key policy, and passwordless phone sign-in.

> **SCREENSHOT:** Authentication Methods policy showing Authenticator enabled with number matching turned on — and the SSPR configuration page showing methods enabled
<img width="900" height="480" alt="Passwordreset" src="https://github.com/user-attachments/assets/1e5e3d06-9d1c-4c9b-b89e-ff4f39050b3e" />
<br/>
<br/>
---

### Phase 6 — Conditional Access (Zero Trust)
Built a full CA policy stack: baseline MFA for all users, legacy auth block, location-based policies for Finance, compliant device requirements, risk-based MFA, high-risk user block, Terms of Use enforcement, and session controls. Used Report-Only mode and the What If tool before enabling each policy.


<img width="1020" height="800" alt="ConditionalPolicy" src="https://github.com/user-attachments/assets/0cdd01c6-3edc-4e9d-a836-e4e0da7a0ba9" />
<img width="822" height="850" alt="ConditionPolicy222" src="https://github.com/user-attachments/assets/810ba579-6c0b-4c3c-8bda-b5cde924ec70" />

<br/>
<br/>
---

### Phase 7 — Identity Protection
Configured risk-based policies, investigated risky sign-ins, remediated a simulated credential breach, set up real-time SOC notifications, and tested detection using Tor Browser to trigger anonymous IP risk signals.
<img width="1026" height="800" alt="RiskyUser" src="https://github.com/user-attachments/assets/a419ae3e-5af5-4ad5-8757-44ec0448192a" />
<img width="1062" height="474" alt="RiskySignin" src="https://github.com/user-attachments/assets/6351d30d-3146-45d5-874d-53f75af50e97" />

<br/>
<br/>


---

### Phase 8 — Hybrid Identity
Installed and configured Azure AD Connect, enabled Password Hash Sync and Password Writeback, configured OU filtering to exclude servers and service account OUs, added attribute filtering to block personal data from syncing (GDPR), and verified Seamless SSO on domain-joined workstations.

> **SCREENSHOT:** Azure AD Connect sync status page showing last sync time + Entra Users page filtered to "On-premises sync enabled: Yes" showing synced users

---

### Phase 9 — Identity Governance
Built entitlement management catalogues and access packages with approval workflows. Configured quarterly access reviews with auto-apply. Built a Lifecycle Workflow to automate new hire onboarding (TAP generation, group assignment, welcome email) triggered by employeeHireDate.
<img width="1028" height="457" alt="Catalogue" src="https://github.com/user-attachments/assets/a28b4c82-2836-4f01-a781-38cb024ebe23" />
<img width="1000" height="502" alt="AccessPackage" src="https://github.com/user-attachments/assets/da6f6034-d691-482c-baaf-242314663eb6" />

<br/>
<br/>

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


