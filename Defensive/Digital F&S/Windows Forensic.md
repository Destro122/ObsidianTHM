### **Acquisition et analyse de preuves sur Windows**
#### **Types d’images forensiques**
1. **Disk image (image disque)**
    - Copie bit-à-bit du disque (HDD/SSD).
    - Données **non volatiles** → survivent après redémarrage.
    - Contient : fichiers, documents, médias, historique de navigation, etc.

2. **Memory image (image mémoire vive)**
    - Copie du contenu de la RAM.
    - Données **volatiles** → perdues si l’ordinateur est éteint ou redémarré.
    - Contient : fichiers ouverts, processus en cours, connexions réseau actives.
    - ⚠️ **Priorité** : à capturer avant extinction/redémarrage.

---

#### **Outils populaires**

- **FTK Imager**
    - Acquisition : création d’images disques (formats variés).
    - Analyse basique : visualiser et explorer le contenu d’une image.
    - Interface graphique conviviale.
- **Autopsy**
    - Plateforme open-source d’analyse d’images disques.
    - Fonctions : recherche par mots-clés, récupération de fichiers supprimés, métadonnées, détection de fichiers suspects (extension mismatch).
- **DumpIt**
    - Outil en ligne de commande pour acquérir une image mémoire.
- Génère la capture RAM dans différents formats.
- **Volatility**
    - Outil open-source d’analyse mémoire.
    - Utilise des plugins spécialisés pour examiner processus, connexions, artefacts, etc.
    - Compatible Windows, Linux, macOS, Android.

---

👉 En résumé : sur Windows, les enquêteurs doivent acquérir **deux images complémentaires (disque + mémoire)**. Les outils comme **FTK Imager et Autopsy** servent surtout pour les disques, tandis que **DumpIt et Volatility** sont essentiels pour la mémoire.