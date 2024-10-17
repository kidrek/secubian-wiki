# SRUM

L'artefact "SRUM" ou System Resource Usage Monitor est une fonctionnalité, introduit au sein du système d'exploitation Microsoft Windows depuis la version 8, qui collecte et stocke des informations sur l'utilisation des ressources du système par les applications sur un système d'exploitation Microsoft Windows. Il enregistre des données telles que **la consommation de CPU**, de **mémoire**, de **réseau** et de **stockage** par **les processus en cours d'exécution**. Ces données peuvent être utilisées pour diagnostiquer les problèmes de performance du système, pour optimiser l'utilisation des ressources mais également lors d'une investigation numérique.

La base de données SRUM (System Resource Usage Monitor) est stockée dans un fichier caché appelé ```SRUDB.dat```, qui se trouve dans le répertoire suivant : ```C:\Windows\System32\SRU\```

<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| Velociraptor | ```#windows``` | https://docs.velociraptor.app/artifact_references/pages/windows.kapefiles.targets/ |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| Plaso / Log2timeline | ```#linux```  | https://plaso.readthedocs.io/en/latest/sources/user/Parsers-and-plugins.html |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>


------
## Références :
- https://esmyl.medium.com/srum-forensics-dfir-aa9522a925c5