# Premier pas 

*Dans le but de prendre en main les outils liés à la cybersécurité, j'ai souhaité les découvrir par deux moyens : une mise en situation concrète -  à travers l'administration de mon propre VPS - et par ma toute nouvelle inscription à TryHackMe.*  
*L'idée est de consigner ici mon expérience : mes découvertes, difficultés, réussites,*
*frustrations ou enthousiasmes.*  
  

Dans une approche globale du domaine, il me semble judicieux d'entamer mon travail en identifiant les menaces principales auquel mon serveur pourrait être confronté afin de définir les outils à user et puis les mettre en place.  
Je tâcherai d'avancer ainsi pas à pas afin de construire un système robuste.  
Je pensais débuter par les menaces suivantes : 

 - Attaque 'brute force' pour accèder au serveur. 
 - Attaque sur le réseau : DDoS, DoS, MiTM. 
 - Exploitation de programmes non patchés ou mal configuré. 

# Un système à jour 

[](https://wiki.debian.org/UnattendedUpgrades)
 
log files for updates : 
/var/log/dpkg.log
/var/log/unattended-upgrades/unattended-upgrades.log
/var/log/unattended-uogrades/unattended-uogrades-dpkg.log 

- [ ] need a mail-transport-agent (MTA) or mailx to send emails (sSMTP ? )

