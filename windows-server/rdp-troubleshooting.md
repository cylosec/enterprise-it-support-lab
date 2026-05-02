# RDP Troubleshooting Procedure

## Objective

Provide a standardized process for diagnosing and resolving Remote Desktop Protocol (RDP) connectivity issues in enterprise Windows environments.

This procedure supports:

* Remote server administration
* User remote access failures
* Administrative workstation access
* VPN + RDP connection workflows
* Authentication failures
* Session lockouts
* Hostname resolution failures
* Firewall and port connectivity issues

RDP is a critical support function for Service Desk, Systems Administration, and Infrastructure Support.

---

# Step 1: Identify the Issue

Common user reports include:

* “Remote Desktop won’t connect”
* “The remote computer cannot be found”
* “Access is denied”
* “Your credentials did not work”
* “I can ping the server but RDP fails”
* “Session is stuck or disconnected”
* “Connection times out”

Determine whether the issue is:

* Network related
* Authentication related
* DNS related
* Firewall related
* Session related
* Permission related

---

# Step 2: Verify Basic Connectivity

Run:

```powershell id="w4n8zp"
ping hostname
ping 10.x.x.x
```

Examples:

```powershell id="s9v3mr"
ping DC01
ping server01
```

Verify:

* Host is reachable
* No packet loss
* Internal DNS resolves correctly

If IP works but hostname fails, DNS is likely the issue.

---

# Step 3: Verify DNS Resolution

Run:

```powershell id="c7m1yt"
nslookup hostname
nslookup yourdomain.local
```

Confirm:

* Correct internal IP returned
* Internal DNS responding properly

Incorrect DNS frequently causes RDP failures.

---

# Step 4: Confirm Remote Desktop is Enabled

On the target machine verify:

```text id="d2x7kl"
System Properties → Remote → Allow remote connections to this computer
```

Also confirm:

```text id="p6j4ws"
Allow connections only from computers running Network Level Authentication (recommended)
```

is configured according to policy.

---

# Step 5: Verify User Permissions

Confirm the user is:

* Local Administrator (if required)
* Member of Remote Desktop Users group
* Approved for remote access
* Not restricted by policy

Common issue:

```text id="h8v5rn"
Access is denied
```

often results from missing permissions.

---

# Step 6: Check Firewall and Port Access

Verify:

* Windows Firewall allows RDP
* TCP Port 3389 is open
* VPN connection is active if remote access requires VPN
* Network segmentation is not blocking access

Test:

```powershell id="y3q9db"
Test-NetConnection hostname -Port 3389
```

Successful output confirms port reachability.

---

# Step 7: Review Existing Sessions

Common issues include:

* Frozen disconnected sessions
* Locked administrative sessions
* Maximum session limits reached

Use:

```powershell id="u5k8lx"
query user
```

or

```powershell id="g7n2pw"
qwinsta
```

to review active sessions.

Reset stuck sessions if necessary.

---

# Step 8: Validate Credentials

Verify:

* Correct username format

Examples:

```text id="n4f7zm"
yourdomain\j.smith
j.smith@yourdomain.local
```

* Password is current
* Account is not locked
* MFA or VPN requirements are satisfied

Password reset may be required if authentication fails.

---

# Step 9: Validate Successful Access

After correction, confirm:

* User successfully logs in
* Required applications launch
* Shared drives available
* Printer access works
* Citrix access functions if required

Always validate business functionality, not just login.

---

# Step 10: Document the Ticket

Record:

* Connectivity verified
* DNS tested
* Firewall/port status confirmed
* User permissions corrected
* Session reset performed if needed
* Final resolution status

Strong documentation supports repeatability and escalation workflows.

---

# Example Ticket Note

```text id="m1x6qr"
User unable to RDP to Finance application server.

Verified DNS resolution and confirmed successful ping to target host.
Tested TCP 3389 connectivity and found Windows Firewall blocking inbound RDP.

Updated firewall rule, verified Remote Desktop Users group membership, and confirmed successful login using domain credentials.

Issue resolved and ticket closed.
```

---

# Security Notes

Never:

* Leave RDP exposed publicly without VPN or proper controls
* Grant remote access without approval
* Ignore failed login patterns
* Leave stale disconnected privileged sessions active

RDP is a high-value attack surface and must be managed carefully.

---

# Related Procedures

* DNS Troubleshooting
* DHCP Management
* Password Reset Procedure
* Account Lockout Resolution
* Domain Join Troubleshooting

---
