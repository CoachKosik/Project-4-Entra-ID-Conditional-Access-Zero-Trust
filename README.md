<p align="center">
  <img src="screenshots/conditional_access_banner.png" width="100%">
</p>

<h1 align="center">🛑 Project 4 — Entra ID Zero Trust Conditional Access</h1>
<h3 align="center">Risk-Based MFA ▸ Geo Blocking ▸ Governance-Based Enforcement</h3>

---

## 🟦 Why This Project Matters to IAM Hiring Managers

Conditional Access is **the #1 control used in modern identity security**, and most candidates only show the MFA basics.

This project demonstrates **enterprise-grade Zero Trust enforcement**, including:

- 🔐 Risk-based authentication requirements  
- 🌍 Country geo-blocking aligned with least privilege principles  
- 🚫 Blocking legacy protocols that bypass MFA  
- 🧪 Test validation using multiple user identities  
- 🧾 Full screenshot evidence for audit requirements

These are the skills used daily by:

🟦 IAM Analysts  
🟦 Identity Governance Engineers  
🟦 Azure Security & Entra ID Administrators  
🟦 SOC / SecOps IAM Support Teams

---

## 📌 Overview

This lab enforces **Microsoft Zero Trust Conditional Access standards**, including:

✔ Require MFA for all users  
✔ Block legacy authentication  
✔ Block sign-ins from non-allowed locations  
✔ Use group-based scope instead of assigning policies directly to users  
✔ Capture validation screenshots for hiring manager proof

This is **Project 4 of 4** in my Enterprise IAM portfolio series.

---

## 📚 Table of Contents

- [Objectives](#-objectives)
- [Zero Trust Standards](#-zero-trust-standards)
- [Conditional Access Policies](#-conditional-access-policies)
- [Risk & Geo Logic](#-risk--geo-logic)
- [Legacy Auth Blocking](#-legacy-auth-blocking)
- [Validation Evidence](#-validation-evidence)
- [What I Learned](#-what-i-learned)
- [Next Steps](#-next-steps)
- [Repo Structure](#-repo-structure)

---

## 🎯 Objectives

| Goal | Outcome |
|------|---------|
| Enforce MFA on every signin | Zero Trust authentication |
| Block high-risk login patterns | Mitigate account compromise |
| Restrict logins by geography | Prevent foreign credential abuse |
| Remove legacy auth | Prevent password-only entry |
| Produce audit-ready evidence | Hiring manager validation |

---

## 🔐 Zero Trust Standards

> **Verify explicitly ▸ Use least privilege ▸ Assume breach**

This project maps to official Microsoft Zero Trust guidance:

- Conditional Access required for all identities  
- Legacy authentication blocked  
- No broad “All Cloud Apps – All Users” allow rules  
- MFA enforcement independent from user enrollment status

---

## 🛡 Conditional Access Policies

<details>
<summary><strong>01 — Require MFA for All Users</strong></summary>

- Assignment → All users  
- Cloud Apps → All  
- Grant → Require MFA  
- Status → On

📸 Screenshot  
![MFA Policy Overview](screenshots/CA-Policy01-Overview.png)

</details>

<details>
<summary><strong>02 — Block Legacy Authentication</strong></summary>

- Blocks POP, IMAP, SMTP, ActiveSync
- Removes password-only sign-in paths

📸 Screenshot  
![Legacy Policy Block](screenshots/CA-Policy03-Grant.png)

</details>

<details>
<summary><strong>03 — Block Non-US Sign-ins</strong></summary>

- Includes → All users  
- Excludes → Break-glass account  
- Locations → Block all except United States  
- Grant → Block

📸 Screenshot (example placeholder)  
`![Geo Block Policy](screenshots/geo-block-policy.png)`

</details>

---

## 🧠 Risk & Geo Logic

| Signal | Action |
|--------|--------|
| Unknown country | Block |
| High-risk sign-in | Require MFA |
| Offline legacy protocol | Block |
| Trusted device | MFA still required |

---

## 🚫 Legacy Authentication Blocking

✔ SMTP  
✔ POP  
✔ IMAP  
✔ ActiveSync  
✔ Basic auth token replay

📌 **99% of cloud account compromises occur WITHOUT MFA.**  
This policy neutralizes that threat.

---

## 🧪 Validation Evidence

<details>
<summary><strong>📋 Test Users & Results</strong></summary>

| User | Country | Result |
|------|---------|--------|
| Maverick Blaze | USA | Allowed w/ MFA prompt |
| Eddie Spark | USA | Allowed w/ MFA prompt |
| Sierra Nova | Germany | BLOCKED |
| Mara Flux | Legacy Protocol | BLOCKED |

</details>

<details>
<summary><strong>📸 Enforcement Screenshot Samples</strong></summary>

![MFA Prompt](screenshots/mfa-authentication-prompt.png)  
![More Info Required](screenshots/mfa-more-information-required.png)  
![Authenticator Registered](screenshots/mfa-authenticator-enabled.png)

</details>

---

## 🧠 What I Learned

✔ Conditional Access is the enforcement engine behind Zero Trust  
✔ Legacy auth must be disabled explicitly — it is NOT auto-blocked  
✔ MFA enforcement must NOT depend on user self-enrollment  
✔ Geo and risk-based rules MUST include break-glass exclusions  
✔ IAM portfolios **must contain evidence**, not claims

---

## 🚀 Next Steps

This completes a **4-part IAM portfolio series**:

| Project | Focus |
|---------|-------|
| 1️⃣ Entra Identity Basics | Users ▸ Groups ▸ RBAC |
| 2️⃣ MFA Enforcement | Baseline Zero Trust MFA |
| 3️⃣ Identity Lifecycle (JML) | Joiner ▸ Mover ▸ Leaver |
| 4️⃣ Conditional Access | Full Zero Trust Guardrails |

🔗 See all repos at: **https://github.com/CoachKosik**

---

## 📂 Repo Structure

```text
Project-4-Entra-ID-Conditional-Access/
│ README.md
└── screenshots/
   ├─ conditional_access_banner.png
   ├─ CA-Policy01-Overview.png
   ├─ CA-Policy03-Grant.png
   ├─ geo-block-policy.png     (rename yours if different)
   ├─ mfa-authentication-prompt.png
   ├─ mfa-more-information-required.png
   ├─ mfa-authenticator-enabled.png
```

---

⭐ If this project helped you, STAR the repo
👀 Recruiters DO click your GitHub activity
🧑‍💻 Connect with me on LinkedIn → linkedin.com/in/justin-kosik
