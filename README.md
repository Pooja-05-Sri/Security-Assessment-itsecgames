# Security-Assessment-itsecgames
Security assessment of http://www.itsecgames.com  — vulnerability scan, SSL/TLS analysis, and mitigation recommendations (AccuKnox Security Officer Trainee Task)

**AccuKnox Security Officer Trainee – Problem Statement**

**Assessor:** Pooja Sri Telagamsetti  
**Role Applied:** Security Officer Trainee – AccuKnox  
**Assessment Date:** 20 September 2025

---

## Executive Summary
This repository contains a public security posture evaluation of the endpoint **http://www.itsecgames.com**.  
All scans were conducted using only publicly available, non-intrusive tools. The assessment identified header misconfigurations, TLS/certificate issues, exposed services and outdated software, and DNS observations. The repository includes the full consolidated report (PDF), screenshots of raw tool output, and video demonstration links.

---

## Objectives
- Identify vulnerabilities on the domain using publicly available tools.  
- Detect misconfigurations, outdated software, and known CVEs.  
- Assess SSL/TLS configuration and certificate health.  
- Highlight exposed information (headers, banners, error messages).  
- Provide a prioritized list of findings and mitigation recommendations.

---

##  Tools Used
- SSL Labs — SSL/TLS configuration and certificate analysis  
- SecurityHeaders.io — HTTP response header analysis  
- Nmap (online) — Port & service discovery with version detection  
- Nikto Web Server Scanner —  Web server vulnerability scanning
- DNS Lookup Tool / MXToolbox — DNS records enumeration  
- WhatWeb / Wappalyzer — Technology fingerprinting


---

## 📁 Repo Structure

Security-Assessment-itsecgames/
│
├── README.md        ← Overview of the assignment, tools, how to reproduce scans
├── Security_Assessment_Report.pdf ← Your full detailed PDF report
├── Screenshots/     ← All screenshots of scan results
│   ├── security_headers.png
│   ├── ssl_labs.png
│   ├── nmap_scan.png
│   ├── dns_lookup.png
│   ├── nikto_scan.png
└── Video-links.txt 



---

## 📑 Quick Findings (Executive)
| Priority | Finding | Tool / Evidence |
|----------|---------|-----------------|
| High     | Served over HTTP; HTTPS not enforced / certificate name mismatch | SecurityHeaders / SSL Labs (ssl_labs.png) |
| High     | Outdated OpenSSH 6.7p1 exposed on port 22 | Nmap (nmap_scan.png) |
| High     | Missing security headers: CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy, Permissions-Policy | SecurityHeaders (security_headers.png) |
| Medium   | Server header reveals Apache (version disclosure) | HTTP response headers (security_headers.png / nmap) |
| Medium   | SPF TXT includes internal references (mme.local) | DNS Lookup (dns_lookup.png) |

> See the full prioritized table and detailed remediation recommendations in `Report.pdf`.

---

## 🔍 How to Reproduce the Scans
**(Use only non-intrusive scans on public sites — do not run aggressive or authenticated tests.)**

1. **Security Headers**  
   - Visit: https://securityheaders.com  
   - Enter: `http://www.itsecgames.com` → Run scan → Save screenshot `security_headers.png`.

2. **SSL/TLS (SSL Labs)**  
   - Visit: https://www.ssllabs.com/ssltest/  
   - Enter: `www.itsecgames.com` → Start test → Save results screenshot `ssl_labs.png`.

3. **Nmap (Online Basic Scan)**  
   - Visit an online nmap service : https://hackertarget.com/nmap-online-port-scanner/
    - Enter: `www.itsecgames.com` → Start test → Save results screenshot `nmap_port_scanner.png`.

4. **DNS Lookup**  
   - Use MXToolbox or any DNS lookup tool; export or screenshot the A, MX, NS, TXT and SOA results as `dns_lookup.png`.

5.  **Nikto Web Server Scanner**  
   - Visit: [https://hackertarget.com/nikto-website-scanner/](https://hackertarget.com/nikto-website-scanner/) (or another Nikto web interface).  
   - Enter: `http://www.itsecgames.com` → Run the scan to uncover common web server misconfigurations, outdated components, and publicly accessible files/directories.  
   - Save the results screenshot `Screenshots/nikto_scan.png`.
   - Download the Nikto report from the website `nikto.online-Report(www.itsecgames.com).txt`.

---

## Report Contents (Security Assessment Report.pdf)
The attached `Report.pdf` includes:
- Problem statement & scope  
- Tools & methodology  
- Per-tool findings (screenshots + commentary)  
- Prioritized findings table (severity, risk, evidence)  
- Clear mitigation recommendations for each finding  
- Conclusion & next steps

---

## Video Demonstration Links


- Video 1 — SSL Labs scan & explanation: https://drive.google.com/file/d/1V0vnYtK8h30F-5tBS52Zy70dlEPVODIK/view?usp=drive_link 
- Video 2 — SecurityHeaders scan & explanation: https://drive.google.com/file/d/1ohZzU5tP1LVqc5HtVXdCVShptDRaX76j/view?usp=drive_link
- Video 3 — Nmap scan walk-through: https://drive.google.com/file/d/1ReAG4BzgZIBQM6Ui4J3534KJ2GJ6CWuR/view?usp=drive_link
- Video 4 — DNS Lookup Views the live DNS records for a domain: https://drive.google.com/file/d/1ikrX_f3wo7mloP0rgwzLanmyoLdQlTEa/view?usp=drive_link
- Video 5 — Nikto web server scanner: https://drive.google.com/file/d/1J1_TuDqfuxPZSrimmUTv9AHumPg3NAWz/view?usp=drive_link


---

## Recommended Next Steps (for the site owner)

1. Enforce HTTPS with a valid certificate covering `itsecgames.com` and `www.itsecgames.com`. Configure HTTP → HTTPS redirect and HSTS.  
2. Update server software (OpenSSH, Apache) to supported versions and remove exposed version banners.  
3. Add security headers (CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy, Permissions-Policy).  
4. Harden SSH (disable password auth, use keys, restrict allowed IPs).  
5. Review DNS SPF, add DKIM/DMARC if missing, and remove internal hostnames from public records.  
6. Implement continuous monitoring and periodic scans (integrate into CI/CD / CI pipeline).

---

## Contact
**Pooja Sri Telagamsetti**  
LinkedIn: https://www.linkedin.com/in/pooja-sri-telagamsetti-021ab7232  
Email: tpsri555@gmail.com

---

## Note
All testing performed was non-intrusive and limited to publicly available information and tools. No exploitation or intrusive attacks were performed.

---

