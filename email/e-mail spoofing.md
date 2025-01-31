# [Starting point](https://github.com/CanIPhish/spf-bypass)

I found the link above when I was asked to do a phishing exercise. 
My question was how to spoof a legitimate domain name to make the exercise as credible as possible. 
We'll start with the end result to understand the methodology and theory behind the vulnerability exploited. 

This will be the starting point for documenting the processes involved in sending/receiving an email. 

# End result 

Using the following commands, I was able to send a malicious email appearing to come from a perfectly legitimate agent:

```bash
telnet <target.mailserver.com> 25
helo <attackerdomain.com>
mail from: <attacker@attackerdomain.com>
rcpt to: <target@target.com>
data
from: "Sender, Legitimate" <Legitimate_Sender@spoofed.com>
to: target@target.com
subject: Presentation - Email Demo
This is a test.

. # That dot is inform telnet that the data is complete and can be sent.    # It's not part of the e-mail. 
```

Where 'target' is the person being phished and 'spoofed' is the legitimate sender I claim to represent.
For `attackerdomain.com`, we need to own a domain name and a mail server. I will try to provide later a step by step to configure it but that's not the point here. 

# Information gathering 

- <target\@target.com> : target e-mail address. Let's try with `becode_corporate_j@yopmail.com`
- <targer.mailserver.com> : we need to retrieve the [MX](MX) record corresponding to the target domain name, using `dig :
     `dig yopmail.com MX 
     `yopmail.com.		86400	IN	MX	1 smtp.yopmail.com
    So we got `smtp.yopmail.com`
-  <Legitimate_Sender\@spoofed.com> : we can't spoofed any domain of our choice. We need to find one which [](authentication%20process.md#DMARC|DMARC) policy is set to `none`.  Again, using dig : 
    `dig _dmarc.tomandco.com TXT `
    `"v=DMARC1 ; p=none ; sp=none"

With this information, along with a mail server and domain name that we control, we are now able to send the phishing email. 

# Explaining the vulnerability

It's all about using authentication measures that depend on the [DNS](DNS) protocol. 
To summarise the [structure of an email](structure%20of%20an%20email.md), there are two independent parts:
 - [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope) : here we find the fields "MAIL FROM" and "RCPT TO".
 - [](Mstructure%20of%20an%20email#Message%20header|Message%20header) : where we find the "FROM" and "TO" fields. 

The [](authentication%20process.md#SPF|SPF) is responsible for checking legitimate IP addresses to use the domain name used in the [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope).
[](authentication%20process.md#DKIM|DKIM) adds a digital signature to emails so that the recipient's server can verify the sender's domain and ensure that the message hasn't been altered in transit.

[](authentication%20process.md#DMARC|DMARC) is responsible for checking whether the information between the [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope) and the [](structure%20of%20an%20email.md#Message%20header|message%20header) matches, and what to do if it doesn't. 
To do this, it relies on the initial checks of the [](authentication%20process.md#SPF|SPF) and [](authentication%20process.md#DKIM|DKIM) and verifies that they match what is in the message headers. 
It then determines what to do if they do not match. And that's what we're exploiting here, since the policy chosen by the spoofed domain administrator is `none`. 

In short, we control the sending mail server and the domain name. For the latter, we have published legitimate [](authentication%20process.md#SPF|SPF) and [](authentication%20process.md#DKIM|DKIM) registries. 
As the information in the [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope) is checked by the recipient, there will be no alert, as this is the reality: the attacker's domain is used and checked during authentication. 

It's the [](authentication%20process.md#DMARC|DMARC) that should react, since the envelope and the content do not match. Unfortunately for the target, given the [](authentication%20process.md#DMARC|DMARC) policy (`none`) chosen by the administrator of the spoofed domain, the email will end up in their normal inbox. 
An additional subtlety in the case of the [](authentication%20process.md#DMARC|DMARC) registry chosen for our example: the absence of administrative emails. This means that no use of the domain name (legitimate or otherwise) is logged. This reduces the risk of being taken to task for fraudulent use of the domain name. 

\* This is in addition to other anti-phishing/spam control mechanisms put in place by the email service provider. 








