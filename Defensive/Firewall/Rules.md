Un **pare-feu (firewall)** contrôle le trafic réseau en appliquant des **règles**. Ces règles peuvent être par défaut ou personnalisées afin d’autoriser, bloquer ou rediriger certains flux.
### Composants d’une règle :

- **Source** : adresse IP d’origine du trafic.
- **Destination** : adresse IP destinataire.
- **Port** : numéro du port utilisé (ex. 80 pour HTTP, 22 pour SSH).
- **Protocole** : protocole de communication (TCP, UDP, etc.).
- **Action** : traitement appliqué (Allow, Deny, Forward).
- **Direction** : trafic entrant (inbound) ou sortant (outbound).
### Types d’actions :

- **Allow** → autoriser le trafic (ex. autoriser HTTP sortant sur port 80).
- **Deny** → bloquer le trafic (ex. bloquer SSH entrant sur port 22)
- **Forward** → rediriger le trafic (ex. transférer HTTP entrant vers le serveur web interne).

### Direction des règles :

- **Inbound** : gèrent le trafic entrant (ex. autoriser HTTP entrant).
- **Outbound** : gèrent le trafic sortant (ex. bloquer SMTP sortant sauf pour le serveur mail).
- **Forward** : redirigent le trafic vers une autre machine interne (ex. rediriger HTTP vers un serveur web).
    
👉 En bref : le firewall applique des règles basées sur l’**adresse, protocole, port, action et direction** pour sécuriser et contrôler les communications réseau.