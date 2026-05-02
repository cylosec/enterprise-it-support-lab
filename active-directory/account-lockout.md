# Active Directory Account Lockout Resolution

## Objective

Provide a standardized process for identifying, troubleshooting, and resolving user account lockouts in Active Directory while maintaining security controls and minimizing business disruption.

This procedure supports common Service Desk scenarios involving:

* Repeated failed login attempts
* Forgotten passwords
* Cached credential failures
* VPN authentication failures
* Citrix Workspace login loops
* Outlook and Microsoft 365 authentication issues
* Remote Desktop login failures

---

# Step 1: Verify User Identity

Before making any account changes, verify the user’s identity using approved internal verification methods.

Examples include:

* Employee ID
* Manager confirmation
* Registered phone verification
* Security verification questions
* Existing approved service ticket

Never unlock accounts without proper verification.

---

# Step 2: Confirm Lockout Symptoms

Common user reports include:

* “My password is correct but I still can’t log in”
* “My account says it is locked”
* “VPN keeps rejecting my login”
* “Citrix keeps looping back to login”
* “Outlook keeps asking for my password”

Determine whether this is a true lockout or a password mismatch.

---

# Step 3: Open Active Directory Users and Computers

Launch:

```text id="q4dsp7"
Active Directory Users and Computers (ADUC)
```

Or run:

```powershell id="8fpvsa"
dsa.msc
```

Locate the affected user account.

---

# Step 4: Check Account Status

Right-click the user account:

```text id="v1jksm"
Properties → Account
```

Look for:

```text id="9x8zmd"
Account is locked out
```

If enabled:

```text id="zhqj0e"
☑ Unlock account
```

Do not unlock repeatedly without identifying the source of the failed logins.

---

# Step 5: Investigate Root Cause

Common causes include:

* Incorrect saved passwords on workstation
* Mobile device mail app using old credentials
* VPN client cached credentials
* Citrix Workspace saved sessions
* RDP disconnected sessions
* Mapped drives using old passwords
* Service accounts using expired credentials
* Password recently changed on one device only

Repeated lockouts usually indicate a credential caching issue.

---

# Step 6: Reset Password if Needed

If the user does not know the correct password or repeated failures continue:

Perform a password reset and require:

```text id="e0jx9t"
☑ User must change password at next logon
```

Then clear all saved credentials on affected systems.

---

# Step 7: Validate Access

Confirm successful login to:

* Windows workstation
* VPN
* Citrix Workspace
* Outlook / Microsoft 365
* Remote Desktop session
* Required business applications

Ensure the issue is fully resolved before closing the ticket.

---

# Step 8: Document the Ticket

Record:

* Identity verification completed
* Account unlock performed
* Password reset performed (if applicable)
* Root cause identified
* Cached credentials cleared
* Successful login confirmed
* Final resolution status

Proper documentation supports compliance and recurring issue tracking.

---

# Example Ticket Note

```text id="7y1cwr"
User identity verified via registered phone confirmation.

AD account found locked due to repeated failed VPN login attempts.
Unlocked account and identified cached credentials in Citrix Workspace.

Password reset performed and user required to change password at next login.

Confirmed successful access to VPN and Outlook.
Issue resolved and ticket closed.
```

---

# Security Notes

Never:

* Unlock accounts without verification
* Ignore repeated lockout patterns
* Disable lockout policies without approval
* Share passwords insecurely

Always investigate the cause, not just the symptom.

---

# Related Procedures

* Password Reset Procedure
* MFA Troubleshooting
* Citrix Workspace Login Issues
* VPN Access Support
* Suspicious Login Investigation

---
