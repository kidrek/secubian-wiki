# Comptes utilisateurs

Les comptes utilisateurs permettent de s'authentifier et accéder à un système d'exploitation de manière "légitime". J'entends par légitime sans exploitation de vulnérabilité au sein de services. Il reste tout à fait possible d'accéder à un système en utilisant les informations d'authentification volées d'un compte utilisateur, mais le process reste légitime.

Référence MITRE : 
- Tactiques : 
  - ```TA0003 - Persistence```
  - ```TA0004 - Privilege Escalation```
  - ```TA0005 - Defense Evasion```
- Techniques : 
  - ```T1078 - Valid Accounts```
  - ```T1098 - Account Manipulation```
  - ```T1098.004 - Account Manipulation: SSH Authorized Keys```
  - ```T1136.001 - Create Account: Local Account```


L'authentification peut être réalisée de plusieurs manières : 
- via un échange d'informations d'authentification standard : login/mot de passe;
- via un échange de clé et de passphrase lors d'une authentification ```ssh```.

Lors de ce second cas, les clés sont repertoriées à plusieurs emplacements : 
- ```$HOME/.ssh/authorized_keys```, par défaut ;
- ```grep -ire "AuthorizedKeysFile" /etc/ssh/``` pour les configurations personnalisées ; 

## Fichier de définition 

- ```/etc/passwd``` : contient la définition des comptes utilisateurs. Nous y trouvons également : 
  - les répertoires associés aux profiles de chacun des utilisateurs ; 
  - l'interpréteur de commande ```SHELL``` (ex: ```/bin/bash```, ```/bin/zsh```) associé à chacun des comptes utilisateurs ; 
  - les mots de passe chiffrés sur les anciennes distributions ; 
- ```/etc/shadow``` : contient les mots de passe des comptes utilisateurs ainsi que la politique de sécurité associée ;
- ```/etc/groups``` : groupes auxquels appartiennent les comptes utilisateurs ; 


## SUDO

Il est possible sur les systèmes d'exploitation Linux, d'accorder l'exécution de commande à privilège pour certains comptes utilisateurs via ```sudo```.

La configuration est définie dans les fichiers présents à ces emplacements : 
- ```/etc/sudoers```
- ```/etc/sudoers.d```


## Références 

- https://pberba.github.io/assets/posts/common/20220201-linux-persistence.pdf
- https://pberba.github.io/security/2021/11/23/linux-threat-hunting-for-persistence-account-creation-manipulation/