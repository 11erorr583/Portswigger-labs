# Web Application Security & Penetration Testing Reports

This repository contains detailed technical evaluations and penetration testing documentation based on security challenges from **PortSwigger Web Security Academy**. 

The assessments focus on identifying core web application vulnerabilities, validating attack paths, analyzing root causes, and providing actionable remediation strategies to secure enterprise applications.

---

## 🛠️ Summary of Evaluated Labs

| Lab ID | Target Vulnerability Class | Core Vulnerability Mechanism | Severity Level |
| :--- | :--- | :--- | :--- |
| **Lab 1** | SQL Injection (CWE-89) | Direct WHERE clause concatenation | High |
| **Lab 2** | SQL Injection / Auth Bypass (CWE-89) | Authentication logic subversion | Critical |
| **Lab 3** | SQL Injection (UNION-based) (CWE-89) | Schema & column enumeration | High |
| **Lab 4** | Reflected XSS (CWE-79) | Missing HTTP response entity encoding | Medium |
| **Lab 5** | Stored XSS (CWE-79) | Persistent database storage without encoding | High |
| **Lab 6** | DOM-based XSS (CWE-79) | Unsafe `document.write` execution sink | Medium |
| **Lab 7** | DOM-based XSS (CWE-79) | Dynamic `<select>` element DOM injection | Medium |
| **Lab 8** | Broken Authentication (CWE-203) | Measurable response error discrepancy | High |
| **Lab 9** | Broken Access Control (CWE-306) | Unprotected administrative route | Critical |
| **Lab 10** | Broken Access Control (CWE-203 / CWE-306) | Obscurity bypassed via script disclosure | High |

---

## 🔑 Key Remediation Strategies

To mitigate these vulnerabilities, applications must enforce defense-in-depth across all application layers:

### 1. Database Security
* **Parameterized Queries:** Use prepared statements or ORMs across all database access code to strictly separate query logic from user inputs.
* **Input Validation:** Enforce strict allowlists and type validation for all incoming request parameters.

### 2. Output Encoding & DOM Protection
* **Context-Aware Encoding:** Apply contextual HTML entity encoding on dynamic values returned in HTTP responses.
* **Safe DOM Manipulation:** Replace unsafe sinks (such as `document.write()`) with safe DOM APIs like `textContent` or `setAttribute()`.
* **Content Security Policy (CSP):** Implement strict CSP headers to restrict unauthorized inline script execution.

### 3. Authentication & Access Control
* **Generic Messaging:** Standardize login failure responses to prevent account enumeration.
* **Rate Limiting:** Implement IP-based rate limiting and brute-force mitigation mechanisms.
* **Server-Side Authorization:** Enforce Role-Based Access Control (RBAC) at the server routing layer rather than relying on URL obscurity or client-side checks.

---

## 📄 Documentation

For full step-by-step walkthroughs, payload details, and root cause analyses, refer to the included document in this repository:
* `penetration report.docx`

---
*Disclaimer: The testing documented in this repository was conducted exclusively in controlled laboratory environments for educational and defensive security research purposes.*