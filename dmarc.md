<!-- TITLE: DMARC -->
<!-- SUBTITLE: Domain-based Message Authentication Reporting and Conformance -->

DMARC, or Domain-Based Message Authentication Reporting and Conformance, is an authentication method that uses both SPF and DKIM to verify whether or not any given email was actually sent by the owner of the “Friendly-From” domain that the user sees. This gives the recipient server confidence that the sender is who they say they are.

DMARC works by verifying that both SPF and DKIM pass and at least one of them is aligned. Both authentications passing indicates that the email is coming from an authorized server and that the Header information has not been tampered with to falsify alignment, and the alignment proves that the sender owns the DNS space of the “Friendly-From” and is therefore who they say that they are.  
SPF alignment proves this because the MX records in the SPF domain (Envelope-From domain) must be correct in order for the SMTP conversation to complete and can only be changed by the DNS zone’s owner, so if the SPF domain is the same as the “Friendly-From” domain, the owner of that DNS zone is the sender.  

DKIM alignment proves this because the public DKIM key must be correct in order to decrypt the signature and can only be uploaded by the DNS zone’s owner, so if DKIM passes and uses the same domain as the “Friendly-From” domain, the owner of that DNS zone is the sender.
Any message that does not align is treated as phishing. The sender has a policy in the DMARC record to specify what to do with mail that does not pass DMARC. The policy can be one of the three options below: 
p=none - The ISP is instructed not to interfere with a message that fails DMARC and to send a report to the sender. 

p=quarantine - The ISP is instructed to flag an email that fails DMARC as suspicious and subject it to greater scrutiny and/or place it in Spam, as per the ISPs policies, and to send a report to the sender.

p=reject - The ISP is instructed to reject an email that fails DMARC during SMTP transaction and to send a report to the sender. 
 
While DMARC is not necessary, we highly suggest it because this shows ISPs that the sender is serious about their business and the protection of the recipients of the mail. Gmail and Microsoft are leading the charge in adopting DMARC and it will become part of their filtering methods. If your client does not have DMAR, suggest it and work with them to get it in place as it will help combat phishers and spoofers. 
The best practice for setting up DMARC is to set the policy to “p=none” and monitor the reports with a tool, such as Dmarcian or 250ok. This will allow your brand/company to identify every server sending as one of their domains and make sure they are correctly authenticating in the appropriate SPF record and signing with the correct DKIM key.

As the reports begin to indicate successful authentication for authorized senders and do not show legitimate senders being flagged as failures, it is recommended to increase the DMARC “p=” policy by percentages (eg: “pct=10;”) to “p=reject” which requests that ISPs simply bounce any and all emails.  This should be done very carefully over the course of several weeks, depending on the success of identifying and fully authenticating and aligning all legitimate sources of mail.

# DMARC