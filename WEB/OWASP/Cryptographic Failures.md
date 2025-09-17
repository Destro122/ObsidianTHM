Une _erreur cryptographique_ survient lorsqu’une application n’utilise pas correctement (ou pas du tout) des algorithmes de cryptographie pour protéger les données sensibles.

- **Exemples d’usage de la cryptographie :**
    
    - **Données en transit** : chiffrer les communications entre le client et le serveur (ex. accès à un webmail via HTTPS) pour éviter l’interception par des tiers.
        
    - **Données au repos** : chiffrer les informations stockées sur les serveurs (ex. emails) afin que même le fournisseur ne puisse les lire.
        
- **Conséquences d’un échec cryptographique :**
    
    - Fuite de données sensibles (informations personnelles, financières, identifiants, mots de passe).
        
    - Possibilité d’attaques plus avancées, comme les attaques **Man-in-the-Middle**, où un attaquant intercepte le trafic et exploite un chiffrement faible ou absent.
        
    - Parfois, les vulnérabilités sont simples : données exposées directement sur le serveur sans protection.
        

En résumé, une mauvaise implémentation de la cryptographie peut exposer directement les utilisateurs et leurs informations.