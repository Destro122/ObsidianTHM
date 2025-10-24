Les failles d’injection apparaissent lorsque des entrées contrôlées par l’utilisateur sont interprétées comme des commandes ou des paramètres par l’application.

- **Exemples courants :**
    
    - **SQL Injection** : l’attaquant insère du code SQL pour lire, modifier ou supprimer des données sensibles (ex. identifiants, infos personnelles).
        
    - **Command Injection** : l’attaquant injecte des commandes système pour exécuter du code arbitraire sur le serveur.
        
- **Moyens de défense :**
    
    - **Allow list (liste blanche)** : n’accepter que des entrées considérées comme sûres.
        
    - **Stripping input** : supprimer les caractères dangereux avant traitement.

See [[WEB/Vulnerabilities/Command Injection]] for practical examples and exploitation methods.
