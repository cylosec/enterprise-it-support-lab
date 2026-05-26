# Service Request Ticket Template

## Objective

This is the standard format I’d typically use when documenting routine IT support requests inside Jira Service Management or similar ticketing systems.

Most of these requests usually involve:

- Password resets  
- New user onboarding  
- Access requests  
- VPN setup  
- Citrix access  
- Printer setup  
- Software installation  
- Hardware provisioning  
- Group membership updates  

Good documentation helps keep support organized, improves accountability, and makes audits a lot easier later.

---

# Ticket Type

## Service Request

I’d normally use a Service Request ticket for:

- Standard user support  
- Planned onboarding tasks  
- Permission changes  
- Equipment requests  
- Access provisioning  
- Operational support tasks  

Unlike incidents, service requests are usually focused on delivery and fulfillment rather than troubleshooting outages or security events.

---

# Required Ticket Fields

## Summary

Keep the request short and easy to understand.

Example:

```text
New Finance employee onboarding and access provisioning
```

---

## Priority

Typical priorities:

- Low  
- Medium  
- High  

I usually base this on:

- Business urgency  
- Employee start date  
- Operational impact  
- Access dependency requirements  

---

## Requestor

Who submitted the request.

Examples:

- Manager  
- HR representative  
- Department supervisor  
- End user  

---

## Affected User

I normally document:

- Full name  
- Username  
- Department  
- Assigned manager  
- Start date  
- Assigned device if applicable  

Example:

```text
User: John Smith
Department: Finance
Manager: Sarah Johnson
Start Date: Monday
```

---

## Requested Access / Services

This section usually includes:

- AD account creation  
- Security group assignments  
- VPN access  
- Citrix access  
- Shared mailbox permissions  
- Printer mapping  
- Software installation  
- Device setup and provisioning  

I try to follow least privilege whenever possible instead of granting broad access unnecessarily.

---

# Approval Verification

Before provisioning anything, I usually verify:

- Manager approval  
- HR onboarding approval  
- Security approval if elevated access is requested  

I never want to provision access without documentation attached to the request.

---

# Work Performed

This is where I document the actual work completed.

Typical examples:

- Account created  
- Groups assigned  
- Password delivered securely  
- Licensing completed  
- Device configured  
- Validation completed  

Example:

```text
Created Active Directory account for j.smith in Finance OU.

Assigned Finance_RW security group, VPN access group, Microsoft 365 license, and Citrix application access.

Temporary password delivered securely with required password change at first login.
```

---

# Resolution

Document the final outcome clearly.

Example:

```text
Manager notified of completed onboarding.

User confirmed successful first login and access to required systems.

Request completed successfully.
```

---

# Example Full Ticket Summary

```text
Priority: Medium

Summary:
New employee onboarding for Finance department

Requestor:
Finance Manager

Affected User:
John Smith

Services Requested:
AD account creation
VPN access
Citrix access
Microsoft 365 provisioning

Work Completed:
Account created
Groups assigned
Password issued securely
Access validated

Status:
Resolved
```

---

# Security Notes

A few things I try to avoid:

- Creating accounts without approval  
- Overprovisioning permissions  
- Reusing old employee accounts  
- Skipping documentation during onboarding  

Service requests often become part of audit and compliance evidence later.

---

# Related Procedures

- New User Creation  
- Group Membership Management  
- Computer Account Management  
- Password Reset Procedure  
- VPN Access Support  
- Citrix Workspace Access Setup
