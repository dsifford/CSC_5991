# Documentation

## 5.1 Nessus Vulnerability Scanner

**Note:** Nessus is no longer installed on Kali Linux. Skipped...

## 5.2 SAINT Vulnerability Scanner

![saint-1]

![saint-2]

![saint-3]

# Vulnerabilities

## Apache `httpd` Range Header Vulnerability

### Description

A remote hacker could crash the server, disclose certain sensitive information, or execute arbitrary commands.

### Relative Risk (High, Medium, Low)

**Threat Risk:** High

**Cost Risk:** Low (free actually)

### Mitigation

Because this is a bug in the Apache web server, the fix for the bug is in Apache's domain. Apache has since fixed this vulnerability in their software, so the fix on our end is simply updating Apache to a newer release that has the patch applied.

[saint-1]: assets/saint-1.png
[saint-2]: assets/saint-2.png
[saint-3]: assets/saint-3.png
