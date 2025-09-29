## 🛑 **CVE (Common Vulnerabilities and Exposures)**

- **Définition :** Identifiant unique attribué à une vulnérabilité.
- **But :** Permet d’uniformiser et de référencer chaque vulnérabilité découverte dans le monde entier
- **Gestion :** Développé et maintenu par la **MITRE Corporation**.
- **Structure d’un CVE :**
    - **Préfixe :** `CVE`
    - **Année :** année de découverte
    - **Identifiant numérique :** numéro unique attribué (4+ chiffres)

🔎 **Exemple :** `CVE-2024-9374`  
→ Vulnérabilité découverte en 2024, avec l’ID 9374.
- **Utilité :** facilite la recherche dans les bases de données publiques comme la **CVE database**, la **NVD (National Vulnerability Database)** ou directement dans les bulletins des éditeurs logiciels.

---

## ⚖️ **CVSS (Common Vulnerability Scoring System)**

- **Définition :** Système de notation normalisé qui attribue un **score de gravité (0–10)** à chaque vulnérabilité.
- **Objectif :** Prioriser les vulnérabilités selon leur criticité.
- **Critères pris en compte :**
    - Facilité d’exploitation
    - Impact potentiel (confidentialité, intégrité, disponibilité)
    - Conditions requises pour l’attaque

| CVSS Score Range | Severity Levels |
| ---------------- | --------------- |
| 0.0-3.9          | Low             |
| 4.0-6.9          | Medium          |
| 7.0-8.9          | High            |
| 9.0-10           | Critical        |