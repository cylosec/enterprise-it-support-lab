# Active Directory Password Reset Procedure

## Objective

Provide a standardized process for securely resetting user passwords in Active Directory while maintaining security, documentation, and user access continuity.

This procedure supports common Service Desk operations for:

* Forgotten passwords
* Account lockouts
* First-time login password resets
* Temporary password assignment
* Credential access restoration

---

# Step 1: Verify User Identity

Before resetting any password, verify the user’s identity using approved internal verification methods.

Examples include:

* Employee ID
* Manager verification
* Registered phone confirmation
* Security verification questions
* Internal ticket approval from supervisor

Never reset passwords without proper verification.

---

# Step 2: Open Active Directory Users and Computers

Launch:

```text id="2ozz8s"
Active Directory Users and Computers (ADUC)
```

Path:

```text id="m5a7kc"
Start Menu → Administrative Tools → Active Directory Users and Computers
```

Or run:

```powershell
dsa.msc
```

---

# Step 3: Locate the User Account

Search for the user by:

* First and last name
* Username
* Employee ID (if naming standards support it)

Verify:

* Correct department
* Correct Organizational Unit (OU)
* Correct manager assignment
* Account status

Confirm you are modifying the correct account.

---

# Step 4: Reset the Password

Right-click the user account:

```text id="rnay5s"
Reset Password
```

Set:

* Temporary password
* Require password change at next logon

Recommended:

```text id="h62gkr"
☑ User must change password at next logon
☐ User cannot change password
☐ Password never expires
```

Avoid disabling security controls unless specifically approved.

---

# Step 5: Unlock Account (If Locked)

Check:

```text id="b65cf7"
Account is locked out
```

If enabled:

```text id="owx0zt"
☑ Unlock account
```

This is commonly required after multiple failed login attempts.

---

# Step 6: Confirm Additional Access Issues

If login still fails after password reset, verify:

* VPN connection
* MFA prompts
* Citrix Workspace session lock
* Cached credential issues
* RDP disconnected sessions
* Domain trust relationship issues

Password reset alone may not resolve the incident.

---

# Step 7: Document the Ticket

Record:

* User verification completed
* Password reset performed
* Account unlocked (if applicable)
* Temporary password provided securely
* Additional troubleshooting performed
* Final resolution status

Good documentation protects both security and audit requirements.

---

# Example Ticket Note

```text id="35ec6n"
User identity verified via manager approval and employee ID.

Reset AD password and required password change at next login.
Unlocked account due to failed login attempt lockout.

Confirmed successful login after password update.
Issue resolved and ticket closed.
```

---

# Security Notes

Never:

* Send passwords through unsecured email
* Share passwords with unauthorized personnel
* Bypass verification steps
* Disable password policies without approval

Always follow least privilege and security policy requirements.

---

# Related Procedures

* Account Lockout Resolution
* New User Creation
* Group Membership Management
* MFA Access Troubleshooting
* Citrix Workspace Login Issues

---
