**Automated discovery** = utilisation d’outils (ffuf, dirb, gobuster…) pour tester automatiquement des milliers de chemins sur un site afin de trouver des fichiers/répertoires cachés.  
**Wordlists** = simples fichiers texte listant des noms courants (répertoires, fichiers) — exemple recommandé : **SecLists** (`/usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt`).  
Commandes exemples (AttackBox) :

- `ffuf -w /usr/share/wordlists/.../common.txt -u http://10.10.53.67/FUZZ`
    
- `dirb http://10.10.53.67/ /usr/share/wordlists/.../common.txt`
    
- `gobuster dir --url http://10.10.53.67/ -w /usr/share/wordlists/.../common.txt`