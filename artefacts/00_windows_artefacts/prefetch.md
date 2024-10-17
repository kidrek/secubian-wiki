# Prefetch


Les fichiers Prefetch sont des artéfacts Windows très importants pour les enquêtes forensiques :
- Ils sont créés par le système d'exploitation Windows lorsqu'une application est exécutée pour la première fois depuis un emplacement donné. 
- Leur but est d'accélérer le chargement des applications en préchargeant les fichiers et DLL nécessaires.
- Ils contiennent des informations très utiles pour les enquêteurs, comme le nom de l'exécutable, les DLL requises, les horodatages des dernières exécutions, et le nombre de fois que l'application a été lancée.
- Même si un fichier malveillant a été supprimé, sa présence dans les fichiers Prefetch peut encore révéler qu'il a été exécuté.
- Les criminels peuvent désactiver le Prefetch pour effacer plus facilement les traces de leurs activités illégales, au prix d'une dégradation des performances.
- Les fichiers Prefetch se trouvent dans le répertoire ```%SystemRoot%\Prefetch``` (généralement ```C:\Windows\Prefetch```) et suivent une convention de nommage spécifique, mais ont une extension commune ```.pf```.
- Leur analyse, combinée à celle d'autres artéfacts Windows comme les journaux d'événements et la MFT, permet de reconstituer avec précision l'historique des activités sur un système.

En résumé, les fichiers Prefetch sont des éléments essentiels pour toute enquête forensique sur un système Windows, car ils fournissent de précieuses informations sur les applications exécutées. Une attention particulière devra être réalisée car ces derniers peuvent être altérés par un acteur malveillant ayant des privilèges élevés.

Une attention particulière doit être réalisée sur les limites définies par le système d'exploitation. 
- Sur les OS Microsoft Windows XP -> 7, seules 128 entrées (fichiers prefetch) ne peuvent être créés ;
- Sur les OS Microsoft Windows récents à partir de Windows 8, seules 1024 entrées (fichiers prefetch) ne peuvent être réalisées ; 

<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape | ```#windows``` | https://ericzimmerman.github.io/KapeDocs/#!External\Remote_Collections_KAPE\Remote%20Collections%20with%20KAPE.md |
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
| Timesketch | ```#linux```  | |

<br/>


------
## Références :
- https://www.magnetforensics.com/fr/blog/analyse-judiciaire-de-fichiers-de-prerecuperation-dans-windows/
- https://openclassrooms.com/fr/courses/1750151-menez-une-investigation-d-incident-numerique-forensic/6474302-identifiez-les-artefacts-windows-dinteret-pour-linvestigation
- https://book.hacktricks.xyz/v/fr/generic-methodologies-and-resources/basic-forensic-methodology/windows-forensics
- https://www.infosecinstitute.com/resources/digital-forensics/windows-systems-artifacts-digital-forensics-part-iii-prefetch-files/
- https://countuponsecurity.com/2016/05/16/digital-forensics-prefetch-artifacts/
- https://dfir.ru/2024/04/09/operation-based-prefetching/