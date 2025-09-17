Les failles de conception _ne viennent pas d’une mauvaise implémentation ou configuration_, mais de l’architecture même de l’application.

- **Origine :**
    
    - Mauvais _threat modelling_ (analyse des menaces) dès la phase de conception.
        
    - Introduction de raccourcis ou faiblesses volontaires laissés par les développeurs (ex. désactiver une validation OTP pour tester, mais oublier de la réactiver en production).
        
- **Caractéristique clé :**  
    → La vulnérabilité est présente dès l’idée ou le design, et se propage jusqu’à l’application finale.