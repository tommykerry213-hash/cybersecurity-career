# Hands‑On Web Security Labs: Attack & Mitigation Portfolio

## Client‑Side Control Bypass
Performed input manipulation using browser dev tools and Burp Suite.

![Client‑Side Control Screenshot](screenshots/client-side-bypass.png)

**Findings:**
- Bypassed client‑side validation.
- Server accepted unauthorized input.

---

## Path Traversal Practical
Tested directory traversal vulnerabilities using crafted payloads.

![Path Traversal Screenshot](screenshots/path-traversal.png)

**Findings:**
- Accessed restricted files via `../` sequences.
- Recommended input sanitization and whitelist validation.

---

## IDOR Practical
Investigated insecure direct object references.

![IDOR Screenshot](screenshots/idor.png)

**Findings:**
- User IDs exposed in URLs.
- Suggested implementing access control checks.

---

## Authentication Labs
### AUTH1: Login Bypass
![Login Bypass Screenshot](screenshots/auth1-login-bypass.png)

### AUTH2: JWT Token Manipulation
![JWT Token Screenshot](screenshots/auth2-jwt.png)

**Findings:**
- Weak token validation.
- Recommended using signed JWTs and secure secret management.

---

## Misconfiguration Labs
### Directory Listing
![Directory Listing Screenshot](screenshots/misconfig1.png)

### Default Credentials
![Default Credentials Screenshot](screenshots/misconfig2.png)

### Configuration Disclosure
![Configuration Disclosure Screenshot](screenshots/misconfig3.png)
🛡️ Client-Side Control Bypass Assessment
Objective
To evaluate the robustness of client-side validation mechanisms in a shopping platform and demonstrate how insufficient server-side checks can be exploited.
Methodology
Tools Used: Burp Suite (integrated browser, Proxy, and Repeater modules)
Approach:
Intercepted HTTP requests generated during item purchase workflows.
Manipulated client-side parameters (e.g., balance checks) to bypass restrictions.
Resent modified requests directly to the server using Burp Suite Repeater.
Tested repeated submissions to simulate bulk purchases under invalid conditions.
Findings
Client-Side Trust Issue: The application relied solely on client-side validation to enforce purchase rules.
Zero-Balance Exploit: By altering request payloads, purchases were successfully completed despite insufficient account balance.
Replay Vulnerability: Using Burp Suite’s Repeater, identical requests could be resent multiple times, enabling unauthorized acquisition of multiple items.
Root Cause: Lack of robust server-side validation and transaction integrity checks.
Impact
Financial Risk: Unauthorized purchases could lead to direct revenue loss.
Reputation Damage: Exploitation of such vulnerabilities undermines customer trust.
Scalability of Attack: Automated replay could magnify the impact significantly.
Recommendations
Implement server-side validation for all critical business logic (e.g., balance checks, purchase limits).
Introduce anti-replay mechanisms such as nonce values or transaction tokens.
Enforce logging and monitoring to detect abnormal purchase patterns.
Conduct regular penetration testing to identify and remediate similar flaws.


Here i used burp suite in purchasing goods without payment.

🗂 Path Traversal Practical
Objective  
To test whether the application properly validates and restricts file path inputs, preventing unauthorized access to sensitive files outside the intended directory.
Methodology
Used crafted input with ../ sequences to attempt directory traversal.
Submitted requests targeting hidden files, specifically ../secret_config.txt.
Observed server responses to confirm whether traversal was successful.
Tools: Browser developer tools, manual payload injection.
Findings  
The application failed to sanitize user input, allowing traversal outside the intended directory. By exploiting this flaw, I accessed ../secret_config.txt, demonstrating that sensitive configuration files were exposed.
Impact
Unauthorized disclosure of sensitive data (e.g., credentials, API keys, system configs).
Potential compromise of the entire application environment.
Elevated risk of further exploitation, including privilege escalation or system takeover.



Recommendations
Implement strict input validation and canonicalization of file paths.
Restrict file access to whitelisted directories only.
Use built‑in secure file handling APIs rather than direct path concatenation.
Regularly audit and test for path traversal vulnerabilities



🔓 IDOR Practical
Objective  
To test whether the application properly enforces access control, ensuring that users can only view their own profile data and not other users’ information.
Methodology
Observed the profile URL structure: /idor1/profile/{id}.
Manually modified the id parameter in the browser from 3 (guest account) to 1.
Reloaded the page to check if unauthorized data was accessible.
No special tools were required beyond a browser; the test relied on direct URL manipulation.
Findings  
The application failed to enforce authorization checks. By changing the profile ID from 3 to 1, I was able to access the administrator’s profile data. This demonstrates a classic IDOR vulnerability where object references are exposed and not validated against the logged‑in user’s permissions.
Impact
Unauthorized access to sensitive user information (e.g., admin details, emails, roles).
Potential for privilege escalation if administrative functions are exposed.
Risk of data leakage across all user accounts by enumerating IDs.
Weakens trust in the application’s access control model.

idor vid.mp4

Recommendations
Implement strict server‑side authorization checks to ensure users can only access their own resources.
Avoid exposing predictable identifiers (like sequential user IDs) in URLs.
Use indirect references (e.g., UUIDs or opaque tokens) instead of direct IDs.
Conduct regular access control testing to detect IDOR vulnerabilities early.

🔑 AUTH1: Login Bypass Fundamentals
Objective  
To test whether the application’s login mechanism properly validates user credentials and prevents unauthorized access through injection techniques.
Methodology
Attempted SQL Injection in the login form.
Entered the payload:
Username: admin' --
Password: anything
The -- sequence commented out the remainder of the SQL query, bypassing password verification.
Observed the server’s response to confirm successful login as the administrator.
Findings  
The application failed to sanitize user input in the login form. By injecting admin' --, the SQL query was altered to ignore the password check, granting direct access to the admin account. This demonstrates a fundamental authentication bypass vulnerability.
Impact
Full administrative access without valid credentials.
Exposure of sensitive data and system controls.
Potential for privilege escalation and complete compromise of the application.
Undermines trust in the authentication system.

Recommendations
Use parameterized queries (prepared statements) to prevent SQL injection.
Implement robust input validation and sanitization.
Enforce multi‑factor authentication for privileged accounts.
Regularly conduct penetration testing and code reviews to identify injection flaws.



🔑 AUTH2: JWT Token Manipulation
Objective  
To test whether the application properly validates JSON Web Tokens (JWTs), ensuring that payloads and signatures cannot be tampered with to escalate privileges.
Methodology
Captured a valid JWT issued by the application.
Decoded the token payload to reveal fields such as id, username, and role.
Edited the payload, changing the role value from "user" to "admin".
Re‑encoded the token using the none algorithm (no signature).
Submitted the manipulated token to the application to test if access was granted.
Findings  
The application accepted the modified JWT without verifying its signature. By altering the payload and removing the signature requirement, I successfully escalated privileges from a regular user to an administrator.
Impact
Unauthorized administrative access without valid credentials.
Exposure of sensitive data and privileged functionality.
Potential compromise of the entire application environment.
Demonstrates a critical flaw in token validation that undermines trust in authentication.

Recommendations
Enforce strict signature validation for all JWTs.
Disallow the use of the none algorithm or weak signing methods.
Use strong cryptographic algorithms (e.g., HS256, RS256) with secure key management.
Implement token expiration and rotation policies.
Regularly audit authentication mechanisms for weaknesses in token handling.

MISCONFIG1: Directory Listing Enabled (example structure)
Objective  
To test whether directory listing was improperly enabled, exposing internal files.
Methodology
Navigated to application directories without specifying filenames.
Observed whether the server displayed file listings.
Findings  
Directory listing was enabled, revealing sensitive files and scripts.
Impact
Disclosure of internal code and configuration.
Easier reconnaissance for attackers.
Recommendations
Disable directory listing in server configuration.
Restrict access to sensitive directories.
MISCONFIG2: Default Credentials (example structure)
Objective  
To test whether default or weak credentials were left active.
Methodology
Attempted login using common default credentials (e.g., admin/admin).
Verified successful access.
Findings  
Default credentials were still active, granting unauthorized access.
Impact
Immediate compromise of administrative accounts.
Risk of full system takeover.
Recommendations
Enforce strong password policies.
Remove or change default credentials before deployment.
Implement multi‑factor authentication.




⚙️ MISCONFIG3: Configuration File Exposure
Objective  
To test whether sensitive configuration files (such as .env) are improperly exposed and accessible through the application, potentially leaking secrets and credentials.
Methodology
Attempted direct access to the .env file via the application.
Observed whether the server restricted access or returned file contents.
Successfully retrieved environment variables, including database credentials, API keys, and secret keys.
Tools: Browser and manual URL/file path manipulation.
Findings  
The application allowed direct access to the .env configuration file. This file contained sensitive information such as database connection strings, JWT secrets, API keys (Stripe, AWS, SendGrid), and administrator passwords. The exposure demonstrates a misconfiguration that fails to protect critical environment variables.
Impact
Disclosure of database credentials, enabling unauthorized database access.
Exposure of cryptographic secrets (JWT, API keys), allowing token forgery and service abuse.
Potential compromise of cloud services (AWS, Stripe, SendGrid).
Full administrative takeover of the application using leaked credentials.
Severe risk of data breaches and financial loss.


Recommendations
Restrict public access to configuration files (.env, .config, etc.).
Store secrets securely using environment variables at the OS level or secret management tools (e.g., Vault, AWS Secrets Manager).
Implement proper file permissions and server hardening.
Regularly audit deployments to ensure sensitive files are not exposed.
Rotate all exposed keys and credentials immediately.


⚙️ MISCONFIG4: Backup Files Exposure
Objective  
To test whether backup files and hidden directories were improperly exposed, allowing unauthorized access to sensitive system data.
Methodology
Used Gobuster to enumerate hidden files and directories.
Targeted common backup file extensions such as .zip, .bak, .backup.
Discovered a backup archive (backup.zip) stored in a web‑accessible directory.
Downloaded and unzipped the file to inspect its contents.
Found administrator credentials and configuration data inside the backup.
Used the exposed credentials to log into the admin panel.
Findings  
The application exposed backup files in publicly accessible directories. By unzipping the discovered archive, I gained access to sensitive information including admin credentials, API keys, and system configuration details. This misconfiguration allowed full administrative access to the application.
Impact
Unauthorized access to the admin panel.
Disclosure of sensitive system information (database details, API keys, user records).
Potential for complete compromise of the application and its data.
High risk of data breaches and service abuse.

Recommendations
Never store backup files in web‑accessible directories.
Implement strict access controls and file permissions.
Regularly audit deployments for exposed archives or sensitive files.
Use secure backup storage solutions outside the web root.
Rotate all exposed credentials and API keys immediately.


🔐 CRYPTO1: Weak Password Hashing
Objective  
To test whether the application uses secure password hashing algorithms, ensuring that stored credentials cannot be easily cracked.
Methodology
Identified that user passwords were hashed using MD5/SHA1, both of which are deprecated and insecure.
Extracted a sample hash (e10adc3949ba59abbe56e057f20f883e).
Used a common wordlist and hash‑cracking tool to attempt recovery.
The hash was cracked instantly, revealing the original password (123456).
Findings  
The application relies on weak hashing algorithms (MD5/SHA1) that are vulnerable to dictionary attacks, rainbow tables, and GPU‑accelerated brute force. Passwords were cracked almost instantly, demonstrating the inadequacy of these algorithms for secure credential storage.
Impact
Rapid compromise of user accounts.
Exposure of sensitive data if password reuse occurs across systems.
Increased risk of large‑scale breaches due to weak password protection.
Undermines trust in the application’s authentication system.

Recommendations
Replace MD5/SHA1 with modern, secure hashing algorithms such as bcrypt, scrypt, Argon2, or PBKDF2.
Implement salting to ensure unique hashes for identical passwords.
Enforce strong password policies to reduce susceptibility to dictionary attacks.
Regularly audit password storage mechanisms for compliance with current security standards.


🔐 CRYPTO2: Insecure Encryption Implementation
Objective  
To test whether the application uses secure encryption methods and proper key management for protecting sensitive data.
Methodology
Identified that the application was using deprecated encryption algorithms (e.g., DES).
Observed that encryption keys were hardcoded in the source code (secret01).
Tested decryption using the exposed key and weak cipher.
Successfully recovered plaintext data, demonstrating insecure encryption practices.
Findings  
The application relied on outdated encryption (DES) with hardcoded keys and weak randomness. This allowed sensitive data to be decrypted easily, exposing critical information. The lack of secure key management and reliance on weak ciphers made the system vulnerable to brute force and cryptanalysis attacks.
Impact
Exposure of sensitive data such as credentials, tokens, and configuration details.
Increased risk of database dumps or intercepted traffic being decrypted.
Potential compromise of entire systems if encryption keys are leaked.
Undermines trust in the confidentiality of the application’s data.


Recommendations
Replace deprecated algorithms (DES, RC4, etc.) with modern standards such as AES‑256.
Implement secure key management practices (e.g., environment variables, secret vaults).
Use strong randomness for key generation and initialization vectors.
Regularly audit cryptographic implementations for compliance with current security standards.
Rotate and revoke exposed keys immediately.


<img width="487" height="331" alt="Screenshot 2026-08-03 104645" src="https://github.com/user-attachments/assets/aa6e8bba-5c2e-422b-b85b-395e2837aa7d" />
<img width="551" height="356" alt="Screenshot 2026-08-03 061026" src="https://github.com/user-attachments/assets/2e828d2e-e116-4a61-95c2-5dcecdd79efb" />
<img width="505" height="315" alt="Screenshot 2026-08-03 044712" src="https://github.com/user-attachments/assets/536b10da-dff2-496d-96f0-e47521f5f5d1" />
<img width="272" height="136" alt="Screenshot 2026-08-03 044636" src="https://github.com/user-attachments/assets/3050f197-5676-4cae-8fbe-9b2b793a0efb" />
<img width="482" height="266" alt="Screenshot 2026-08-02 041816" src="https://github.com/user-attachments/assets/ac34a573-0016-4f2e-bebc-a73cf74e4358" />
<img width="497" height="296" alt="Screenshot 2026-08-02 041454" src="https://github.com/user-attachments/assets/a117fa0b-f2bc-4cf6-8082-153ea8d5ca5c" />
<img width="466" height="188" alt="Screenshot 2026-08-01 021054" src="https://github.com/user-attachments/assets/d17589ef-d44f-4103-8176-ecb17ccce5cb" />
<img width="433" height="323" alt="Screenshot 2026-08-01 020611" src="https://github.com/user-attachments/assets/febc8e7e-7804-4127-b396-70eae7eb37a3" />
<img width="610" height="292" alt="Screenshot 2026-07-30 004239" src="https://github.com/user-attachments/assets/0b42d1b1-13d5-4b99-904b-b6b3e0b98098" />
<img width="592" height="242" alt="Screenshot 2026-07-30 002846" src="https://github.com/user-attachments/assets/376fd111-f085-4795-bbd6-06730e89b0b8" />
<img width="596" height="332" alt="Screenshot 2026-07-28 112759" src="https://github.com/user-attachments/assets/e7e331e2-757f-4d18-9fd1-f0f6fc305900" />
<img width="568" height="332" alt="Screenshot 2026-07-28 112131" src="https://github.com/user-attachments/assets/81127442-bca7-4001-9406-0db8e5e827de" />
<img width="512" height="295" alt="Screenshot 2026-07-27 110513" src="https://github.com/user-attachments/assets/e8eba9a5-21f1-475e-8ff1-ce16a96691fc" />
<img width="506" height="269" alt="Screenshot 2026-07-26 141357" src="https://github.com/user-attachments/assets/237a4ea6-82e2-41fc-97fb-97fa33372c5f" />
<img width="635" height="479" alt="Screenshot 2026-07-25 200855" src="https://github.com/user-attachments/assets/44153a64-0eb3-4375-9810-8ca1c3968dd7" />
