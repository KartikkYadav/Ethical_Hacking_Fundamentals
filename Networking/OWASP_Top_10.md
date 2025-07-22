# OWASP – Open Worldwide Application Security Project

OWASP stands for **Open Worldwide Application Security Project** (formerly "Open Web Application Security Project"). It is a **non-profit foundation** that works to improve the **security of software**.

---

## 🔐 What Does OWASP Do?

OWASP provides:

- **Open-source tools and documentation**  
- **Security guidelines and standards**  
- **Community-driven projects**  
- **Awareness materials and training resources**

---

## 📚 Core OWASP Projects

| Project                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **OWASP Top 10**         | A list of the top 10 most critical web application security risks           |
| **OWASP ASVS**           | Application Security Verification Standard – for secure development         |
| **OWASP ZAP**            | Zed Attack Proxy – a free penetration testing tool for web apps             |
| **OWASP Cheat Sheets**   | Concise security best practices for developers                              |
| **OWASP SAMM**           | Software Assurance Maturity Model – for evaluating software security        |
| **OWASP Mobile Top 10**  | Top 10 security issues specific to mobile applications                      |

---

## 🧠 Why OWASP Matters

- Helps **developers, security testers**, and **organizations** build **more secure software**
- Encourages **community participation** and **transparency**
- Sets the **baseline standard** for web and app security worldwide

---

# 🛡️ OWASP Top 10 – 2021

The OWASP Top 10 (2021) introduces **reorganized categories**, reflecting modern threats, business logic flaws, and increased attention to **software design and supply chain risks**.

---

### 🔹 A01:2021 – Broken Access Control

**Description:**  
Access control policies are often not enforced properly. Attackers can act as other users or access unauthorized functions.

**Examples:**
- URL tampering  
- Forceful browsing  
- Elevation of privilege  

> *Access control failures are now the #1 risk, responsible for 94% of tested applications.*

---

### 🔹 A02:2021 – Cryptographic Failures  
*Formerly “Sensitive Data Exposure”*

**Description:**  
Weak or misconfigured encryption exposes sensitive data such as passwords, credit cards, or PII.

**Examples:**
- Using HTTP instead of HTTPS  
- Insecure key storage  
- Weak hashing (e.g., MD5)  

> *Emphasizes cryptographic issues, not just data exposure.*

---

### 🔹 A03:2021 – Injection

**Description:**  
Still a critical issue where attackers send malicious input to interpreters (e.g., SQL, NoSQL, LDAP).

**Examples:**
- SQL Injection  
- Command Injection  
- Server-Side Template Injection  

> *Classic vulnerability still prevalent in many apps.*

---

### 🔹 A04:2021 – Insecure Design  
*New Category*

**Description:**  
Covers missing or flawed security controls due to poor application architecture or design choices.

**Examples:**
- No threat modeling  
- Insecure default flows  
- No secure development lifecycle  

> *Encourages proactive security by design, not reactive patching.*

---

### 🔹 A05:2021 – Security Misconfiguration

**Description:**  
Default settings, overly verbose error messages, or unused features left enabled.

**Examples:**
- Exposed admin panels  
- Misconfigured HTTP headers  
- Open cloud storage (S3 buckets)  

> *Misconfiguration is now widespread across cloud and container environments.*

---

### 🔹 A06:2021 – Vulnerable and Outdated Components  
*Formerly “Using Components with Known Vulnerabilities”*

**Description:**  
Third-party libraries, frameworks, and dependencies may contain flaws that are exploitable.

**Examples:**
- Log4Shell (Log4j)  
- Apache Struts vulnerabilities  
- Outdated jQuery  

> *Dependency management is now a software supply chain concern.*

---

### 🔹 A07:2021 – Identification and Authentication Failures  
*Formerly “Broken Authentication”*

**Description:**  
Authentication weaknesses may allow brute-force, credential stuffing, or session hijacking.

**Examples:**
- Predictable login tokens  
- Missing multi-factor authentication (MFA)  
- Weak password recovery mechanisms  

> *Account security remains a top concern.*

---

### 🔹 A08:2021 – Software and Data Integrity Failures  
*New Category*

**Description:**  
Includes issues like insecure CI/CD pipelines, unsigned code, or deserialization of untrusted data.

**Examples:**
- Malicious software updates  
- Unverified plugins  
- CI/CD script tampering  

> *Highlights integrity of code and infrastructure (e.g., SolarWinds attack).*

---

### 🔹 A09:2021 – Security Logging and Monitoring Failures  
*Previously A10:2017*

**Description:**  
Lack of logs or alerting systems prevents breach detection and response.

**Examples:**
- No login audit trails  
- No alerting on suspicious activities  
- Logging sensitive data insecurely  

> *Crucial for incident response, forensics, and threat detection.*

---


## 🔹 A10:2021 – Server‑Side Request Forgery (SSRF) *(New Entry)*

**Description:**  
SSRF allows attackers to trick a server into making requests to internal or external systems.

**Examples:**
- Fetching internal metadata (e.g., AWS EC2)  
- Scanning internal network via open SSRF  
- Accessing internal‑only APIs  

> Growing threat due to increased cloud service usage.

---

# 🛡️ OWASP Top 10 – 2017

The OWASP Top 10 (2017) is a list of the most critical web application security risks.

---

## 🔹 A1 – Injection

**Description:**  
Occurs when untrusted data is sent to an interpreter as part of a command or query.  
**Examples:** SQL, OS, and LDAP injection.  
**Impact:** Can lead to data loss, corruption, or full system compromise.

> “Code injection occurs when attackers send malicious input to execute unintended commands.”

---

## 🔹 A2 – Broken Authentication

**Description:**  
Vulnerabilities in authentication mechanisms that allow attackers to compromise user credentials.  
**Impact:** Account takeover, privilege escalation, full system access.

> “Allows attackers to impersonate users or gain unauthorized access.”

---

## 🔹 A3 – Sensitive Data Exposure

**Description:**  
Inadequate protection of sensitive data (e.g., PII, credit cards, health info).  
**Impact:** Data theft, compliance violations (e.g., GDPR, HIPAA).

> “Failure to encrypt or securely store sensitive information.”

---

## 🔹 A4 – XML External Entities (XXE)

**Description:**  
Flaws in XML parsers that allow external entity references to be exploited.  
**Impact:** Internal file disclosure, SSRF, and remote code execution.

> “Vulnerable XML processing can leak internal files or access internal systems.”

---

## 🔹 A5 – Broken Access Control

**Description:**  
Improper enforcement of user roles or permissions.  
**Impact:** Unauthorized access to functions or data.

> “Attackers can access unauthorized resources or perform privileged actions.”

---

## 🔹 A6 – Security Misconfiguration

**Description:**  
Default settings, verbose error messages, or unnecessary features expose the system.  
**Impact:** System compromise, information leakage, pivoting.

> “Poorly configured servers, frameworks, or apps make easy targets.”

---

## 🔹 A7 – Cross‑Site Scripting (XSS)

**Description:**  
Allows attackers to inject client-side scripts into web pages.  
**Impact:** Session hijacking, defacement, phishing, or malware delivery.

> “Client-side code injection via input that isn’t properly sanitized.”

---

## 🔹 A8 – Insecure Deserialization

**Description:**  
Deserialization of untrusted data can lead to remote code execution.  
**Impact:** DoS, privilege escalation, or injection attacks.

> “Unsafe deserialization can allow attackers to control application flow.”

---

## 🔹 A9 – Using Components with Known Vulnerabilities

**Description:**  
Usage of outdated libraries, frameworks, or software components with publicly known flaws.  
**Impact:** Full compromise, especially if the component runs with high privileges.

> “Your app is only as secure as the components it uses.”

---

## 🔹 A10 – Insufficient Logging & Monitoring

**Description:**  
Lack of proper logging and alerting to detect and respond to attacks.  
**Impact:** Undetected breaches and delayed responses.

> “Without visibility, malicious activities go unnoticed.”
>
# 🛡️ OWASP Top 10 – 2013

The **OWASP Top 10 for 2013** highlights the most critical risks to web applications based on data from security professionals and organizations worldwide.

---

## 🔹 A1 – Injection

**Description:**  
Injection flaws occur when untrusted data is sent to an interpreter as part of a command or query.

**Examples:**
- **SQL Injection**
- **Command Injection**
- **LDAP Injection**

> Attackers can trick the interpreter into executing unintended commands or accessing unauthorized data.

---

## 🔹 A2 – Broken Authentication and Session Management

**Description:**  
Flaws in authentication or session handling allow attackers to compromise passwords, keys, or session tokens.

**Examples:**
- Weak password reset mechanisms  
- Session IDs exposed in URLs  
- No session timeout

> Attackers may impersonate other users or hijack sessions.

---

## 🔹 A3 – Cross-Site Scripting (XSS)

**Description:**  
XSS flaws occur when apps include untrusted data in a web page without proper validation or escaping.

**Examples:**
- Storing JavaScript in comment fields  
- Reflecting malicious input in error messages

> Attackers can execute scripts in the victim's browser to hijack sessions, redirect users, or deface websites.

---

## 🔹 A4 – Insecure Direct Object References

**Description:**  
Occurs when apps expose references to internal implementation objects (like files, database records, keys) without proper access control.

**Examples:**
- `/account?user_id=1234` *(where changing the ID gives access to another user)*

> Attackers can manipulate parameters to access unauthorized resources.

---

## 🔹 A5 – Security Misconfiguration

**Description:**  
This covers misconfigured permissions, error messages, open cloud storage, outdated software, and unnecessary services.

**Examples:**
- Default admin accounts  
- Detailed stack traces in production  
- Open ports/services

> Such misconfigurations provide easy entry points for attackers.

---

## 🔹 A6 – Sensitive Data Exposure

**Description:**  
Failure to protect sensitive data such as financial, healthcare, or PII.

**Examples:**
- No HTTPS  
- Weak crypto algorithms *(e.g., MD5)*  
- Storing passwords in plain text

> Exposed data can lead to identity theft, fraud, or regulatory violations.

---

## 🔹 A7 – Missing Function Level Access Control

**Description:**  
Applications do not enforce authorization checks on every function or endpoint.

**Examples:**
- Frontend hides admin button, but attacker directly calls admin API

> Attackers can escalate privileges by directly invoking restricted functions.

---

## 🔹 A8 – Cross-Site Request Forgery (CSRF)

**Description:**  
CSRF tricks a user into executing unwanted actions on a web application where they're authenticated.

**Examples:**
- Auto-submitting a form that changes email/password

> Can result in unauthorized actions being performed on behalf of the user.

---

## 🔹 A9 – Using Components with Known Vulnerabilities

**Description:**  
Using outdated libraries, frameworks, or other software components with known flaws.

**Examples:**
- Using an old version of Apache Struts or jQuery  
- Unpatched CMS plugins

> Attackers scan for apps using vulnerable components and exploit them.

---

## 🔹 A10 – Unvalidated Redirects and Forwards

**Description:**  
Applications redirect or forward users to untrusted URLs without proper validation.

**Examples:**
- Redirecting to a URL fr


