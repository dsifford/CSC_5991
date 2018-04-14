# Documentation

## Lab 01: Take advantage of a misconfigured service.

`nmap` scan of target machine showing `nfs` available on port `2049`

```
$ nmap -p0-65536 192.168.2.85
[...]
2049/tcp  open  nfs
[...]
```

`showmount` is used to list the shared filesystems. Here we see that the root
filesystem is shared.

```
$ showmount -e 192.168.2.85
Export list for 192.168.2.85:
/ *
```

We then mount the root filesystem to a temp directory on our local system and
add our public ssh key to the remote target's `authorized_keys` file so that we
can have root-level ssh access without a password in the future

## Lab 02: Crack Linux passwords using John the Ripper.

In this exercise, we copy over the `/etc/passwd` and `/etc/shadow` file from the
target over to our local system and run John the Ripper to unhash the passwords
for each service.

The following passwords are discovered:

| Service  | Password    |
| -------- | ----------- |
| postgres | `postgres`  |
| msfadmin | `msfadmin`  |
| service  | `service`   |
| sys      | `batman`    |
| klog     | `123456789` |
| user     | `toor`      |

## Lab 03: Backdoors

In this exercise we attempt to locate a backdoor using vulnerable software.

After doing a quick `nmap` port scan of port 21 (FTP), we identify that the
target is using `vsftpd v2.3.4`.

```
$ nmap -A -p 21 192.168.2.85
[...]
PORT    STATE SERVICE VERSION
21/tcp  open  ftp     vsftpd 2.3.4
[...]
```

Looking through www.exploit-db.com, we discover that there is a known
vulnerability, including a Metasploitable module, for this version of the
`vsftpd` software that allows "Backdoor Command Execution". This should suit our
needs nicely.

We then quickly verify that the vulnerability exists using telnet. Confirmed.

Next, we compromise the system using Metasplot and the
`exploit/unix/ftp/vsftpd_234_backdoor` module.

# Vulnerabilities

## Vulnerability (Lab 01)

Root filesystem is being shared publicly over `nfs`

### Description

The metasploitable VM has their root filesystem shared with the public over
`nfs`. This is a potentially catestrophic vulnerability and should be fixed
immediately as it allows anyone to take over the entire system.

### Risk

**Impact:** 10/10

**Probability:** 8/10

**Magnitude:** 0.8

### Mitigation

The mitigation of this risk involves closing the `nfs` port completely from the
public. If a certain directory is meant to be publically available, then that
directory only should be shared.

## Vulnerability (Lab 02)

Use of default passwords for services and weak passwords for users.

### Description

The system uses passwords that are easily guessable and easily cracked using
public password lists. This is a problem because it creates an attack vector for
bad actors to gain access to these services.

### Risk

**Impact:** 8/10

**Probability:** 9/10

**Magnitude:** 0.81

### Mitigation

Change the passwords to something more secure and educate your users about the
use of secure passwords

## Vulnerability (Lab 03)

Located software that has a preinstalled backdoor.

### Description

The `vsftpd 2.3.4` software has a known backdoor compromising the codebase. This
backdoor allows hackers to gain root access to any system that is running the
software. This is an extremely dangerous and critical vulnerability and should
be addressed as soon as possible.


### Risk

**Impact:** 10/10

**Probability:** 9/10

**Magnitude:** 0.9

### Mitigation

To mitigate this vulnerability, install a software update or patch as soon as possible.

