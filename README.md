# 🔐 Security Testing Portfolio

![Testing](https://img.shields.io/badge/Testing-Manual-blue)
![Type](https://img.shields.io/badge/Type-Security%20%26%20Functional-red)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Bugs Found](https://img.shields.io/badge/Bugs%20Found-5-critical)

A portfolio of security and functional vulnerabilities discovered through manual exploratory testing on web applications.

> **All testing was performed on authorized or intentionally vulnerable applications for educational purposes only.**

---

## 👨‍💻 About Me

Manual Software Tester with hands-on experience in functional testing, input validation testing, and basic security testing. This repository documents real vulnerabilities I identified, reported, and tracked across multiple applications.

---

## 📊 Summary

| Metric | Count |
|--------|-------|
| Applications Tested | 3 |
| Security Vulnerabilities | 3 |
| UI / Functional Bugs | 2 |
| Critical / High Severity | 3 |
| Medium Severity | 2 |

---

## 🧪 Applications Tested

| Application | Type | Focus Area |
|-------------|------|------------|
| [VulnBank](https://github.com/Commando-X/vuln-bank) | Intentionally Vulnerable | Security & Business Logic |
| [Mifos X Web App](https://mifos.org/) | Open Source Finance App | UI & Functional |
| [WordPress Playground](https://playground.wordpress.net/) | Sandbox Environment | Functional & Workflow |

---

## 🚨 Vulnerabilities & Bugs Discovered

---

### 📁 VulnBank — Security Testing

#### 🔴 BUG-001 — Payment Process Bypasses Virtual Card Requirement
| Field | Details |
|-------|---------|
| Severity | Critical |
| Type | Business Logic Flaw |
| Impact | Unauthorized or invalid transactions possible |

The bill payment flow allows users to complete payments without possessing a valid virtual card, bypassing a core financial control.

👉 [View Full Issue Report](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/1)

---

#### 🔴 BUG-002 — Improper Validation of Recipient Account in Fund Transfer
| Field | Details |
|-------|---------|
| Severity | High |
| Type | Input Validation / Business Logic |
| Impact | Transaction integrity compromised |

The fund transfer module accepts invalid or non-existent recipient account details without any validation, allowing transactions to proceed to incorrect destinations.

👉 [View Full Issue Report](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/2)

---

#### 🔴 BUG-003 — Negative Loan Amount Accepted Due to Missing Input Validation
| Field | Details |
|-------|---------|
| Severity | High |
| Type | Input Validation |
| Impact | Financial and logical inconsistency |

The loan amount input field accepts negative values with no server-side or client-side validation, creating a logical flaw that could be exploited to manipulate financial calculations.

👉 [View Full Issue Report](https://github.com/Commando-X/vuln-bank/issues/35)

---

### 📁 Mifos X Web App — UI & Functional Testing

#### 🟡 BUG-004 — Username Text Overlaps Account Icon on Login Page
| Field | Details |
|-------|---------|
| Severity | Medium |
| Type | UI Bug |
| Impact | Readability and user experience degraded |

When a long username is entered in the login page input field, the text overlaps with the account icon inside the input box, making the field difficult to read and visually broken.

👉 [View Evidence](https://gist.github.com/merajalamwork-hue/e1227b081556d61e8ca52bee4fa9912f)

---

### 📁 WordPress Playground — Functional Testing

#### 🟠 BUG-005 — 404 Error After Creating New User
| Field | Details |
|-------|---------|
| Severity | Medium |
| Type | Functional / Workflow Bug |
| Impact | Core admin functionality broken |

**Steps to Reproduce:**
1. Open WordPress Playground
2. Navigate to **Users → Add New**
3. Enter a username and email address
4. Click **Create New User**
5. Observe the redirect

**Expected:** User is created and system redirects to user list or confirmation page

**Actual:** Application redirects to a **404 Page Not Found** screen, breaking the entire user creation workflow

👉 Evidence: `https://github.com/user-attachments/assets/4f6088bf-f143-4ba6-a823-aa9019cf0fbb


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

## 📁 Repository Structure

```
security-testing-portfolio/
├── README.md                  # This file — all findings summarized
└── evidence/                  # Screenshots and screen recordings
    └── *.mp4 / *.png
```

---

## 👤 Author

**Meraj Alam**
- GitHub: [@merajalamwork-hue](https://github.com/merajalamwork-hue)

> ⚠️ **Disclaimer:** All testing was performed on intentionally vulnerable or authorized sandbox applications for educational and portfolio purposes only.
