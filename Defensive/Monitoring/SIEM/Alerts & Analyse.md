### 1. Dashboards

Les **tableaux de bord** sont essentiels : ils présentent les données normalisées sous forme de résumés visuels et d’**insights exploitables**. On y retrouve par exemple :

- Alertes récentes
- Notifications système / santé
- Tentatives de connexion échouées
- Nombre d’événements ingérés
- Règles déclenchées
- Domaines les plus visités

### 2. Correlation Rules

Ces règles permettent une détection rapide des menaces. Exemples :
- Plusieurs échecs de connexion en peu de temps → alerte brute force.
- Connexion réussie après des échecs → alerte connexion suspecte.
- Détection d’un périphérique USB interdit.
- Trafic sortant élevé → suspicion d’exfiltration de données.

**Cas concrets :**

- Event ID 104 = suppression de logs → alerte.
- Event ID 4688 + exécution de `whoami` → alerte commande suspecte.
### 3. Investigation d’alertes

Une fois une alerte générée, l’analyste :
- Vérifie si c’est un **faux positif** (et ajuste la règle si nécessaire).
- Confirme un **vrai positif** et enquête plus en détail.
- Contacte le propriétaire de l’actif.
- Peut aller jusqu’à **isoler l’hôte** infecté ou **bloquer une IP**.

👉 En bref : le SIEM centralise les logs, applique des règles de corrélation pour détecter les menaces, les analystes s’appuient sur les **dashboards** pour enquêter et réagir rapidement.