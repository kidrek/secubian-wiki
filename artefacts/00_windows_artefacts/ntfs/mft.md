# $MFT

La MFT est une structure de données importante dans les systèmes de fichiers Windows. Il contient des métadonnées sur tous les fichiers et dossiers présents sur un volume NTFS.

Quelques points clés sur le $MFT : 
- Il permet de stocker des informations essentielles sur chaque fichier, comme son nom, sa taille, ses dates de création/modification, ses autorisations d'accès, etc. 
- Ces données vont permettre de reconstituer l'état d'un système en cas d'incident, d'attaque ou de besoin d'investigation numérique

<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| dd | ```#linux```  | |
| kape |  ```#windows``` | https://github.com/EricZimmerman/KapeFiles/blob/master/Targets/Windows/%24MFT.tkape |
| Velociraptor | ```#linux```  | |


<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| analyseMFT |   | |
| Suite d'outils Sleuthkit - mmls | ```#linux```  | |


```
$ mmls image.E01
$ icat -o 63 image.E01 > mft.raw
$ analyseMFT.py -f mft.raw -o mftanalysed.csv
```

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| nfstool | ```#linux```  | Gihub / thewhiteninja |


------
## Références :

- https://dfir.ru/2019/01/19/ntfs-today/
- https://dfir.ru/2021/01/10/standard_information-vs-file_name/