- **Navigateur intégré** : Burp Suite inclut un navigateur Chromium déjà configuré pour fonctionner avec le proxy (pas besoin de modifier son navigateur habituel).
    
- **Lancement** : via le bouton _Open Browser_ dans l’onglet Proxy. Toutes les requêtes passent automatiquement par le proxy.
    
- **Paramètres** : de nombreuses options liées au Burp Browser sont disponibles dans _Project options_ et _User options_.
    

---

### Problème sous Linux en root (ex. AttackBox)

- **Cause** : impossibilité de créer un environnement sandbox, empêchant le démarrage du Burp Browser.
    

**Solutions** :

1. **Option recommandée (sécurisée)** : créer un utilisateur non-root et lancer Burp Suite avec ce compte.
    
2. **Option rapide (moins sécurisée)** : activer _Allow Burp's browser to run without a sandbox_ dans  
    `Settings -> Tools -> Burp's browser`.
    
    - ⚠️ Risque : si le navigateur est compromis, l’attaquant peut avoir accès au système entier.
        
    - Utilisable sans trop de risque dans un environnement d’entraînement (AttackBox).