# Active Directory New User Creation Procedure

## Objective

Provide a standardized process for securely creating new user accounts in Active Directory while ensuring proper access control, documentation, and onboarding readiness.

This procedure supports:

* New employee onboarding
* Department transfers requiring new access
* Contractor account provisioning
* Temporary staff onboarding
* Privileged access requests with approval

Proper provisioning reduces security risk and improves first-day productivity.

---

# Step 1: Verify Approved Request

Before creating any account, confirm there is an approved onboarding request.

Required approval may include:

* HR onboarding request
* Manager approval
* Department authorization
* Security approval for privileged access
* Ticket created through approved service desk workflow

Never create accounts without documented authorization.

---

# Step 2: Gather Required Information

Confirm the following:

* Full legal name
* Job title
* Department
* Manager
* Start date
* Username naming standard
* Required applications
* Required security groups
* Required shared mailbox access
* VPN access requirements
* Citrix access requirements
* MFA enrollment requirements

Access should be based on least privilege.

---

# Step 3: Open Active Directory Users and Computers

Launch:

```text id="0lf7dr"
Active Directory Users and Computers (ADUC)
```

Or run:

```powershell id="3wq8np"
dsa.msc
```

Navigate to the correct Organizational Unit (OU).

Example:

```text id="6u7n0x"
Users → Finance → Standard Users
```

Correct OU placement is important for Group Policy and security controls.

---

# Step 4: Create the User Account

Right-click the OU:

```text id="rxn0r2"
New → User
```

Enter:

* First name
* Last name
* Full display name
* Username (logon name)

Follow company naming standards consistently.

Example:

```text id="lz6d3z"
firstname.lastname
flastname
employeeID format
```

depending on organizational policy.

---

# Step 5: Set Initial Password

Configure:

* Temporary password
* Require password change at first login

Recommended:

```text id="yrv8xw"
☑ User must change password at next logon
☐ User cannot change password
☐ Password never expires
```

Avoid exceptions unless specifically approved.

---

# Step 6: Assign Group Memberships

Add the user to required security groups.

Examples:

* Department access groups
* Shared drive permissions
* Distribution groups
* VPN access group
* Citrix application access
* Printer access groups
* Microsoft 365 licensing groups

Never assign Domain Admin or privileged groups without formal approval.

---

# Step 7: Configure Additional Access

Verify setup for:

* Microsoft 365 mailbox
* VPN access
* MFA enrollment
* Citrix Workspace access
* Shared mailbox permissions
* RDP access (if approved)
* Line-of-business applications

Provisioning often extends beyond Active Directory.

---

# Step 8: Validate Account Readiness

Confirm:

* Account is enabled
* Correct OU placement
* Group memberships assigned
* Licensing completed
* Login ready for start date

Prevent first-day access failures whenever possible.

---

# Step 9: Document the Ticket

Record:

* Request approval verified
* User account created
* Temporary password assigned securely
* Groups assigned
* Additional services provisioned
* Manager notified
* Final onboarding completion status

Strong documentation supports audits and compliance.

---

# Example Ticket Note

```text id="pv0prz"
Verified HR onboarding request and manager approval.

Created new AD user account for John Smith in Finance OU.
Assigned standard Finance security groups, VPN access, Microsoft 365 license, and Citrix application access.

Temporary password issued securely with required password change at first login.

Manager notified and onboarding completed successfully.
```

---

# Security Notes

Never:

* Create accounts without approval
* Overprovision access
* Assign privileged access casually
* Reuse old accounts for new employees
* Share passwords insecurely

Always follow least privilege and formal onboarding controls.

---

# Related Procedures

* Password Reset Procedure
* Group Membership Management
* Computer Account Management
* MFA Enrollment Support
* Citrix Workspace Access Setup

---
