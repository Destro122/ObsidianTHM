Dans un réseau, chaque appareil génère des **logs** lorsqu’une activité se produit (connexion SSH, navigation web, authentification, etc.). Ces journaux, collectés par un **SIEM**, permettent une meilleure visibilité et détection des incidents.

### Sources de logs :

- **Machines Windows** : événements enregistrés avec des IDs uniques via l’Event Viewer.
- **Machines Linux** : logs stockés dans différents fichiers (ex. `/var/log/auth.log` pour l’authentification, `/var/log/cron` pour les tâches planifiées, `/var/log/httpd` pour le web).
- **Serveur web** : logs Apache/HTTP pour surveiller les requêtes et détecter d’éventuelles attaques.
### Méthodes d’ingestion des logs par un SIEM :

1. **Agent / Forwarder** → logiciel installé sur l’endpoint pour envoyer les logs.
2. **Syslog** → protocole standard pour centraliser les données.
3. **Upload manuel** → importation de fichiers de logs pour analyse.
4. **Port-forwarding** → configuration d’un port d’écoute pour recevoir les logs.
    

👉 Ces méthodes permettent au SIEM de **centraliser, normaliser et analyser** les logs en temps réel pour renforcer la sécurité.