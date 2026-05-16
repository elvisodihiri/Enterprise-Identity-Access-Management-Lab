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

<img width="1858" height="944" alt="login" src="https://github.com/user-attachments/assets/63738c56-ca9f-47a6-9d98-3312e4d8ed7f" />


<br/>
<br/>
---

### Phase 2 — Administrative Units & Scoped Delegation
Built department based Administrative Units with dynamic membership rules. Delegated Helpdesk Admin, User Admin, and Authentication Admin roles scoped per-department so HR admins can only touch HR users. Configured a Restricted Management AU to protect exec accounts from even Global Admins.

<img width="1834" height="785" alt="AdminUnit" src="https://github.com/user-attachments/assets/612568f2-7c62-45f2-8987-fa756299db0f" />


<br/>
<br/>
<br/>

---

### Phase 3 — Advanced Group Management
Created Microsoft 365 Groups, dynamic security groups with complex attribute rules, group nesting (cloud AGDLP model), group-based licensing, and group writeback to on-prem AD.

<img width="1633" height="565" alt="DynamicGroups" src="https://github.com/user-attachments/assets/2ebe58b1-6841-4f0b-a7fd-e9b383eb4222" />
<img width="1630" height="617" alt="DynamicRules" src="https://github.com/user-attachments/assets/68166a2c-ab98-474f-a5f8-42aa30331ef9" />


<br/>
<br/>
---

### Phase 4 — RBAC & Custom Roles
Audited existing role assignments, designed a least-privilege RBAC model, created a custom Entra ID role (`NWD-ServiceDesk-UserEditor`) with specific permissions granted and blocked, and configured PIM-eligible role assignments.

<img width="990" height="593" alt="CustomRole" src="https://github.com/user-attachments/assets/8150e69c-778a-4e4c-b99d-d700c7155f38" />


<br/>
<br/>
---

### Phase 5 — Authentication & Passwordless
Configured Microsoft Authenticator with number matching (MFA fatigue prevention), SSPR with on-prem writeback, Temporary Access Pass for new hire onboarding, FIDO2 security key policy, and passwordless phone sign-in.

<img width="996" height="480" alt="Passwordreset" src="https://github.com/user-attachments/assets/61b9d731-b18c-4b42-9405-91a52113fd49" />


<br/>
<br/>
---

### Phase 6 — Conditional Access (Zero Trust)
Built a full CA policy stack: baseline MFA for all users, legacy auth block, location-based policies for Finance, compliant device requirements, risk-based MFA, high-risk user block, Terms of Use enforcement, and session controls. Used Report-Only mode and the What If tool before enabling each policy.

<img width="1620" height="839" alt="ConditionalPolicy" src="https://github.com/user-attachments/assets/d782ad93-4a88-4e75-ac96-7d3a3fdb5a47" />
<img width="822" height="897" alt="ConditionPolicy222" src="https://github.com/user-attachments/assets/66aa927b-f334-45b6-aa59-f73c65b5c373" />


<br/>
<br/>
---

### Phase 7 — Identity Protection
Configured risk-based policies, investigated risky sign-ins, remediated a simulated credential breach, set up real-time SOC notifications, and tested detection using Tor Browser to trigger anonymous IP risk signals.

<img width="1526" height="879" alt="RiskyUser" src="https://github.com/user-attachments/assets/3d111d6d-ff4c-48a5-ad19-a12f1ade2381" />
<img width="1462" height="474" alt="RiskySignin" src="https://github.com/user-attachments/assets/dda8fd7c-a7f8-42a7-8749-de3719fd73fa" />

<br/>
<br/>


---

### Phase 8 — Hybrid Identity
Installed and configured Azure AD Connect, enabled Password Hash Sync and Password Writeback, configured OU filtering to exclude servers and service account OUs, added attribute filtering to block personal data from syncing (GDPR), and verified Seamless SSO on domain-joined workstations.
<img width="977" height="544" alt="Connect Sync" src="https://github.com/user-attachments/assets/b2cae731-9692-48a9-9128-b7e434e8d200" />
<img width="1494" height="882" alt="ADConnectUsers" src="https://github.com/user-attachments/assets/6e7eef62-bce3-4a1a-ac27-39375830759a" />


<br/>
<br/>
---

### Phase 9 — Identity Governance
Built entitlement management catalogues and access packages with approval workflows. Configured quarterly access reviews with auto-apply. Built a Lifecycle Workflow to automate new hire onboarding (TAP generation, group assignment, welcome email) triggered by employeeHireDate.

<img width="1628" height="457" alt="Catalogue" src="https://github.com/user-attachments/assets/721c57da-aa9f-4580-ba88-dc849e3d45fa" />
<img width="1291" height="592" alt="AccessPackage" src="https://github.com/user-attachments/assets/fa4e049d-3935-4e35-9c1c-1383946992a7" />

<br/>
<br/>

---

### Phase 10 — B2B Guest Access
Configured external collaboration settings, invited B2B guests, set up cross-tenant access with MFA trust for a partner organisation, created an external-facing access package, and restricted guest directory enumeration permissions.
<img width="1349" height="905" alt="Crosstenant" src="https://github.com/user-attachments/assets/a37f12e1-1102-47e9-b267-b6daa3c52718" />

<br/>
<br/>


---

### Phase 11 — Enterprise Applications & SSO
Configured SAML 2.0 SSO, restricted app access to specific groups, set up SCIM automatic provisioning (Joiner/Mover/Leaver), created app roles (Finance.Viewer / Finance.Editor), and mapped roles as claims in the SAML token.
<img width="1634" height="565" alt="enterprise App" src="https://github.com/user-attachments/assets/2ee49e9e-d403-4fec-a3cf-1e83e996d838" />
<img width="1064" height="901" alt="Enterprise App2" src="https://github.com/user-attachments/assets/e4dae138-4833-44d2-bf70-95205e0b6cc6" />


<br/>
<br/>

---

### Phase 12 — Monitoring & Troubleshooting
Exported logs to Log Analytics, wrote KQL queries to detect sign-ins from outside the UK, MFA failures, stale accounts, and break-glass usage. Created alert rules for SOC notification and built an identity security workbook.


<br/>
<br/>

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

## Conclusion 

This project demonstrates hands-on, enterprise-level experience in Identity & Access Management, aligned with SC-300 certification objectives. 

It reflects the ability to: 

Design secure identity architectures 

Implement Zero Trust access controls 

Manage privileged access securely 

Maintain identity governance at scale 

Troubleshoot complex IAM issues 

---


