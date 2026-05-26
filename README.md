# Enterprise IT Support Lab

A hands-on IT support and service desk lab I built to simulate real-world enterprise troubleshooting, Help Desk operations, and security-focused support workflows.

This project focuses on practical experience with things like:

- Active Directory administration  
- Windows Server 2019  
- DNS and DHCP troubleshooting  
- RDP and remote support  
- Citrix Workspace troubleshooting  
- Jira ticket management  
- User provisioning and deprovisioning  
- Password resets and account lockouts  
- Computer account management  
- Domain join troubleshooting  
- Printer troubleshooting  
- VPN and network troubleshooting  
- Security alert escalation  
- Wazuh SIEM monitoring and investigation workflows  

The main goal of this lab has been building real operational experience beyond certifications by practicing the kinds of issues IT support and SOC teams deal with every day.

---

# Lab Environment

## Infrastructure

### Primary Systems

- Windows Server 2019 Domain Controller  
- Ubuntu Server running Wazuh SIEM  
- Windows 11 workstation  
- Kali Linux VM for testing and validation  
- macOS host system running VMware Fusion  
- Lenovo ThinkCentre M70q dedicated server  

### Core Technologies

- Active Directory  
- Group Policy  
- DNS  
- DHCP  
- Remote Desktop Protocol (RDP)  
- Citrix Workspace  
- VMware / Hyper-V  
- Jira Service Management  
- Wazuh SIEM  
- PowerShell  
- Windows Administration Tools  

---

# Repository Structure

```text
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

Some of the workflows I’ve been practicing include:

- New user creation  
- Password resets  
- Account unlocks  
- Group membership management  
- User provisioning and deprovisioning  
- Computer account management  
- Domain join troubleshooting  
- OU placement and device lifecycle management  
- Access request workflows  

---

# Windows Server Support

A lot of my focus has been around troubleshooting common enterprise support issues like:

- DNS problems  
- DHCP scope management  
- RDP failures  
- Domain join issues  
- User authentication problems  

I wanted the lab to feel closer to real Service Desk operations instead of just isolated tutorials.

---

# End User Support

Some of the more common user-side troubleshooting scenarios include:

- Citrix Workspace login issues  
- VPN troubleshooting  
- Printer mapping failures  
- MFA login support  
- Outlook and Microsoft 365 access issues  
- Network connectivity troubleshooting  

These are the kinds of tickets that come up constantly in real environments, so I wanted hands-on exposure to the actual workflow and troubleshooting process.

---

# Security Escalation Support

I also started integrating more SOC-style escalation and security workflows into the lab, including:

- Suspicious login investigations  
- Phishing escalation procedures  
- Wazuh alert triage  
- Privileged access review  
- Incident documentation workflows  

This helped bridge the gap between traditional IT support and security operations.

---

# Goal of This Project

The purpose of this repository is to document repeatable enterprise IT support procedures and real-world troubleshooting workflows that align with actual Help Desk, Service Desk, and entry-level SOC responsibilities.

I built this lab to strengthen practical experience, improve troubleshooting methodology, and develop stronger escalation and documentation habits used in professional IT environments.

The biggest focus has been learning how systems actually communicate, fail, authenticate, and recover in both local and hybrid environments.

---

# Ongoing Development

This project is still growing and will continue expanding with:

- Additional troubleshooting procedures  
- Real-world ticket scenarios  
- Jira workflow examples  
- Security escalation documentation  
- PowerShell automation  
- Screenshots and validation evidence  
- SIEM monitoring workflows  
- Hybrid identity and authentication projects  

A lot of this has turned into documenting the same types of operational processes I’d expect to see in a real enterprise support environment.
