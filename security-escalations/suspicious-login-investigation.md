# Suspicious Login Investigation Procedure

## Objective

Provide a standardized process for identifying, documenting, and escalating suspicious login activity in enterprise environments.

This procedure supports:

* Multiple failed login attempts
* Login attempts from unusual locations
* Privileged account access anomalies
* Impossible travel alerts
* VPN authentication anomalies
* MFA bypass concerns
* After-hours administrative access
* Wazuh SIEM authentication alerts

Proper investigation helps prevent account compromise and improves security response.

---

# Step 1: Identify the Alert

Common sources include:

* Wazuh SIEM alerts
* VPN authentication logs
* Microsoft 365 sign-in alerts
* Domain Controller security logs
* User reports of unexpected lockouts
* MFA push notifications not initiated by the user

Common indicators:

* Repeated failed login attempts
* Successful login from unfamiliar location
* Privileged account login outside business hours
* Multiple devices attempting authentication

Never ignore repeated failed logins tied to privileged accounts.

---

# Step 2: Validate the User

Confirm:

* User identity
* Current location
* Whether the login attempt was legitimate
* Whether the user recently changed password
* Whether multiple devices are involved
* VPN usage expectations

Questions to ask:

* “Were you trying to log in during this time?”
* “Are you traveling or working remotely?”
* “Did you approve an MFA request recently?”
* “Did you recently change your password?”

Never assume a successful login is legitimate without validation.

---

# Step 3: Review Authentication Logs

Check:

* Source IP address
* Timestamp
* Username
* Login result (success/failure)
* Device involved
* Authentication method
* MFA status
* VPN source details

Examples:

* Windows Security Event Logs
* Wazuh alert data
* VPN logs
* Microsoft 365 sign-in history
* Firewall authentication logs

Focus on patterns, not single events.

---

# Step 4: Identify Risk Indicators

Examples:

* Unknown external IP
* Geographic impossibility
* Brute-force pattern
* Service account abuse
* Privileged account misuse
* Repeated lockout behavior
* Login from TOR/VPN providers
* Authentication attempts after termination
* Multiple failed attempts followed by success

Higher risk requires faster escalation.

---

# Step 5: Immediate Containment Actions

If risk is elevated:

* Reset password
* Unlock account if needed
* Force MFA revalidation
* Disable account temporarily if necessary
* Revoke active sessions if available
* Notify Security Team
* Preserve logs for investigation

Containment should prioritize preventing compromise first.

Do not wait for full analysis if the account may be compromised.

---

# Step 6: Escalate if Required

Escalate immediately for:

* Confirmed unauthorized access
* Privileged account exposure
* Successful compromise indicators
* Lateral movement concerns
* Multiple affected accounts
* Business-critical systems involved
* Repeated suspicious behavior after password reset

Help Desk should escalate early rather than delay.

---

# Step 7: Confirm Recovery

Verify:

* User access restored securely
* Password reset successful
* MFA functioning properly
* No ongoing suspicious activity
* Monitoring continues if required

Resolution should include prevention, not only restoration.

---

# Step 8: Document the Ticket

Record:

* Alert source
* Validation steps
* Log findings
* Containment actions
* Escalation path
* Final resolution status

Strong documentation is critical for audits and incident review.

---

# Example Ticket Note

```text id="j7p4vm"
Wazuh alert triggered for repeated failed VPN login attempts against user j.smith.

Verified with user that no login attempts were initiated during alert window.
Authentication logs showed 17 failed attempts from unfamiliar external IP.

Password reset completed, account unlocked, and MFA revalidation enforced.

Escalated to Security Team for source IP review and continued monitoring.

No successful compromise confirmed.
Incident resolved.
```

---

# Example Interview Answer

## Question

“How would you handle a suspicious login alert?”

## Strong Answer

```text id="y3v8kn"
I would first validate whether the login was legitimate by confirming with the user and reviewing authentication logs.

I would check source IP, login timestamps, MFA status, and whether there were repeated failures or unusual locations involved.

If risk is elevated, I would reset the password, secure the account, preserve logs, and escalate to Security immediately if compromise or privileged access is involved.
```

This answer performs very well in interviews because it shows both Help Desk judgment and SOC escalation awareness.

---

# Security Notes

Never:

* Ignore repeated failed login patterns
* Assume success means legitimate access
* Delay escalation for privileged account alerts
* Reset passwords without preserving useful evidence

Security response should balance speed, containment, and documentation.

---

# Related Procedures

* Account Lockout Resolution
* Password Reset Procedure
* Incident Response Ticket Template
* Phishing Escalation
* Wazuh Alert Triage

---
