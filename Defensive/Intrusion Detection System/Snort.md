- Open-source **IDS** créé en 1998.
- Combine **détection par signatures** (attaques connues) et **par anomalies** (comportements suspects).
- Fonctionne avec des **fichiers de règles intégrés** (déjà fournis) mais permet aussi :
    - de créer des **règles personnalisées** pour des besoins spécifiques,
    - de désactiver des règles inutiles ou non pertinentes.
### **Modes de fonctionnement de Snort**
1. **Packet Sniffer Mode**
    - Lit et affiche les paquets réseau **sans analyse**.
    - Utile pour le **diagnostic** et le monitoring du trafic.
2. **Packet Logging Mode**
    - Enregistre le trafic réseau dans des fichiers **PCAP**.
    - Sert aux **enquêtes forensiques** et à l’analyse a posteriori d’attaques.
3. **NIDS Mode (Network Intrusion Detection System)**
    - Mode principal de Snort.
    - Analyse le trafic en temps réel et déclenche des **alertes** si une règle correspond à une attaque connue.
    - Sert à la **détection proactive** des menaces.
---
### **Fichiers Snort**

- Dossier principal : `/etc/snort`
    
- Fichiers importants :
    
    - **snort.conf** → fichier de configuration (réseau à surveiller, règles activées, etc.)
        
    - **rules/** → contient les fichiers de règles (par défaut + personnalisées).
        
    - **local.rules** → fichier dédié aux règles personnalisées.
        

### **Format d’une règle Snort**

Exemple :
```php
alert icmp any any -> $HOME_NET any (msg:"Ping Detected"; sid:10001; rev:1;)
```
- **Action** : ex. `alert` (que faire quand ça matche)
    
- **Protocole** : TCP, UDP, ICMP…
    
- **Source IP/port** : origine du trafic (ex. `any`)
    
- **Destination IP/port** : cible (ex. `$HOME_NET`)
    
- **Metadata** :
    
    - `msg` → message affiché
        
    - `sid` → identifiant unique
        
    - `rev` → version/révision de la règle
        

### **Création & Test d’une règle**

1. Ajouter une règle dans **local.rules** (ex. détecter un ping ICMP sur `127.0.0.1`).
    
2. Lancer Snort en mode détection temps réel :
```bash
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf
```
Tester avec un `ping 127.0.0.1` → Snort déclenche une alerte **"Loopback Ping Detected"**.
### **Analyse de fichiers PCAP**

Snort peut aussi analyser du trafic **historique** (fichiers `.pcap`) pour la **forensic analysis** :
```bash
sudo snort -q -l /var/log/snort -r Task.pcap -A console -c /etc/snort/snort.conf
```
