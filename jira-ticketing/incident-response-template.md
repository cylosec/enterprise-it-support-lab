# Incident Response Ticket Template

## Objective

Provide a standardized template for documenting security incidents, escalations, and investigation workflows within Jira Service Management or enterprise ticketing platforms.

This template supports:

* Suspicious login investigations
* Phishing reports
* Malware detection alerts
* Privileged access concerns
* Account compromise investigations
* Endpoint security alerts
* Wazuh SIEM escalations
* Unauthorized access attempts

Strong ticket documentation improves response speed, audit readiness, and escalation quality.

---

# Ticket Type

## Incident

Used for:

* Security events
* Service disruptions
* Potential policy violations
* Access anomalies
* Urgent operational issues

Incidents require investigation, ownership, and resolution tracking.

---

# Required Ticket Fields

## Summary

Short, clear description of the issue.

Example:

```text id="4c4q7v"
Multiple failed login attempts detected for Finance user account
```

---

## Priority

Examples:

* Low
* Medium
* High
* Critical

Priority should reflect business impact and security risk.

---

## Reporter

Who submitted the issue.

Examples:

* End user
* SOC Analyst
* Automated SIEM alert
* Manager
* Security Team

---

## Affected User / Asset

Document:

* Username
* Hostname
* Department
* Device name
* IP address (sanitized if public documentation)
* Server involved if applicable

Example:

```text id="h4y7mz"
User: j.smith
Host: FIN-LAPTOP-22
Department: Finance
```

---

## Description

Detailed explanation of:

* What happened
* When it happened
* How it was detected
* Immediate business impact
* Security relevance

Example:

```text id="y2m9xp"
Wazuh alert triggered for repeated failed VPN login attempts from an unknown external source against user j.smith.

User reported being unable to access Outlook and VPN services.

Potential credential lockout or suspicious access attempt under investigation.
```

---

## Investigation Notes

Document:

* Verification steps
* Log review findings
* SIEM findings
* User validation
* Actions taken
* Escalation decisions

Example:

```text id="n8r5kw"
Reviewed Wazuh authentication logs and confirmed 14 failed login attempts from unfamiliar source IP.

Verified user location and confirmed user was not attempting access during alert window.

Reset password, unlocked account, and escalated to Security for source IP review.
```

---

## Resolution

Document final outcome.

Example:

```text id="f6j3vr"
Password reset completed, account unlocked, and MFA revalidation performed.

Security team reviewed source activity and confirmed failed external access attempt with no successful compromise.

Incident resolved and monitoring continued.
```

---

## Closure Notes

Include:

* User confirmation
* Manager notification if required
* Preventive recommendations
* Lessons learned if applicable

---

# Example Full Ticket Summary

```text id="k7v2qd"
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

Never:

* Close incidents without investigation
* Ignore repeated failed login patterns
* Skip documentation during security events
* Leave privilege escalation concerns unresolved

Good tickets are part of security operations.

---

# Related Procedures

* Password Reset Procedure
* Account Lockout Resolution
* Suspicious Login Investigation
* Phishing Escalation
* Wazuh Alert Triage

---
