# 🛡️ Defensive Index

Ce répertoire regroupe l’ensemble des notions, outils et concepts liés à la **sécurité défensive**, à la **surveillance**, à la **détection d’incidents** et à la **réponse aux menaces**.  
Chaque sous-section est interconnectée avec ses thématiques voisines (Firewall ↔ IDS ↔ SIEM ↔ SOC).

---

## 🔍 Digital Forensics & Sécurité
Étude, acquisition et analyse des preuves numériques utilisées dans les investigations.

- [[Digital Forensic]] – Introduction aux enquêtes numériques.  
- [[Method]] – Phases NIST : collecte, examen, analyse, reporting.  
- [[Preuves]] – Chaîne de garde et meilleures pratiques.  
- [[Windows Forensic]] – Analyse spécifique des systèmes Windows.

Liens utiles : [[SIEM]] | [[SOC]]

---

## 🔥 Firewalls
Barrière de protection entre réseaux internes et externes, essentielle dans toute stratégie défensive.

- [[Firewall Types]] – Stateless, Stateful, Proxy, Next-Gen Firewalls.  
- [[Linux Firewall]] – iptables, nftables, ufw, règles et commandes.  
- [[Rules]] – Structure, syntaxe et logique des règles de filtrage.

Liens utiles : [[IDS]] | [[SOC]] | [[Network Visibility]]

---

## 🕵️ Intrusion Detection System (IDS)
Outils de surveillance du trafic réseau et des hôtes pour identifier des comportements anormaux.

- [[Snort]] – IDS open-source, configuration, règles et détection.  
- [[Types of IDS]] – Comparaison HIDS, NIDS et Hybrid IDS.

Liens utiles : [[SIEM]] | [[SOC]] | [[Firewall]]

---

## 📊 SIEM (Security Information and Event Management)
Collecte, corrélation et analyse centralisée des événements de sécurité.

- [[Why SIEM]] – Rôle et utilité du SIEM dans une infrastructure moderne.  
- [[Log Sources and Injections]] – Collecte et ingestion des logs.  
- [[Network Visibility]] – Types de logs (host/network) et supervision.  
- [[Alerts & Analyse]] – Dashboards, règles de corrélation et investigation.

Liens utiles : [[SOC]] | [[IDS]]

---

## 🧠 SOC (Security Operations Center)
Centre opérationnel regroupant les analystes, process et technologies pour détecter et répondre aux menaces.

- [[SOC]] – Fonctionnement et mission du centre de sécurité.  
- [[People]] – Rôles des analystes tiers et hiérarchie du SOC.  
- [[Process]] – Gestion des alertes (5Ws), triage, escalade.  
- [[Technology]] – Outils complémentaires (EDR, SIEM, SOAR, XDR).

Liens utiles : [[SIEM]] | [[Firewall]] | [[Digital Forensic]]

---
## Mitigation 
- See [[Race Conditions]] for vulnerability context.
- See [[Command Injection]] for techniques related to input sanitization and safe system call handling.
- See [[SQLi - Remediation]] for defensive practices against SQL injection.
## 📚 Tags
#defensive #forensics #firewall #siem #soc #ids