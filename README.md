# 🔐 Security Testing Portfolio

## 👨‍💻 About
I am a Manual Software Tester with experience in functional and basic security testing. This repository showcases vulnerabilities identified during testing of web applications.

---

## 🧪 Applications Tested
- VulnBank  
- Mifos X Web App  

---

## 🚨 Vulnerabilities Discovered

### 📁 VulnBank Testing

#### 🔴 1. Payment Process Bypasses Virtual Card Requirement  
- Allows bill payments without a valid virtual card  
- **Impact:** Unauthorized or invalid transactions  

👉 [View Issue](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/1)

---

#### 🔴 2. Improper Validation of Recipient Account in Fund Transfer  
- System accepts invalid or incorrect recipient account details  
- **Impact:** Transaction integrity issue  

👉 [View Issue](https://github.com/merajalamwork-hue/security-testing-portfolio/issues/2)

---

#### 🔴 3. Negative Loan Amount Accepted Due to Missing Input Validation  
- Application allows negative values in loan amount field  
- **Impact:** Logical and financial inconsistency  

👉 [View Issue](https://github.com/Commando-X/vuln-bank/issues/35)

---

## 🖥️ UI / Functional Issues

### 📁 Mifos X Web App

#### 🟡 UI Bug – (Username input text overlaps with account icon when entering long values

)
- When a long username is entered in the login page's username input field, the text overlaps with the account/user icon inside the input box. This affects readability and UI clarity.


- **Impact:** Affects user experience  

👉 https://gist.github.com/merajalamwork-hue/e1227b081556d61e8ca52bee4fa9912f

---

## 🧠 Testing Approach
- Manual exploratory testing  
- Input validation testing  
- Transaction workflow testing  
- Basic security checks  

---

## ⚠️ Disclaimer
This repository is for educational purposes only. Testing was performed on authorized or intentionally vulnerable applications.
