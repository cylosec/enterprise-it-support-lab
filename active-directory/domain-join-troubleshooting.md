# Domain Join Troubleshooting

## Objective

Provide a standardized process for diagnosing and resolving domain join failures in Active Directory environments.

This procedure supports:

* New workstation deployment
* Reimaged systems
* Replacement devices
* Trust relationship failures
* DNS-related domain join issues
* Authentication failures during domain enrollment

Successful domain joins are critical for policy enforcement, authentication, and enterprise access control.

---

# Step 1: Verify Basic Requirements

Before joining a machine to the domain, confirm:

* Correct hostname assigned
* Network connectivity available
* Proper DNS server configured
* Reachability to Domain Controller
* Valid domain credentials available
* Time synchronization is correct
* Device is not already joined incorrectly

Most domain join failures begin with DNS or connectivity issues.

---

# Step 2: Confirm DNS Configuration

Run:

```powershell id="7knf4s"
ipconfig /all
```

Verify:

* Preferred DNS points to internal Domain Controller
* Not public DNS like 8.8.8.8 or ISP DNS
* Correct subnet and gateway

Example:

```text id="vw8gk1"
DNS Server: 10.0.0.66
```

Incorrect DNS is the most common cause of join failures.

---

# Step 3: Test Domain Controller Connectivity

Run:

```powershell id="oljlwm"
ping domaincontroller
ping cylosec.local
nslookup cylosec.local
```

Also verify SRV records:

```powershell id="r8m0yb"
nslookup -type=SRV _ldap._tcp.dc._msdcs.cylosec.local
```

Expected result:

* Domain Controller resolves properly
* LDAP service records return correctly

This confirms AD discovery is working.

---

# Step 4: Verify Time Synchronization

Run:

```powershell id="3qj0ze"
w32tm /query /status
```

Large time drift can break Kerberos authentication and prevent domain joins.

Correct if needed:

```powershell id="u5yz6f"
w32tm /resync
```

---

# Step 5: Attempt Domain Join

Navigate:

```text id="l2pw1v"
System Properties → Computer Name → Change
```

Select:

```text id="smk3d9"
Domain
```

Enter:

```text id="z4vy5n"
cylosec.local
```

Use authorized domain credentials.

Example:

```text id="ys7g4q"
Administrator
Domain Admin account
Delegated join account
```

depending on company policy.

---

# Step 6: Common Error Troubleshooting

### Error:

```text id="v0kh6y"
The specified domain either does not exist or could not be contacted
```

Usually caused by:

* DNS misconfiguration
* Firewall blocking communication
* Domain Controller offline
* Network segmentation issues

---

### Error:

```text id="m8r5ns"
Access is denied
```

Usually caused by:

* Insufficient permissions
* Incorrect credentials
* Existing duplicate computer account

---

### Error:

```text id="w3j9az"
The trust relationship between this workstation and the primary domain failed
```

Usually resolved by:

* Removing from domain
* Rejoining domain
* Resetting computer account in AD

---

# Step 7: Verify Computer Object in AD

After successful join:

Open:

```text id="6x0pmt"
Active Directory Users and Computers
```

Confirm:

* Computer object exists
* Correct hostname
* Correct OU placement
* Group Policy applies properly

Move to correct OU if needed.

---

# Step 8: Validate User Login

Test:

* Domain user login
* Group Policy application
* Shared drive access
* Printer mapping
* VPN access
* Citrix access if required

Successful join must include operational validation.

---

# Step 9: Document the Ticket

Record:

* DNS verified
* Connectivity tested
* Domain join completed
* OU placement corrected
* User login validated
* Final resolution status

Documentation improves repeatability and audit readiness.

---

# Example Ticket Note

```text id="e7wc5u"
New Finance workstation unable to join domain due to incorrect public DNS assignment.

Updated DNS to internal Domain Controller (10.0.0.66), verified LDAP SRV records, and completed successful domain join to cylosec.local.

Moved system to Finance Workstations OU and confirmed successful domain user login and Group Policy application.

Issue resolved and deployment completed.
```

---

# Security Notes

Never:

* Use public DNS for internal domain operations
* Join devices without approval
* Leave stale duplicate computer accounts unresolved
* Ignore trust relationship failures

Domain joins directly impact enterprise security posture.

---

# Related Procedures

* Computer Account Management
* DNS Troubleshooting
* DHCP Management
* RDP Troubleshooting
* New User Creation

---
