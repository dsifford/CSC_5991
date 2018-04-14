# Documentation

## Lab 01: User System Monitoring and Surveillance Needs Using Spytech SpyAgent

This exercise walks students through how to get up and running with Spytech
SpyAgent on Windows systems. There are no specific vulnerabilities to log here,
since we are creating the vulnerability for the purpose of example. Because
there is no data to log or track, below I'll quickly review what the lab asks of
students.

After installing the software, students are then told to start and silently run
it briefly to allow it to collect some general tracking info from us on the
system. After that, students then open up and observe the depth of the
information able to be obtained from the software, including keystrokes
separated by process, web activity, emails sent and received, and more.

## Lab 02: Hiding Files Using NTFS Streams

This exercise walks students through how to create a hidden executable embedded
onto another arbitrary file on an NTFS file system.

In this lab, students are directed to `mklink` of an example `backdoor.exe` file
that links to an embedded version of the built-in Calculator application onto a
`readme.txt` file.

There are no specific extraneous vulnerabilities to note here, other than the
fact that this method could be used by bad actors to embed secret malicious
programs into files of any type to then allow them to execute once they obtain
access to the system.

## Lab 03: Find Hidden Files Using ADS Spy

This lab piggybacks off of Lab 04 in that we use ADS Spy to locate the Alternate
Data Stream "backdoor" that we created using the ADS Spy tool.

Using this tool, we do a full scan of all NTFS drive, excluding "safe" system
info streams and, sure enough, our "backdoor" and the associated link shows up
in the results.

There are no specific vulnerabilities to note here.

## Lab 04: Hiding Files Using the Stealth Files Tool

In this lab, we take a look at another way of hiding files within files. This
time, we use the "Stealth Files Tool", which is a tool that encrypts executable
files using a given password and embeds the file content into another file.

After embedding, the person who encrypted the file can then extract the program
using the same password they chose to encrypt it.

In this exercise, we do this to embed the built-in Calculator application to an
arbitrary txt file.

There are no specific vulnerabilities to note here.

## Lab 05: Extracting SAM Hashes Using PWdump7 Tool

In this lab, we quickly use the `PwDump7` utility to dump password hashes for
all users on a Windows 7 system to a text file.

This lab is done in one step. There is nothing of interest to note here, and no
specific vulnerabilities.

## Lab 06: Creating the Rainbow Tables Using Winrtge

In this lab, we use the `Winrtge` application to generate rainbow tables of an
`ntlm` hashed, min-length 4, max-length 9, 4_000_000 chain password set.

The creation of the rainbow tables for this exercise took approximately 35
minutes to complete.

There are no vulnerabilities to note.

## Lab 07: Password Cracking Using RainbowCrack

In this lab, we use `RainbowCrack` to crack the set of user password hashes
obtained in `Lab 05` using the rainbow tables that we generated in `Lab 06`.

After importing the hashes and searching the rainbow tables we generated, the
plain-text passwords were able to be cracked in seconds.

There are no vulnerabilities to note.

# Vulnerabilities

## Lab 01

No vulnerabilities discovered in this lab.

## Lab 02

No vulnerabilities discovered in this lab.

## Lab 03

No vulnerabilities discovered in this lab.

## Lab 04

No vulnerabilities discovered in this lab.

## Lab 05

No vulnerabilities discovered in this lab.

## Lab 06

No vulnerabilities discovered in this lab.

## Lab 07

No vulnerabilities discovered in this lab.
