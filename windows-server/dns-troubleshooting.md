# DNS Troubleshooting Procedure

## Objective

This is the standard process I’d typically follow when troubleshooting DNS-related issues in an enterprise Windows environment.

Most DNS problems usually show up as:

- Unable to reach internal resources  
- Domain join failures  
- Login/authentication issues  
- VPN connectivity problems  
- Printer mapping failures  
- RDP connection issues  
- Slow network access  
- “Server not found” errors  

A lot of people think “internet issue,” but many times the real problem is DNS.

---

# Step 1: Identify the Symptoms

Common user reports usually include:

- “I can’t access internal websites”  
- “VPN connects but nothing works”  
- “I can ping IPs but not hostnames”  
- “Printer disappeared”  
- “Unable to join the domain”  
- “Outlook won’t connect”  
- “RDP can’t find the server”  

One of the biggest clues is when connectivity works by IP address but fails by hostname.

---

# Step 2: Verify Local IP and DNS Configuration

First thing I usually check:

```powershell
ipconfig /all
```

What I’m looking for:

- Correct IP assignment  
- Default gateway  
- Internal DNS server assignment  
- DHCP enabled status  
- Domain suffix  

Example healthy result:

```text
IPv4 Address: 10.x.x.x
DNS Server: 10.x.x.x
Domain: yourdomain.local
DHCP Enabled: Yes
```

Things that usually stand out as problems:

```text
169.254.x.x
Public DNS servers internally
Missing DNS suffix
Incorrect gateway
```

Public DNS inside an Active Directory environment causes a lot of authentication issues.

---

# Step 3: Test Basic Connectivity

Before blaming DNS completely, I usually verify network reachability first.

```powershell
ping 10.x.x.1
ping DC01
ping yourdomain.local
```

What I’m checking:

- Gateway reachable  
- Domain Controller reachable  
- Hostname resolution functioning  

If pinging the IP works but hostname fails, DNS becomes the likely issue.

---

# Step 4: Verify DNS Resolution

Next I’ll normally test name resolution directly.

```powershell
nslookup DC01
nslookup yourdomain.local
```

For Active Directory environments, I’ll also verify SRV records:

```powershell
nslookup -type=SRV _ldap._tcp.dc._msdcs.yourdomain.local
```

Expected result:

```text
SRV service location:
priority = 0
weight = 100
port = 389
svr hostname = DC01.yourdomain.local
```

If SRV records fail, clients usually can’t properly locate Domain Controllers.

---

# Step 5: Flush and Re-register DNS

If the workstation has stale or incorrect records, I’ll usually refresh DNS registration.

```powershell
ipconfig /flushdns
ipconfig /registerdns
```

On servers or Domain Controllers, I may also restart Netlogon:

```powershell
net stop netlogon
net start netlogon
```

This republishes important AD-related DNS records.

---

# Step 6: Review DNS Records on the Server

On the DNS server side, I’ll usually verify:

- Correct A records exist  
- No stale or duplicate entries  
- Reverse lookup zones configured  
- PTR records functioning  
- Dynamic updates configured properly  

Duplicate or stale records can create inconsistent authentication and connectivity issues.

---

# Step 7: Verify Reverse Lookup Configuration

If I see something like:

```text
Server: UnKnown
```

during `nslookup`, that usually points toward missing reverse lookup or PTR records.

Things I normally verify:

- Reverse lookup zone exists  
- PTR records created correctly  
- Dynamic updates enabled  
- Correct subnet associated with the reverse zone  

Reverse lookup problems can sometimes affect authentication and logging visibility.

---

# Step 8: Validate Business Functionality

After corrections, I’ll usually validate actual business functionality instead of just checking connectivity.

Things I normally test:

- User login works  
- Domain join succeeds  
- Shared drives resolve correctly  
- Printers reconnect  
- VPN access functions properly  
- RDP connections succeed  
- Outlook and Microsoft 365 connectivity restored  

The DNS layer might be fixed, but the user still needs their workflow restored.

---

# Step 9: Document the Ticket

For documentation, I usually include:

- DNS issue identified  
- Connectivity tested  
- DNS records corrected  
- Cache flushed and re-registered  
- Reverse lookup configured if needed  
- Validation completed  
- Final resolution status  

Good DNS documentation becomes really helpful for recurring infrastructure issues later.

---

# Example Ticket Note

```text
User unable to access internal resources after connecting to VPN.

Verified workstation was using incorrect public DNS server instead of internal Domain Controller DNS.

Updated DNS configuration, flushed local DNS cache, and re-registered DNS records.

Validated successful hostname resolution, VPN connectivity, shared drive access, and domain authentication.

Issue resolved successfully.
```

---

# Example Interview Answer

## Question

“How do you troubleshoot DNS issues?”

## My Answer

```text
I usually start by verifying the workstation’s IP configuration using ipconfig /all to confirm the correct DNS server assignment.

Then I test connectivity and name resolution using ping and nslookup to determine whether the issue is network-related or DNS-specific.

If needed, I’ll flush and re-register DNS records, verify SRV records for Active Directory environments, and review DNS server records for stale or duplicate entries.
```

---

# Security Notes

A few things I try to avoid:

- Using public DNS inside internal AD environments  
- Leaving stale Domain Controller records active  
- Ignoring duplicate DNS entries  
- Misconfiguring dynamic DNS updates  

DNS directly impacts authentication, access control, and overall network reliability.

---

# Related Procedures

- DHCP Management  
- Domain Join Troubleshooting  
- Computer Account Management  
- VPN Troubleshooting  
- RDP Troubleshooting  
- Active Directory Troubleshooting
