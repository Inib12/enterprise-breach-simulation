# TECHNICAL REPORT, ENTERPRISE BREACH SIMULATION
## Overview
This report presents the technical investigation of three simulated cyberattack scenarios conducted using BlueTeamLabs. The objective was to identify attack methods, extract indicators of compromise (IOCs), analyze attacker behavior, and determine key security weaknesses.

## TASK 1: FOLLINA EXPLOIT (CVE-2022-30190)
Attack Summary
The attack involved a malicious Microsoft Word document that exploited the Follina vulnerability. The document referenced external HTML content, which triggered the MSDT protocol and enabled remote code execution without requiring macros.

## Timeline
- Malicious DOCX file delivered to victim
- User opens file in Microsoft Word (WINWORD.EXE)
- Word retrieves external HTML content from remote server
- Remote content triggers ms-msdt protocol
- msdt.exe executes attacker-controlled commands
- PowerShell is launched
- Additional payload execution may occur

## Indicators of Compromise (IOCs)
## File IOCs
- Filename: 05-2022-0438.doc
- SHA-256: 4a24048f81afbe9fb62e7a6a49adbd1faf41f266b5f9feecdceb567aec096784
- SHA-1: 06727ffda60359236a8029e0b3e8a0fd11c23313
- MD5: 52945af1def85b171870b31fa4782e52
## Network / Domain IOCs
-Domain: www.xmlformats.com
## Process / Behavior IOCs
- WINWORD.EXE
- msdt.exe
- rundll32.exe
- powershell.exe
- cmd.exe

## Tools Used
- BlueTeamLabs
- VirusTotal

## Findings
The attack successfully exploited a vulnerability in Microsoft Office that allowed code execution without user interaction such as enabling macros. The use of a trusted system binary (msdt.exe) made detection more difficult.
## Key Weakness:
- Lack of patching and exposure of the MSDT protocol enabled exploitation.
____________________________________________________________________________
## TASK 2: BRUTE FORCE ATTACK
## Attack Summary
The attack involved repeated login attempts targeting the Administrator account. The attacker used automated methods to attempt thousands of password combinations from a single external IP address.

## Timeline
- Attacker connects from IP 113.161.192.227
- Multiple login attempts initiated against Administrator account
- System logs repeated failed login attempts (Event ID 4625)
- Source ports change across attempts, indicating automation
- Total of 3103 failed login attempts recorded
- No successful authentication achieved

## Indicators of Compromise (IOCs)
## Network IOCs
- Attacker IP: 113.161.192.227
- Geolocation: Vietnam
## System IOCs
- Targeted Username: Administrator
- Event ID: 4625 (Audit Failure)
- Total Failed Attempts: 3103

##Tools Used
- BlueTeamLabs
- Windows Event Logs
- Excel
- Texteditor

## Findings
The attacker attempted to gain unauthorized access through brute force techniques. The absence of protective controls allowed a high number of login attempts without restriction.
## Key Weakness:
- No account lockout policy, lack of MFA, and exposed administrative account.
____________________________________________________________________________
## TASK 3: PHISHING ATTACK
## Attack Summary
The attack involved a phishing email impersonating Amazon. The email attempted to trick the user into clicking a malicious link and submitting login credentials.

## Timeline
- Attacker sends phishing email to victim
- Email spoofed to appear as Amazon
- Email contains urgent message about account lock
- User is prompted to click a malicious link
- Link redirects to attacker-controlled resource
- Credentials may be captured if user interacts

## Indicators of Compromise (IOCs)
## Email IOCs
- Sender: amazon@zyevantoby.cn
- Domain: zyevantoby.cn
- Sending IP: 45.156.23.138
- Subject: Your Account has been locked
- Message-ID: 000756bf516d$9bad2034$6e61f7fb$@vinuqou
## URL IOCs
- Fake Amazon logo URL (external resource)
- Facebook profile link: amir.boyka.7

## Tools Used
- BlueTeamLabs
- Cyberchef
- Thunderbird
- Texteditor

## Findings
The phishing attack relied on social engineering techniques, including urgency and brand impersonation, to deceive the user. Weak email filtering allowed the message to reach the victim.
## Key Weakness:
- Lack of phishing awareness and insufficient email security controls.
___________________________________________________________________________
## TASK 4: SHIBA INSIDER
## Attack Summary
The analysis of the insider.pcap file reveals a complete HTTP communication between an internal client (192.168.176.1) and an internal server (192.168.176.145) over a non-standard port (8081). The session begins with a normal TCP three-way handshake, confirming successful connection establishment, after which the client sends an HTTP GET request to access /index.php with parameters such as name=admin. This use of URL parameters suggests possible input manipulation or probing activity, commonly associated with attempts to test or exploit web application vulnerabilities. The server responds with HTTP/1.0 200 OK, indicating that the request was successfully processed, and continues exchanging data in plain text format over unencrypted HTTP, which exposes the communication to potential interception or tampering. The session concludes with a proper connection termination (FIN, ACK), showing no abrupt disruption. Overall, while the traffic flow appears normal at the protocol level, the presence of suspicious URL parameters, use of a non-standard port, and lack of encryption indicate potential reconnaissance or early-stage exploitation activity within the internal network.

## Timeline
## Initial Connection Attempt
- Client (192.168.176.1) sends SYN to server (192.168.176.145:8081)
## Connection Established (TCP Handshake)
- Server responds with SYN-ACK
- Client replies with ACK
## HTTP Request Sent (Potential Attack Begins)
- Client sends: GET /index.php?name=admin&...
## Data Exchange
- Multiple ACK packets exchanged
 - Data transferred over unencrypted HTTP
## Session Termination
- Client and server exchange FIN, ACK
- Connection closed normally.


## Indicators of Compromise (IOCs)
- Source IP Address: 192.168.176.1
- Destination IP Address :192.168.176.145
- Destination Port:8081
- HTTP Method:GET
- Protocol Used: HTTP (unencrypted)
- Response Message: HTTP/1.0 200 OK
- Response Content Type: text/plain
- Full TCP Session Established: SYN → SYN-ACK → ACK
- Normal Session Termination: FIN, ACK

## URL IOCs
- IOC URL: /index.php?name=admin&.

## Tools Used
- BlueTeamLabs
- Cyberchef
- Wireshark
- Texteditor
- Steghide

## Findings
The insider.pcap analysis shows an internal host communicating with a web server over port 8081, where a suspicious HTTP GET request (/index.php?name=admin) indicates possible web application probing or input manipulation. Although the session appears normal at the network level, the use of unencrypted HTTP, non-standard port access, and manipulated URL parameters suggests potential early-stage exploitation activity within the internal network.
## Key Weakness: 
- Web application accepts and processes unsanitized user input via URL parameters over unencrypted HTTP, making it vulnerable to injection attacks and interception.



