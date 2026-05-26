# Active Directory Group Membership Management

## Objective

This is the standard process I’d typically follow when managing user group memberships in Active Directory.

Most of these requests usually involve:

- Shared drive access  
- Department transfers  
- VPN access  
- Citrix access  
- Application permissions  
- Printer access  
- Role changes  
- Privileged access requests  

Group management is one of those areas where small mistakes can create major security issues, so I always try to verify access carefully before making changes.

---

# Step 1: Verify the Access Request

Before modifying any permissions, I usually confirm the request has proper approval.

Depending on the environment, this could include:

- Manager approval  
- Department authorization  
- Application owner approval  
- Security approval for elevated access  
- Valid Service Desk ticket documentation  

I never want to add permissions without some kind of authorization trail.

---

# Step 2: Confirm the Required Access

Before touching AD, I normally verify:

- Correct user account  
- What resource they need access to  
- Level of access required  
- Whether the access is temporary or permanent  
- Start/end dates if temporary  
- Existing permissions that might conflict  

I try to avoid adding users into overly broad groups if there’s a more limited access option available.

---

# Step 3: Open Active Directory Users and Computers

Usually I’ll launch:

```powershell
dsa.msc
```

Then locate the user account in ADUC.

---

# Step 4: Review Existing Group Memberships

Right-click the user:

```text
Properties → Member Of
```

I usually review things like:

- Department groups  
- Shared drive access  
- Application access groups  
- VPN groups  
- Citrix delivery groups  
- Printer groups  
- Distribution lists  
- Administrative groups  

This helps avoid duplicate permissions or leftover access from previous roles.

---

# Step 5: Add or Remove Groups

Use:

```text
Add…
```

Or remove outdated memberships when needed.

Common examples:

- Add user to Finance shared drive group  
- Remove old department permissions  
- Add VPN Remote Access group  
- Add Citrix application access  
- Update printer access groups  

I try to avoid assigning highly privileged access unless it’s specifically approved.

---

# Step 6: Validate Access Changes

After updating memberships, I usually confirm:

- AD replication completed  
- User logged out and back in  
- VPN reconnected if needed  
- Citrix session refreshed  
- Outlook restarted if mailbox permissions changed  

A lot of users think the change “didn’t work” when the session just hasn’t refreshed yet.

---

# Step 7: Handle Privileged Access Carefully

Extra caution is usually needed for groups involving:

- Local Administrator access  
- Server administration  
- Domain Admins  
- Security tooling  
- Remote privileged access  
- Application administration  

These changes normally require stronger documentation and security review.

---

# Step 8: Document the Ticket

For documentation, I usually include:

- Approval verified  
- Groups added or removed  
- Type of access granted  
- Temporary vs permanent access  
- Validation completed  
- User confirmed access  
- Final resolution status  

Good documentation helps during audits and future access reviews.

---

# Example Ticket Note

```text
Verified manager approval for Finance shared drive access request.

Added user to Finance_RW security group and removed previous Sales department access group.

Confirmed successful access after user logout/login and VPN reconnect.

Access request completed successfully.
```

---

# Security Notes

A few things I try to avoid:

- Granting access without approval  
- Leaving old permissions active after role changes  
- Adding users to privileged groups casually  
- Ignoring least privilege principles  

Group management is one of the biggest areas tied to identity and access security.

---

# Related Procedures

- New User Provisioning  
- Password Reset Procedure  
- VPN Troubleshooting  
- Citrix Access Support  
- Shared Drive Access Requests  
- Computer Account Management
