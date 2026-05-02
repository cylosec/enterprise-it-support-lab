# Phishing Email Escalation Procedure

## Objective

Provide a standardized process for identifying, documenting, and escalating suspected phishing emails in enterprise environments.

This procedure supports:

* User-reported phishing emails
* Credential harvesting attempts
* Fake MFA requests
* Business email compromise attempts
* Malicious attachment delivery
* Fake invoice/payment scams
* Internal spoofing attempts
* Executive impersonation attacks

Fast response reduces the risk of credential theft and malware execution.

---

# Step 1: Identify the Report

Common user reports include:

* “This email looks suspicious”
* “I clicked a strange link”
* “I opened an attachment by mistake”
* “I received a fake invoice”
* “My manager asked me to buy gift cards”
* “I received an MFA prompt I didn’t initiate”

Treat all reports seriously until verified.

---

# Step 2: Instruct the User Immediately

Tell the user:

* Do not click additional links
* Do not open attachments
* Do not reply to the sender
* Do not forward externally
* Leave the message intact for review

If they already clicked:

* Determine what action occurred
* Whether credentials were entered
* Whether files were downloaded
* Whether MFA prompts were approved

This changes the severity immediately.

---

# Step 3: Review the Email Indicators

Check:

* Sender address
* Reply-to mismatch
* Domain spoofing
* Suspicious URLs
* Unexpected attachments
* Urgent payment requests
* Credential prompts
* Fake Microsoft 365 login pages

Examples:

* Slight misspellings
* Display name spoofing
* Internal impersonation

Many phishing attempts rely on urgency and trust.

---

# Step 4: Determine Severity

Higher severity includes:

* User entered credentials
* Attachment executed
* Privileged user targeted
* Finance or executive impersonation
* MFA approval clicked
* Multiple users received same email
* Known malware indicators present

Higher severity requires immediate escalation.

---

# Step 5: Immediate Containment Actions

If user interacted:

* Reset password immediately
* Force MFA revalidation
* Disable account temporarily if required
* Revoke active sessions if available
* Notify Security Team
* Preserve email headers and logs

Containment should happen before full analysis if compromise risk exists.

---

# Step 6: Escalate to Security

Escalate for:

* Credential exposure
* Malware execution
* Executive impersonation
* Privileged account targeting
* Widespread delivery across organization
* Suspicious attachment execution

Help Desk should not independently close high-risk phishing incidents.

---

# Step 7: Confirm Recovery

Verify:

* Password reset completed
* MFA secure
* User access restored safely
* Security review completed
* Additional monitoring enabled if required

The goal is secure recovery, not just ticket closure.

---

# Step 8: Document the Ticket

Record:

* Original report details
* Email indicators observed
* User actions taken
* Containment steps
* Escalation path
* Final resolution status

This documentation is often used during incident review.

---

# Example Ticket Note

```text id="k6p3zm"
User reported suspicious Microsoft 365 password expiration email.

Review confirmed spoofed sender domain and credential harvesting link.
User clicked link but did not enter credentials.

Password reset completed as precaution and MFA revalidation enforced.

Email escalated to Security Team for header analysis and organization-wide review.

No confirmed compromise identified.
Incident resolved.
```

---

# Example Interview Answer

## Question

“How would you handle a phishing report?”

## Strong Answer

```text id="m2w8ty"
I would first determine whether the user clicked the link, opened an attachment, or entered credentials because that drives severity.

I would review sender details, domain mismatches, suspicious links, and attachment behavior.

If there is any risk of credential exposure or malware execution, I would immediately secure the account, preserve evidence, and escalate to Security rather than treating it as a normal help desk ticket.
```

This answer performs very well in interviews.

---

# Related Procedures

* Incident Response Ticket Template
* Password Reset Procedure
* Suspicious Login Investigation
* Wazuh Alert Triage
* Privileged Access Review

---
