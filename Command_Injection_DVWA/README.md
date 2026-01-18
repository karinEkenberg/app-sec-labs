# Command Injection - DVWA (Low Security)


<img width="960" height="1032" alt="Skärmbild 2026-01-18 074711" src="https://github.com/user-attachments/assets/eb897031-8887-4ed2-9208-be2de8e76e22" />

## Vulnerability Overview
This lab demonstrates a classic OS Command Injection vulnerability in a web application. The application takes user input intended for a system command (`ping`) without proper sanitization, allowing an attacker to append arbitrary malicious commands.

## Lab Details
* **Target:** DVWA (Damn Vulnerable Web App) on Metasploitable 2
* **Security Level:** Low
* **Vulnerability Type:** CWE-78: OS Command Injection

## Discovery & Exploitation

### 1. Analysis
The application accepts an IP address to perform a ping test.
* **Normal Input:** `127.0.0.1` -> Returns ping statistics.

### 2. Injection Testing
By appending a semicolon (`;`), which acts as a command separator in Linux, additional commands can be chained.

* **Payload:** `127.0.0.1; whoami`
* **Result:** The application displayed `www-data`, confirming code execution as the web server user.

### 3. Data Exfiltration
Using the established injection point to read sensitive system files.
* **Payload:** `127.0.0.1; cat /etc/passwd`
* **Impact:** Full disclosure of system users.

## Remediation (Secure Coding)
The vulnerability exists because the input is passed directly to `shell_exec()`.

**Fix:**
1.  **Input Validation:** Strictly validate that the input contains only IP address characters (numbers and dots).
2.  **API Usage:** Use language-specific APIs (e.g., PHP's built-in network functions) instead of calling system shell commands whenever possible.
3.  **Sanitization:** If `shell_exec` is unavoidable, use functions like `escapeshellarg()` to escape special characters.
