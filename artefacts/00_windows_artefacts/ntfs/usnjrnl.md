# $UsnJrnl

L'$UsnJrnl, pour "Update Sequence Number Journal", est un journal des changements (change log journal) qui enregistre les modifications effectuées sur les fichiers et dossiers d'un volume NTFS au sein de l’attribut $EXTEND de la MFT. Il est important de noter que chaque partition NTFS contient son journal $UsnJrnl. 

Il s'agit d'une source précieuse dans les investigations numériques. Il permet notamment de détecter des activités suspectes mais également toute tentative d'alteration, de dissiumulation comme le "time stomping" (modification des horodatages) ou les tentatives d'effacement de traces.
Ce journal peut également apporter des précisions sur l'exécution des binaires, via les modifications (Reason : DATA_EXTEND|DATA_TRUNCATION|CLOSE) des fichiers PREFETCH de ces derniers. Cela permet de contourner la limitation de 8 entrées MAX dans les fichiers ".pf".

Il est composé de 2 DataStream : 
- $MAX, stockant les métadonnées du journal
- $J, stockant l'ensemble des entrées du journal.

<br/>

Voici une liste non exhaustive des principaux attributs présents au sein du journal : 
- Timestamp - Le timestamp associé à la modification du fichier
- Filename - Le nom du fichier modifié
- Attribute – L'attribut pour spécifier s'il s'agit d'un fichier ou d'un répertoire
- Reason — L'action réalisée sur le fichier
  - CLOSE
  - DATA_EXTEND 
  - DATA_OVERWRITE 
  - DATA_TRUNCATION
  - FILE_CREATE
  - FILE_DELETE 
  - RENAME_NEW_NAME
  - SECURITY_CHANGE

<br/>

Les informations relatives à l'$UsnJrnl sont également stockées dans l'attribut $STANDARD_INFORMATION d'un enregistrement MFT.

Principales caractéristiques du $UsnJrnl :
- Il contient des informations détaillées sur les événements survenus, comme la création, la suppression, la modification ou le renommage de fichiers. 
- Cet artefact est très utile pour les enquêtes forensiques, car il permet de reconstituer l'historique des activités sur le système de fichiers, y compris pour des fichiers supprimés. 
- Il est stocké à la racine du volume NTFS, dans le répertoire $Extend. 
- Il enregistre un plus grand nombre d'événements que le $LogFile, qui est plus bas niveau.

Attention, car il comporte quelques limitations : 
- La taille du DataStream "$J" est définie au sein du système d'exploitation et de ce fait est limitée. Il est possible de la consulter via la commande ```fsutil usn queryjournal C:```. A titre indicatif, elle permet dans la majorité des usages de stocker jusqu'à 20 jours.
- Il ne s'agit pas d'un fichier standard mais d'un fichier système. Son extraction ne se fera pas via un copier/coller standard. Mieux vaut privilégier des outils spécifiques tels que l'EDR/..



<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| FTK Imager | ```#windows```  | |
| Kape | ```#windows``` | https://github.com/EricZimmerman/KapeFiles/blob/master/Targets/Windows/%24J.tkape |
| MFTECmd.exe | ```#windows```  | |
| Velociraptor | ```#linux```  | |


<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| Log2timeline | ```#linux``` ```#windows```  | |


<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| nfstool | ```#linux```  | Gihub / thewhiteninja |


<br/>

------
## Références :

- https://artefacts.help/windows_usnjrnl.html
- https://en.wikipedia.org/wiki/NTFS#Master_File_Table
- https://notes.qazeer.io/dfir/windows/_artefacts_overview/usnjrnl
- https://blog.haboob.sa/blog/advanced-usn-journal-forensics
- https://www.otorio.com/resources/usnjrnl-extraction-for-efficient-investigation/
- https://forensafe.com/blogs/usnjournal.html
- https://plaso.readthedocs.io/en/latest/sources/user/Parsers-and-plugins.html
- https://docs.velociraptor.app/blog/2020/2020-11-13-the-windows-usn-journal-f0c55c9010e/
- https://docs.velociraptor.app/artifact_references/pages/windows.carving.usn/