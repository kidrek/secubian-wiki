# Recent docs

Il s'agit de clés au sein de la base de registre qui retrace les derniers fichiers et répertoires accédés. Ces informations sont d'ailleurs disponibles dans le "menu démarrer Windows/Recent".
!! Attention !! Ce système fonctionne en mode rollover, cela implique que seules les 150 dernières entrées sont présentes et peuvent être analysées.

- Document Name - Correspond au nom du fichier ou dossier récemment accédé ; 
- File Type - Correspond à l'extension du document ;
- Accessed Date - Correspond à l'horodatage de la dernière modification de la clé ;

<br/>

## Emplacement 

Pour rappel, la ruche des comptes utilisateurs est présente dans chacun de leur dossiers personnels: ```%SystemDrive%:\Users\<USERNAME>\NTUSER.dat```.


| Emplacement | 
|-------------|
|NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs|


| Valeurs attendues | Description | 
|-------------------|-------------|
| .{extension} | Recense l'ensemble des fichiers ayant cette extension | 
| Folder | Recense l'ensemble des répertoires accédés | 


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
| velociraptor - recentdocs parser |  | https://docs.velociraptor.app/artifact_references/pages/windows.registry.recentdocs/ |
| regripper | ```#linux``` | https://github.com/warewolf/regripper/blob/master/plugins/trustrecords.pl |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>


------
## Références :
- https://forensafe.com/blogs/recentdocs.html

