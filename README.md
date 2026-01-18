# Application Security Portfolio

## About This Repository
This repository serves as a documentation hub for my practical exercises in Application Security. As an IT Security Student with a background in Web Development (.NET, C#, React), my focus goes beyond simple exploitation. I aim to understand the root cause of vulnerabilities and document how to remediate them effectively.

## Repository Structure
This repository is organized into self-contained project folders. Each folder represents a specific vulnerability or challenge and typically contains:
* **Vulnerability Analysis:** How the flaw was discovered (Discovery).
* **Exploitation:** Proof of Concept (PoC) demonstrating the impact.
* **Remediation:** Code analysis and proposed fixes (Secure Coding).

## Methodology
All assessments follow industry-standard frameworks, primarily the **OWASP Testing Guide**. The workflow emphasizes:
1.  **Reconnaissance:** Understanding the application logic using tools like Burp Suite.
2.  **Verification:** Confirming vulnerabilities manually to avoid false positives.
3.  **Mitigation:** Leveraging development knowledge to suggest architectural or code-level fixes.

## Lab Environment & Tools
* **Attacker OS:** Kali Linux
* **Primary Tools:** Burp Suite Community, OWASP ZAP, SQLMap, Nmap.
* **Targets:**
    * **Metasploitable 2:** Hosting legacy vulnerable apps like DVWA.
    * **Docker Containers:** Hosting modern targets like OWASP Juice Shop.
    * **Local Labs:** Custom .NET/C# scenarios for secure code review.

## Green IT & Best Practices
I strive to maintain an efficient workflow by using lightweight containerization (Docker) where possible and focusing on precise, manual testing over resource-intensive automated scanning when appropriate.

## Disclaimer
All activities documented here were performed on isolated, locally hosted environments or authorized educational platforms.
