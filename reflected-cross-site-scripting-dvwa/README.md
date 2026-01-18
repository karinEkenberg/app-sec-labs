# Reflected Cross-Site Scripting (XSS) - DVWA

## Vulnerability Overview
Reflected XSS occurs when an application receives data in an HTTP request and includes that data within the immediate response in an unsafe way. This allows attackers to inject malicious scripts (JavaScript) that execute in the victim's browser, potentially stealing session cookies or redirecting users.

## Lab Details
* **Target:** DVWA (Damn Vulnerable Web App)
* **Security Level:** Low
* **Vulnerability:** CWE-79: Improper Neutralization of Input During Web Page Generation

## Execution

### 1. Discovery
The application accepts user input via the "name" parameter and reflects it directly on the page without encoding.

### 2. Exploitation (Proof of Concept)
By injecting standard HTML script tags, we can force the browser to execute arbitrary JavaScript.
* **Payload:** `<script>alert(document.cookie)</script>`
* **Objective:** Demonstrate access to sensitive session data (Session Hijacking potential).

### 3. Impact
The resulting popup displayed the active `PHPSESSID`, confirming that an attacker could exfiltrate this token to hijack the user's active session.

<img width="960" height="1032" alt="Skärmbild 2026-01-18 183327" src="https://github.com/user-attachments/assets/0a1efc0e-183e-4f4e-8381-6f7987201f65" />
<img width="960" height="1032" alt="Skärmbild 2026-01-18 183357" src="https://github.com/user-attachments/assets/7db23e53-1ed9-4e25-b675-74b0a29d741f" />


## Remediation (Secure Coding)
The vulnerability exists because the application echos user input directly to the DOM.

**Fix:**
1.  **Output Encoding:** Convert special characters into their corresponding HTML entities before rendering.
    * *Vulnerable:* `echo $_GET['name'];`
    * *Fixed:* `echo htmlspecialchars($_GET['name'], ENT_QUOTES, 'UTF-8');`
2.  **Context Awareness:** Ensure encoding matches the context (HTML body, JavaScript variable, CSS attribute) where the data is placed.
