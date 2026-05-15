# 🌐 Functional Testing — WordPress Playground

> Detailed bug report for workflow issue found in WordPress Playground — a browser-based WordPress sandbox environment.

🔗 **Application:** [WordPress Playground](https://playground.wordpress.net/)
🔗 **Testing Type:** Functional & Workflow Testing

---

## 📊 Summary

| Metric | Count |
|--------|-------|
| Total Bugs Found | 1 |
| Functional / Workflow Bugs | 1 |
| Severity | Medium |

---

## BUG-005 — 404 Error After Creating New User in Admin Panel

| Field | Details |
|-------|---------|
| ID | BUG-005 |
| Severity | Medium |
| Type | Functional / Workflow Bug |
| Module | Admin Panel → User Management |
| Component | Add New User Form |
| Status | Reported |

### Description
When an administrator attempts to create a new user through the WordPress admin panel, the application redirects to a **404 Page Not Found** error immediately after form submission. The entire user creation workflow breaks at the final step, leaving the admin with no confirmation of success or failure and no way to verify if the user was actually created.

### Steps to Reproduce
1. Open [WordPress Playground](https://playground.wordpress.net/)
2. Log in as administrator
3. In the left sidebar navigate to **Users → Add New**
4. Fill in the following fields:
   - Username: any valid username (e.g. `testuser01`)
   - Email: any valid email (e.g. `testuser01@test.com`)
   - Role: Subscriber (default)
5. Click **"Add New User"** button
6. Observe the page redirect

### Test Inputs Used
| Field | Value Used |
|-------|------------|
| Username | `testuser01` |
| Email | `testuser01@test.com` |
| First Name | `Test` |
| Last Name | `User` |
| Role | Subscriber |
| Send Notification | Checked |

### Expected Result
- New user is successfully created
- System redirects to the **Users list page** showing the newly created user
- Or a **success confirmation message** is displayed on screen
- Admin has clear feedback that the action completed successfully

### Actual Result
- Application redirects to a **404 Page Not Found** page
- No success or failure message is displayed
- It is unclear whether the user was actually created or not
- The admin workflow is completely broken at the final step

### Additional Investigation
| Question | Finding |
|----------|---------|
| Is the user actually created despite the 404? | Unclear — needs database check |
| Does it happen every time? | Yes — 100% reproducible |
| Does it affect all user roles? | Not fully tested |
| Is it specific to Playground environment? | Likely yes — sandbox routing issue |

### Impact
- Core admin functionality is interrupted
- Administrator receives no feedback on action success or failure
- Could lead to duplicate user creation attempts
- Poor and confusing experience for anyone administering the site

### Root Cause Analysis
This is likely a **URL routing issue specific to the WordPress Playground sandbox environment**. When the form submits, it redirects to a URL that does not exist within the Playground's virtual file system or routing configuration, resulting in a 404 response.

### Fix Recommendation
The post-submission redirect URL should be validated against the Playground's routing system to ensure it resolves to an existing page. The redirect after user creation should point to `users.php` within the admin context of the Playground environment.

### Environment
| Field | Details |
|-------|---------|
| Platform | WordPress Playground (browser-based) |
| Browser | Chrome (Latest) |
| OS | macOS |
| WordPress Version | Playground default |

### Evidence


https://github.com/user-attachments/assets/b2744558-a608-4f69-9712-493a78a23a76 — full screen recording showing reproduction from login to 404 error

---

## 🧠 Testing Approach

- **End-to-End Workflow Testing** — followed complete user creation flow from start to finish
- **Exploratory Testing** — tested admin panel features without predefined scripts
- **Negative Path Testing** — observed system behavior at workflow boundaries
