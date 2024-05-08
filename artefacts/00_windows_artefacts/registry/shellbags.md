# Shellbags

Les Shellbags sont des clés de registre Windows qui stockent des informations sur les dossiers et fichiers récemment ouverts par les utilisateurs. Elles permettent de se souvenir de l'apparence et de la disposition des fenêtres d'explorateur pour chaque dossier.
Chaque entrée de Shellbag contient des informations comme le chemin complet du dossier, la dernière date d'accès, le type de dossier, et des métadonnées sur l'apparence de la fenêtre. Cela permet de reconstituer l'historique de navigation des utilisateurs.

Pour Windows XP, les Shellbags se trouvent sous la clé ```HKCU\Software\Microsoft\Windows\Shell\BagMRU``` et ```HKCU\Software\Microsoft\Windows\ShellNoRoam\BagMRU```

Pour les versions plus récentes, elles sont stockées dans ```HKEY_CURRENT_USER\Software\Microsoft\Windows\Shell\Bags```.
<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| kape | ```#windows``` | |
| velociraptor | ```#linux``` | |

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
| .. |  | |

<br/>


------
## Références :

- 
- 