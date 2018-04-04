# Module 5: Enumeration

## Lab 01: Scanning a Target Using Zenmap Tools

### Zenmap initial scan (w/ OS Detection Enabled)

```
Starting Nmap 6.47 ( http://nmap.org ) at 2018-04-04 12:38 Pacific Daylight Time
Initiating ARP Ping Scan at 12:38
Scanning 192.168.2.82 [1 port]
Completed ARP Ping Scan at 12:38, 0.06s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 12:38
Completed Parallel DNS resolution of 1 host. at 12:38, 0.02s elapsed
Initiating SYN Stealth Scan at 12:38
Scanning 192.168.2.82 [1000 ports]
Discovered open port 23/tcp on 192.168.2.82
Discovered open port 1723/tcp on 192.168.2.82
Discovered open port 5900/tcp on 192.168.2.82
Discovered open port 135/tcp on 192.168.2.82
Discovered open port 53/tcp on 192.168.2.82
Discovered open port 17/tcp on 192.168.2.82
Discovered open port 445/tcp on 192.168.2.82
Discovered open port 80/tcp on 192.168.2.82
Discovered open port 111/tcp on 192.168.2.82
Discovered open port 139/tcp on 192.168.2.82
Discovered open port 5357/tcp on 192.168.2.82
Discovered open port 5800/tcp on 192.168.2.82
Discovered open port 19/tcp on 192.168.2.82
Discovered open port 2049/tcp on 192.168.2.82
Discovered open port 13/tcp on 192.168.2.82
Discovered open port 7/tcp on 192.168.2.82
Discovered open port 49157/tcp on 192.168.2.82
Discovered open port 9/tcp on 192.168.2.82
Discovered open port 1039/tcp on 192.168.2.82
Discovered open port 49153/tcp on 192.168.2.82
Discovered open port 49156/tcp on 192.168.2.82
Discovered open port 49152/tcp on 192.168.2.82
Discovered open port 1047/tcp on 192.168.2.82
Discovered open port 49155/tcp on 192.168.2.82
Discovered open port 49154/tcp on 192.168.2.82
Discovered open port 1048/tcp on 192.168.2.82
Discovered open port 49175/tcp on 192.168.2.82
Completed SYN Stealth Scan at 12:38, 1.79s elapsed (1000 total ports)
Initiating OS detection (try #1) against 192.168.2.82
Nmap scan report for 192.168.2.82
Host is up (0.00s latency).
Not shown: 973 closed ports
PORT      STATE SERVICE
7/tcp     open  echo
9/tcp     open  discard
13/tcp    open  daytime
17/tcp    open  qotd
19/tcp    open  chargen
23/tcp    open  telnet
53/tcp    open  domain
80/tcp    open  http
111/tcp   open  rpcbind
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
1039/tcp  open  sbl
1047/tcp  open  neod1
1048/tcp  open  neod2
1723/tcp  open  pptp
2049/tcp  open  nfs
5357/tcp  open  wsdapi
5800/tcp  open  vnc-http
5900/tcp  open  vnc
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49156/tcp open  unknown
49157/tcp open  unknown
49175/tcp open  unknown
MAC Address: 00:50:56:01:24:31 (VMware)
Device type: general purpose
Running: Microsoft Windows 7|2008
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_8
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, or Windows 8
Uptime guess: 12.064 days (since Fri Mar 23 11:05:39 2018)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=254 (Good luck!)
IP ID Sequence Generation: Incremental

Read data files from: C:\Program Files\Nmap
OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 4.26 seconds
           Raw packets sent: 1084 (48.394KB) | Rcvd: 1017 (41.466KB)
```

### Null Session

```

C:\Users\Administrator>net use \\192.168.2.82\IPC$ "" /u:""
The command completed successfully.


C:\Users\Administrator>net use
New connections will be remembered.


Status       Local     Remote                    Network

-------------------------------------------------------------------------------
OK                     \\192.168.2.82\IPC$       Microsoft Windows Network
The command completed successfully.


```

## Lab 02: Make use of the `telnet` utility to perform banner grabbing

### `telnet` banner grabbing (HTTP GET)

```
$ telnet 192.168.2.82 80
Trying 192.168.2.82...
Connected to 192.168.2.82.
Escape character is '^]'.

GET / HTTP/1.0

HTTP/1.1 200 OK
Content-Type: text/html
Last-Modified: Wed, 18 Sep 2013 18:55:58 GMT
Accept-Ranges: bytes
ETag: "b2c6f1b5a0b4ce1:0"
Server: Microsoft-IIS/7.0
X-Powered-By: ASP.NET
Date: Wed, 04 Apr 2018 19:57:57 GMT
Connection: close
Content-Length: 689

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>IIS7</title>
<style type="text/css">
<!--
body {
	color:#000000;
	background-color:#B3B3B3;
	margin:0;
}

#container {
	margin-left:auto;
	margin-right:auto;
	text-align:center;
	}

a img {
	border:none;
}

-->
</style>
</head>
<body>
<div id="container">
<a href="http://go.microsoft.com/fwlink/?linkid=66138&amp;clcid=0x409"><img src="welcome.png" alt="IIS7" width="571" height="411" /></a>
</div>
</body>
</html>
```

### `telnet` banner grabbing (HTTP HEAD)

```
$ telnet 192.168.2.82 80
Trying 192.168.2.82...
Connected to 192.168.2.82.
Escape character is '^]'.
HEAD / HTTP /1.0

HTTP/1.1 200 OK
Content-Length: 689
Content-Type: text/html
Last-Modified: Wed, 18 Sep 2013 18:55:58 GMT
Accept-Ranges: bytes
ETag: "b2c6f1b5a0b4ce1:0"
Server: Microsoft-IIS/7.0
X-Powered-By: ASP.NET
Date: Wed, 04 Apr 2018 19:56:48 GMT
Connection: close
```

## Lab 03: Enumerating NetBIOS Using the SuperScan Tool

### NetBIOS Enumeration Results

```
NetBIOS information on 192.168.2.82

3 names in table

 WINDOWSSRVR2008 00  UNIQUE  Workstation service name
 WORKGROUP       00  GROUP   Workstation service name
 WINDOWSSRVR2008 20  UNIQUE  Server services name

MAC address 5: 00:50:56:01:24:31

Attempting a NULL session connection on 192.168.2.82

NULL session successful to \\192.168.2.82\IPC$

MAC addresses on 192.168.2.82


Workstation/server type on 192.168.2.82


Users on 192.168.2.82


Groups on 192.168.2.82


RPC endpoints on 192.168.2.82

Entry 0
  Interface:  "12345778-1234-abcd-ef00-0123456789ac" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49157]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 1
  Interface:  "2f5f6521-cb55-1059-b446-00df0bce31db" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\tapsrv]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "Unimodem LRPC Endpoint"
Entry 2
  Interface:  "367abb81-9844-35f1-ad32-98f038001003" ver 2.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49175]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 3
  Interface:  "6b5bdd1e-528c-422c-af8c-a4079be4fe48" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49156]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "Remote Fw APIs"
Entry 4
  Interface:  "12345678-1234-abcd-ef00-0123456789ab" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49156]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "IPSec Policy agent endpoint"
Entry 5
  Interface:  "50abc2a4-574d-40b3-9d66-ee4fd5fba076" ver 5.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49155]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 6
  Interface:  "3473dd4d-2e88-4006-9cba-22570909dd10" ver 5.1
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\wkssvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "WinHttp Auto-Proxy Service"
Entry 7
  Interface:  "3473dd4d-2e88-4006-9cba-22570909dd10" ver 5.1
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\W32TIME_ALT]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "WinHttp Auto-Proxy Service"
Entry 8
  Interface:  "1ff70682-0a51-30e8-076d-740be8cee98b" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 9
  Interface:  "378e52b0-c0a9-11cf-822d-00aa0051e40f" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 10
  Interface:  "86d35949-83c9-4044-b424-db363231fd0c" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 11
  Interface:  "86d35949-83c9-4044-b424-db363231fd0c" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49154]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 12
  Interface:  "a398e520-d59a-4bdd-aa7a-3c1e0303a511" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "IKE/Authip API"
Entry 13
  Interface:  "a398e520-d59a-4bdd-aa7a-3c1e0303a511" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49154]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "IKE/Authip API"
Entry 14
  Interface:  "c9ac6db5-82b7-4e55-ae8a-e464ed7b4277" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "73736573-6f69-656e-6e76-000000000000"
  Annotation: "Impl friendly name"
Entry 15
  Interface:  "c9ac6db5-82b7-4e55-ae8a-e464ed7b4277" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49154]"
  Object Id:  "73736573-6f69-656e-6e76-000000000000"
  Annotation: "Impl friendly name"
Entry 16
  Interface:  "c9ac6db5-82b7-4e55-ae8a-e464ed7b4277" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\srvsvc]"
  Object Id:  "73736573-6f69-656e-6e76-000000000000"
  Annotation: "Impl friendly name"
Entry 17
  Interface:  "30b044a5-a225-43f0-b3a4-e060df91f9c1" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\atsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 18
  Interface:  "30b044a5-a225-43f0-b3a4-e060df91f9c1" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49154]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 19
  Interface:  "30b044a5-a225-43f0-b3a4-e060df91f9c1" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\srvsvc]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 20
  Interface:  "f6beaff7-1e19-4fbb-9f8f-b89e2018337c" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\eventlog]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "Event log TCPIP"
Entry 21
  Interface:  "f6beaff7-1e19-4fbb-9f8f-b89e2018337c" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49153]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "Event log TCPIP"
Entry 22
  Interface:  "3c4728c5-f0ab-448b-bda1-6ce01eb0a6d5" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\eventlog]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "DHCP Client LRPC Endpoint"
Entry 23
  Interface:  "3c4728c5-f0ab-448b-bda1-6ce01eb0a6d5" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49153]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "DHCP Client LRPC Endpoint"
Entry 24
  Interface:  "3c4728c5-f0ab-448b-bda1-6ce01eb0a6d6" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\eventlog]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "DHCPv6 Client LRPC Endpoint"
Entry 25
  Interface:  "3c4728c5-f0ab-448b-bda1-6ce01eb0a6d6" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49153]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: "DHCPv6 Client LRPC Endpoint"
Entry 26
  Interface:  "76f226c3-ec14-4325-8a99-6a46348418af" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\InitShutdown]"
  Object Id:  "b08669ee-8cb5-43a5-a017-84fe00000000"
  Annotation: ""
Entry 27
  Interface:  "d95afe70-a6d5-4259-822e-2c84da1ddb0d" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\InitShutdown]"
  Object Id:  "765294ba-60bc-48b8-92e9-89fd77769d91"
  Annotation: ""
Entry 28
  Interface:  "d95afe70-a6d5-4259-822e-2c84da1ddb0d" ver 1.0
  Binding:    "ncacn_ip_tcp:192.168.2.82[49152]"
  Object Id:  "765294ba-60bc-48b8-92e9-89fd77769d91"
  Annotation: ""
Entry 29
  Interface:  "c9ac6db5-82b7-4e55-ae8a-e464ed7b4277" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\lsass]"
  Object Id:  "00736665-0000-0000-0000-000000000000"
  Annotation: "Impl friendly name"
Entry 30
  Interface:  "c9ac6db5-82b7-4e55-ae8a-e464ed7b4277" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\protected_storage]"
  Object Id:  "00736665-0000-0000-0000-000000000000"
  Annotation: "Impl friendly name"
Entry 31
  Interface:  "12345778-1234-abcd-ef00-0123456789ac" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\pipe\\lsass]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""
Entry 32
  Interface:  "12345778-1234-abcd-ef00-0123456789ac" ver 1.0
  Binding:    "ncacn_np:192.168.2.82[\\PIPE\\protected_storage]"
  Object Id:  "00000000-0000-0000-0000-000000000000"
  Annotation: ""

Password and account policies on 192.168.2.82


Shares on 192.168.2.82


Domains on 192.168.2.82


Remote time of day on 192.168.2.82


Logon sessions on 192.168.2.82


Drives on 192.168.2.82


Trusted Domains on 192.168.2.82


Remote services on 192.168.2.82


Remote registry items on 192.168.2.82



Enumeration complete

```

## Lab 04: Enumerating NetBIOS Using the NetBIOS Enumerator Tool

### Results

![netbios-enum]

## Lab 05: Enumerating the System Using Hyena

**Note:** This lab is nothing more than an advertisement for Hyena. There are no specific learning points. Everything mentioned can be found on their product page on their website. Because of this, I don't find it useful to include screenshots here since they don't differ at all from the ones in the book.

# Vulnerabilities

## System at risk of NetBIOS Enumeration

### Description

The user table of the system is vulnerable to enumeration and the system is potentially vulnerable to a remote user creating a null session backdoor via NetBIOS. This particular issue only affects older versions of Windows (it has since been patched).

### Risk

**Impact:** 9/10

**Breach Probability:** 8/10

**Magnitude:** 0.72

### Mitigation

This is a particularly harmful vulnerability and it is recommended that it is addressed as soon as possible.

The easiest way to fix this is to disable NetBIOS over TCP/IP connections. 

Consult your documentation for specific details as to how to do this.

## System leaks software information in HTTP HEAD requests

### Description

Currently, bad actors could potentially obtain including, but not limited to, the OS, the OS version, the server software, etc. when sending HTTP GET or HEAD requests to your IP at port 80.

This is harmful because the bad actor could then refer to a vulnerability database and find targeted exploits for the software/system.

### Risk

**Impact:** 4/10

**Breach Probability:** 2/10

**Magnitude:** 0.08

### Mitigation

If not using the system as a web server, close port 80 (and all other ports that you don't actively need open).

[netbios-enum]: assets/netbios-enum.png
