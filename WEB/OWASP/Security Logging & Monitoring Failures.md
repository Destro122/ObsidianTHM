Le **logging** consiste à enregistrer toutes les actions des utilisateurs dans une application web. Il est crucial pour :

- **Tracer les attaques** et déterminer l’impact et le risque.
- **Répondre aux incidents** et respecter les réglementations (ex. fuite de données personnelles).
- **Prévenir des attaques futures** en détectant la présence d’attaquants.

### 🔹 Informations importantes à logger

- Codes HTTP
- Horodatages
- Noms d’utilisateur
- Endpoints/API
- Adresses I
Ces logs doivent être **sécurisés** et **répliqués** à différents endroits.

### 🔹 Surveillance et détection d’activités suspectes

- Tentatives non autorisées multiples (ex. authentifications échouées)
- Accès depuis des IP ou localisations inhabituelles
- Utilisation d’outils automatisés (identifiable via User-Agent ou rapidité des requêtes)
- Utilisation de payloads connus par les attaquants

### 🔹 Réaction à la détection

- Noter le **niveau d’impact** de l’activité suspecte
- Déclencher des alertes pour les actions à fort impact
- Réduire les dégâts ou stopper l’attaquant dès détection