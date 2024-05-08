# Run MRU

Cet artefact permet de suivre les applications exécutées, les dossiers/urls accédés via le raccourcis "WIN + R". L'horodatage de la dernière écriture de la clé indique l'horodatage de l'élément le plus récemment lancé.

La clé ```MRUList``` spécifie à l'analyste l'ordre dans lequel les applications/dossiers/urls ont été accédés.

<br/>

## Emplacement 

Pour rappel, la ruche des comptes utilisateurs est présente dans chacun de leur dossiers personnels: ```%SystemDrive%:\Users\<USERNAME>\NTUSER.dat```.


| Emplacement | 
|------------------------|
| NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU |


<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape | ```#windows``` | https://ericzimmerman.github.io/KapeDocs/#!External\Remote_Collections_KAPE\Remote%20Collections%20with%20KAPE.md#run-kape-using-the-mapped-drive-to-the-target |
| velociraptor | ```#linux``` | |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| regripper | ```#linux``` | https://github.com/warewolf/regripper/blob/master/plugins/trustrecords.pl |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>

------
## Références :

- https://nk0.gitbook.io/dfir/windows/forensics/evidence-of-execution/run-mru