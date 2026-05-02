# Active Directory Computer Account Management

## Objective

Provide a standardized process for managing computer accounts in Active Directory to support endpoint lifecycle management, domain security, and enterprise workstation administration.

This procedure supports:

* New workstation deployment
* Domain joining systems
* Moving computers to correct Organizational Units (OUs)
* Disabling stale computer accounts
* Re-enabling disabled devices
* Removing retired endpoints
* Troubleshooting trust relationship failures
* Device replacement workflows

Proper computer account management improves security, policy enforcement, and support efficiency.

---

# Step 1: Verify Request and Asset Information

Before making changes, confirm:

* Approved deployment or decommission request
* Device hostname
* Assigned user
* Department
* Asset tag or inventory ID
* Device type (desktop, laptop, server, VM)
* Replacement or retirement status
* Manager or department approval if required

Never remove or disable endpoints without verification.

---

# Step 2: Open Active Directory Users and Computers

Launch:

```text id="w2h7pn"
Active Directory Users and Computers (ADUC)
```

Or run:

```powershell id="n3x8lk"
dsa.msc
```

Locate the computer account.

Computer objects are often stored in:

```text id="f6y1ma"
Computers
Workstations
Servers
Department-specific OUs
```

depending on organizational structure.

---

# Step 3: Verify Computer Account Status

Check:

* Correct hostname
* Correct OU placement
* Enabled or disabled state
* Last known login activity
* Assigned policies via OU
* Duplicate or stale accounts

Incorrect OU placement often causes Group Policy and login issues.

---

# Step 4: Move Computer to Correct OU

If needed:

Right-click the computer:

```text id="a8z4tr"
Move…
```

Place the device into the correct OU based on:

* Department
* Device type
* Security policy requirements
* Remote access rules
* Administrative controls

OU placement determines policy enforcement and access controls.

---

# Step 5: Disable Stale or Retired Devices

For decommissioned systems:

Right-click:

```text id="p7m1ds"
Disable Account
```

This prevents unauthorized domain access while preserving audit history.

Common reasons:

* Employee termination
* Device replacement
* Hardware retirement
* Lost or stolen equipment

Avoid immediate deletion unless policy requires it.

---

# Step 6: Re-enable Existing Devices

For returning or reimaged systems:

```text id="c5j9vk"
Enable Account
```

Verify:

* Device ownership
* Security compliance
* Correct OU placement
* Updated hostname if needed

Re-enable only after validation.

---

# Step 7: Remove Old Computer Accounts

Only after policy approval:

```text id="e4x2rq"
Delete
```

Usually performed after:

* Confirmed retirement
* Backup verification
* Replacement completed
* Retention period satisfied

Deletion should follow asset lifecycle policy.

---

# Step 8: Troubleshoot Trust Relationship Failures

Common user report:

```text id="g9r5wb"
The trust relationship between this workstation and the primary domain failed
```

Common resolution steps:

* Remove system from domain
* Rejoin domain
* Reset computer account
* Confirm DNS resolution
* Validate domain controller connectivity

This is a frequent Service Desk escalation scenario.

---

# Step 9: Document the Ticket

Record:

* Device verified
* OU changes performed
* Disable/enable/delete action completed
* Domain rejoin completed if required
* Validation successful
* Final resolution status

Proper documentation supports audits and asset tracking.

---

# Example Ticket Note

```text id="t8v3yx"
Verified replacement request for retired Finance workstation FIN-PC-104.

Disabled old computer account and moved replacement device to Finance Workstations OU.

Confirmed successful domain join, Group Policy application, and user login.

Asset transition completed and ticket closed.
```

---

# Security Notes

Never:

* Delete devices without approval
* Leave stale endpoints active indefinitely
* Ignore trust relationship failures
* Place systems in incorrect OUs
* Re-enable devices without validation

Computer accounts are part of identity security.

---

# Related Procedures

* Domain Join Troubleshooting
* New User Creation
* Group Membership Management
* RDP Troubleshooting
* DNS Troubleshooting

---
