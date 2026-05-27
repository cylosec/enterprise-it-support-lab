# DHCP Management Procedure

## Objective

This is the standard process I’d typically follow when managing or troubleshooting DHCP issues in an enterprise Windows environment.

Most DHCP-related tickets usually involve:

- New workstation connectivity problems  
- IP assignment failures  
- Duplicate IP conflicts  
- Scope exhaustion  
- Incorrect subnet assignments  
- Printer connectivity issues  
- Reservation management  
- Domain join failures  

DHCP issues can affect way more than internet access — they often impact authentication, DNS resolution, printers, VPN access, and domain communication.

---

# Step 1: Identify the Issue

Most users usually report things like:

- “No internet connection”  
- “Limited connectivity”  
- “Printer disappeared”  
- “Can’t connect to internal resources”  
- “IP address conflict detected”  
- “New workstation won’t connect”  
- “Unable to join the domain”  

A lot of the time, the root cause traces back to DHCP assignment problems.

---

# Step 2: Verify Client IP Configuration

First thing I usually check:

```powershell
ipconfig /all
```

What I’m looking for:

- Assigned IP address  
- Subnet mask  
- Default gateway  
- DNS server assignment  
- DHCP enabled status  

Example of a healthy result:

```text
IPv4 Address: 10.x.x.x
Subnet Mask: 255.255.255.0
Default Gateway: 10.x.x.1
DNS Server: 10.x.x.x
DHCP Enabled: Yes
```

Things that immediately stand out as problems:

```text
169.254.x.x (APIPA)
Duplicate IP warnings
Missing gateway
Public DNS inside internal AD environment
```

If I see a 169.254 address, DHCP usually failed completely.

---

# Step 3: Renew the DHCP Lease

Next I’ll usually try renewing the lease.

```powershell
ipconfig /release
ipconfig /renew
```

This forces the workstation to request a fresh lease from the DHCP server.

If renewal still fails, then I start looking deeper into server-side or network issues.

---

# Step 4: Test Network Reachability

Then I’ll test basic connectivity.

```powershell
ping 10.x.x.1
ping DC01
ping yourdomain.local
```

What I’m checking:

- Gateway reachable  
- Domain Controller reachable  
- Internal DNS resolving correctly  

If pinging IPs works but hostnames fail, DNS is usually involved too.

---

# Step 5: Review DHCP Scope on the Server

On the DHCP server side, I’ll usually verify:

- Scope is active  
- Available IP addresses remain  
- Correct subnet configured  
- Exclusions configured properly  
- Reservations assigned correctly  
- Lease duration looks reasonable  

A full DHCP scope can completely prevent new devices from connecting properly.

---

# Step 6: Check for Duplicate IP Addresses

Duplicate IPs can create really inconsistent issues.

Common symptoms:

- Random disconnects  
- Login problems  
- Printer failures  
- VPN instability  
- Intermittent connectivity issues  

Things I usually verify:

- No static IP conflicts  
- Reserved IPs not manually assigned elsewhere  
- Printers and servers using proper reservations  

These are some of the more annoying issues because they can appear random at first.

---

# Step 7: Manage DHCP Reservations

For devices needing consistent IP addresses, I’ll usually use DHCP reservations instead of random static assignments.

Common devices include:

- Printers  
- Servers  
- Network appliances  
- Specialized workstations  

Reservations are normally configured using:

- MAC address  
- Hostname  
- Assigned internal IP  

I generally prefer reservations over manually configured static IPs whenever possible.

---

# Step 8: Validate Business Functionality

After fixing the issue, I’ll usually validate actual business functionality, not just connectivity.

Things I normally test:

- User login works  
- Domain join succeeds  
- Printers reconnect  
- Shared drives resolve correctly  
- VPN access functions properly  
- Citrix Workspace connects successfully  

The network layer might be fixed, but the user still needs their actual workflow restored.

---

# Step 9: Document the Ticket

For documentation, I usually include:

- DHCP issue identified  
- Lease renewed or reservation corrected  
- Scope changes performed  
- Duplicate IP conflict resolved  
- Validation completed  
- Final resolution status  

Good notes help a lot when recurring network issues come back later.

---

# Example Ticket Note

```text
New workstation unable to join domain due to DHCP assignment failure.

System received APIPA address (169.254.x.x) because DHCP scope was exhausted.

Expanded available scope range, renewed DHCP lease, and confirmed proper assignment of internal IP address and DNS settings.

Validated successful domain join to yourdomain.local and confirmed user login.

Issue resolved successfully.
```

---

# Security Notes

A few things I try to avoid:

- Assigning undocumented static IPs  
- Ignoring duplicate IP conflicts  
- Using public DNS in internal AD environments  
- Leaving DHCP scopes unmanaged  

DHCP directly affects authentication, endpoint communication, and overall network reliability.

---

# Related Procedures

- DNS Troubleshooting  
- Domain Join Troubleshooting  
- Computer Account Management  
- Printer Troubleshooting  
- VPN Troubleshooting  
- RDP Troubleshooting
