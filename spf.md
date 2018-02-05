<!-- TITLE: SPF -->
<!-- SUBTITLE: Sender Policy Framework -->

![Ibp](/uploads/ibp.png "Ibp"){.pagelogo}

Sender Policy Framework, refers to a TXT record stored in a domain’s DNS zone that indicates which IP addresses and/or servers are allowed to send mail “from” that domain. The Return-Path domain is always checked for SPF authentication, comparing the IP address that sent the email to the Return-Path domain’s SPF record. Some recipient servers will also check the SPF record of the user-visible “Friendly-From” domain, but that is not required.

The SPF record of the top domain (say for example collegedata.com) authorizes for itself and for all subdomains that don’t have their own SPF record. The subdomain (mail.collegedata.com) SPF record overrides the top domain for only itself. In the interest of security, we want to be very specific about who is and is not allowed to send mail as you and as any possible subdomain, which means we want to cover every base with a specific and locked down SPF record.

An SPF record can be no longer than 255 characters.
# SPF