# UserAssist

L'artefact UserAssist est un ensemble d'entrées de registre qui permettent de suivre les programmes exécutés par un utilisateur particulier. Il est stocké dans la clé de registre ```HKEY_USERS{SID}\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist```.
Les données sont enregistrées de manière encodée en utilisant le chiffrement par substitution ROT-13. Chaque exécution d'un programme est associée à une valeur contenant le chemin complet et un compteur d'exécutions, mais sans horodatage.

<br/>

## Emplacement 

Les données sont présentes dans la ruche de chacun des utilisateurs : 

``` C:\Users\xxx\NTUSER.DAT ```

Plus spécifiquement au sein de la clé : 

```HKEY_CURRENT_USER\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\(GUID)\Count```

<br/>

Chacunes des valeurs sont encodées via ROT-13 :
- GUID for XP
    - ```75048700``` Active Desktop
- GUID for Win7
    - ```CEBFFSCD``` Executable File Execution
    - ```F4E57C48``` Shortcut File Execution
- Program Locations for Win7 Userassist
    - ProgramFilesX64 ```6D809377-...```
    - ProgramFilesX86 ```7C5A40EF...```
    - System ```1AC14E77-...```
    - SystemX86 ```D6523180-...```
    - Desktop ```B4BFCC3A-...```
    - Documents ```FDD39AD0-..```
    - Downloads ```374DE290-...```
    - UserProfiles ```0762D272-...```

<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape | ```#windows``` | https://ericzimmerman.github.io/KapeDocs/#!External\Remote_Collections_KAPE\Remote%20Collections%20with%20KAPE.md#run-kape-using-the-mapped-drive-to-the-target |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| log2timeline | ```#linux``` | |
| regripper | ```#linux``` | https://github.com/warewolf/regripper/blob/master/plugins/trustrecords.pl |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
|  |  | |

<br/>


------
## Références :
- 