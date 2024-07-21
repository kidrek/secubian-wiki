# Hiberfil.sys

L'artefact "hiberfil.sys" est un fichier système présent sur les systèmes d'exploitation Microsoft Windows qui sert à stocker les données nécessaires à la mise en veille prolongée (hibernation) de l'ordinateur. Lorsque l'ordinateur est mis en hibernation, toutes les données en cours d'utilisation sont enregistrées dans ce fichier afin de pouvoir être restaurées lorsque l'ordinateur est réactivé.

Le fichier "hiberfil.sys" est généralement situé à la racine du disque dur système (généralement sous C:) et est de taille équivalente à la quantité de mémoire vive (RAM) installée sur l'ordinateur. Cela signifie que plus la quantité de RAM est importante, plus la taille du fichier "hiberfil.sys" sera grande.

- Chemin de l'artefact : ```%SYSTEMDRIVE%\hiberfil.sys```

Il est possible de désactiver la fonction de mise en veille prolongée dans les paramètres d'alimentation de Windows, ce qui entraînera la suppression du fichier "hiberfil.sys" et libérera de l'espace disque. Cependant, cela signifie que l'ordinateur ne pourra plus être mis en hibernation et mettra plus de temps à démarrer à chaque redémarrage.

Pour activer ou désactiver hiberfil.sys dans un système d'exploitation Microsoft Windows, vous devez ouvrir une invite de commandes en tant qu'administrateur et exécuter la commande suivante :

- Pour activer hiberfil.sys : ```powercfg /h on```
- Pour désactiver hiberfil.sys : ```powercfg /h off```

L'état de cette option est stockée au sein de la base de registre dans la clé : ```HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power\HiberbootEnabled```

<br/>

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| Volatility | #linux #windows | |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>


------
## Références :
- https://learn.microsoft.com/en-us/troubleshoot/windows-client/setup-upgrade-and-drivers/disable-and-re-enable-hibernation
