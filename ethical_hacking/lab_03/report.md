# Documentation

## 3.1 Passive Reconnaissance

Below are all steps pertaining to `nslookup`.

![nslookup]

## 3.2 Google Queries

### Aegon Executive Board Members

#### Alexander R. Wynaendts

* CEO and Chairman of the Executive and Management Boards
* Began at Aegon in 1997
* Appointed to executive board in 2003
* Appointed to CEO in 2007
* Nationality: Dutch

**More Info:** https://www.bloomberg.com/research/stocks/private/person.asp?personId=5318684&privcapId=247906

#### Matt Rider

* CFO and member of the Executive and Management Boards
* Joined Aegon in 2017
* Previously CEO of ING Insurance (2010-2013)
* Nationality: American

### Aegon Headquarters

* Located in The Hague in the Netherlands
* **Address:** AEGONplein 50, 2591 TV Den Haag, Netherlands
* **Telephone:** +31 70 344 3210

### Advanced Google Queries

![password.txt]

![config.txt]

![cgi-bin]

![classified]

## 3.3 Active Reconnaissance

### Windows

![3.3-1]

![3.3-2]

![3.3-3]

### \*nix

![3.3-4]

### Intermediate Lab

![3.3-5]

![3.3-6]

## 3.4 Collection and Analysis with Maltego (Optional)

Skipped...

## 3.5 Look@LAN

Look@LAN is not installed on any of the computers. Skipped...

## 3.6 Zenmap

![zenmap]

## 3.7 Hping3

### Flags

* `-c`: Stop after sending and receiving `count` packets
* `-S`: Sets the `SYN` tcp flag
* `-p`: Sets the destination `port`
* `-2`: Enable UDP mode
* `-F`: Set `FIN` tcp flag

![hping]

Of note: FIN scan did not pick up any open ports on my singular Debian machine, hence the 100% packet loss.

# Vulnerabilities

No vulnerabilities noted in this lab. If these ports were accessible outside of the LAN, then perhaps this could be an issue.

However, since the network is closed, there does not appear to be an issue in terms of bad actors penetrating the system.

[nslookup]: assets/nslookup.png
[password.txt]: assets/password.txt.png
[config.txt]: assets/config.txt.png
[cgi-bin]: assets/cgi-bin.png
[classified]: assets/classified.png
[3.3-1]: assets/3.3-1.png
[3.3-2]: assets/3.3-2.png
[3.3-3]: assets/3.3-3.png
[3.3-4]: assets/3.3-4.png
[3.3-5]: assets/3.3-5.png
[3.3-6]: assets/3.3-6.png
[zenmap]: assets/zenmap.png
[hping]: assets/hping.png
