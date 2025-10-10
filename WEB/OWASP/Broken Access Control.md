On parle de [[Broken Access Control]] lorsque l'on accède à acceder à une page du site qui nous permet de bypass les autorisations nécessaires. 

Chopper des infos d'autres utilisateurs, fonctionnalité admin etc..
### Insecure Direct Object Reference ([[IDOR]])
**IDOR** or **Insecure Direct Object Reference** refers to an access control vulnerability where you can access resources you wouldn't ordinarily be able to see. This occurs when the programmer exposes a Direct Object Reference, which is just an identifier that refers to specific objects within the server. By object, we could mean a file, a user, a bank account in a banking application, or anything really.

Exemple : changer l'url avec ?note_id=2 au lieu du miens (1)
