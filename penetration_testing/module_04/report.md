# Documentation

## Lab 01: Scanning a Target Using `nmap` Tools 

### `nmap` Simple Scan Results

```
$ nmap 192.168.2.83

Starting Nmap 6.40 ( http://nmap.org ) at 2018-04-04 13:50 EDT
Nmap scan report for 192.168.2.83
Host is up (0.00022s latency).
Not shown: 980 closed ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
593/tcp   open  http-rpc-epmap
1433/tcp  open  ms-sql-s
3306/tcp  open  mysql
3389/tcp  open  ms-wbt-server
5800/tcp  open  vnc-http
5900/tcp  open  vnc
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
49160/tcp open  unknown
49163/tcp open  unknown
49165/tcp open  unknown
MAC Address: 00:50:56:01:24:30 (VMware)

Nmap done: 1 IP address (1 host up) scanned in 6.71 seconds
```

### `nmap` Simple Scan Results (Explicit Port List)

```
$ nmap -p 1-65535 192.168.2.83

Starting Nmap 6.40 ( http://nmap.org ) at 2018-04-04 13:54 EDT
Nmap scan report for 192.168.2.83
Host is up (0.00026s latency).
Not shown: 65509 closed ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
593/tcp   open  http-rpc-epmap
1433/tcp  open  ms-sql-s
3306/tcp  open  mysql
3388/tcp  open  cbserver
3389/tcp  open  ms-wbt-server
5504/tcp  open  unknown
5800/tcp  open  vnc-http
5900/tcp  open  vnc
5985/tcp  open  wsman
47001/tcp open  unknown
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
49160/tcp open  unknown
49163/tcp open  unknown
49164/tcp open  unknown
49165/tcp open  unknown
49174/tcp open  unknown
MAC Address: 00:50:56:01:24:30 (VMware)

Nmap done: 1 IP address (1 host up) scanned in 15.63 seconds
```

### Network Sweep (port 139)

```
$ nmap -p 139 192.168.2.*

Starting Nmap 6.40 ( http://nmap.org ) at 2018-04-04 13:57 EDT
Nmap scan report for 192.168.2.1
Host is up (0.00054s latency).
PORT    STATE    SERVICE
139/tcp filtered netbios-ssn
MAC Address: 00:50:56:01:24:36 (VMware)

Nmap scan report for 192.168.2.81
Host is up (0.00043s latency).
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: 00:50:56:01:24:33 (VMware)

Nmap scan report for 192.168.2.82
Host is up (0.00060s latency).
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: 00:50:56:01:24:31 (VMware)

Nmap scan report for 192.168.2.83
Host is up (0.00049s latency).
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: 00:50:56:01:24:30 (VMware)

Nmap scan report for 192.168.2.84
Host is up (0.00053s latency).
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: 00:50:56:01:24:2E (VMware)

Nmap scan report for 192.168.2.85
Host is up (0.00038s latency).
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: 00:50:56:01:24:32 (VMware)

Nmap scan report for 192.168.2.86
Host is up (0.000036s latency).
PORT    STATE  SERVICE
139/tcp closed netbios-ssn

Nmap done: 256 IP addresses (7 hosts up) scanned in 14.74 seconds
```

### OS Fingerprinting

```
$ nmap -O 192.168.2.*

Starting Nmap 6.40 ( http://nmap.org ) at 2018-04-04 14:01 EDT
Nmap scan report for 192.168.2.1
Host is up (0.00051s latency).
All 1000 scanned ports on 192.168.2.1 are filtered
MAC Address: 00:50:56:01:24:36 (VMware)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.2.81
Host is up (0.00044s latency).
Not shown: 990 closed ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1025/tcp open  NFS-or-IIS
1026/tcp open  LSA-or-nterm
1027/tcp open  IIS
1028/tcp open  unknown
1029/tcp open  ms-lsa
1030/tcp open  iad1
3389/tcp open  ms-wbt-server
MAC Address: 00:50:56:01:24:33 (VMware)
Device type: general purpose
Running: Microsoft Windows 7|2008
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_8
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, or Windows 8
Network Distance: 1 hop

Nmap scan report for 192.168.2.82
Host is up (0.00043s latency).
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
Network Distance: 1 hop

Nmap scan report for 192.168.2.83
Host is up (0.00040s latency).
Not shown: 980 closed ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
593/tcp   open  http-rpc-epmap
1433/tcp  open  ms-sql-s
3306/tcp  open  mysql
3389/tcp  open  ms-wbt-server
5800/tcp  open  vnc-http
5900/tcp  open  vnc
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49157/tcp open  unknown
49158/tcp open  unknown
49160/tcp open  unknown
49163/tcp open  unknown
49165/tcp open  unknown
MAC Address: 00:50:56:01:24:30 (VMware)
Device type: general purpose
Running: Microsoft Windows 7|2012
OS CPE: cpe:/o:microsoft:windows_7:::ultimate cpe:/o:microsoft:windows_2012
OS details: Microsoft Windows 7 or Windows Server 2012
Network Distance: 1 hop

Nmap scan report for 192.168.2.84
Host is up (0.00055s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 00:50:56:01:24:2E (VMware)
No exact OS matches for host (If you know what OS is running on it, see http://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=6.40%E=4%D=4/4%OT=22%CT=1%CU=31523%PV=Y%DS=1%DC=D%G=Y%M=005056%TM
OS:=5AC51312%P=x86_64-unknown-linux-gnu)SEQ(SP=106%GCD=1%ISR=109%TI=Z%CI=I%
OS:II=I%TS=8)OPS(O1=M5B4ST11NW7%O2=M5B4ST11NW7%O3=M5B4NNT11NW7%O4=M5B4ST11N
OS:W7%O5=M5B4ST11NW7%O6=M5B4ST11)WIN(W1=7120%W2=7120%W3=7120%W4=7120%W5=712
OS:0%W6=7120)ECN(R=Y%DF=Y%T=40%W=7210%O=M5B4NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40
OS:%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=
OS:%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%
OS:W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=
OS:)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%
OS:DFI=N%T=40%CD=S)

Network Distance: 1 hop

Nmap scan report for 192.168.2.85
Host is up (0.00018s latency).
Not shown: 977 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
512/tcp  open  exec
513/tcp  open  login
514/tcp  open  shell
1099/tcp open  rmiregistry
1524/tcp open  ingreslock
2049/tcp open  nfs
2121/tcp open  ccproxy-ftp
3306/tcp open  mysql
5432/tcp open  postgresql
5900/tcp open  vnc
6000/tcp open  X11
6667/tcp open  irc
8009/tcp open  ajp13
8180/tcp open  unknown
MAC Address: 00:50:56:01:24:32 (VMware)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.33
Network Distance: 1 hop

Nmap scan report for 192.168.2.86
Host is up (0.000036s latency).
All 1000 scanned ports on 192.168.2.86 are closed
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 256 IP addresses (7 hosts up) scanned in 32.17 seconds
```

### User Enumeration `nmap` Script

```
$ nmap 192.168.2.85 --script smb-enum-users.nse

Starting Nmap 6.40 ( http://nmap.org ) at 2018-04-04 14:04 EDT
Nmap scan report for 192.168.2.85
Host is up (0.00014s latency).
Not shown: 977 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
512/tcp  open  exec
513/tcp  open  login
514/tcp  open  shell
1099/tcp open  rmiregistry
1524/tcp open  ingreslock
2049/tcp open  nfs
2121/tcp open  ccproxy-ftp
3306/tcp open  mysql
5432/tcp open  postgresql
5900/tcp open  vnc
6000/tcp open  X11
6667/tcp open  irc
8009/tcp open  ajp13
8180/tcp open  unknown
MAC Address: 00:50:56:01:24:32 (VMware)

Host script results:
| smb-enum-users: 
|   METASPLOITABLE\backup (RID: 1068)
|     Full name:   backup
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\bin (RID: 1004)
|     Full name:   bin
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\bind (RID: 1210)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\daemon (RID: 1002)
|     Full name:   daemon
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\dhcp (RID: 1202)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\distccd (RID: 1222)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\ftp (RID: 1214)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\games (RID: 1010)
|     Full name:   games
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\gnats (RID: 1082)
|     Full name:   Gnats Bug-Reporting System (admin)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\irc (RID: 1078)
|     Full name:   ircd
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\klog (RID: 1206)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\libuuid (RID: 1200)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\list (RID: 1076)
|     Full name:   Mailing List Manager
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\lp (RID: 1014)
|     Full name:   lp
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\mail (RID: 1016)
|     Full name:   mail
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\man (RID: 1012)
|     Full name:   man
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\msfadmin (RID: 3000)
|     Full name:   msfadmin,,,
|     Flags:       Normal user account
|   METASPLOITABLE\mysql (RID: 1218)
|     Full name:   MySQL Server,,,
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\news (RID: 1018)
|     Full name:   news
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\nobody (RID: 501)
|     Full name:   nobody
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\postfix (RID: 1212)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\postgres (RID: 1216)
|     Full name:   PostgreSQL administrator,,,
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\proftpd (RID: 1226)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\proxy (RID: 1026)
|     Full name:   proxy
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\root (RID: 1000)
|     Full name:   root
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\service (RID: 3004)
|     Full name:   ,,,
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\sshd (RID: 1208)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\sync (RID: 1008)
|     Full name:   sync
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\sys (RID: 1006)
|     Full name:   sys
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\syslog (RID: 1204)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\telnetd (RID: 1224)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\tomcat55 (RID: 1220)
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\user (RID: 3002)
|     Full name:   just a user,111,,
|     Flags:       Normal user account
|   METASPLOITABLE\uucp (RID: 1020)
|     Full name:   uucp
|     Flags:       Account disabled, Normal user account
|   METASPLOITABLE\www-data (RID: 1066)
|     Full name:   www-data
|_    Flags:       Account disabled, Normal user account

Nmap done: 1 IP address (1 host up) scanned in 6.87 seconds
```

## Lab 02: Scanning a Target Using Zenmap Tools

### Zenmap Intense Scan (Windows 2008 Server)

```
Starting Nmap 6.47 ( http://nmap.org ) at 2018-04-04 11:07 Pacific Daylight Time
NSE: Loaded 118 scripts for scanning.
NSE: Script Pre-scanning.
Initiating ARP Ping Scan at 11:07
Scanning 192.168.2.82 [1 port]
Completed ARP Ping Scan at 11:07, 0.05s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:07
Completed Parallel DNS resolution of 1 host. at 11:07, 0.02s elapsed
Initiating SYN Stealth Scan at 11:07
Scanning 192.168.2.82 [1000 ports]
Discovered open port 445/tcp on 192.168.2.82
Discovered open port 53/tcp on 192.168.2.82
Discovered open port 111/tcp on 192.168.2.82
Discovered open port 23/tcp on 192.168.2.82
Discovered open port 5900/tcp on 192.168.2.82
Discovered open port 135/tcp on 192.168.2.82
Discovered open port 1723/tcp on 192.168.2.82
Discovered open port 139/tcp on 192.168.2.82
Discovered open port 80/tcp on 192.168.2.82
Discovered open port 49154/tcp on 192.168.2.82
Discovered open port 49157/tcp on 192.168.2.82
Discovered open port 49175/tcp on 192.168.2.82
Discovered open port 5357/tcp on 192.168.2.82
Discovered open port 1047/tcp on 192.168.2.82
Discovered open port 5800/tcp on 192.168.2.82
Discovered open port 19/tcp on 192.168.2.82
Discovered open port 17/tcp on 192.168.2.82
Discovered open port 9/tcp on 192.168.2.82
Discovered open port 49155/tcp on 192.168.2.82
Discovered open port 49152/tcp on 192.168.2.82
Discovered open port 2049/tcp on 192.168.2.82
Discovered open port 1048/tcp on 192.168.2.82
Discovered open port 49156/tcp on 192.168.2.82
Discovered open port 49153/tcp on 192.168.2.82
Discovered open port 13/tcp on 192.168.2.82
Discovered open port 7/tcp on 192.168.2.82
Discovered open port 1039/tcp on 192.168.2.82
Completed SYN Stealth Scan at 11:07, 1.58s elapsed (1000 total ports)
Initiating Service scan at 11:07
Scanning 27 services on 192.168.2.82
Completed Service scan at 11:10, 131.21s elapsed (27 services on 1 host)
Initiating OS detection (try #1) against 192.168.2.82
NSE: Script scanning 192.168.2.82.
Initiating NSE at 11:10
Completed NSE at 11:11, 73.77s elapsed
Nmap scan report for 192.168.2.82
Host is up (0.0026s latency).
Not shown: 973 closed ports
PORT      STATE SERVICE     VERSION
7/tcp     open  echo
9/tcp     open  discard?
13/tcp    open  daytime     Microsoft Windows USA daytime
17/tcp    open  qotd        Windows qotd (English)
19/tcp    open  chargen
23/tcp    open  telnet      Microsoft Windows XP telnetd
53/tcp    open  domain      Microsoft DNS 6.0.6001
| dns-nsid:
|_  bind.version: Microsoft DNS 6.0.6001 (17714650)
80/tcp    open  http        Microsoft IIS httpd 7.0
| http-methods: OPTIONS TRACE GET HEAD POST
| Potentially risky methods: TRACE
|_See http://nmap.org/nsedoc/scripts/http-methods.html
|_http-title: IIS7
111/tcp   open  rpcbind     2-4 (RPC #100000)
| rpcinfo:
|   program version   port/proto  service
|   100000  2,3,4        111/tcp  rpcbind
|   100000  2,3,4        111/udp  rpcbind
|   100003  2,3         2049/tcp  nfs
|   100003  2,3         2049/udp  nfs
|   100005  1,2,3       1048/tcp  mountd
|   100005  1,2,3       1048/udp  mountd
|   100021  1,2,3,4     1047/tcp  nlockmgr
|   100021  1,2,3,4     1047/udp  nlockmgr
|   100024  1           1039/tcp  status
|_  100024  1           1039/udp  status
135/tcp   open  msrpc       Microsoft Windows RPC
139/tcp   open  netbios-ssn
445/tcp   open  netbios-ssn
1039/tcp  open  status      1 (RPC #100024)
1047/tcp  open  nlockmgr    1-4 (RPC #100021)
1048/tcp  open  mountd      1-3 (RPC #100005)
1723/tcp  open  pptp        Microsoft
2049/tcp  open  nfs         2-3 (RPC #100003)
5357/tcp  open  http        Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-methods: No Allow or Public header in OPTIONS response (status code 503)
|_http-title: Service Unavailable
5800/tcp  open  vnc-http    TightVNC (user: windowssrvr2008; VNC TCP port: 5900)
|_http-title: TightVNC desktop [windowssrvr2008]
5900/tcp  open  vnc         VNC (protocol 3.8)
| vnc-info:
|   Protocol version: 3.8
|   Security types:
|     None (1)
|     Tight (16)
|_  WARNING: Server does not require authentication
49152/tcp open  msrpc       Microsoft Windows RPC
49153/tcp open  msrpc       Microsoft Windows RPC
49154/tcp open  msrpc       Microsoft Windows RPC
49155/tcp open  msrpc       Microsoft Windows RPC
49156/tcp open  msrpc       Microsoft Windows RPC
49157/tcp open  msrpc       Microsoft Windows RPC
49175/tcp open  msrpc       Microsoft Windows RPC
MAC Address: 00:50:56:01:24:31 (VMware)
Device type: general purpose
Running: Microsoft Windows 7|2008
OS CPE: cpe:/o:microsoft:windows_7::- cpe:/o:microsoft:windows_7::sp1 cpe:/o:microsoft:windows_server_2008::sp1 cpe:/o:microsoft:windows_8
OS details: Microsoft Windows 7 SP0 - SP1, Windows Server 2008 SP1, or Windows 8
Uptime guess: 12.004 days (since Fri Mar 23 11:05:40 2018)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=262 (Good luck!)
IP ID Sequence Generation: Incremental
Service Info: OSs: Windows, Windows XP; CPE: cpe:/o:microsoft:windows, cpe:/o:microsoft:windows_xp

Host script results:
| ms-sql-info:
|   Windows server name: WINDOWSSRVR2008
|   [192.168.2.82\SQLEXPRESS]
|     Instance name: SQLEXPRESS
|     Version: Microsoft SQL Server 2008 SP1
|       Version number: 10.00.2531.00
|       Product: Microsoft SQL Server 2008
|       Service pack level: SP1
|       Post-SP patches applied: No
|     TCP port: 49174
|     Named pipe: \\192.168.2.82\pipe\MSSQL$SQLEXPRESS\sql\query
|_    Clustered: No
| nbstat: NetBIOS name: WINDOWSSRVR2008, NetBIOS user: <unknown>, NetBIOS MAC: 00:50:56:01:24:31 (VMware)
| Names:
|   WINDOWSSRVR2008<00>  Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
|_  WINDOWSSRVR2008<20>  Flags: <unique><active>
| smb-os-discovery:
|   OS: Windows Server (R) 2008 Datacenter 6001 Service Pack 1 (Windows Server (R) 2008 Datacenter 6.0)
|   OS CPE: cpe:/o:microsoft:windows_server_2008::sp1
|   Computer name: WindowsSrvr2008
|   NetBIOS computer name: WINDOWSSRVR2008
|   Workgroup: WORKGROUP
|_  System time: 2018-04-04T18:09:57+00:00
| smb-security-mode:
|   Account that was used for smb scripts: guest
|   User-level authentication
|   SMB Security: Challenge/response passwords supported
|_  Message signing disabled (dangerous, but default)
|_smbv2-enabled: Server supports SMBv2 protocol

TRACEROUTE
HOP RTT     ADDRESS
1   2.59 ms 192.168.2.82

NSE: Script Post-scanning.
Read data files from: C:\Program Files\Nmap
OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 210.93 seconds
           Raw packets sent: 1090 (48.658KB) | Rcvd: 1017 (41.466KB)
```

### Zenmap Xmas Tree Scan

```
Starting Nmap 6.47 ( http://nmap.org ) at 2018-04-04 11:27 Pacific Daylight Time
NSE: Loaded 118 scripts for scanning.
NSE: Script Pre-scanning.
Initiating ARP Ping Scan at 11:28
Scanning 192.168.2.82 [1 port]
Completed ARP Ping Scan at 11:28, 0.06s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:28
Completed Parallel DNS resolution of 1 host. at 11:28, 0.01s elapsed
Initiating XMAS Scan at 11:28
Scanning 192.168.2.82 [1000 ports]
Completed XMAS Scan at 11:28, 2.52s elapsed (1000 total ports)
Initiating Service scan at 11:28
Initiating OS detection (try #1) against 192.168.2.82
Retrying OS detection (try #2) against 192.168.2.82
NSE: Script scanning 192.168.2.82.
Initiating NSE at 11:28
Completed NSE at 11:28, 0.00s elapsed
Nmap scan report for 192.168.2.82
Host is up (0.00021s latency).
All 1000 scanned ports on 192.168.2.82 are closed
MAC Address: 00:50:56:01:24:31 (VMware)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.21 ms 192.168.2.82

NSE: Script Post-scanning.
Read data files from: C:\Program Files\Nmap
OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.40 seconds
           Raw packets sent: 1164 (47.736KB) | Rcvd: 1013 (41.632KB)
```

### Zenmap Null Scan

```
Starting Nmap 6.47 ( http://nmap.org ) at 2018-04-04 12:03 Pacific Daylight Time
NSE: Loaded 118 scripts for scanning.
NSE: Script Pre-scanning.
Initiating ARP Ping Scan at 12:03
Scanning 192.168.2.82 [1 port]
Completed ARP Ping Scan at 12:03, 0.05s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 12:03
Completed Parallel DNS resolution of 1 host. at 12:03, 0.01s elapsed
Initiating NULL Scan at 12:03
Scanning 192.168.2.82 [1000 ports]
Increasing send delay for 192.168.2.82 from 0 to 5 due to 60 out of 149 dropped probes since last increase.
Completed NULL Scan at 12:04, 7.35s elapsed (1000 total ports)
Initiating Service scan at 12:04
Initiating OS detection (try #1) against 192.168.2.82
Retrying OS detection (try #2) against 192.168.2.82
NSE: Script scanning 192.168.2.82.
Initiating NSE at 12:04
Completed NSE at 12:04, 0.00s elapsed
Nmap scan report for 192.168.2.82
Host is up (0.000027s latency).
All 1000 scanned ports on 192.168.2.82 are closed
MAC Address: 00:50:56:01:24:31 (VMware)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.03 ms 192.168.2.82

NSE: Script Post-scanning.
Read data files from: C:\Program Files\Nmap
OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.05 seconds
           Raw packets sent: 1128 (46.296KB) | Rcvd: 1013 (41.632KB)
```

## Lab 03: Scanning a Target Using `hping3` Utility

### Single Port Scan

```
$ hping3 -I eth0 192.168.2.82 -p 139
HPING 192.168.2.82 (eth0 192.168.2.82): NO FLAGS are set, 40 headers + 0 data bytes
len=46 ip=192.168.2.82 ttl=128 DF id=7189 sport=139 flags=RA seq=0 win=0 rtt=1.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7190 sport=139 flags=RA seq=1 win=0 rtt=0.7 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7191 sport=139 flags=RA seq=2 win=0 rtt=0.9 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7192 sport=139 flags=RA seq=3 win=0 rtt=0.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7193 sport=139 flags=RA seq=4 win=0 rtt=0.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7194 sport=139 flags=RA seq=5 win=0 rtt=0.7 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7195 sport=139 flags=RA seq=6 win=0 rtt=0.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7196 sport=139 flags=RA seq=7 win=0 rtt=0.7 ms
```

### Enumerated Port Scan

```
$ hping3 -I eth0 192.168.2.82 -p ++130
HPING 192.168.2.82 (eth0 192.168.2.82): NO FLAGS are set, 40 headers + 0 data bytes
len=46 ip=192.168.2.82 ttl=128 DF id=7197 sport=130 flags=RA seq=0 win=0 rtt=1.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7198 sport=131 flags=RA seq=1 win=0 rtt=0.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7199 sport=132 flags=RA seq=2 win=0 rtt=0.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7200 sport=133 flags=RA seq=3 win=0 rtt=0.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7201 sport=134 flags=RA seq=4 win=0 rtt=0.6 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7202 sport=135 flags=RA seq=5 win=0 rtt=0.7 ms
```

### Idle Scan

```
$ hping3 -I eth0 -SA 192.168.2.82
HPING 192.168.2.82 (eth0 192.168.2.82): SA set, 40 headers + 0 data bytes
len=46 ip=192.168.2.82 ttl=128 DF id=7204 sport=0 flags=R seq=0 win=0 rtt=2.0 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7205 sport=0 flags=R seq=1 win=0 rtt=0.7 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7206 sport=0 flags=R seq=2 win=0 rtt=0.7 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7207 sport=0 flags=R seq=3 win=0 rtt=0.7 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7208 sport=0 flags=R seq=4 win=0 rtt=0.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7209 sport=0 flags=R seq=5 win=0 rtt=0.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7210 sport=0 flags=R seq=6 win=0 rtt=0.8 ms
len=46 ip=192.168.2.82 ttl=128 DF id=7211 sport=0 flags=R seq=7 win=0 rtt=0.7 ms
```

# Vulnerabilities

## All ports open on system are open to public

### Description

Currently on the Windows 2008 VM, all ports that are open on the internal system are also open and visible to the entire world. This is a problem because hackers can enumerate the system quickly and, by scanning ports, could obtain information related to what specific services are being used on the machine. 

If any one of these exposed services have a vulnerability, then that presents an attack vector for the hacker.

### Risk

**Impact:** 6/10

**Breach Probability:** 8/10

**Risk Magnitude:** 0.48

### Mitigation

Mitigation for this vulnerability is fairly straightforward and involves simply setting up a firewall so that only machines or systems on the same network can access non-public services.

This will prevent external systems from enumerating and accessing ports on the system that they shouldn't be accessing.
