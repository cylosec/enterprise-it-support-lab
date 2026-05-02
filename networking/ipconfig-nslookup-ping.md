# IPConfig, NSLookup, and Ping Troubleshooting Guide

## Objective

Provide a standardized procedure for using the three most common networking commands in Help Desk and Service Desk troubleshooting:

* `ipconfig`
* `nslookup`
* `ping`

These commands are often the first steps used to diagnose:

* Login failures
* Domain join issues
* DNS problems
* VPN access failures
* RDP connectivity issues
* Printer mapping failures
* Internal application access problems
* General network connectivity issues

Strong command-line troubleshooting is a core IT support skill.

---

# Step 1: Check IP Configuration

## Command

```cmd id="x8m4wr"
ipconfig /all
```

## Purpose

Displays:

* IPv4 address
* Subnet mask
* Default gateway
* DNS server
* DHCP status
* MAC address
* Domain membership

This helps confirm whether the system is properly connected to the network.

---

## What to Look For

### Healthy Example

```text id="j2v9pn"
IPv4 Address: 10.x.x.x
Subnet Mask: 255.255.255.0
Default Gateway: 10.x.x.1
DNS Server: 10.x.x.x
DHCP Enabled: Yes
Connection-specific DNS Suffix: yourdomain.local
```

---

### Common Red Flags

```text id="v7p3km"
169.254.x.x
Missing Default Gateway
Public DNS (8.8.8.8 / 1.1.1.1)
DHCP Disabled unexpectedly
Wrong subnet
```

### Meaning

* `169.254.x.x` = DHCP failure (APIPA address)
* Public DNS = often breaks Active Directory functions
* Missing gateway = no route to network resources

---

# Step 2: Test Basic Connectivity

## Command

```cmd id="c4y8lt"
ping hostname
ping 10.x.x.x
```

## Examples

```cmd id="m6q2zd"
ping DC01
ping yourdomain.local
ping 10.x.x.x
```

## Purpose

Tests:

* Host reachability
* Packet loss
* DNS resolution
* Internal network connectivity

---

## What Results Mean

### Success

```text id="n1w7rv"
Reply from 10.x.x.x
```

System is reachable.

---

### Failure

```text id="k8p4xz"
Request timed out
Ping request could not find host
Destination host unreachable
```

Possible causes:

* DNS failure
* Host offline
* Firewall blocking ICMP
* Network segmentation
* VPN disconnected

---

# Step 3: Verify DNS Resolution

## Command

```cmd id="r5t9yb"
nslookup hostname
nslookup yourdomain.local
```

## Examples

```cmd id="f3v8qn"
nslookup DC01
nslookup yourdomain.local
```

## Purpose

Confirms:

* Internal DNS is working
* Correct server name resolution
* Domain Controller discovery
* Accurate hostname-to-IP mapping

---

## What to Look For

### Healthy Example

```text id="u2m6pk"
Server: DC01.yourdomain.local
Address: 10.x.x.x

Name: DC01.yourdomain.local
Address: 10.x.x.x
```

---

### Common Problems

```text id="w9r3lc"
Non-existent domain
Request timed out
Wrong IP returned
Public DNS responding
```

These usually indicate DNS misconfiguration.

---

# Step 4: Verify Active Directory Discovery

## Command

```cmd id="p7x4dm"
nslookup -type=SRV _ldap._tcp.dc._msdcs.yourdomain.local
```

## Purpose

Confirms:

* LDAP service records exist
* Domain Controller is discoverable
* Active Directory services are functioning

This is critical for:

* Domain joins
* User authentication
* Group Policy processing

---

# Step 5: Resolve Common Findings

## If IP is Missing

Run:

```cmd id="g4k9zt"
ipconfig /release
ipconfig /renew
```

This requests a new DHCP lease.

---

## If DNS is Wrong

Verify:

* Internal DNS points to Domain Controller
* Not public DNS like Google DNS

Correct DNS settings before further troubleshooting.

---

## If Ping by IP Works but Hostname Fails

This almost always points to DNS problems.

Investigate:

* DNS server assignment
* DNS registration
* Cached DNS records

Run:

```cmd id="q8n2vb"
ipconfig /flushdns
```

if stale records are suspected.

---

# Step 6: Document the Ticket

Record:

* IP configuration verified
* Connectivity tested
* DNS resolution tested
* Corrective action performed
* Validation completed
* Final resolution status

Good documentation improves repeatability and escalations.

---

# Example Ticket Note

```text id="z3w7pf"
User unable to access shared drives and Outlook.

Found workstation using public DNS instead of internal DNS.
ipconfig /all showed DNS pointing to 8.8.8.8.

Updated DNS to internal server (10.x.x.x), flushed DNS cache, and verified successful name resolution using nslookup.

Confirmed successful login to yourdomain.local resources and restored access.

Issue resolved and ticket closed.
```

---

# Example Interview Answer

## Question

“What commands do you run first for connectivity problems?”

## Strong Answer

```text id="h6v2mq"
I start with ipconfig /all to verify IP address, gateway, DNS, and DHCP status.

Then I use ping to test connectivity and determine whether the issue is network-related or DNS-related.

Finally, I use nslookup to confirm name resolution and verify that internal DNS is functioning properly, especially for domain-related issues.
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
