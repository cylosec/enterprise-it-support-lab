# Core Networking Troubleshooting Commands

## Objective

Provide a standardized quick-reference guide for the most common networking commands used in Help Desk, Service Desk, and IT Support troubleshooting.

This procedure supports:

* Connectivity failures
* DNS resolution issues
* VPN troubleshooting
* Domain join failures
* Printer connectivity issues
* RDP failures
* Internet access problems
* Internal resource access failures

These are often the first commands used during ticket triage.

---

# 1. IP Configuration

## Command

```powershell id="v8x3qw"
ipconfig /all
```

## Purpose

Displays:

* IP address
* Subnet mask
* Default gateway
* DNS server
* DHCP status
* MAC address
* Domain membership

## Common Use

Check for:

* Missing IP address
* APIPA address (169.254.x.x)
* Incorrect DNS server
* Wrong subnet
* Public DNS in internal environment

This is often the first command to run.

---

# 2. Test Connectivity

## Command

```powershell id="y2n7pk"
ping hostname
ping 10.x.x.x
```

## Purpose

Tests:

* Basic network connectivity
* Host reachability
* Packet loss
* DNS resolution

## Common Use

Examples:

```powershell id="q4m8rz"
ping DC01
ping yourdomain.local
ping 10.x.x.x
```

If IP works but hostname fails, DNS is likely the issue.

---

# 3. DNS Resolution

## Command

```powershell id="g7w1lb"
nslookup hostname
nslookup yourdomain.local
```

## Purpose

Verifies:

* Name resolution
* DNS server response
* Correct IP mapping

## Common Use

Check:

* Internal DNS working properly
* Server resolving correctly
* Domain controller discovery

---

# 4. Active Directory SRV Record Check

## Command

```powershell id="h9v4xt"
nslookup -type=SRV _ldap._tcp.dc._msdcs.yourdomain.local
```

## Purpose

Verifies:

* LDAP discovery
* Domain Controller availability
* Active Directory service records

Critical for domain joins and authentication troubleshooting.

---

# 5. Route Verification

## Command

```powershell id="d6p2zm"
tracert hostname
```

## Purpose

Shows:

* Network path
* Routing failures
* Network hops
* Latency bottlenecks

Useful for VPN and remote connectivity issues.

---

# 6. Port Connectivity Test

## Command

```powershell id="c3y8kn"
Test-NetConnection hostname -Port 3389
```

## Purpose

Verifies:

* Specific port availability
* Firewall issues
* RDP connectivity
* Service accessibility

Examples:

* Port 3389 = RDP
* Port 443 = HTTPS
* Port 389 = LDAP

---

# 7. Flush DNS Cache

## Command

```powershell id="m5r7xd"
ipconfig /flushdns
```

## Purpose

Clears:

* Stale cached DNS records

Useful when hostname resolution behaves inconsistently.

---

# 8. Renew DHCP Lease

## Command

```powershell id="p1w4qb"
ipconfig /release
ipconfig /renew
```

## Purpose

Requests:

* New DHCP lease
* Updated IP configuration

Useful for APIPA or DHCP failures.

---

# 9. Active User Sessions

## Command

```powershell id="t8z3cv"
query user
```

## Purpose

Displays:

* Logged-in users
* RDP sessions
* Disconnected sessions

Useful for RDP troubleshooting.

---

# 10. Time Sync Verification

## Command

```powershell id="k7x9mj"
w32tm /query /status
```

## Purpose

Verifies:

* System time
* Kerberos synchronization

Time drift can break domain authentication.

---

# Example Interview Answer

## Question

“What commands do you run first for login or connectivity issues?”

## Strong Answer

```text id="z4p6nk"
I usually start with ipconfig /all to verify IP address, DNS, and DHCP status.

Then I use ping and nslookup to confirm connectivity and DNS resolution.

If RDP is involved, I test port 3389 using Test-NetConnection.

For domain-related issues, I verify LDAP SRV records and time synchronization to rule out Active Directory and Kerberos issues.
```

This answer performs very well in interviews.

---

# Related Procedures

* DNS Troubleshooting
* DHCP Management
* RDP Troubleshooting
* Domain Join Troubleshooting
* Citrix Workspace Troubleshooting

---
