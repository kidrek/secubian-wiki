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

<br/>

### _ Les fichiers accédés

Ces artefacts sont plus génériques mais permettent de retracer les différentes actions réalisées sur des fichiers. 

| Nom | Description | Références |
|-----|-------------|------------|
|RecentDocs| Cet artefact retrace les derniers fichiers et répertoires accédés. |[détails](./00_windows_artefacts/registry/recentdocs.md)|
|ShellBags| Cet artefact permet de retracer les dossiers et fichiers récemment ouverts par les utilisateurs.|[détails](./00_windows_artefacts/registry/shellbags.md)|
|Trusted Documents| Cet artefact permet de visualiser les actions de confiances accordées à certains documents Microsoft Office (ex: execution de macro) |[détails](./00_windows_artefacts/registry/trustedDocuments.md)|



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
| AppCompatCache |  |  |
| EventLogs |  |  |
| Last Visited MRU | Cet artefact permet de suivre les programmes graphiques accédant à des fichiers via la fenetre "Ouvrir/Sauvegarder un fichier". Cette action est également enrichie au sein de la clé ```OpenSaveMRU```, incluant le chemin du fichier accédé. | [détails](./00_windows_artefacts/registry/lastvisitedmru.md) |
| Prefetch |  |  |
| Run MRU |  | [détails](./00_windows_artefacts/registry/runmru.md)  |
| Services |  |  |
| UserAssist | Les programmes basés sur l'interface graphique lancés à partir du bureau sont suivis dans le lanceur d'un système Windows. | [détails](./00_windows_artefacts/userassist.md) |


## Références 

- https://github.com/Psmths/windows-forensic-artifacts
