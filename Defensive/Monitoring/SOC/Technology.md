Avoir les **personnes** et les **processus** ne suffit pas : la **technologie** (solutions de sécurité) est indispensable pour **détecter et répondre efficacement** aux menaces, tout en réduisant l’effort manuel de l’équipe SOC.

Les solutions technologiques :
- Centralisent les informations de tous les appareils et applications du réseau.
- Automatisent la détection et la réponse.
---
### Principales solutions de sécurité
- **SIEM (Security Information and Event Management)**
    - Collecte les logs de multiples sources (appareils, applications).
    - Utilise des règles de détection + corrélation de logs pour identifier une activité suspecte.
    - Modernes SIEM → ajoutent **analytique comportementale**, **threat intelligence** et **machine learning**.
    - **Limite** : n’offre que des capacités de **détection**, pas de réponse.
- **EDR (Endpoint Detection and Response)**
    - Surveillance détaillée en temps réel et historique des terminaux (endpoints).
    - Peut exécuter des réponses automatiques.
    - Forte capacité de détection et d’investigation au niveau endpoint.
- **Firewall**
    - Barrière entre le réseau interne et externe (Internet).
    - Surveille et filtre le trafic entrant/sortant.
    - Peut bloquer du trafic suspect via des règles de détection.

---

### Autres solutions utiles

- **Antivirus**
- **EPP (Endpoint Protection Platform)**
- **IDS/IPS (Intrusion Detection/Prevention System)**
- **XDR (Extended Detection and Response)**
- **SOAR (Security Orchestration, Automation and Response)**
Le choix dépend de :
- la **surface de menace** à protéger,
- les **ressources disponibles** de l’organisation.