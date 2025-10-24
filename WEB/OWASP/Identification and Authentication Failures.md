L’authentification et la gestion des sessions sont essentielles aux applications web modernes. Les identifiants (souvent **nom d’utilisateur + mot de passe**) permettent de vérifier l’identité d’un utilisateur, puis le serveur lui attribue un **cookie de session** pour suivre ses actions malgré le protocole HTTP(S) stateless.

- **Failles courantes :**
    
    - **[[Brute Force]] attacks** : essais multiples pour deviner identifiants.
        
    - **Mots de passe faibles** : absence de politique de mots de passe robustes.
        
    - **Cookies de session faibles/prévisibles** : possibilité pour un attaquant de forger ses propres cookies.
        
- **Mesures de protection :**
    
    - Politique de mots de passe forts.
        
    - Blocage automatique après plusieurs tentatives ratées.
        
    - Authentification multi-facteurs (MFA).