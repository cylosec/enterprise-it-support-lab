# Active Directory Password Reset Procedure

## Objective

This is a standard process I’d typically follow when helping a user regain access to their account in Active Directory.

Most password reset tickets usually involve:

- Forgotten passwords  
- Locked accounts  
- First-time logins  
- Temporary password resets  
- Remote users unable to authenticate  

The goal is to restore access quickly while still following proper security and verification procedures.

---

# Step 1: Verify the User First

Before resetting anything, always verify the user’s identity.

Depending on the environment, this could include:

- Employee ID  
- Manager confirmation  
- Call-back verification  
- MFA confirmation  
- Existing support ticket approval  

Even for something as simple as a password reset, it’s important not to skip verification steps.

---

# Step 2: Open Active Directory Users and Computers

Usually I’ll open:

```powershell
dsa.msc
```

Or navigate through:

```text
Start Menu → Administrative Tools → Active Directory Users and Computers
```

---

# Step 3: Find the User Account

Search using:

- Username  
- Full name  
- Employee ID  
- Email address (depending on naming standards)

Before making changes, I usually double-check:

- Correct department  
- Correct OU  
- Account status  
- Whether the account is disabled or locked out  

Easy mistake to make in larger environments if names are similar.

---

# Step 4: Reset the Password

Right-click the account → **Reset Password**

Normally I’ll:

- Set a temporary password  
- Require the user to change it at next login  

Typical settings:

```text
☑ User must change password at next logon
☐ User cannot change password
☐ Password never expires
```

I usually avoid touching additional security settings unless there’s a specific reason or approval.

---

# Step 5: Unlock the Account (If Needed)

A lot of tickets are actually lockout issues instead of forgotten passwords.

If the account shows locked:

```text
☑ Unlock account
```

This usually happens after too many failed login attempts, old cached credentials, or expired passwords on mobile devices.

---

# Step 6: If Login Still Fails

Sometimes resetting the password doesn’t fully resolve the issue.

At that point I’d start checking things like:

- VPN connectivity  
- MFA prompts  
- Cached credentials  
- Citrix Workspace sessions  
- RDP session locks  
- DNS/domain communication issues  
- Whether the device is still talking to the domain properly  

A lot of “password issues” end up being authentication or connectivity problems instead.

---

# Step 7: Document Everything

For ticket notes, I try to keep documentation short but clear.

Usually including:

- User verification completed  
- Password reset performed  
- Account unlocked  
- Temporary password delivered securely  
- Additional troubleshooting steps  
- Confirmation user regained access  

Good documentation helps both the next technician and audit/security reviews later.

---

# Example Ticket Note

```text
Verified user identity through manager approval and employee verification.

Reset Active Directory password and required password change at next login.
Unlocked account after multiple failed login attempts.

User confirmed successful login after password update.
Issue resolved.
```

---

# Security Notes

A few things I always avoid:

- Sending passwords through unsecured email  
- Skipping identity verification  
- Disabling password policies unnecessarily  
- Sharing credentials with unauthorized users  

Even simple Service Desk tickets still fall under security responsibility.

---

# Related Issues Often Connected

- MFA problems  
- VPN login failures  
- Citrix login issues  
- Account lockouts  
- Remote user authentication issues  
- Password sync problems in hybrid environments
