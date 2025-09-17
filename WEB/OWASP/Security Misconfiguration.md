**Security Misconfigurations**  
Ces failles apparaissent quand la sécurité _aurait pu être correctement configurée_, mais ne l’a pas été. Elles sont très fréquentes et souvent dues à la négligence.

- **Exemples courants :**
    
    - Permissions mal configurées (ex. S3 buckets accessibles).
        
    - Fonctionnalités inutiles laissées actives (services, comptes, privilèges).
        
    - Comptes par défaut avec mots de passe non changés.
        
    - Messages d’erreur trop détaillés.
        
    - Absence d’en-têtes HTTP de sécurité.
        
- **Conséquences :**  
    → Peut mener à d’autres vulnérabilités (XXE, injection de commandes, accès à des données sensibles).
    
- **Cas particulier : Debugging interfaces**
    
    - Les frameworks offrent des outils de débogage utiles en développement, mais dangereux en production s’ils sont exposés.
        
    - Exemple : **Patreon (2015)** — un _debug console_ Werkzeug (Python) accessible publiquement a permis à des attaquants d’exécuter du code arbitraire.