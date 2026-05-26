# Phishing Email Escalation Procedure

## Objective

This is the standard process I’d typically follow when handling suspected phishing emails in an enterprise environment.

Most phishing-related tickets usually involve:

- Suspicious email reports  
- Fake Microsoft 365 login pages  
- Credential harvesting attempts  
- Fake MFA prompts  
- Malicious attachments  
- Executive impersonation  
- Fake invoice/payment scams  
- Internal spoofing attempts  

The biggest priority is reducing the risk of credential theft, malware execution, or unauthorized access as quickly as possible.

---

# Step 1: Identify the User Report

Most users usually report things like:

- “This email looks suspicious”  
- “I clicked a weird link”  
- “I opened the attachment already”  
- “I got a fake invoice”  
- “My manager emailed me asking for gift cards”  
- “I received an MFA prompt I didn’t approve”  

I try to treat every phishing report seriously until proven otherwise.

---

# Step 2: Instruct the User Immediately

First thing I normally tell the user:

- Don’t click anything else  
- Don’t open additional attachments  
- Don’t reply to the sender  
- Don’t forward the message externally  
- Leave the email intact for investigation  

If they already interacted with the email, I’ll try to determine:

- Whether they clicked a link  
- Entered credentials  
- Downloaded files  
- Approved MFA prompts  
- Executed attachments  

That changes the severity level immediately.

---

# Step 3: Review the Email Indicators

Next I’ll review common phishing indicators like:

- Sender address  
- Reply-to mismatch  
- Spoofed domains  
- Suspicious URLs  
- Unexpected attachments  
- Urgent payment requests  
- Fake login prompts  
- Microsoft 365 impersonation attempts  

A lot of phishing emails rely heavily on urgency, fear, or impersonation.

Common examples:

- Slightly misspelled domains  
- Fake display names  
- Internal impersonation  
- “Password Expiring” emails  
- Fake DocuSign or invoice notifications  

---

# Step 4: Determine Severity

Higher severity situations usually include:

- User entered credentials  
- Attachment was executed  
- MFA approval was accepted  
- Privileged account targeted  
- Executive impersonation  
- Multiple users received the same message  
- Malware indicators identified  

At that point, I’d treat it more like a security incident than a normal help desk ticket.

---

# Step 5: Immediate Containment Actions

If the user interacted with the phishing attempt, I’d usually move quickly to containment.

Typical actions:

- Reset password immediately  
- Force MFA revalidation  
- Disable account temporarily if needed  
- Revoke active sessions if available  
- Notify Security Team  
- Preserve logs and email headers  

Containment is usually more important than full investigation in the first few minutes.

---

# Step 6: Escalate to Security

I’d escalate immediately for situations involving:

- Credential exposure  
- Malware execution  
- Executive impersonation  
- Privileged account targeting  
- Widespread phishing campaigns  
- Suspicious attachments being opened  

High-risk phishing incidents shouldn’t be handled entirely at the Help Desk level.

---

# Step 7: Confirm Recovery

Before resolving the incident, I usually verify:

- Password reset completed  
- MFA secured  
- User access restored safely  
- Security review completed  
- Monitoring enabled if necessary  

The goal is secure recovery, not just quickly closing the ticket.

---

# Step 8: Document the Ticket

For documentation, I usually include:

- Original user report  
- Phishing indicators observed  
- User actions taken  
- Containment actions performed  
- Escalation path  
- Final resolution status  

Good documentation becomes important during security reviews and post-incident analysis.

---

# Example Ticket Note

```text
User reported suspicious Microsoft 365 password expiration email.

Review identified spoofed sender domain and credential harvesting link.
User clicked the link but did not enter credentials.

Password reset completed as precaution and MFA revalidation enforced.

Email escalated to Security Team for header analysis and organization-wide review.

No confirmed compromise identified.
Incident resolved successfully.
```

---

# Example Interview Answer

## Question

“How would you handle a phishing report?”

## My Answer

```text
I’d first determine whether the user clicked the link, opened an attachment, entered credentials, or approved MFA prompts because that immediately affects severity.

Then I’d review sender information, domain mismatches, suspicious URLs, and attachment behavior.

If there’s any indication of credential exposure or malware execution, I’d secure the account immediately, preserve evidence, and escalate to Security rather than treating it like a standard Help Desk ticket.
```

---

# Security Notes

A few things I try to avoid:

- Dismissing phishing reports too quickly  
- Delaying password resets after credential exposure  
- Allowing suspicious sessions to remain active  
- Closing incidents without escalation when compromise risk exists  

Phishing incidents can escalate very quickly if not handled properly.

---

# Related Procedures

- Incident Response Ticket Template  
- Password Reset Procedure  
- Suspicious Login Investigation  
- Wazuh Alert Triage  
- MFA Troubleshooting  
- Privileged Access Review
