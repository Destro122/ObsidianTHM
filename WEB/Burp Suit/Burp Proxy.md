Burp Proxy intercepte les requête entre un client et un serveur afin de les analyser, les envoyer dans d'autres outils ou juste les envoyer au serveur. 

- **Interception des requêtes** : permet de bloquer les requêtes avant qu’elles atteignent le serveur afin de les modifier, transférer ou supprimer. L’option _Intercept is on_ active/désactive cette fonction.
    
- **Prise de contrôle** : l’interception donne un contrôle total sur le trafic web, essentiel pour les tests d’applications.
    
- **Capture & journalisation** : toutes les requêtes (même sans interception active) sont enregistrées pour analyse ultérieure.
    
- **Support WebSocket** : les échanges WebSocket sont également capturés et loggés.
    
- **Historique** : les requêtes et communications sont visibles dans les onglets _HTTP history_ et _WebSockets history_ et peuvent être réutilisées dans d’autres modules.
    
- **Paramètres Proxy** : accessibles via _Proxy settings_, ils permettent d’ajuster le comportement du proxy.
    

---

### Fonctions Notables dans les Paramètres

- **Interception des réponses** : possible via des règles définies, mais désactivée par défaut.
    
- **Match & Replace** : utilisation de regex pour modifier dynamiquement les requêtes/réponses (ex. changer l’user-agent ou les cookies).

