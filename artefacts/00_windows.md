# Système d'exploitation Microsoft Windows

## Les fichiers accédés/altérés

### _ Le système de fichiers NTFS
Ces artefacts permettent de retracer les différentes actions réalisées sur le système de fichiers. 

| Nom | Description | Références |
|-----|-------------|------------|
| $BITMAP |  | |
| $I30 |  | [détails](./00_windows_artefacts/ntfs/i30.md) |
| $LOGFILE | Le $LOGFILE, également appelé "Transaction Log", est un artefact important du système de fichiers NTFS (New Technology File System) utilisé par Windows. Pour les enquêtes forensiques, le $LOGFILE est très utile car il permet de reconstituer l'historique des modifications sur le système de fichiers, y compris pour des fichiers supprimés qui n'auraient plus de métadonnées dans la MFT. Cependant, le $LOGFILE manque de précision temporelle car il n'inclut pas d'horodatages détaillés comme le $UsnJrnl. | [détails](./00_windows_artefacts/ntfs/logfile.md) |
| $MFT |  La MFT est une structure de données importante dans les systèmes de fichiers Windows. Il contient des métadonnées sur tous les fichiers et dossiers présents sur un volume NTFS.  | [détails](./00_windows_artefacts/ntfs/mft.md) |
| $SECURE |  | |
| $USNJRNL | Le $UsnJrnl est un journal des changements (change log journal) qui enregistre les modifications effectuées sur les fichiers et dossiers d'un volume NTFS au sein de l’attribut $EXTEND de la MFT. | [détails](./00_windows_artefacts/ntfs/usnjrnl.md) |

Voici quelques références utiles : 
- http://ntfs.com/ntfs_basics.htm

<br/>

### _ Les fichiers accédés

Ces artefacts sont plus génériques mais permettent de retracer les différentes actions réalisées sur des fichiers. 

| Nom | Description | Références |
|-----|-------------|------------|
| EventLogs - Accès aux partages réseau| Il est tout à fait possible d'accéder à l'historique des répertoires partagés distants accédés via la journalisation de les EventIDs 5140, 5142, 5143 et 5144. Néanmoins, il est nécessaire d'activer une stratégie d'audit ```Audit File Share``` (très verbeux)  |  |
| EventLogs - Accès aux fichiers partagés | Il est tout à fait possible d'accéder à l'historique des fichiers accédes sur des dossiers distants via la journalisation de les EventIDs 5145. Néanmoins, il est nécessaire d'activer une stratégie d'audit ```Audit Detailed File Share``` (très verbeux)  |  |
| JumpList |  |   |
| Map Network Drive MRU |  |   |
| MountPoints2 |  |   |
| OpenSaveMRU |  |   |
| Recent Apps |  |   |
|RecentDocs| Cet artefact retrace les derniers fichiers et répertoires accédés. |[détails](./00_windows_artefacts/registry/recentdocs.md)|
| Run MRU |  | [détails](./00_windows_artefacts/registry/runmru.md)  |
|ShellBags| Cet artefact permet de retracer les dossiers et fichiers récemment ouverts par les utilisateurs.|[détails](./00_windows_artefacts/registry/shellbags.md)|
|Trusted Documents| Cet artefact permet de visualiser les actions de confiances accordées à certains documents Microsoft Office (ex: execution de macro) |[détails](./00_windows_artefacts/registry/trustedDocuments.md)|
| TypedPaths |  |   |
| Windows 10 Timeline |  Il s'agit d'une timeline intégrée à partir de Microsoft Windows 10 version 1803, qui a pour objectif de journaliser l'ensemble des événements réalisés sur le système (ex: programmes exécutés, fichiers locaux accédés, ...) | [détails](./00_windows_artefacts/windows_timeline_ activitiescache.md) |
| WebCacheV01.dat | | |
| Windows Search database | | |
| WordWheelQuery | | |

<br/>

## Les applications exécutées

Chaque exécution de processus est journalisée de différentes manières : 
- A travers des fichiers sur le système (ex: Prefetch) ;
- A travers les ruches système de la base de registre ;
- A travers les ruches de chacun des utilisateurs, présentes dans le fichiers NTUSER.DAT de chacun des profils utilisateurs ;
- A travers la journalisation système et les différents EventID dédiés ;

<br/>

| Nom | Description | Références |
|-----|-------------|------------|
| Amcache | Amcache est une ruche de la base de registre dédiée comprenant de nombreuses informations  |  |
| AppCompatCache |  |  |
| Background Activity Moderator (BAM) |  |  |
| Common Dialogs / CIDSizeMRU |  |  |
| Common Dialogs / Last Visited MRU | Cet artefact permet de suivre les programmes graphiques accédant à des fichiers via la fenetre "Ouvrir/Sauvegarder un fichier". Cette action est également enrichie au sein de la clé ```OpenSaveMRU```, incluant le chemin du fichier accédé. | [détails](./00_windows_artefacts/registry/lastvisitedmru.md) |
| Desktop Activity Moderator (DAM) |  |  |
| EventLogs | Il est tout à fait possible d'accéder à la timeline des applications exécutés via la journalisation de l'EventID 4688 et 4689. Néanmoins, il est nécessaire d'activer une stratégie d'audit ```Audit Process Creation``` et ```ProcessCreationIncludeCmdLine_Enabled```  |  |
| JumpList |  |   |
| LNK files |  | [détails](./00_windows_artefacts/lnk.md)  |
| MUICache |  | [détails](./00_windows_artefacts/muicache.md)  |
| Program Compatibility Assistant (PCA) |  |  |
| Prefetch |  | [détails](./00_windows_artefacts/prefetch.md) |
| Recent Apps |  |   |
| Run MRU |  | [détails](./00_windows_artefacts/registry/runmru.md)  |
| Services |  |  |
| System Resource Usage Monitor (SRUM) |  |  |
| UserAssist | Les programmes basés sur l'interface graphique lancés à partir du bureau sont suivis dans le lanceur d'un système Windows. | [détails](./00_windows_artefacts/registry/userassist.md) |
| Windows 10 Timeline |  Il s'agit d'une timeline intégrée à partir de Microsoft Windows 10 version 1803, qui a pour objectif de journaliser l'ensemble des événements réalisés sur le système (ex: programmes exécutés, fichiers locaux accédés, ...) | [détails](./00_windows_artefacts/windows_timeline_ activitiescache.md) |


<br/>

## La navigation web

L'analyse de la navigation web réalisée par l'attaquant est cruciale. 
Elle permet de mettre en avant : 
- le téléchargement d'outil, lui permettant d'élever ses privilèges ou d'étendre son emprise sur le système d'informations ; 
- des communications avec son infrastructure de Command&Control "C2";
- de l'exfiltration de données métiers ;

Les artefacts intéressants sont : 
- L'historique de navigation ; 
- Les cookies associés aux différents sites visités, permettront de retracer l'historique des sites visités ; 
- le cache des ressources présentes sur les sites visités ; 
- les sessions de l'utilisateur (ex: accès à la boite de mail perso/pro) ; 
- La configuration du navigateur qui a pu être altérée (modification du proxy en place, installation d'extensions malveillantes) ;

Même si la plupart des données sont stockées dans des fichiers présents dans le profil utilisateur, leur emplacement diffère en fonction du navigateur utilisé.


| Nom | Description | Références |
|-----|-------------|------------|
|  Google Chrome   |  | [détails](./00_webbrowsers/google_chrome.md) |
|  Microsoft Edge   |  | [détails](./00_webbrowsers/microsoft_edge.md) |
|  Microsoft Edge / Chronium  |  | [détails](./00_webbrowsers/microsoft_edge_chromium.md) |
|  Microsoft Internet Explorer   |  |  [détails](./00_webbrowsers/microsoft_internet_explorer.md) |
|  Mozilla Firefox   |   |  [détails](./00_webbrowsers/mozilla_firefox.md) |
|  TypedURLs   |  |  |






## Références 

- https://github.com/Psmths/windows-forensic-artifacts
- https://notes.qazeer.io/dfir/windows/_artefacts_overview
