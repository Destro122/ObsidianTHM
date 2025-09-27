### **Netfilter**
C’est le **framework interne de Linux** qui fournit les fonctionnalités de base d’un pare-feu :

- **Filtrage de paquets**
- **NAT (Network Address Translation)**
- **Suivi de connexions**

Plusieurs utilitaires reposent sur Netfilter :

- **iptables** → l’outil historique et le plus répandu.
- **nftables** → successeur d’iptables, plus moderne et performant.
- **firewalld** → basé sur des zones réseau préconfigurées, plus simple à gérer.

### **ufw (Uncomplicated Firewall)**

- Interface simplifiée pour gérer les règles iptables/nftables.
- Plus accessible aux débutants grâce à des commandes claires.

**Exemples de commandes :**

- Vérifier l’état du pare-feu : `sudo ufw status`
- Activer/désactiver : `sudo ufw enable` / `sudo ufw disable`
- Autoriser tout le trafic sortant par défaut : `sudo ufw default allow outgoing`
- Bloquer SSH entrant : `sudo ufw deny 22/tcp`
- Lister les règles : `sudo ufw status numbered`
- Supprimer une règle : `sudo ufw delete <numéro>`