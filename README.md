# OIBSIP_Task7_Nikto_Scanning
Performed vulnerability assessment on a web server using Nikto. Identified security misconfigurations, missing security headers, cookie security issues, and analyzed potential web application vulnerabilities as part of the Oasis Infobyte Cybersecurity Internship

## Objective
To perform vulnerability scanning on a web server using Nikto and identify potential security weaknesses.

## Tools Used
- Nikto
- Linux Terminal

## Steps Performed
1. Installed Nikto on Linux.
2. Selected a target web server for testing.
3. Executed Nikto scan using the target URL.
4. Analyzed the scan results.
5. Identified security misconfigurations and missing security headers.

## ## Findings and Analysis

### Missing Security Header: X-Content-Type-Options

Nikto reported that the security header **X-Content-Type-Options** was missing from the web server response.

**Recommended Value:**
X-Content-Type-Options: nosniff

**Purpose:**
- Prevents MIME-type sniffing by browsers.
- Reduces the risk of executing malicious files with incorrect content types.
- Considered a common web security hardening measure.

**Important Note:**
Merely using compression does not mean the website is vulnerable. Additional conditions must exist for exploitation, therefore this finding is primarily informational.

---

### Missing Security Header: Permissions-Policy

Nikto identified that the **Permissions-Policy** security header was not configured.

**Purpose:**
This header controls browser features such as:
- Camera
- Microphone
- Geolocation

**Impact:**
The absence of this header is not a direct vulnerability, but it weakens browser-level security controls and overall hardening of the application.

---

### Strange HTTP Methods Accepted

Nikto reported that the web server returned a valid response when presented with unexpected or malformed HTTP methods.

**Example:**
FOOBAR / HTTP/1.1

**Potential Concern:**
Some web servers incorrectly handle unsupported HTTP methods, which can occasionally indicate misconfiguration.

**Important Note:**
This finding is often considered informational and may be a false positive. Additional testing and verification are usually required before concluding that a security issue exists.

---

### DEBUG HTTP Verb Response

Nikto reported that the server responded to the HTTP DEBUG method.

**Background:**
Historically, the DEBUG method could expose request details and debugging information under certain server configurations.

**Potential Risk:**
If improperly configured, the server could reveal internal information that may assist an attacker.

**Important Note:**
A response to the DEBUG method does not necessarily mean that the method is enabled or vulnerable. Further investigation is required to determine whether any sensitive information can actually be disclosed.

---

## Conclusion

The Nikto vulnerability assessment identified several security hardening recommendations, including missing security headers and responses to unusual HTTP methods. While none of the findings directly confirm critical vulnerabilities, they highlight areas where server configuration and security controls can be improved. Implementing recommended headers and reviewing server behavior would strengthen the overall security posture of the web application.
