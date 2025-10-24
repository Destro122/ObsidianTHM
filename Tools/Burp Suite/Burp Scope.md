- **Problème** : sans scope, Burp capture _tout_ le trafic → rapidement encombrant et inutile.
    
- **Solution** : définir un **scope** (périmètre) pour cibler uniquement les applis web à tester.
    

---

### Mise en place du scope

1. Aller dans l’onglet **Target**.
    
2. Clic droit sur la cible → **Add to Scope**.
    
3. Burp propose d’arrêter de logger le hors-scope → en général, choisir **Yes**.
    
4. Vérifier/modifier le périmètre dans **Scope settings** (inclure/exclure domaines/IP).
    

---

### Affinage côté Proxy

- Même si le logging hors-scope est désactivé, le proxy **intercepte toujours tout**.
    
- Pour éviter ça :
    
    - Aller dans **Proxy → Proxy settings → Intercept Client Requests**.
        
    - Activer l’option **And URL Is in target scope**.
        

👉 Résultat : seul le trafic défini dans le scope est intercepté et loggé → interface plus claire et mieux ciblée.

---