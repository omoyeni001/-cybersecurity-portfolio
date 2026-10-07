Authorized Penetration Testing Lab

Prepared by: Omoyeni Odunayo Emmanuel
Assessment Reference: PT-LAB-001
Assessment Date: 24 September 2026
Environment: Authorized Cybersecurity Training Lab

Project Overview

This project documents a controlled penetration testing exercise performed in an authorized cybersecurity laboratory.

The assessment focused on identifying exposed services, discovering vulnerabilities, testing selected weaknesses, and documenting security risks and recommended remediation.

The purpose of the exercise was to develop practical skills in network reconnaissance, service enumeration, web application testing, vulnerability identification, and basic privilege escalation investigation.

Objectives

* Identify active hosts within the laboratory network.
* Enumerate open ports and running services.
* Assess exposed FTP services.
* Identify and assess password hashes.
* Perform web directory and resource enumeration.
* Test file-upload functionality in a controlled environment.
* Perform local system enumeration.
* Identify potential privilege escalation opportunities.
* Document findings and recommend security improvements.

Methodology

The assessment followed this general process:

1. Network Discovery
2. Port and Service Enumeration
3. FTP Assessment
4. Hash Identification and Password Assessment
5. Web Enumeration
6. Web Application Assessment
7. File Upload Testing
8. Controlled Shell Testing
9. Local System Enumeration
10. Privilege Escalation Investigation
11. Evidence Collection
12. Reporting and Recommendations

Tools Used

* Kali Linux
* ARP Scan
* Nmap
* FTP
* Hash-Identifier
* Hashcat
* FFUF
* Netcat
* LinPEAS
* PSPY
* Python HTTP Server

1. Network Discovery

I first identified active systems within the authorized laboratory network using ARP Scan.

sudo su
arp-scan -l

Evidence

2. Port and Service Enumeration

Nmap was used to identify open ports, services, versions, and additional information about the target.

nmap -Pn -A -p- <TARGET_IP>

Evidence

3. FTP Assessment

The FTP service was tested to determine whether anonymous access was permitted.

ftp <TARGET_IP>

Where permitted by the laboratory configuration, anonymous authentication was tested.

Evidence

4. File and Hash Assessment

A file obtained during the authorized FTP assessment was reviewed to determine whether it contained sensitive information.

Hash identification was performed using:

hash-identifier

Password recovery testing was performed in the controlled laboratory environment using Hashcat and an approved wordlist.

hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt

Evidence

5. Web Enumeration

FFUF was used to discover web resources within the authorized target environment.

Example:

ffuf -u http://<TARGET_IP>/FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

Evidence

6. Web Application Assessment

The discovered web application was reviewed as part of the authorized assessment.

Testing focused on understanding the application’s authentication, accessible functionality, and potential security weaknesses.

Evidence

7. File Upload Testing

The application’s file-upload functionality was assessed in the controlled laboratory environment.

The objective was to determine whether uploaded files were properly validated and restricted.

Evidence

8. Controlled Shell Testing

Netcat was used during the controlled laboratory exercise to demonstrate communication with the test environment.

nc -nvlp 1234

Evidence

9. Local Enumeration

LinPEAS was used to collect information about the local system and identify possible security weaknesses.

chmod +x linpeas.sh
./linpeas.sh

Where necessary, the file was transferred to the laboratory target using a temporary Python HTTP server.

python3 -m http.server 80

Evidence

10. Process Monitoring

PSPY was used to monitor processes and identify potentially interesting scheduled or background activities.

Evidence

Key Findings

The assessment identified several security weaknesses within the intentionally vulnerable laboratory environment, including:

* Anonymous FTP access.
* Exposure of a potentially sensitive file through FTP.
* Exposure of a password hash.
* Weak password protection that could be recovered through dictionary testing.
* Discoverable web resources.
* Weaknesses associated with file-upload functionality.
* Potential opportunities for further command-execution testing.
* Local configuration and process information that could support privilege-escalation investigation.

Security Recommendations

Based on the assessment, the following controls are recommended:

1. Disable anonymous FTP access unless there is a documented business requirement.
2. Replace insecure FTP with encrypted file-transfer protocols.
3. Protect sensitive files from unauthorized access.
4. Enforce strong password policies.
5. Use secure password hashing mechanisms.
6. Validate and restrict uploaded files.
7. Apply least-privilege principles.
8. Remove unnecessary services and software.
9. Regularly patch and update systems.
10. Monitor suspicious processes and system activity.

Skills Demonstrated

This project demonstrates practical experience with:

* Network reconnaissance
* Port scanning
* Service enumeration
* FTP security assessment
* Password/hash analysis
* Web enumeration
* File-upload security testing
* Linux enumeration
* Privilege escalation investigation
* Security documentation
* Vulnerability remediation

Disclaimer

This project was performed in an authorized cybersecurity training laboratory using intentionally vulnerable systems.

All testing activities were conducted for educational and security-training purposes. No unauthorized systems were targeted.
