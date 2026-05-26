# Incident Response Ticket Template

## Objective

This is the standard format I’d typically use when documenting security incidents, escalations, or suspicious activity inside Jira Service Management or similar ticketing platforms.

Most of these tickets usually involve:

- Suspicious login attempts  
- Phishing reports  
- Malware alerts  
- Account lockouts  
- Unauthorized access attempts  
- VPN authentication failures  
- Endpoint security alerts  
- Wazuh SIEM escalations  

Good documentation helps speed up investigations, improves escalation quality, and keeps everything organized for audit and security review purposes.

---

# Ticket Type

## Incident

I’d usually use an Incident ticket for:

- Security events  
- Service disruptions  
- Access anomalies  
- Potential policy violations  
- Urgent operational issues  

These types of tickets normally require investigation, ownership, and proper resolution tracking.

---

# Required Ticket Fields

## Summary

Keep it short and clear.

Example:

```text
Multiple failed login attempts detected for Finance user account
```

---

## Priority

Typical priorities:

- Low  
- Medium  
- High  
- Critical  

I usually base priority on:

- Business impact  
- Security risk  
- User impact  
- Potential exposure  

---

## Reporter

Who submitted or generated the alert.

Examples:

- End user  
- SOC Analyst  
- Automated SIEM alert  
- Security Team  
- Manager  

---

## Affected User / Asset

I normally document:

- Username  
- Hostname  
- Department  
- Device name  
- IP address (sanitized if needed)  
- Server or application involved  

Example:

```text
User: j.smith
Host: FIN-LAPTOP-22
Department: Finance
```

---

## Description

This section explains:

- What happened  
- When it happened  
- How it was detected  
- Business impact  
- Why it matters from a security standpoint  

Example:

```text
Wazuh alert triggered for repeated failed VPN login attempts from an unknown external source targeting user j.smith.

User reported being unable to access Outlook and VPN services.

Potential credential lockout or suspicious authentication activity under investigation.
```

---

## Investigation Notes

This is usually where I document:

- Validation steps  
- Log review findings  
- SIEM activity  
- User verification  
- Actions taken  
- Escalation decisions  

Example:

```text
Reviewed Wazuh authentication logs and identified 14 failed login attempts from unfamiliar external source IP.

Verified user location and confirmed the user was not attempting access during the alert timeframe.

Reset password, unlocked account, and escalated source IP activity to Security team for further review.
```

---

## Resolution

This section explains the final outcome.

Example:

```text
Password reset completed, account unlocked, and MFA revalidation performed.

Security team reviewed source activity and confirmed failed external access attempts with no successful compromise identified.

Incident resolved and monitoring continued.
```

---

## Closure Notes

Before closing the ticket, I usually include:

- User confirmation  
- Manager notification if needed  
- Preventive recommendations  
- Lessons learned if applicable  

Helps keep the incident fully documented for future review.

---

# Example Full Ticket Summary

```text
Priority: High

Summary:
Repeated failed VPN login attempts for Finance user

Affected User:
j.smith

Description:
User account locked after repeated failed login attempts detected through Wazuh alerting.

Investigation:
Confirmed failed external login attempts from unknown IP source.
Password reset completed.
Account unlocked.
MFA verified.

Resolution:
No successful compromise identified.
Access restored.
Security monitoring continued.

Status:
Resolved
```

---

# Security Notes

A few things I try to avoid:

- Closing incidents too quickly  
- Ignoring repeated failed login activity  
- Skipping documentation during investigations  
- Leaving privilege escalation concerns unresolved  

Good ticket documentation is part of good security operations.

---

# Related Procedures

- Password Reset Procedure  
- Account Lockout Resolution  
- Suspicious Login Investigation  
- Phishing Escalation  
- Wazuh Alert Triage  
- VPN Authentication Troubleshooting
