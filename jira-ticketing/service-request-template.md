# Service Request Ticket Template

## Objective

Provide a standardized template for documenting routine IT support requests within Jira Service Management or enterprise ticketing systems.

This template supports:

* Password resets
* New user onboarding
* Access requests
* Group membership changes
* Printer setup
* VPN access requests
* Citrix access support
* Software installation requests
* Hardware provisioning

Strong documentation improves support quality, accountability, and audit readiness.

---

# Ticket Type

## Service Request

Used for:

* Planned user support
* Standard access requests
* Onboarding workflows
* Equipment provisioning
* Permission changes
* Non-incident operational requests

Service requests focus on delivery, not incident response.

---

# Required Ticket Fields

## Summary

Short, clear request description.

Example:

```text id="v3j8nk"
New Finance employee onboarding and access provisioning
```

---

## Priority

Examples:

* Low
* Medium
* High

Priority should reflect business urgency and start-date requirements.

---

## Requestor

Who submitted the request.

Examples:

* Manager
* HR
* End user
* Department supervisor

---

## Affected User

Document:

* Full name
* Username
* Department
* Manager
* Start date
* Device assignment if applicable

Example:

```text id="x7m1pr"
User: John Smith
Department: Finance
Manager: Sarah Johnson
Start Date: Monday
```

---

## Requested Access / Service

Document:

* AD account creation
* Security group assignment
* VPN access
* Citrix access
* Shared mailbox permissions
* Printer mapping
* Software installation
* Device provisioning

Access should follow least privilege.

---

## Approval Verification

Document:

* Manager approval
* HR onboarding approval
* Security approval if privileged access required

Never provision access without documented approval.

---

## Work Performed

Document:

* Account created
* Groups assigned
* Password issued securely
* Licensing completed
* Device prepared
* Validation completed

Example:

```text id="m9q4vd"
Created AD account for j.smith in Finance OU.

Assigned Finance_RW security group, VPN access group, Microsoft 365 license, and Citrix application access.

Temporary password issued securely with required password change at first login.
```

---

## Resolution

Document final completion.

Example:

```text id="d5y2lx"
Manager notified of completed onboarding.
User confirmed successful first login and access to required systems.

Request completed successfully.
```

---

# Example Full Ticket Summary

```text id="r8v6kt"
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

Never:

* Create accounts without approval
* Overprovision access
* Reuse old user accounts
* Skip documentation for onboarding

Service requests often become audit evidence.

---

# Related Procedures

* New User Creation
* Group Membership Management
* Computer Account Management
* Password Reset Procedure
* Citrix Workspace Access Setup

---
