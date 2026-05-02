# Active Directory Group Membership Management

## Objective

Provide a standardized process for securely managing user group memberships in Active Directory while maintaining least privilege, access control, and audit compliance.

This procedure supports:

* Access requests
* Department transfers
* Role changes
* Shared drive permissions
* Application access provisioning
* VPN and Citrix access
* Printer access groups
* Privileged access approval workflows

Improper group assignments are one of the most common security risks in enterprise environments.

---

# Step 1: Verify Approved Access Request

Before modifying any group membership, confirm there is documented approval.

Required approval may include:

* Manager authorization
* Department owner approval
* Application owner approval
* Security approval for privileged access
* Service desk ticket with proper documentation

Never modify access without approval.

---

# Step 2: Identify Required Access

Confirm:

* User account
* Requested resource
* Required access level
* Temporary or permanent access
* Start and end date (if temporary)
* Existing access conflicts

Avoid adding users to broad groups when a narrower permission set is appropriate.

---

# Step 3: Open Active Directory Users and Computers

Launch:

```text id="2p6w1z"
Active Directory Users and Computers (ADUC)
```

Or run:

```powershell id="w7j2ka"
dsa.msc
```

Locate the affected user account.

---

# Step 4: Review Existing Group Memberships

Right-click user:

```text id="9k4vtx"
Properties → Member Of
```

Review:

* Department groups
* Shared drive access
* Application access groups
* VPN access groups
* Citrix delivery groups
* Printer access groups
* Distribution groups
* Administrative privilege groups

This helps prevent duplicate or conflicting permissions.

---

# Step 5: Add or Remove Groups

Use:

```text id="s8x1md"
Add…
```

or remove outdated memberships when appropriate.

Examples:

* Add to Finance Shared Drive group
* Remove from former department group
* Add VPN Remote Access group
* Add Citrix application access group

Avoid assigning users directly to highly privileged groups.

---

# Step 6: Validate Access Propagation

Confirm:

* Replication completed
* Login refresh completed
* VPN reconnect performed
* Citrix session refreshed
* Outlook restarted if mailbox access changed

Some permissions require session refresh before taking effect.

---

# Step 7: Review Privileged Access Carefully

Special handling required for:

* Local Administrators
* Server access
* Domain Admins
* Application administrators
* Security tooling access
* Remote privileged access

These changes often require security review and stronger documentation.

---

# Step 8: Document the Ticket

Record:

* Approval source verified
* Group added or removed
* Access type granted
* Temporary vs permanent access
* Validation completed
* Final resolution status

Documentation is critical for audits and access reviews.

---

# Example Ticket Note

```text id="m4v2jk"
Verified manager approval for Finance shared drive access.

Added user to Finance_RW security group and removed previous Sales department access group.

Confirmed successful access after user re-login and VPN reconnect.

Access request completed and ticket closed.
```

---

# Security Notes

Never:

* Grant access without approval
* Leave outdated permissions after role changes
* Add users to privileged groups casually
* Ignore least privilege requirements

Access management is one of the most audited areas in IT operations.

---

# Related Procedures

* New User Creation
* Password Reset Procedure
* Computer Account Management
* VPN Access Support
* Citrix Workspace Access Setup

---
