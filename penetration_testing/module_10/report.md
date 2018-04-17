# Documentation

## Lab 01: Metasploit Fundamentals

**Metasploitable VM IP:** `192.168.2.85`

This exercise walks us through the most basic and fundamental aspects of the
Metasploit application; specifically, the cli interface.

In this exercise, the lab guide describes very briefly, 3 of the 10 `msfcli`
modes in their most general sense (i.e., what do they do.).

At steps 9 and 11 of the lab, it appears that the folks responsible for writing
the lab guide may have merged together two labs, because the instructions
abruptly change and seem to make no sense with each other. I'm not sure exactly
what they are trying to describe here, or their point.

It appears on step 11, the writers have a `psexec` exploit active, but we were
not given any explanation as to what this is or how we should activate it, so
I'm at a loss here as to what exactly we should be doing here.

In steps 13-18, we take a look at using `generate` to generate bytecode for the
`shell_bind_tcp` exploit. We see that this function generates bytecode that
includes the null byte `\x00`, which supposedly is not accepted by most systems.
The solution to this, we're told, is to use the `generate` command, but this
time specify `-b '\x00'` to exclude this character from the generated code. We
also take a look at selecting a specific encoder using the `-e` flag.

It's now becoming clear that this lab is not really a "lab" in the sense that we
are supposed to follow along and do actions to complete some certain task, but
rather it's just a product manual describing what some of the several dozen
flags do.

We do not use any of the modes or exploit any systems with Metasploit. Thus,
there are no specific vulnerabilities to note.

**Note to the grader:** This has so far been the most unorganized and chaotic
lab we have done this semester. If I'm able to provide any feedback, it would be
to, if nothing else, rewrite this lab.

## Lab 02: Port and Vulnerability Scanning

In this exercise, we look at using Metasploit's built-in port scanning modules
vs standard `nmap` scanning against our target.

We begin by doing a standard port scan against our target IP (in this case
`192.168.2.x`).

```
msf > nmap -v -sV 192.168.2.0/24
```

The results of this command show that the following IP addresses have port 80
open:

```
msf > cat subnet_1.gnmap | grep 80/open | awk '{ print $2 }'

192.168.2.82
192.168.2.83
192.168.2.85
```

**Note:** We do not have the `auxiliary/scanner/portscan/svn` module available,
so we are unable to complete step 5.

Using the `auxiliary/scanner/portscan/tcp` module, with the following options,
we are given the following results:

```
msf auxiliary(tcp) > set INTERFACE eth0
INTERFACE => eth0
msf auxiliary(tcp) > set PORTS 80
PORTS => 80
msf auxiliary(tcp) > set RHOSTS 192.168.2.0/24
RHOSTS => 192.168.2.0/24
msf auxiliary(tcp) > set THREADS 50
THREADS => 50
msf auxiliary(tcp) > run
[...]
192.168.2.82:80 - TCP OPEN
192.168.2.83:80 - TCP OPEN
192.168.2.85:80 - TCP OPEN
[...]
```

Next, we use the SMB scanner module to scan for software versions.

```
msf auxiliary(tcp) > use auxiliary/scanner/smb/smb_version
msf auxiliary(smb_version) > set RHOSTS 192.168.2.81-86
RHOSTS => 192.168.2.81-86
msf auxiliary(smb_version) > set THREADS 20
THREADS => 20
msf auxiliary(smb_version) > run
```

The `run` command returned the following information:

### Hosts

| address        | mac | name | os_name           | os_flavor               | os_sp | purpose | info | comments |
| -------------- | --- | ---- | ----------------- | ----------------------- | ----- | ------- | ---- | -------- |
| `192.168.2.81` |     |      | Microsoft Windows | 7 Professional          | b7600 | client  |      |          |
| `192.168.2.82` |     |      | Microsoft Windows | 2008 Datacenter         | SP1   | server  |      |          |
| `192.168.2.83` |     |      | Microsoft Windows | Server 2012 R2 Standard | b9600 | server  |      |          |
| `192.168.2.84` |     |      | Linux             | Ubuntu                  |       | server  |      |          |
| `192.168.2.85` |     |      | Linux             | Debian                  |       | server  |      |          |
| `192.168.2.86` |     |      | Unknown           |                         |       | device  |      |          |

## Lab 03: Client Side Attack

**Note to Grader:** This lab bases everything on an incorrect premise that we
have some system available over port 80 at `192.168.2.5`. This is incorrect and
completely bricks the entire lab if one were to follow the instructions
verbatim.

In this lab, we use Metasplot's `msfpayload` to generate an executable
"backdoor" program called `backdoor.exe` that we share using an apache server to
our vulnerable windows host.

The lab does not go into detail as to what the backdoor is exploiting, so I can
only guess, based on the command, that it involves exploiting something
involving `reverse_tcp`.

Once the `backdoor.exe` file is downloaded onto the target system, we then run
`exploit` in `msfconsole` which then opens up the backdoor and allows us to
access the target system and see that our faux password file is available to us
from the remote machine.

The specific vulnerability involves social engineering in order for the backdoor
to be installed on the system.

## Lab 04: Armitage

In this lab, we are given a brief introduction to Armitage. This lab is
identical to the lab that we did with Armitage last semester.

In brief, we first scan all systems on our host for vulnerabilities and then,
once the scan is complete, we "Launch" a `usermap_script` attack on our
Metasploitable host to map the user table and give us that information.

This process of running this command is simply a nice GUI frontend for the
metasploit framework. The commands being ran internally are the same commands
that we've ran in Metasplot earlier in these labs.

Once we run the attack, we can then "interact" with the shell on the target
system or view the "exploit" information in tabs in the GUI.

Because we are attacking a highly-vulnerable-on-purpose system, there are no
specific vulnerabilities to note.

# Vulnerabilities

No vulnerabilities discovered in this lab.

This lab showcases several dozen known exploits of a highly vulnerable on
purpose system. So there are no specific vulnerabilities to cover here, other
than to say that the highly vulnerable system should not be used in production.
