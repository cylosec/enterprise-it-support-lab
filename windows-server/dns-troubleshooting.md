# Enterprise IT Support Lab

A hands-on enterprise IT support and service desk lab built to simulate real-world Help Desk, Service Desk Analyst, and IT Support operations.

This project demonstrates practical experience with:

* Active Directory administration
* Windows Server 2019
* DNS and DHCP troubleshooting
* RDP and remote support workflows
* Citrix Workspace troubleshooting
* Jira ticket management
* User provisioning and deprovisioning
* Password resets and account lockout resolution
* Computer account management
* Domain join troubleshooting
* OU placement and device lifecycle management
* Printer troubleshooting
* VPN and network troubleshooting
* Security alert escalation
* Wazuh SIEM integration for security operations

This lab was built to strengthen practical enterprise IT experience and support career growth into roles such as:

* Service Desk Analyst
* Help Desk Technician
* IT Support Specialist
* Desktop Support Technician
* Systems Support Analyst
* SOC Analyst
* Security Operations Analyst

---

# Lab Environment

## Infrastructure

### Primary Systems

* Windows Server 2019 Domain Controller
* Ubuntu Server running Wazuh SIEM
* Windows 11 endpoint workstation
* Kali Linux VM for testing and validation
* macOS host system with VMware Fusion
* Lenovo ThinkCentre M70q dedicated server

### Core Technologies

* Active Directory
* Group Policy
* DNS
* DHCP
* Remote Desktop Protocol (RDP)
* Citrix Workspace
* VMware / Hyper-V
* Jira Service Management
* Wazuh SIEM
* PowerShell
* Windows Administration Tools

### Standardized Public Documentation Values

To maintain security best practices and avoid exposing internal infrastructure, all examples in this repository use sanitized placeholder values:

* Domain: `yourdomain.local`
* Internal DNS / Domain Controller IP: `10.x.x.x`
* Domain Controller Hostname: `DC01`
* Example usernames: `firstname.lastname`, `j.smith`, `svc_backup`

This repository is intended for professional portfolio demonstration and follows public documentation security standards.

---

# Repository Structure

```text id="2fx9vc"
enterprise-it-support-lab/

├── active-directory/
│   ├── user-creation.md
│   ├── password-reset.md
│   ├── group-management.md
│   ├── account-lockout.md
│   ├── computers-management.md
│   └── domain-join-troubleshooting.md
│
├── windows-server/
│   ├── dns-troubleshooting.md
│   ├── dhcp-management.md
│   └── rdp-troubleshooting.md
│
├── citrix/
│   └── workspace-troubleshooting.md
│
├── jira-ticketing/
│   ├── incident-response-template.md
│   └── service-request-template.md
│
├── printers/
│   └── printer-troubleshooting.md
│
├── networking/
│   ├── ipconfig-nslookup-ping.md
│   └── common-powershell-commands.md
│
├── security-escalations/
│   ├── suspicious-login-investigation.md
│   └── phishing-escalation.md
│
├── screenshots/
│
└── README.md
```

---

# Core Help Desk Scenarios

## Active Directory

* New user creation
* Password resets
* Account unlocks
* Group membership management
* User provisioning and deprovisioning
* Computer account management
* Domain join troubleshooting
* OU placement and device lifecycle management
* Access request workflows

## Windows Server Support

* DNS troubleshooting
* DHCP scope management
* RDP troubleshooting
* Domain join troubleshooting
* User login failures

## End User Support

* Citrix Workspace login issues
* VPN access troubleshooting
* Printer mapping and printer failures
* MFA login issues
* Outlook and Microsoft 365 access support

## Security Escalation Support

* Suspicious login investigations
* Phishing email escalation
* Privileged account review
* Wazuh alert triage
* Incident documentation and escalation workflows

---

# Example Safe Enterprise Commands

## Verify DNS Configuration

```powershell id="ntgblq"
ipconfig /all
```

Expected Example:

```text id="b5v75k"
DNS Server: 10.x.x.x
Domain: yourdomain.local
```

---

## Verify Domain Controller Discovery

```powershell id="lcpfcv"
nslookup -type=SRV _ldap._tcp.dc._msdcs.yourdomain.local
```

Expected Result:

```text id="v11zmb"
SRV service location:
priority = 0
weight = 100
port = 389
svr hostname = DC01.yourdomain.local
```

---

## Launch Active Directory Users and Computers

```powershell id="zobq4k"
dsa.msc
```

---

## Verify Time Synchronization

```powershell id="7c0dzd"
w32tm /query /status
```

---

# Goal of This Project

This repository is designed to document practical, repeatable enterprise IT support procedures that align with real-world service desk and SOC analyst responsibilities.

The goal is to demonstrate hands-on capability beyond certifications by showing operational workflows, troubleshooting methodology, escalation judgment, and documentation standards used in professional IT environments.

---

# Ongoing Development

This repository will continue expanding with:

* Step-by-step procedures
* Real troubleshooting scenarios
* Jira ticket examples
* Incident response templates
* Security escalation documentation
* PowerShell automation examples
* Screenshots and validation evidence

This project is continuously updated to reflect enterprise IT support practices used in production environments.

---
