# Introduction

Dans le but d'authentifier un e-mail, plusieurs mécanismes sont mis en place par le protocol [DNS](DNS). Ils sont au nombre de 3, à savoir : 

- [#SPF](#SPF) : vérifie la légitimité d'une adresse IP à user du nom de domaine contenu dans le [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope) de l'e-mail. 
- [#DKIM](#DKIM) : vérifie la signature (privé) d'un e-mail avec la clé publique contenu dans le registre DNS correspondant. 
- [#DMARC](#DMARC) : il s'assure que les informations - situés dans le [](structure%20of%20an%20email.md#SMTP%20envelope|SMTP%20envelope) -vérifiés par le [#SPF](#SPF) et le [#DKIM](#DKIM) correspondent avec le nom de domaine contenu dans le [](structure%20of%20an%20email.md#Message%20header|message%20header). De plus, il est chargé d'indiquer la politique a suivre en cas de non-alignement ainsi que les addresses e-mails à qui faire suivre les rapports d'utilisation.
  
# SPF 



# DKIM 

# DMARC

