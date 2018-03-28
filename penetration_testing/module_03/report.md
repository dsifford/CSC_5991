# Documentation

## Lab 01: Footprinting a Target Using `ping` Utility

### Mile2 `ping` data

#### IP Address: `104.25.227.26`

![ping01]

#### Maximum Frame Size: 1472

![ping02]

#### Analysis

| Reply Address    | Input TTL |         Return TTL |
| ---------------- | --------: | -----------------: |
| `12.123.159.30`  |        10 | Expired in transit |
| `12.122.132.121` |        11 | Expired in transit |
| `173.241.128.29` |        12 | Expired in transit |
| `69.174.23.14`   |        13 | Expired in transit |
| `104.25.227.26`  |        14 |                 53 |
| `104.25.227.26`  |        15 |                 53 |
| `104.25.227.26`  |        16 |                 53 |
| `104.25.227.26`  |        17 |                 53 |
| `104.25.227.26`  |        18 |                 53 |

## Lab 02: Footprinting a Target Using `nslookup` Utility

### `nslookup` Findings

- **DNS Server Name:** 8.8.8.8
- **Non-Authoritative Answer:** `104.25.226.26`, `104.25.227.26`
- **CNAME Alias:** `elinore.ns.cloudflare.com`
- **Canonical Name:** `google-public-dns-a.google.com`
- **MX:** `mile2.com`

## Lab 03: Google Hacking (Google Queries)

![cgi-bin]

![classified]

![config.txt]

## Lab 04: Identifying Vulnerabilities and Information Disclosures in Search Engines using Search Diggity

I was unable to obtain any useful results with Search Diggity because Google was able to detect it every time I tried.

![search]

## Lab 05: People Search Using the Spokeo Online Tool

### Spokeo Findings

**Person:** Richard Schott
**Current Address:** 1460 Oxford Rd, Grosse Pointe, MI
**Relatives:** Kellie Schott, Spencer Schott, Nancy Schott, Jane Schott

# Vulnerabilities

No vulnerabilities discovered in this lab.

[ping01]: assets/ping01.jpeg
[ping02]: assets/ping02.jpeg
[cgi-bin]: assets/cgi-bin.png
[classified]: assets/classified.png
[config.txt]: assets/config.txt.png
[search]: assets/search.png

