### **1. Content-Security-Policy (CSP)**

- Définit les sources autorisées pour charger du contenu (scripts, styles, images, etc.).
    
- Aide à limiter les injections de code malveillant ([[XSS]]).
    
- Exemple :
	Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'

    default-src 'self' → uniquement le site lui-même

    script-src → scripts autorisés depuis self + un CDN

    style-src → feuilles de style uniquement depuis self

### **2. Strict-Transport-Security (HSTS)**

- Force l’utilisation de **HTTPS**.
    
- Exemple :
	Strict-Transport-Security: max-age=63072000; includeSubDomains; preload

    max-age → durée en secondes

    includeSubDomains → inclut les sous-domaines

    preload → permet l’ajout dans les listes de préchargement des navigateurs