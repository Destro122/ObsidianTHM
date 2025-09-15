---
aliases:
  - DNS
---
Le DNS est dans la couche applicative ([[OSI Model]]). Il permet de relier un nom de domaine à une adresse IP.

Il utilise le port UDP 35 et le port TCP 53 par défaut.

- A Record : Map une nom à une IPv4
- AAAA Record : pareille mais IPv6
- CNAME Record : relie un nom de domaine a un autre nom de domaine
- MX Record : Mail Exchange, map le service mail responsable du domaine 

`nslookup` permet de connaitre l'adresse ip à l'aide d'un nom de domaine 

