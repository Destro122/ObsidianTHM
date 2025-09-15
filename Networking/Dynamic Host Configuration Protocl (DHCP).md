---
aliases:
  - DHCP
---
DHCP est dans le layer application de l'[[OSI Model]]
Ce protocol permet de configurer le réseau de notre machine quand on se connecte a un nouveau réseau : 
- Adresse IP
- Router
- DNS
DHCP communique en UDP sur les ports 67 ( serveur<-) et 68 ( client -> )

Quatre étapes :  DORA
 1.  Découverte : Recherche un serveur DHCP sur le réseau
 2.  Offre : adresse IP disponible pour le client
 3. Requête : Réponse du client qui accepte l'ip
 4. Ack : Confirme que l'ip est assigné au client
 