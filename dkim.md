<!-- TITLE: DKIM -->
<!-- SUBTITLE: Domain Keys Identified Mail -->

![Ibp Logo](/uploads/ibp_logo.png "Ibp Logo"){.pagelogo}

DKIM, or Domain Keys Identified Mail, is a method of informing the recipient server that the signing server owns the DNS zone of the domain in the signature, and that the portions of the message that have been signed are unchanged between transmission and reception.

In order to do this, DKIM utilizes an encryption algorithm that has a public – private key pair. This means that two keys are generated and what one key encrypts can only be decrypted by the other key (and not by the encrypting key). A sender will post the “public” key in the DNS and list the location in the DKIM signature with the “d=” domain and the “s=” selector. For example, RentPath B2B’s would be s=m1 and d=e.rentpath.com. So, the public key is stored in m1.domainkey.e.rentpath.com. The private key is kept secret by the owner of the DNS and stored in the sending email server.

The sending server will then encrypt a “signature” listing certain information from the Header with the private key, so that the recipient server can decrypt the “signature” with the public key (that is found using the “d=” and “s=” in the unencrypted portion of the signature) and compare it to the Header it actually received. If the information in the decrypted signature matches the information it received in the unencrypted Header, it knows the Header has not been tampered with.  

Additionally, the sending server will use the public key to encrypt the body of the message into a “hash” which cannot be decrypted and read by a bad actor without the private key. The recipient server will then use the public key (found via the “d=” and “s=”) to create its own hash of the message body and see if that hash is the same as the one created by the sender, indicating if the body of the message has been tampered with or not.*

# DKIM