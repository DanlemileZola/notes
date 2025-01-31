# Introduction

Dans le but d'authentifier un e-mail, plusieurs mécanismes sont mis en place par le protocol [[DNS]]. Ils sont au nombre de 3, à savoir : 

- [[#SPF]] : vérifie la légitimité d'une adresse IP à user du nom de domaine contenu dans le [[structure of an email#SMTP envelope|SMTP envelope]] de l'e-mail. 
- [[#DKIM]] : vérifie la signature (privé) d'un e-mail avec la clé publique contenu dans le registre DNS correspondant. 
- [[#DMARC]] : il s'assure que les informations - situés dans le [[structure of an email#SMTP envelope|SMTP envelope]] -vérifiés par le [[#SPF]] et le [[#DKIM]] correspondent avec le nom de domaine contenu dans le [[structure of an email#Message header|message header]]. De plus, il est chargé d'indiquer la politique a suivre en cas de non-alignement ainsi que les addresses e-mails à qui faire suivre les rapports d'utilisation.
  
# SPF 



# DKIM 

# DMARC

