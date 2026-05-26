# Active Directory New User Creation Procedure

## Objective

This is the standard process I’d typically follow when creating new user accounts in Active Directory.

Most onboarding requests usually involve:

- New employee setup  
- Contractor onboarding  
- Department transfers  
- VPN access requests  
- Microsoft 365 provisioning  
- Citrix access setup  
- Shared drive permissions  

The goal is to get users operational on day one while still following proper security and access control procedures.

---

# Step 1: Verify the Request First

Before creating any account, I usually confirm there’s an approved onboarding request.

Depending on the environment, this could include:

- HR onboarding approval  
- Manager authorization  
- Department request  
- Security approval for elevated access  
- Valid Service Desk ticket  

I never want to create accounts without documentation or approval attached to the request.

---

# Step 2: Gather User Information

Before opening AD, I normally verify:

- Full legal name  
- Job title  
- Department  
- Assigned manager  
- Start date  
- Username format  
- Required applications  
- VPN requirements  
- MFA requirements  
- Shared mailbox access  
- Citrix access if applicable  

I try to follow least privilege as much as possible instead of overprovisioning access right away.

---

# Step 3: Open Active Directory Users and Computers

Usually I’ll launch:

```powershell
dsa.msc
```

Then navigate to the correct OU.

Example:

```text
Users → Finance → Standard Users
```

Correct OU placement matters because it affects Group Policy, login scripts, security settings, and overall organization.

---

# Step 4: Create the User Account

Right-click the OU:

```text
New → User
```

Then enter:

- First name  
- Last name  
- Display name  
- Username/logon name  

Depending on the environment, naming standards might look like:

```text
firstname.lastname
flastname
employeeID format
```

Consistency is important in larger environments.

---

# Step 5: Configure the Initial Password

Normally I’ll:

- Set a temporary password  
- Require password change at first login  

Typical settings:

```text
☑ User must change password at next logon
☐ User cannot change password
☐ Password never expires
```

I usually avoid exceptions unless they’re specifically approved.

---

# Step 6: Assign Group Memberships

Next I’ll add the user into the required groups.

Common examples:

- Department access groups  
- Shared drive permissions  
- Distribution lists  
- VPN access groups  
- Citrix application groups  
- Printer access groups  
- Microsoft 365 licensing groups  

I try to avoid assigning elevated privileges unless there’s documented approval.

---

# Step 7: Configure Additional Services

Provisioning usually extends beyond just Active Directory.

I’ll typically verify setup for:

- Microsoft 365 mailbox  
- VPN access  
- MFA enrollment  
- Citrix Workspace access  
- Shared mailbox permissions  
- RDP access if approved  
- Business applications  

A lot of onboarding tickets fail because one small service gets missed.

---

# Step 8: Validate the Account

Before closing the ticket, I usually confirm:

- Account is enabled  
- User is in the correct OU  
- Group memberships are correct  
- Licensing completed successfully  
- Login is ready for start date  

The goal is avoiding first-day login issues whenever possible.

---

# Step 9: Document the Ticket

For documentation, I usually include:

- Approval verified  
- User account created  
- Temporary password delivered securely  
- Groups assigned  
- Additional services configured  
- Manager notified  
- Final onboarding status  

Good documentation helps with audits and future troubleshooting.

---

# Example Ticket Note

```text
Verified HR onboarding request and manager approval.

Created new Active Directory user account for John Smith in Finance OU.

Assigned standard Finance security groups, Microsoft 365 licensing, VPN access, and Citrix application permissions.

Temporary password issued securely with required password change at first login.

Manager notified and onboarding completed successfully.
```

---

# Security Notes

A few things I try to avoid:

- Creating accounts without approval  
- Overprovisioning access  
- Assigning privileged groups casually  
- Reusing old employee accounts  
- Sharing passwords insecurely  

User provisioning directly impacts identity and access security across the environment.

---

# Related Procedures

- Password Reset Procedure  
- Group Membership Management  
- VPN Access Support  
- MFA Enrollment  
- Citrix Workspace Access Setup  
- Computer Account Management
