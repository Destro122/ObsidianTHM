IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability.

Un IDOR survient quand une application permet d’accéder à une ressource (profil, facture, fichier…) simplement en modifiant un identifiant fourni côté client (URL, POST, cookie, en-tête) **sans vérifier que le requérant est bien autorisé**. Exemple :  
`/profile?user_id=1305` → changer `1305` en `1000` donne accès au profil d’un autre utilisateur.

---
# Étapes pour détecter et confirmer un IDOR

1. **Modifier l’identifiant visible**
    - Dans l’URL : change `user_id=1305` → `user_id=1000`.
    - Dans un POST : intercepte la requête (DevTools ou Burp) → édite le champ `user_id`.
    - Dans un cookie / header : modifie et renvoie la requête.
2. **Tester la logique d’autorisation** (critère de confirmation)
    - Crée **2 comptes distincts** (A et B).
    - Connecte-toi en A et demande la ressource de B (`user_id=B_id`).
    - Si A voit la ressource de B => IDOR confirmé.
    - Tester aussi quand **non authentifié** (si la ressource est visible sans login, c’est grave).
3. **Vérifier les variations d’identifiants**
    - Incrémente/décrémente l’ID (`+1`, `-1`) pour voir si d’autres profils sont accessibles.
    - Tenter des IDs hauts/0/negatifs/strings.
4. **Savoir où chercher l’endpoint vulnérable**
    - Barre d’adresse (querystring).
    - Requêtes AJAX (onglet Network dans DevTools).
    - Fichiers JS (chercher `/user/`, `details`, `profile`, `user_id` dans le source).
    - Paramètres non documentés (parameter mining).