# LastVisitedMRU / LastVisitedPidlMRU

Cet artefact permet de suivre les derniers dossiers dans lesquels un élément a été ouvert ou enregistré avec une application via la fenêtre "Ouvrir/Sauvegarder un fichier" listé au sein de la clé ```OpenSaveMRU```.


Voici les informations pouvant être collectées au sein de cet artefact : 
- File Name : Le nom de l'application ;
- Full Path : L'emplacement du dossier où se situe le fichier accédé via la fenêtre "Open"/"Save As" ;
- Parent Key Modification Date : La date et l'heure correspondant à la modification de la clé MRU ;
- Registry Value Name - Le nom de la valeur dans la clé de registre ;
- MRU Order : L'ordre dans lequel les dossiers ont été accédés par les applications. La valeur 1 indique que le fichier a été consulté le plus récemment ;
- Located At - Le chemin d'accès complet à la valeur dans la clé de registre ;


<br/>

## Emplacement 

Pour rappel, la ruche des comptes utilisateurs est présente dans chacun de leur dossiers personnels: ```%SystemDrive%:\Users\<USERNAME>\NTUSER.dat```.


| Système d'exploitation | Emplacement | 
|------------------------|-------------|
| Microsoft Windows XP | NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedMRU | 
| Microsoft Windows 7 |  NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidLMRU <br/>NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRULegacy | 

<br/>

Comme évoqué ci-dessus, cet artefact est enrichi avec la clé ```OpenSaveMRU```.

| Emplacement | 
|------------------------|
|  NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePidlMRU | 


<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape | ```#windows``` | https://ericzimmerman.github.io/KapeDocs/#!External\Remote_Collections_KAPE\Remote%20Collections%20with%20KAPE.md#run-kape-using-the-mapped-drive-to-the-target |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| regripper | ```#linux``` | https://github.com/warewolf/regripper/blob/master/plugins/trustrecords.pl |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
|  |  | |

<br/>


------
## Références :
- https://forensafe.com/blogs/lastvisitedmru.html
- https://nk0.gitbook.io/dfir/windows/forensics/evidence-of-execution/office-apps-forensics/lastvisitedpidlmru