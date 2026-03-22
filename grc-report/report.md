## GRC REPORT, EXECUTIVE SUMMARY
## Overview
This report evaluates the governance, risk, and compliance (GRC) implications of four simulated cyberattack scenarios: a document-based exploit (Follina), a brute-force attack, a phishing attack, and an insider-related web application attack (Shiba Insider). The objective is to assess business impact, determine risk levels, evaluate compliance obligations, and recommend security controls to strengthen the organization’s security posture.
____________________________________________________________________________
## BUSINESS IMPACT
The identified attacks expose the organization to significant operational and security risks.
## Key Impacts Identified:
- Unauthorized Access: Attackers may gain access to critical systems and accounts
- Data Breach Risk: Exposure of sensitive or personally identifiable information (PII)
- Financial Loss: Potential costs from incident response, downtime, and penalties
- Reputational Damage: Loss of customer trust and brand credibility
- Operational Disruption: Systems may be compromised or rendered unavailable
- Internal Network Exploitation: The insider scenario shows that internal systems can be targeted, increasing risk of lateral movement
- Each attack scenario demonstrates how common vulnerabilities can escalate into major business risks if not properly controlled.
____________________________________________________________________________
## RISK LEVEL
A qualitative risk assessment was conducted based on likelihood and impact.
## Follina Exploit
- Likelihood: High
- Impact: High
- Risk Level: Critical
## BruteForce Attack
- Likelihood: High
- Impact: High
- Risk Level: Critical
## Phishing Attack
- Likelihood: High
- Impact: High
- Risk Level: Critical
## Shiba Insider
- Likelihood: Medium
- Impact: High
- Risk Level: High

## Summary:
- External attacks (phishing, brute force, exploitation) present critical risk
- Internal or insider-based attack presents high risk, especially due to trust within internal networks
____________________________________________________________________________
## COMPLIANCE IMPLICATIONS
The incidents were evaluated against the General Data Protection Regulation.
## Key Considerations:
- Exposure of user credentials through phishing
- Unauthorized access via brute force or exploitation
- Potential interception of unencrypted internal communication
- Risk of data leakage through vulnerable web applications

## Implications:
- These incidents may qualify as reportable data breachesif personal data is involved
- Organizations may be required to report incidents within 72 hours
- Non-compliance may result in:
  - Financial penalties
  - Legal consequences
  - Regulatory sanctions
____________________________________________________________________________
## RECOMMENDED CONTROLS
Based on the identified risks and control failures, the following measures are recommended:
## New Controls
- Implement Multi-Factor Authentication (MFA) across all user accounts
- Deploy secure email gateways with phishing detection capabilities
- Enable Endpoint Detection and Response (EDR) solutions
- Enforce account lockout policies after multiple failed login attempts
- Implement SPF, DKIM, and DMARC to prevent email spoofing
____________________________________________________________________________
## Security Improvements
- Establish a robust patch management process
- Improve network monitoring and traffic analysis
- Enable logging and alerting for abnormal internal activity
- Strengthen web application security testing (e.g., input validation checks)
- Configure firewalls and intrusion detection systems
- Monitor internal communications for suspicious behavior
- Enforce secure configuration of servers and application
____________________________________________________________________________
## Training Needs
- Conduct regular security awareness training for employees
- Run phishing simulation exercises
- Promote awareness of risks from internal threats and misuse of systems
- Educate users on:
  - Identifying suspicious emails
  - Verifying links and sender addresses
  - Safe handling of attachments
____________________________________________________________________________
## CONCLUSION
The analysis of the four attack scenarios demonstrates that both external and internal threats can significantly impact an organization if appropriate controls are not in place.
While external attacks exploit weak authentication and user behavior, the insider scenario highlights the risks associated with unmonitored internal activity and insecure web applications.
Implementing layered security controls, enforcing secure development practices, and strengthening user awareness will significantly reduce the organization’s exposure to cyber threats and improve overall resilience.
