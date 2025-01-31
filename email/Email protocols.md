
In order to authenticate - or in our case, to bypass authentication but we will see this later - a standard  was set up.
It is structured around three mechanisms: [[DMARC]], [[DKIM]] and [[SPF]].

[[SPF]] (Sender Policy Framework) is used to check a mail server legitimacy.
With an SPF record in place, Internet Service Providers can verify that a mail server's IP address is authorized to send email for a specific domain. 
An SPF record is a [[DNS]] TXT record containing a list of the IP addresses that are allowed to send email on behalf of your domain.

[[DKIM]] (DomainKeys Identified Mail) is used for the authentication of an email that’s being sent. A domain owner adds a DKIM record to the DNS records on the sending domain. 
This TXT record will contain a public key that’s used by receiving mail servers to verify a message’s signature.
DKIM gives emails a signature header that is added to the email and secured with encryption. Each DKIM signature contains all the information needed for an email server to verify that the signature is real, and it is encrypted by a pair of DKIM keys.
These signatures travel with the emails and are verified along the way by the email servers that move the emails toward their final destination.

[[DMARC]] (Domain-based Message Authentication Reporting and Conformance) is used to authenticate an email by aligning [[SPF]]and [[DKIM]] mechanisms.
A DMARC record is a text entry within the DNS record that tells the world your email domain’s policy after checking SPF and DKIM status. DMARC authenticates if either SPF, DKIM, or both pass. This is what is referred as DMARC alignment. 

Understanding how authentication works, we can easily bypass this security. Or rather, find a domain that we can spoof because it's not DMARC compliant. 
To achieve this, we identify an interesting target and need to look for its DMARC record, using `dig` : 

     `dig tomandco.com _dmarc.tomandco.com TXT`

The part of interest to us being : 

     
     ;; ANSWER SECTION:
    _dmarc.tomandco.com.	86400	IN	TXT	"v=DMARC1 ; p=none ; sp=none"


![[dmarc_tomandco.png|600]]

`p=none`inform that there is no action required if messages fail DMARC. That's a weakness to exploit. 




