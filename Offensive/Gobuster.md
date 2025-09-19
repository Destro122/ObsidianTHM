gobuster command flags

---

## Available Commands

- **dir** → énumération de répertoires/fichiers
    
- **dns** → énumération de sous-domaines DNS
    
- **fuzz** → fuzzing, remplace le mot-clé `FUZZ` dans l’URL, headers ou body
    
- **gcs** → Google Cloud Storage bucket enumeration
    
- **s3** → Amazon AWS S3 bucket enumeration
    
- **tftp** → TFTP enumeration
    
- **vhost** → VHOST enumeration (généralement avec l’adresse IP comme URL)
    

---

## Flags utiles

- **-t / --threads** : nombre de threads (par défaut 10). Plus rapide avec gros wordlists si augmenté.
    
- **-w / --wordlist** : chemin du wordlist utilisé.
    
- **--delay** : délai entre requêtes (utile pour éviter la détection).
    
- **--debug** : mode debug, utile si erreurs inattendues.
    
- **-o / --output** : enregistre les résultats dans un fichier.
    
- **-q / --quiet** : sortie plus silencieuse (pas de bannière, moins de bruit).
    
- **-v / --verbose** : sortie verbeuse (plus de détails).
    

---

## Notes

- On utilise principalement **dir**, **dns** et **vhost** en pentest web.
    
- Augmenter le nombre de threads (`-t`) accélère l’énumération mais peut surcharger le serveur cible.
    
- Ajouter un délai (`--delay 1500ms`) peut aider à contourner la détection.