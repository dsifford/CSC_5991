# Documentation

## 4.1 Banner Grabbing

![telnet-1]

![telnet-2]

## 4.2 Null Sessions

![null-session-1]

![null-session-2]

## 4.3 NetBIOS Enumeration

![netbios]

## 4.4 SMTP Enumeration

![smtp]

# Vulnerabilities

## Vulnerability 01

### Description

Non-public ports and server information is accessible outside the network. This makes it easy for a hacker to determine which sorts of exploits your server might be vulnerable to.

Additionally, detailed information about shared drives and users on the system can be accessed (user SIDs, etc.).

### Relative Risk (High, Medium, Low)

**Low**

### Mitigation

Mitigation for this vulnerability simply involves adjusting the access settings of the various ports on the system (i.e., use a firewall).

[telnet-1]: assets/telnet-1.png
[telnet-2]: assets/telnet-2.png
[null-session-1]: assets/null-session-1.png
[null-session-2]: assets/null-session-2.png
[netbios]: assets/netbios.png
[smtp]: assets/smtp.png
