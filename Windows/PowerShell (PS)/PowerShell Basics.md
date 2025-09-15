
Powershell permet d'automatiser des tâches et de manage la config.  
Fait en .NET.
Il est orienté Objet.
Développé pour windows il est maintenant sur MacOS et Linux 

#### **Syntaxe de base : Verbe-Nom**
Les command-lets (cmdlets) sont les lignes de commandes PowerShell exemple : Get-Content

- Get-Command : renvoie une liste des commandes PS
- Get-Command -CommandType "Function" : renvoie uniquement les fonctions (filtre)
- Get-Help : Obtenir l'aide sur une commande
- dir/Get-ChildItem : voir les fichiers dans le dossier
- cd/SetLocation

Il est possible de télécharger des cmdlets pour nos différents usages. 
- Find-Module + filtres : chercher des modules
- Install-Module -Nama "name" : installe le module
