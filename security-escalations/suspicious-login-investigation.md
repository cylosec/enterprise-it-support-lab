# Suspicious Login Investigation Procedure

## Priority: High (P2)

### Reason

Potential account compromise involving authentication anomalies, possible credential exposure, and elevated business risk if unauthorized access is successful.

---

# Objective

This is the standard process I’d typically follow when investigating suspicious login activity in an enterprise environment.

Most of these investigations usually involve:

- Multiple failed login attempts  
- Unusual login locations  
- VPN authentication anomalies  
- Impossible travel alerts  
- MFA concerns  
- Privileged account activity  
- After-hours administrative logins  
- Wazuh SIEM authentication alerts  

The goal is to quickly determine whether the activity is legitimate, contain potential compromise, and escalate if necessary.

---

# Step 1: Identify the Alert

Suspicious login alerts can come from several places, including:

- Wazuh SIEM alerts  
- VPN authentication logs  
- Microsoft 365 sign-in alerts  
- Domain Controller security logs  
- User-reported lockouts  
- Unexpected MFA push notifications  

Common indicators I usually look for:

- Multiple failed login attempts  
- Successful login from unfamiliar location  
- Administrative access outside business hours  
- Multiple devices attempting authentication  
- Repeated lockout behavior  

Repeated failed logins tied to privileged accounts are something I never ignore.

---

# Step 2: Validate the User

Before assuming compromise, I’ll usually verify:

- User identity  
- Current location  
- Whether the login was expected  
- Recent password changes  
- VPN usage expectations  
- Whether multiple devices are involved  

Typical questions I’d ask:

- “Were you attempting to log in during this timeframe?”  
- “Are you currently traveling or working remotely?”  
- “Did you approve any MFA prompts recently?”  
- “Did you recently change your password?”  

Even successful logins still need validation if the behavior looks unusual.

---

# Step 3: Review Authentication Logs

Next I’ll review available authentication logs and alert data.

Things I normally check:

- Source IP address  
- Timestamp  
- Username  
- Success vs failure attempts  
- Device information  
- Authentication method  
- MFA status  
- VPN source information  

Common log sources include:

- Windows Security Event Logs  
- Wazuh alerts  
- Microsoft 365 sign-in history  
- VPN logs  
- Firewall authentication logs  

I usually focus more on behavior patterns instead of isolated events.

---

# Step 4: Identify Risk Indicators

Higher-risk indicators usually include:

- Unknown external IPs  
- Impossible travel activity  
- Brute-force login behavior  
- Service account abuse  
- Privileged account misuse  
- TOR/VPN provider usage  
- Authentication attempts after termination  
- Multiple failures followed by successful login  

The higher the risk indicators, the faster I’d escalate.

---

# Step 5: Immediate Containment Actions

If compromise risk appears elevated, I’d usually move into containment immediately.

Typical actions:

- Reset password  
- Unlock account if needed  
- Force MFA revalidation  
- Disable account temporarily if necessary  
- Revoke active sessions if available  
- Notify Security Team  
- Preserve logs and evidence  

I’d rather secure the account quickly than wait too long trying to fully analyze the activity first.

---

# Step 6: Escalate if Necessary

I’d escalate immediately for situations involving:

- Confirmed unauthorized access  
- Privileged account exposure  
- Successful compromise indicators  
- Multiple affected accounts  
- Lateral movement concerns  
- Business-critical systems  
- Continued suspicious behavior after password reset  

In security situations, escalating early is usually better than escalating late.

---

# Step 7: Confirm Recovery

Before resolving the incident, I usually verify:

- User access restored securely  
- Password reset successful  
- MFA functioning correctly  
- No ongoing suspicious activity  
- Monitoring continues if needed  

The goal isn’t just restoring access — it’s making sure the account is actually secure afterward.

---

# Step 8: Document the Ticket

For documentation, I normally include:

- Alert source  
- Validation steps  
- Authentication log findings  
- Containment actions performed  
- Escalation path  
- Final resolution status  

Strong documentation becomes important later during audits or incident review.

---

# Example Ticket Note

```text
Wazuh alert triggered for repeated failed VPN login attempts targeting user j.smith.

Verified with user that no login attempts were initiated during the alert timeframe.

Authentication logs identified 17 failed login attempts from unfamiliar external IP address.

Password reset completed, account unlocked, and MFA revalidation enforced.

Escalated to Security Team for source IP investigation and continued monitoring.

No successful compromise confirmed.
Incident resolved successfully.
```

---

# Example Interview Answer

## Question

“How would you handle a suspicious login alert?”

## My Answer

```text
I’d first verify whether the login activity was legitimate by confirming with the user and reviewing authentication logs.

I’d check things like source IP address, login timestamps, MFA status, repeated failures, and whether unusual locations or VPN activity were involved.

If the risk appeared elevated, I’d immediately secure the account, preserve evidence, and escalate to Security if compromise or privileged access exposure was suspected.
```

This type of response usually works well because it demonstrates both Help Desk troubleshooting and security escalation awareness.

---

# Security Notes

A few things I try to avoid:

- Ignoring repeated failed login patterns  
- Assuming successful login automatically means legitimate access  
- Delaying escalation for privileged account alerts  
- Resetting accounts without preserving useful evidence  

Security response needs to balance speed, containment, and proper documentation.

---

# Related Procedures

- Account Lockout Resolution  
- Password Reset Procedure  
- Incident Response Ticket Template  
- Phishing Escalation  
- Wazuh Alert Triage  
- MFA Troubleshooting
