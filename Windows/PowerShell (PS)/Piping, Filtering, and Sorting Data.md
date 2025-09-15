Représenté par le symbole |  Piping permet de créer une séquence d'opérations sur un flow de data.

Exemple : Get-ChildItem | Sort-Object Length

`Sort-Object` : Permet de trier les objets avec différents parametre
`Where-Object` : Permet de filtrer avec des conditions 
	- Exemple : Get-ChildItem | Where-Object -Property "Extension" -eq ".txt" renvoie tout les fichiers textes
	- -like permet de chercher par paterne
 `Select-Object` : Permet de limiter le retour de la commande pour afficher par exemple que les noms des fichiers avec Get-ChildItem
  `Select-String` : Permet de chercher un pattern dans un fichier texte
  