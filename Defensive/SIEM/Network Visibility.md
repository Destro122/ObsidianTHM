Un réseau est composé de plusieurs machines (Linux/Windows, serveur de données, site web, etc.) qui communiquent entre elles et génèrent des **logs**. Ces journaux se divisent en deux grandes catégories :

1. **Logs centrés sur l’hôte (Host-Centric)**
    - Décrivent les activités internes à une machine.
    - Exemples : accès à un fichier, tentative de connexion, exécution d’un processus, modification du registre, exécution PowerShell.
2. **Logs centrés sur le réseau (Network-Centric)**
    - Concernent les communications entre machines ou avec Internet.
    - Exemples : connexion SSH, transfert FTP, navigation web, accès via VPN, partage de fichiers réseau.

**Importance du SIEM (Security Information and Event Management)**  
Comme chaque composant génère énormément d’événements, analyser manuellement chaque log est impraticable. Le SIEM centralise les journaux, permet de les corréler et d’en tirer des informations exploitables. Ses principaux avantages sont :

- Collecte et analyse des logs en temps réel.
- Détection et alertes sur les activités anormales.
- Supervision 24/7 et visibilité globale.
- Détection précoce des menaces.
- Visualisation et insights sur les données.
- Possibilité d’investiguer des incidents passés.