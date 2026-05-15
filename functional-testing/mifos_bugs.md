# 🖥️ Functional Testing — Mifos X Web App

> Detailed bug report for UI issue found in Mifos X — an open source banking and financial services platform.

🔗 **Application:** [Mifos X Web App](https://mifos.org/)
🔗 **Testing Type:** UI & Functional Testing

---

## 📊 Summary

| Metric | Count |
|--------|-------|
| Total Bugs Found | 1 |
| UI Bugs | 1 |
| Severity | Medium |

---

## BUG-004 — Username Text Overlaps Account Icon on Login Page

| Field | Details |
|-------|---------|
| ID | BUG-004 |
| Severity | Medium |
| Type | UI Bug |
| Module | Login Page |
| Component | Username Input Field |
| Status | Reported |

### Description
The username input field on the Mifos X login page does not properly constrain text display when a long username is entered. The typed text overflows and visually overlaps with the account/user icon positioned inside the input box on the right side. This makes the field difficult to read and breaks the visual integrity of the login form.

### Steps to Reproduce
1. Open the Mifos X Web App login page
2. Click on the **Username** input field
3. Type a long username (20+ characters) — e.g. `merajalamwork_testing_user`
4. Observe the text inside the input field
5. Notice the text overlaps with the account icon on the right

### Test Inputs Used
| Input Length | Value Example | Overlap Triggered |
|-------------|---------------|-------------------|
| Short (under 10 chars) | `meraj` | No ✅ |
| Medium (10–15 chars) | `merajalam123` | Partial overlap |
| Long (20+ chars) | `merajalamwork_testing_user` | Full overlap ❌ |

### Expected Result
The input field should either:
- Truncate the visible text with an ellipsis (`...`) before it reaches the icon, or
- Add sufficient right-side padding so text never overlaps with the icon regardless of length

### Actual Result
Long usernames overflow into the icon space, causing the text and icon to visually overlap. This makes it impossible to clearly read what has been typed.

### Impact
- Reduces readability — user cannot see what they are typing
- Breaks visual consistency of the login form
- Degrades user experience, especially for users with long usernames or email addresses used as usernames

### Root Cause Analysis
The input field likely lacks a `padding-right` CSS property large enough to account for the icon width. The icon is positioned absolutely inside the input, but the text container does not respect that space.

### Fix Recommendation
Add sufficient `padding-right` to the username input field in CSS to prevent text from entering the icon area:
```css
input[type="text"] {
  padding-right: 40px; /* adjust based on icon width */
}
```

### Browsers Tested
| Browser | Version | Bug Present |
|---------|---------|-------------|
| Chrome | Latest | ✅ Yes |

### Evidence
👉 [View Screenshot Evidence](https://gist.github.com/merajalamwork-hue/e1227b081556d61e8ca52bee4fa9912f)

---

## 🧠 Testing Approach

- **UI / Visual Testing** — checked layout integrity across different input lengths
- **Boundary Value Analysis** — tested short, medium, and long input values
- **Exploratory Testing** — manually explored login form behavior without predefined scripts
