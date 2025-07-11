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

### Directory & Subdomain Enumeration

- **Subdomain Scan**: 
  ```bash
  gobuster dns -d <ip addr> -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -i --wildcard
