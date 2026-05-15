# 🔐 Security Testing — VulnBank

> Detailed bug reports for security and business logic vulnerabilities found in VulnBank — an intentionally vulnerable banking web application.

🔗 **Application:** [VulnBank](https://github.com/Commando-X/vuln-bank)
🔗 **Testing Type:** Security & Business Logic Testing

---

## 📊 Summary

| Metric | Count |
|--------|-------|
| Total Bugs Found | 3 |
| Critical | 1 |
| High | 2 |
| OWASP Categories Covered | 3 |

---

## BUG-001 — Payment Process Bypasses Virtual Card Requirement

| Field | Details |
|-------|---------|
| ID | BUG-001 |
| Severity | Critical |
| Type | Business Logic Flaw |
| Module | Bill Payment |
| OWASP Category | [A04:2021 — Insecure Design](https://owasp.org/Top10/A04_2021-Insecure_Design/) |
| Status | Reported |

### Description
The bill payment flow allows users to complete a payment without possessing a valid virtual card. The application fails to verify card validity before processing the transaction, bypassing a core financial security control entirely on the server side.

### Steps to Reproduce
1. Log in to VulnBank with any valid user account
2. Navigate to **Bill Payment** section
3. Enter any bill details (payee, amount)
4. Instead of selecting a valid virtual card, attempt to submit with no card or an invalid card value
5. Click **Pay**
6. Observe that the payment is processed successfully

### Test Inputs Used
| Field | Value Used | Expected Behavior |
|-------|------------|-------------------|
| Virtual Card | None / Invalid | Payment should be blocked |
| Amount | 100 | Should require valid card first |
| Payee | Any | Should not matter without valid card |

### Expected Result
The system should validate that the user has a valid, active virtual card before allowing any payment to proceed. If no valid card exists, the transaction should be rejected with a clear error message.

### Actual Result
Payment is processed successfully without any virtual card validation. No error message is shown. Transaction completes as if the card requirement does not exist.

### Security Impact
- Users can make unauthorized transactions without proper financial credentials
- Core payment security control is completely bypassed
- Could lead to financial fraud in a real banking environment

### Fix Recommendation
Implement server-side validation to verify virtual card existence and validity **before** processing any payment request. Client-side checks alone are insufficient.

---

## BUG-002 — Improper Validation of Recipient Account in Fund Transfer

| Field | Details |
|-------|---------|
| ID | BUG-002 |
| Severity | High |
| Type | Input Validation / Business Logic |
| Module | Fund Transfer |
| OWASP Category | [A03:2021 — Injection / Improper Input Validation](https://owasp.org/Top10/A03_2021-Injection/) |
| Status | Reported |

### Description
The fund transfer module accepts invalid, non-existent, or incorrectly formatted recipient account numbers without any validation. The system allows the transaction to proceed regardless of whether the destination account actually exists.

### Steps to Reproduce
1. Log in to VulnBank
2. Navigate to **Fund Transfer**
3. Enter your own account as the sender
4. In the recipient field enter a random invalid account number (e.g. `0000000000`, `1234`, `ABCDEFGH`)
5. Enter any transfer amount (e.g. `500`)
6. Click **Transfer**
7. Observe the result

### Test Inputs Used
| Field | Value Used | Expected Behavior |
|-------|------------|-------------------|
| Recipient Account | `0000000000` | Should return "Account not found" |
| Recipient Account | `1234` | Should return format validation error |
| Recipient Account | `ABCDEFGH` | Should reject non-numeric input |
| Amount | `500` | Should not process without valid recipient |

### Expected Result
The system should validate that the recipient account exists and is active before processing any fund transfer. Invalid or non-existent accounts should be rejected immediately with a descriptive error.

### Actual Result
The transfer proceeds without any recipient validation. The system accepts all invalid account formats without error and appears to process the transaction.

### Security Impact
- Funds can be transferred to non-existent accounts causing financial loss
- Transaction integrity is completely compromised
- No audit trail for where funds actually go

### Fix Recommendation
Implement both client-side format validation (numeric only, correct length) and server-side existence validation against the accounts database before processing any transfer.

---

## BUG-003 — Negative Loan Amount Accepted Due to Missing Input Validation

| Field | Details |
|-------|---------|
| ID | BUG-003 |
| Severity | High |
| Type | Input Validation |
| Module | Loan Application |
| OWASP Category | [A03:2021 — Injection / Improper Input Validation](https://owasp.org/Top10/A03_2021-Injection/) |
| Status | Reported |
| Reported To | [VulnBank GitHub Issue #35](https://github.com/Commando-X/vuln-bank/issues/35) |

### Description
The loan application input field accepts negative numeric values without any validation error. There is no boundary check on the minimum acceptable loan amount, allowing users to submit logically impossible loan requests.

### Steps to Reproduce
1. Log in to VulnBank
2. Navigate to **Loan Application**
3. In the loan amount field enter a negative value
4. Complete any other required fields normally
5. Submit the form

### Test Inputs Used
| Input Value | Expected Behavior | Actual Behavior |
|-------------|-------------------|-----------------|
| `-1` | Validation error | Accepted ❌ |
| `-1000` | Validation error | Accepted ❌ |
| `-99999` | Validation error | Accepted ❌ |
| `0` | Validation error | Accepted ❌ |
| `1` | Accepted | Accepted ✅ |

### Expected Result
The application should reject any loan amount that is zero, negative, or below a defined minimum threshold. A clear validation message should inform the user of the acceptable range.

### Actual Result
Negative and zero values are accepted without any validation error. The form submits successfully, creating a logically invalid loan record in the system.

### Security Impact
- Creates logically impossible financial records in the database
- Could be exploited to manipulate account balances or loan calculations
- Indicates absence of both frontend and backend input sanitization

### Fix Recommendation
Add both client-side (HTML min attribute, JavaScript validation) and server-side validation to enforce that loan amounts must be positive numbers above a defined minimum value.

---

## 🧠 Testing Approach

- **Boundary Value Analysis** — tested minimum, maximum, and invalid boundary inputs
- **Business Logic Testing** — tested whether security controls could be bypassed
- **Negative Testing** — deliberately entered invalid data to test system robustness
- **Manual Exploratory Testing** — explored payment and transfer flows without predefined scripts

---

## 📚 OWASP References

| Bug | OWASP Category |
|-----|----------------|
| BUG-001 | A04:2021 — Insecure Design |
| BUG-002 | A03:2021 — Improper Input Validation |
| BUG-003 | A03:2021 — Improper Input Validation |
