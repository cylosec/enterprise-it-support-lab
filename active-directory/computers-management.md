# Active Directory Computer Account Management

## Objective

This is the standard process I’d typically follow when managing computer accounts in Active Directory.

Most of these tickets usually involve:

- New workstation deployments  
- Domain joins  
- Reimaged systems  
- Replacing old devices  
- OU cleanup  
- Trust relationship failures  
- Retired or stale endpoints  

Proper computer account management helps keep policies organized, improves security, and avoids a lot of weird login or Group Policy issues later.

---

# Step 1: Verify the Request and Device Information

Before making changes, I usually confirm:

- Device hostname  
- Assigned user  
- Department  
- Asset tag or inventory number  
- Whether it’s a replacement or brand-new system  
- Approval from management if required  

Especially when disabling or deleting systems, I never want to touch the wrong endpoint.

---

# Step 2: Open Active Directory Users and Computers

Usually I’ll launch ADUC using:

```powershell
dsa.msc
```

Then locate the computer object.

Depending on the environment, computer accounts might be stored in:

```text
Computers
Workstations
Servers
Department-specific OUs
```

Some environments are organized really well… others definitely are not.

---

# Step 3: Verify the Computer Account

Before changing anything, I usually check:

- Correct hostname  
- Correct OU placement  
- Whether the account is enabled or disabled  
- Last login activity  
- Group Policy placement  
- Duplicate or stale computer accounts  

Incorrect OU placement causes a surprising amount of problems with policies, printers, scripts, and login behavior.

---

# Step 4: Move the Computer to the Correct OU

If needed:

Right-click the computer → **Move**

Then place the system into the correct OU based on:

- Department  
- Device type  
- Security requirements  
- Remote access permissions  
- Administrative policy structure  

OU structure matters more than people realize since it controls policy inheritance and access management.

---

# Step 5: Disable Old or Stale Devices

For retired or replaced systems:

Right-click → **Disable Account**

I usually disable systems first instead of deleting them immediately.

Common reasons:

- Device replacement  
- Employee termination  
- Lost or stolen equipment  
- Hardware retirement  
- Old test systems  

This keeps audit history intact while preventing domain access.

---

# Step 6: Re-enable Existing Devices

If a device was reimaged or brought back into service:

Right-click → **Enable Account**

Before re-enabling, I normally verify:

- Device ownership  
- Security compliance  
- Correct OU placement  
- Updated hostname if applicable  

Good habit to validate everything before putting it back into production.

---

# Step 7: Delete Old Computer Accounts

Only after approval and retention policy checks.

Right-click → **Delete**

Usually this happens after:

- Retirement is confirmed  
- Replacement deployment is completed  
- Backups are verified  
- Retention requirements are satisfied  

Deleting objects too early can create unnecessary headaches later.

---

# Step 8: Troubleshoot Trust Relationship Failures

One of the more common workstation issues:

```text
"The trust relationship between this workstation and the primary domain failed"
```

Typical troubleshooting steps:

- Remove the computer from the domain  
- Rejoin the domain  
- Reset the computer account  
- Verify DNS resolution  
- Confirm domain controller communication  

This comes up pretty often after reimaging systems, snapshot restores, or long offline periods.

---

# Step 9: Document the Ticket

For documentation, I usually include:

- Device verified  
- OU changes completed  
- Account disabled/enabled/deleted  
- Domain rejoin completed if necessary  
- Validation successful  
- User confirmed access  

Clear documentation helps both IT operations and future troubleshooting.

---

# Example Ticket Note

```text
Verified replacement request for retired Finance workstation FIN-PC-104.

Disabled old computer account and moved replacement workstation into the Finance Workstations OU.

Confirmed successful domain join, Group Policy update, and user login verification.

Asset transition completed successfully.
```

---

# Security Notes

A few things I try to avoid:

- Deleting systems too quickly  
- Leaving stale endpoints active indefinitely  
- Ignoring trust relationship errors  
- Placing devices into incorrect OUs  
- Re-enabling systems without validation  

Computer accounts are still part of identity and access security.

---

# Related Procedures

- Domain Join Troubleshooting  
- DNS Troubleshooting  
- Group Policy Troubleshooting  
- RDP Access Issues  
- User Provisioning  
- Endpoint Replacement Procedures
