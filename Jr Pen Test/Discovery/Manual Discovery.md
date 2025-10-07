- **robots.txt** : fichier indiquant aux moteurs de recherche quelles pages ne doivent pas être indexées. En pentest, il liste souvent des chemins sensibles (admin, zones clients…) que les proprietaires ne veulent pas rendre visibles — utile pour la découverte d’axes d’attaque.
    
- **favicon** : petite icône du site (barre/adresse/onglet). Un favicon non personnalisé peut révéler le framework ou le CMS utilisé. OWASP maintient une base d’icônes pour faire la correspondance. Commande utile :  
    `curl https://.../favicon.ico | md5sum` (comparer le hash).
    
- **sitemap.xml** : liste des pages que le propriétaire souhaite indexer. Peut révéler des pages cachées, anciennes ou difficiles à trouver via la navigation normale.
    
- **HTTP Headers** : en faisant une requête (ex. `curl -v http://target`), les en-têtes peuvent révéler le serveur web (NGINX/Apache), versions, langage (PHP, etc.) ou autres infos utiles permettant d’identifier des versions vulnérables.
    
- **Framework stack** : en recoupant indices (favicon, code source, commentaires, mentions de crédits), on identifie le framework/CMS et la stack. Connaître la stack permet de rechercher vulnérabilités connues, plugins exposés ou chemins par défaut.