# Microsoft Edge based on Chromium

L'analyse de l'historique de navigation web/téléchargement peut apporter des informations précieuses durant une investigation numérique.


## Emplacement des artefacts

* Microsoft Windows : ```%Rootdrive%:\Users\{utilisateur}\AppData\Local\Microsoft\Edge\User Data\Default\```
* MacOS : ```~/Library/Application Support/Microsoft Edge Dev```

| Artefacts | Fichiers | Type de fichiers |
|----|----|----|
| Historique de navigation/téléchargement |```History``` | Bdd Sqlite |
| Information d'authentification | ```Login Data```  |
| Cookies de navigation | ```Network/Cookies``` |
| Liste des extensions installées | ```Extensions``` | 
| Informations relatives aux favicons correspondant aux sites visités | ```Favicons``` |
| Informations relatives aux données saisies dans les formulaires de pages web | ```Web Data``` |

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| Velociraptor | ```#windows``` | https://docs.velociraptor.app/artifact_references/pages/windows.kapefiles.targets/ |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| Plaso / Log2timeline | ```#linux```  | https://plaso.readthedocs.io/en/latest/sources/user/Parsers-and-plugins.html |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>

Sources : 
- https://medium.com/@jsaxena017/web-browser-forensics-part-1-chromium-browser-family-99b807083c25