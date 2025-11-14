<p align="center">
  <img src="screenshots/zt_banner.png" alt="Project 4 — Conditional Access Zero Trust Banner" width="100%">
</p>

# 🛡️ Project 4 — Entra ID (Azure AD) Conditional Access Zero Trust
_Identity Perimeter • Least Privilege • Modern Access Control_

![Entra ID](https://img.shields.io/badge/Microsoft_Entra_ID-IAM-blue?style=flat-square)
![Zero Trust](https://img.shields.io/badge/Zero_Trust-Conditional_Access-blue?style=flat-square)
![MFA](https://img.shields.io/badge/MFA-Required-blue?style=flat-square)
![Location Based](https://img.shields.io/badge/Location_Control-US_Only-blue?style=flat-square)
![Legacy Auth](https://img.shields.io/badge/Legacy_Auth-Blocked-red?style=flat-square)

---

<details open>
  <summary><h2>📚 Table of Contents</h2></summary>

- [Objective](#objective)
- [Zero Trust Architecture](#zero-trust-architecture)
- [Zero Trust Governance Groups](#zero-trust-governance-groups)
- [Named Location — United States](#named-location--united-states)
- [Policy 01 — Require MFA for All Users](#policy-01--require-mfa-for-all-users)
- [Policy 02 — Block Sign-ins From Outside the United-States](#policy-02--block-sign-ins-from-outside-the-united-states)
- [Policy 03 — Block Legacy Authentication](#policy-03--block-legacy-authentication)
- [Evidence & Screenshots](#evidence--screenshots-audit-artifacts)
- [Repo Structure](#repo-structure)

</details>

---

<details open>
 <summary><h2 id="objective">🎯 Objective</h2></summary>

This project demonstrates a **Zero Trust Conditional Access architecture** in Microsoft Entra ID.

Implemented controls:

- 🔐 **Require MFA for all users** (baseline identity hardening)  
- 🌎 **Block sign-ins from outside the United States** (location risk reduction)  
- 🛑 **Block legacy authentication protocols** (POP/IMAP/SMTP/ActiveSync)  
- 🧩 **Zero Trust governance groups** (Admins, AllUsers, BreakGlass, TrustedLocations)  
- 🗺️ **Trusted Named Location — United States**

This Zero Trust implementation aligns with Microsoft’s recommended baseline for modern identity security in cloud environments.

</details>

---

<details open>
  <summary><h2 id="zero-trust-architecture">🏗️ Zero Trust Architecture</h2></summary>

Zero Trust in Entra ID follows three fundamental principles:

### 🔹 **1. Verify Explicitly**
Authentication strength and device posture are validated for every session.

### 🔹 **2. Use Least Privilege**
Access is restricted by identity type, device state, location, and admin tiering.

### 🔹 **3. Assume Breach**
Deny access when risk is detected, legacy protocols are used, or geographic anomalies appear.

---

### ⚡ Architecture Summary
This project enforces:

- MFA → identity verification  
- Device posture → compliant device for admins  
- Geography → US-only sign-ins  
- Protocol hardening → legacy auth blocked  
- BreakGlass account → compliant escape hatch  

</details>

---

<details open>
  <summary><h2 id="zero-trust-governance-groups">👥 Zero Trust Governance Groups</h2></summary>

To support a clean and scalable architecture, four governance groups were created.

---

### **GG-ZT-Admins**  
Used to apply stricter policies to administrative identities.  
![ZT Admin Group Created](screenshots/zt-group-admins-created.png)  
![ZT Admin Group Members](screenshots/zt-group-admins-members.png)

---

### **GG-ZT-AllUsers**  
A broad group representing the standard user population.  
![ZT AllUsers Group Created](screenshots/zt-group-allusers-created.png)  
![ZT AllUsers Group Members](screenshots/zt-group-allusers-members.png)

---

### **GG-ZT-BreakGlass**  
Critical exclusion account for emergencies.  
![ZT BreakGlass Group Created](screenshots/zt-group-breakglass-created.png)  
![ZT BreakGlass Group Members](screenshots/zt-group-breakglass-members.png)

---

### **GG-ZT-TrustedLocations**  
Supports Named Location governance.  
![ZT TrustedLocations Group](screenshots/zt-group-trustedlocations-created.png)

</details>

---

<details open>
  <summary><h2 id="named-location--united-states">🗺️ Named Location — United States</h2></summary>

The **United States** was created as a **trusted location** to enforce geo-based access controls.

![Named Location — United States](screenshots/named-location-united-states.png)

</details>

---

<details open>
  <summary><h2 id="policy-01--require-mfa-for-all-users">🔐 Policy 01 — Require MFA for All Users</h2></summary>

### **Policy Name:**  
`CA-ZT-RequireMFA-AllUsers`

---

### ✅ **Assignments**
Targeted all users while excluding the BreakGlass account.

![Policy 01 Assignments](screenshots/CA-Policy01-Assignments.png)

---

### ✅ **Conditions**
No additional conditions required; applies universally.

![Policy 01 Conditions](screenshots/CA-Policy01-Conditions.png)

---

### ✅ **Grant Controls**
- **Require MFA**

![Policy 01 Grant](screenshots/CA-Policy01-Grant.png)

---

### 🎉 **Final Overview**
![Policy 01 Overview](screenshots/CA-Policy01-Overview.png)

</details>

---

<details open>
  <summary><h2 id="policy-02--block-sign-ins-from-outside-the-united-states">🌎 Policy 02 — Block Sign-ins From Outside the United States</h2></summary>

### **Policy Name:**  
`CA-ZT-Block-NonUS`

---

### ✅ **Assignments**
Applies to all users except BreakGlass.

![Policy 02 Assignments](screenshots/CA-Policy02-Assignments.png)

---

### ✅ **Conditions**
Sign-ins from **outside the U.S.** are included and blocked.

![Policy 02 Location Condition](screenshots/CA-Policy02-Conditions-Locations.png)

---

### ✅ **Grant Controls**
- **Block Access**

![Policy 02 Grant](screenshots/CA-Policy02-Grant.png)

---

### 🎉 **Final Overview**
![Policy 02 Overview](screenshots/CA-Policy02-Overview.png)

</details>

---

<details open>
  <summary><h2 id="policy-03--block-legacy-authentication">🛑 Policy 03 — Block Legacy Authentication</h2></summary>

### **Policy Name:**  
`CA-ZT-Block-Legacy`

Legacy protocols bypass MFA and modern token protections. This policy blocks:

- IMAP  
- POP  
- SMTP auth  
- ActiveSync  
- MAPI  
- Older Office clients  

---

### ✅ **Assignments**
Targeted all users except BreakGlass.

![Policy 03 Assignments](screenshots/CA-Policy03-Assignments.png)

---

### ✅ **Conditions**
Client apps restricted to legacy authentication.

![Policy 03 Client Apps Condition](screenshots/CA-Policy03-Conditions-ClientApps.png)

---

### ✅ **Grant Controls**
- **Block Access**

![Policy 03 Grant](screenshots/CA-Policy03-Grant.png)

---

### 🎉 **Final Overview**
![Policy 03 Overview](screenshots/CA-Policy03-Overview.png)

</details>

---

<details>
  <summary><h2 id="evidence--screenshots-audit-artifacts">🧪 Evidence & Screenshots (Audit Artifacts)</h2></summary>

### 📄 Conditional Access Overview  
![Conditional Access List](screenshots/conditional-access-policy-list.png)

### 🧩 Zero Trust Group Snapshots  
(See Governance Groups section above)

### 🌎 Named Location  
![United States Location](screenshots/named-location-united-states.png)

</details>

---

<details>
  <summary><h2 id="repo-structure">📂 Repo Structure</h2></summary>

```text
project-4-entra-id-conditional-access-zero-trust/
│ README.md
└── screenshots/
    ├─ zt_banner.png
    ├─ zt-group-admins-created.png
    ├─ zt-group-admins-members.png
    ├─ zt-group-allusers-created.png
    ├─ zt-group-allusers-members.png
    ├─ zt-group-breakglass-created.png
    ├─ zt-group-breakglass-members.png
    ├─ zt-group-trustedlocations-created.png
    ├─ named-location-united-states.png
    ├─ CA-Policy01-Assignments.png
    ├─ CA-Policy01-Conditions.png
    ├─ CA-Policy01-Grant.png
    ├─ CA-Policy01-Overview.png
    ├─ CA-Policy02-Assignments.png
    ├─ CA-Policy02-Conditions-locations.png
    ├─ CA-Policy02-Grant.png
    ├─ CA-Policy02-Overview.png
    ├─ CA-Policy03-Assignments.png
    ├─ CA-Policy03-Conditions-clientapps.png
    ├─ CA-Policy03-Grant.png
    ├─ CA-Policy03-Overview.png
    └─ conditional-Access-Policy-List.png
```

</details>
