# DHCP Management Procedure

## Objective

Provide a standardized process for managing and troubleshooting DHCP (Dynamic Host Configuration Protocol) in enterprise Windows environments.

This procedure supports:

* New workstation network connectivity
* IP address assignment failures
* Duplicate IP troubleshooting
* Scope exhaustion issues
* Incorrect subnet assignments
* Reservation management
* Printer and device network assignments
* Domain onboarding support

DHCP is critical for reliable endpoint connectivity and smooth user access.

---

# Step 1: Identify the Issue

Common user reports include:

* “No internet connection”
* “Limited connectivity”
* “Can’t reach internal resources”
* “Printer disappeared from network”
* “IP address conflict detected”
* “New workstation won’t connect”
* “Unable to join domain”

Many of these issues originate from DHCP assignment failures.

---

# Step 2: Verify Client IP Configuration

Run:

```powershell id="e2h7qp"
ipconfig /all
```

Check:

* IP address assigned
* Subnet mask
* Default gateway
* DNS server assignment
* DHCP Enabled = Yes

Example healthy result:

```text id="9a7vlt"
IPv4 Address: 10.x.x.x
Subnet Mask: 255.255.255.0
Default Gateway: 10.x.x.1
DNS Server: 10.x.x.x
DHCP Enabled: Yes
```

Red flags include:

```text id="w4m8cb"
169.254.x.x (APIPA)
Duplicate IP warning
Missing gateway
Public DNS in internal environment
```

APIPA usually means DHCP assignment failed.

---

# Step 3: Renew DHCP Lease

Run:

```powershell id="g1p4xz"
ipconfig /release
ipconfig /renew
```

This requests a fresh IP lease from the DHCP server.

If renewal fails, continue investigating server-side issues.

---

# Step 4: Test Network Reachability

Run:

```powershell id="j9f2wr"
ping 10.x.x.1
ping DC01
ping yourdomain.local
```

Verify:

* Gateway reachable
* Domain Controller reachable
* Internal DNS resolution functioning

If IP works but hostname fails, DNS may also be involved.

---

# Step 5: Review DHCP Scope (Server Side)

On the DHCP server, verify:

* Scope is active
* Available IP addresses remain
* Correct subnet configured
* Correct exclusions applied
* Reservations properly assigned
* Lease duration appropriate

A full scope prevents new devices from receiving addresses.

---

# Step 6: Check for Duplicate IPs

Symptoms include:

* Intermittent disconnects
* Login failures
* Printer mapping failures
* VPN instability

Verify:

* No static IP conflicts
* Reserved IPs not manually assigned elsewhere
* Printers and servers using correct reservations

Duplicate IPs can create difficult intermittent issues.

---

# Step 7: Manage Reservations (If Needed)

For devices requiring fixed IPs:

Examples:

* Printers
* Servers
* Network appliances
* Specialized workstations

Create DHCP reservations using:

* MAC address
* Device hostname
* Assigned fixed internal IP

Avoid unnecessary static IP assignments when DHCP reservations are preferred.

---

# Step 8: Validate Business Function

After correction, confirm:

* User login works
* Domain join works
* Printers reconnect
* Shared drives resolve
* VPN functions properly
* Citrix Workspace access succeeds

Always validate the business impact, not just the network layer.

---

# Step 9: Document the Ticket

Record:

* DHCP issue identified
* Lease renewed or reservation corrected
* Scope adjustments made
* Duplicate IP resolved
* Validation completed
* Final resolution status

Documentation improves future troubleshooting and recurring issue analysis.

---

# Example Ticket Note

```text id="v5r8xm"
New workstation unable to join domain due to DHCP assignment failure.

System received APIPA address (169.254.x.x) because DHCP scope was exhausted.

Expanded available scope range, renewed lease, and confirmed proper assignment of internal IP and DNS settings.

Validated successful domain join to yourdomain.local and confirmed user login.
Issue resolved and ticket closed.
```

---

# Security Notes

Never:

* Assign random static IPs without documentation
* Ignore duplicate IP conflicts
* Use public DNS in internal AD environments
* Leave DHCP scopes unmanaged

DHCP directly impacts authentication, access, and endpoint security.

---

# Related Procedures

* DNS Troubleshooting
* Domain Join Troubleshooting
* Computer Account Management
* Printer Troubleshooting
* RDP Troubleshooting

---
