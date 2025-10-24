### **Modes de déploiement des IDS**

- **HIDS (Host-based IDS)** : installé sur chaque machine → visibilité détaillée des activités de l’hôte, mais lourd à gérer sur de grands réseaux.
- **NIDS (Network-based IDS)** : surveille le trafic réseau global → vision centralisée, détecte les activités suspectes sur l’ensemble du réseau.

### **Modes de détection**

- **Signature-based IDS** : compare les attaques aux **signatures connues** → efficace contre les menaces déjà répertoriées, mais incapable de détecter les **attaques zero-day**.
- **Anomaly-based IDS** : établit un **comportement normal (baseline)** et détecte les écarts → capable de repérer des zero-day, mais génère souvent des **faux positifs** (réduits par un bon tuning).
- **Hybrid IDS** : combine signatures et anomalies → tire parti des deux méthodes (détection rapide des menaces connues + détection de nouvelles menaces).