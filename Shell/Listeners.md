### 🔹 **Rlwrap**
- Petit utilitaire basé sur la librairie GNU Readline.
- **Améliore Netcat** : permet d’utiliser les flèches du clavier, l’historique des commandes, l’édition plus confortable.
- **Exemple** :
```bash
	rlwrap nc -lvnp 443
```
### 🔹 **Ncat**
- Version améliorée de Netcat, développée par le projet **Nmap**.
- Avantages : plus de fonctionnalités, **support du chiffrement SSL**.
- **Exemple simple** :
```bash
ncat -lvnp 4444
ncat --ssl -lvnp 4444
```
### 🔹 **Socat**
- Outil polyvalent qui établit des connexions entre deux flux de données (ex. deux hôtes).
- Très flexible, utilisé pour **tunnels, redirections de ports, shells cryptés, etc.**
- **Exemple simple**:
```bash
socat -d -d TCP-LISTEN:443 STDOUT
```
- `-d -d` : mode verbeux.
- `TCP-LISTEN:443` : ouvre un listener TCP sur le port 443.
- `STDOUT` : affiche la sortie directement dans le terminal.