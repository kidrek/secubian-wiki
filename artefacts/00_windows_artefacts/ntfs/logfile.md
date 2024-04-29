# $LOGFILE

Le $LOGFILE, également appelé "Transaction Log", est un artefact important du système de fichiers NTFS (New Technology File System) utilisé par Windows. Pour les enquêtes forensiques, le $LOGFILE est très utile car il permet de reconstituer l'historique des modifications sur le système de fichiers, y compris pour des fichiers supprimés qui n'auraient plus de métadonnées dans la MFT. Cependant, le $LOGFILE manque de précision temporelle car il n'inclut pas d'horodatages détaillés comme le $UsnJrnl. 

Principales caractéristiques du $LOGFILE : 
- Il s'agit d'un journal des transactions qui enregistre tous les changements effectués sur le volume NTFS, comme la création, la suppression, le renommage ou la modification de fichiers. 
- Ce journal permet au système d'exploiter la fiabilité et la récupérabilité du système de fichiers, en permettant de revenir en arrière en cas de plantage ou de panne électrique.  
- Le $LOGFILE se trouve à la racine du volume NTFS, dans l'entrée MFT (Master File Table) numéro 2.  
- La taille par défaut du $LOGFILE est de 65535 secteurs, mais elle peut être ajustée à l'aide de la commande ```chkdsk /L```.  
- La structure du $LOG comprend une zone de redémarrage et une zone de journalisation, divisée en deux sections : la zone tampon et la zone normale.  
- Les nouvelles entrées sont écrites de manière séquentielle dans ces zones, en remplaçant les plus anciennes lorsqu'elles sont pleines. 

<br/>


## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape |  ```#windows``` | https://github.com/EricZimmerman/KapeFiles/blob/master/Targets/Windows/%24LogFile.tkape |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| nfstool | ```#linux```  | Gihub / thewhiteninja |

<br/>

------
## Références :

- https://dfir.ru/2019/02/16/how-the-logfile-works/
- https://dfir.ru/2018/07/25/a-live-forensic-distribution-writing-to-a-suspect-drive/

