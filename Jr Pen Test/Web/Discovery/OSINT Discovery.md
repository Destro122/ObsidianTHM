**Google Hacking / Dorking**

- Utilise les opérateurs de recherche avancée de Google pour filtrer les résultats et trouver des pages/ressources spécifiques liées à une cible.
    
- Opérateurs utiles :
    
    - `site:exemple.com` → résultats uniquement sur ce domaine
        
    - `inurl:admin` → mots présents dans l’URL
        
    - `filetype:pdf` → fichiers avec une extension donnée
        
    - `intitle:admin` → mot dans le titre de la page
        
- Permet de découvrir panneaux d’administration, docs sensibles, backups publiés, etc.
    

**Wappalyzer**

- Extension/webservice qui identifie les technologies d’un site (frameworks, CMS, bibliothèques, versions, processeurs de paiement…).
    
- Utile pour rapidement connaître la stack et cibler des vulnérabilités connues.
    

**Wayback Machine**

- Archive historique des sites web (archive.org/web).
    
- Permet de retrouver anciennes pages, contenus supprimés ou endpoints obsolètes mais encore accessibles.
    

**GitHub**

- Plateforme de dépôt de code (Git).
    
- Recherche GitHub peut révéler : code source, clés API accidentelles, fichiers de configuration, mots de passe, chemins internes.
    
- Chercher par nom d’entreprise, domaine ou noms de projets liés à la cible.
    

**S3 Buckets (AWS)**

- Stockage en ligne dont les URL suivent souvent le format : `https://{name}.s3.amazonaws.com`.
    
- Mauvaises configurations (public/readable) exposent fichiers sensibles.
    
- Découverte via page source, GitHub, noms prédictifs (`{company}-assets`, `{company}-www`, `{company}-backup`, etc.) ou automatisation.