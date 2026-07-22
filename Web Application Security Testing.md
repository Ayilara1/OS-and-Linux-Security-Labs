# 🌐 Web Application Security Assessment with Burp Suite & OWASP ZAP

![Burp Suite](https://img.shields.io/badge/Burp%20Suite-Web%20Security-orange?style=for-the-badge)
![OWASP ZAP](https://img.shields.io/badge/OWASP-ZAP-red?style=for-the-badge)
![OWASP](https://img.shields.io/badge/OWASP-Top%2010-black?style=for-the-badge)
![Web Security](https://img.shields.io/badge/Web-Application%20Testing-blue?style=for-the-badge)

---

# 📖 Overview

This lab demonstrates practical web application security testing using **Burp Suite Professional** and **OWASP ZAP**. The assessment focused on intercepting HTTP traffic, crawling the application, identifying security vulnerabilities, comparing scanning tools, and validating security weaknesses through controlled testing.

The target application used for this exercise was **Acunetix TestPHP (testphp.vulnweb.com)**, a deliberately vulnerable web application designed for security training.

---

# 🎯 Objectives

- Intercept HTTP requests and responses
- Analyze HTTP headers
- Discover application endpoints
- Identify common web vulnerabilities
- Compare Burp Suite and OWASP ZAP
- Perform vulnerability assessment
- Test basic injection techniques

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Target Application | testphp.vulnweb.com |
| Proxy Tool | Burp Suite |
| Security Scanner | OWASP ZAP |
| Browser | Firefox |

---

# Tools Used

- Burp Suite
- OWASP ZAP
- Firefox Browser

---

# Lab 8 – Web Application Security Testing

## Exercise 1 – HTTP Request and Response Analysis

### Request Headers Observed

The intercepted HTTP request contained the following important headers:

| Header | Description |
|---------|-------------|
| GET / HTTP/1.1 | HTTP request method |
| Host | testphp.vulnweb.com |
| User-Agent | Mozilla Firefox on Linux |
| Accept | Accepted content types |
| Accept-Language | Preferred language |
| Accept-Encoding | Compression methods |
| Connection | Keep-Alive |

### Response Headers

| Header | Value |
|---------|-------|
| Status | HTTP/1.1 200 OK |
| Server | nginx/1.19.0 |
| Content-Type | text/html |
| X-Powered-By | PHP 5.6.40 |
| Content-Length | 4958 Bytes |

![HTTP request and response headers](screenshots/web%20Application%20security/Picture1.jpg)

### Security Observation

The response headers disclosed the underlying web server and PHP version, providing attackers with information that could be used for targeted exploitation if known vulnerabilities exist.

---

# Exercise 2 – Spidering and URL Discovery

Burp Suite's crawler identified multiple application resources.

### Interesting URLs

- `/AJAX/index.php`
- `/robots.txt`
- `/Fractal-Explorer/`
- `/ShockwaveFlash/`
- Multiple external references (Acunetix, W3C, Macromedia)

![URL discovery](screenshots/web%20Application%20security/Picture2.jpg)

### Observation

Spidering successfully enumerated hidden resources and application endpoints, demonstrating how attackers can discover content that may not be directly linked from the application's homepage.

---

# Exercise 3 – Vulnerability Assessment

Burp Suite identified the following security issues:

| Vulnerability | Severity |
|---------------|----------|
| Email Address Disclosure | Low |
| Unencrypted Communication | Medium |
| Clickjacking (Frameable Response) | Medium |

## Example Vulnerability – Email Address Disclosure

### Finding

```
wvs@acunetix.com
```

### Security Impact

Although not critical, exposed email addresses can:

- Reveal valid usernames
- Assist phishing campaigns
- Support social engineering attacks
- Increase spam exposure

![Vulnerabilities](screenshots/web%20Application%20security/Picture3.jpg)

### Recommendation

- Remove unnecessary email addresses from public pages.
- Use generic contact forms instead of exposing internal email addresses.

---

# Exercise 4 – Burp Suite vs OWASP ZAP

## Burp Suite

### Advantages

- Manual request interception
- Powerful Repeater
- Intruder for fuzzing
- Decoder and Comparer
- Excellent for penetration testing

---

## OWASP ZAP

### Advantages

- Automatic crawling
- Passive vulnerability detection
- Built-in active scanner
- User-friendly interface
- Generates detailed security reports

### Observation

Unlike Burp Suite, OWASP ZAP automatically captured and analyzed website traffic without requiring manual interception, making reconnaissance faster.

---

# Exercise 5 – OWASP ZAP Findings

OWASP ZAP identified **11 vulnerabilities** during the assessment.

### Example Finding

## Missing Anti-CSRF Tokens

### Risk

Cross-Site Request Forgery (CSRF)

![OWASP ZAP](screenshots/web%20Application%20security/Picture4.jpg)

### Impact

Attackers could potentially trick authenticated users into performing unwanted actions without their knowledge.

### Mitigation

- Implement Anti-CSRF tokens.
- Use OWASP CSRFGuard or equivalent protection.
- Prevent Cross-Site Scripting (XSS), which can bypass CSRF protections.

---

# Exercise 6 – Tool Comparison

| Feature | Burp Suite | OWASP ZAP |
|---------|------------|-----------|
| Proxy | ✅ | ✅ |
| Spider | ✅ | ✅ |
| Passive Scan | Limited | ✅ |
| Active Scan | Professional Edition | ✅ |
| Reporting | Good | Excellent |
| Ease of Use | Moderate | Easy |

## Preferred Tool

**OWASP ZAP** was preferred for vulnerability scanning because it:

- Automatically identifies vulnerabilities.
- Produces detailed findings.
- Requires less manual configuration.
- Is beginner-friendly.

Burp Suite remains the preferred choice for manual penetration testing due to its advanced interception, request manipulation, and testing capabilities.

---

# Exercise 7 – Injection Testing

Controlled fuzzing and input validation tests were performed.

### Result

A basic SQL Injection payload successfully triggered the intended vulnerable behavior in the training application.

### Security Impact

SQL Injection can allow attackers to:

- Retrieve sensitive database information.
- Modify application data.
- Bypass authentication mechanisms.
- Execute administrative actions.

![injection ](screenshots/web%20Application%20security/Picture5.jpg)

### Recommended Mitigation

- Use parameterized queries (prepared statements).
- Validate and sanitize user input.
- Implement least-privilege database accounts.
- Conduct regular security testing.

---

# Key Findings

- HTTP request and response headers were successfully analyzed.
- Multiple hidden application resources were discovered.
- Burp Suite detected information disclosure and clickjacking issues.
- OWASP ZAP identified additional web application vulnerabilities.
- SQL Injection testing confirmed the importance of secure input validation.
- Both tools provided valuable insights into the application's security posture.

---

# Skills Demonstrated

- Web Application Security Testing
- Burp Suite Proxy
- HTTP Traffic Analysis
- OWASP ZAP Scanning
- Vulnerability Assessment
- Web Enumeration
- SQL Injection Testing
- Clickjacking Analysis
- HTTP Header Analysis
- Security Reporting

---

# Recommendations

- Remove unnecessary information disclosure from HTTP responses.
- Enforce HTTPS across the application.
- Implement anti-CSRF protections.
- Configure `X-Frame-Options` or `Content-Security-Policy` to prevent clickjacking.
- Use prepared statements to mitigate SQL Injection.
- Perform routine vulnerability assessments using both automated and manual testing techniques.

---

# Conclusion

This lab provided practical experience in web application security assessment using Burp Suite and OWASP ZAP. Through traffic interception, endpoint discovery, vulnerability scanning, and controlled exploitation, I gained hands-on experience in identifying common web application security weaknesses and applying appropriate remediation strategies. These skills are essential for penetration testers, application security engineers, and SOC analysts responsible for securing web-based systems.

---

## 👨‍💻 Author

**Ayilara Busari Dare**

Electrical Engineer | Cybersecurity Analyst | SOC Analyst | Web Application Security Enthusiast
