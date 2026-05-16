# 🧪 Manual Testing Portfolio

![Testing](https://img.shields.io/badge/Testing-Manual-blue)
![Type](https://img.shields.io/badge/Type-Security%20%26%20Functional-red)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Bugs Found](https://img.shields.io/badge/Bugs%20Found-5-critical)
![Apps Tested](https://img.shields.io/badge/Apps%20Tested-4-informational)

A structured portfolio of bugs discovered through manual exploratory testing across multiple web applications — covering security vulnerabilities, business logic flaws, and functional/UI issues.

> **All testing was performed on authorized or intentionally vulnerable applications for educational and portfolio purposes only.**

---

## 👨‍💻 About Me

Manual Software Tester with hands-on experience in functional testing, exploratory testing, input validation, and basic security testing. This repository documents real bugs I identified, analyzed, and reported across multiple applications.

---

## 📊 Summary

| Metric | Count |
|--------|-------|
| Applications Tested | 4 |
| Total Bugs Found | 6 |
| Security / Business Logic Bugs | 3 |
| Functional / UI Bugs | 3 |
| Critical / High Severity | 3 |
| Medium Severity | 3 |

---

## 🧪 Applications Tested

| Application | Type | Testing Focus |
|-------------|------|---------------|
| [VulnBank](https://github.com/Commando-X/vuln-bank) | Intentionally Vulnerable Banking App | Security & Business Logic |
| [Mifos X Web App](https://mifos.org/) | Open Source Finance App | UI & Functional |
| [WordPress Playground](https://playground.wordpress.net/) | Sandbox CMS Environment | Functional & Workflow |
| https://app.plane.so/ | Web Application (SaaS)| UI & Functional|


---

## 📁 Repository Structure

```
Manual-Testing-Portfolio/
├── README.md                          # This file — full summary
├── security-testing/
│   └── vulnbank_bugs.md               # Security & business logic bugs
├── functional-testing/
│   ├── mifos_bugs.md                  # UI bug — Mifos X
│   ├── wordpress_bugs.md              # Workflow bug — WordPress
│   └── plane_bugs.md                  # UI & workflow bugs — Plane.so
└── evidence/
    └── *.mp4 / *.png                  # Screenshots and recordings
```

---

## 🔐 Security Testing — VulnBank

> Business logic and input validation vulnerabilities found in an intentionally vulnerable banking application.

---

### 🔴 BUG-001 — Payment Process Bypasses Virtual Card Requirement

| Field | Details |
|-------|---------|
| Severity | Critical |
| Type | Business Logic Flaw |
| Module | Bill Payment |
| Impact | Unauthorized or invalid transactions possible |

The bill payment flow allows users to complete payments without possessing a valid virtual card, bypassing a core financial security control.

👉 [View Full Issue Report](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/1)

---

### 🔴 BUG-002 — Improper Validation of Recipient Account in Fund Transfer

| Field | Details |
|-------|---------|
| Severity | High |
| Type | Input Validation / Business Logic |
| Module | Fund Transfer |
| Impact | Transaction integrity compromised |

The fund transfer module accepts invalid or non-existent recipient account details without any validation, allowing transactions to proceed to incorrect destinations.

👉 [View Full Issue Report](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/2)

---

### 🔴 BUG-003 — Negative Loan Amount Accepted Due to Missing Input Validation

| Field | Details |
|-------|---------|
| Severity | High |
| Type | Input Validation |
| Module | Loan Application |
| Impact | Financial and logical inconsistency |

The loan amount input field accepts negative values with no server-side or client-side validation, creating a logical flaw that could be exploited to manipulate financial calculations.

👉 [View Full Issue Report](https://github.com/Commando-X/vuln-bank/issues/35)

---

## 🖥️ Functional & UI Testing

---

### 📁 Mifos X Web App

### 🟡 BUG-004 — Username Text Overlaps Account Icon on Login Page

| Field | Details |
|-------|---------|
| Severity | Medium |
| Type | UI Bug |
| Module | Login Page |
| Impact | Readability and user experience degraded |

When a long username is entered in the login page input field, the text overlaps with the account icon inside the input box, making the field difficult to read and visually broken.

👉 [View Evidence](https://gist.github.com/merajalamwork-hue/e1227b081556d61e8ca52bee4fa9912f)

---

### 📁 WordPress Playground

### 🟠 BUG-005 — 404 Error After Creating New User in Admin Panel

| Field | Details |
|-------|---------|
| Severity | Medium |
| Type | Functional / Workflow Bug |
| Module | Admin Panel → User Management |
| Impact | Core admin functionality broken |

**Steps to Reproduce:**
1. Open WordPress Playground
2. Navigate to **Users → Add New**
3. Enter a valid username and email address
4. Click **"Create New User"**
5. Observe the redirect

**Expected:** User is created and system redirects to user list or confirmation page

**Actual:** Application redirects to a **404 Page Not Found** screen, breaking the entire workflow with no success or failure feedback

👉 Evidence: https://github.com/user-attachments/assets/f685cf31-d0a3-443a-87e1-6fad8016788f

### 🌐 Plane.so

### 🟡 BUG-006 — "+ Add Quick Link" Text Overlaps Plane AI Text on Mobile Browser

| Field | Details |
|-------|---------|
| Severity | Medium |
| Type | UI / Layout Bug |
| Module | Home Page → Quicklinks & Plane AI Section |
| Impact | Visual confusion for all mobile users on first screen after login |

**Steps to Reproduce:**
1. Open Chrome browser on a mobile device
2. Navigate to https://app.plane.so
3. Sign in with your account
4. Observe the Home page immediately after login
5. Look at the area between the **Plane AI** section and the **Quicklinks** section

**Expected:** "+ Add Quick Link" button and Plane AI text render in clearly separated sections

**Actual:** The two UI elements visually overlap on mobile viewport, merging text from different sections

| Mode | Behaviour |
|------|-----------|
| Desktop browser | ✅ No overlap — layout renders correctly |
| Mobile Chrome | ❌ Overlap occurs — sections bleed into each other |

**Environment:** Samsung Galaxy A22 4G · Android 13 · Chrome 148.0.7778.120

🔗 [View Issue](https://github.com/makeplane/plane/issues/9084)

---


---

## 🧠 Testing Approach

- Manual exploratory testing
- Input validation & boundary value testing
- Business logic & transaction workflow testing
- Basic security checks (authentication, authorization flows)
- UI consistency and responsiveness testing

---

## 📈 Key Learnings

- How missing input validation creates security and financial risks
- Identifying business logic flaws that bypass critical controls
- Difference between functional bugs and security vulnerabilities
- Writing structured, evidence-backed bug reports
- How workflow-breaking bugs affect core user journeys

---

## 👤 Author

**Meraj Alam**
- GitHub: [@merajalamwork-hue](https://github.com/merajalamwork-hue)
