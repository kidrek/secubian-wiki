# Script de démarrage à l'ouverture de session

Ces scripts sont exécutés à l'ouverture de session d'un compte utilisateur.
Ils peuvent ainsi servir à un acteur malveillant pour maintenir son emprise sur un système compromis. C'est ce que nous appelons "mécanisme de persistence".

Référence MITRE : 
- Tactiques : 
  - ```TA0003 - Persistence```
  - ```TA0004 - Privilege Escalation```
- Technique : ```T1546.004 - Event Triggered Execution: Unix Shell Configuration Modification```

## Configurations 

Ces scripts peuvent se trouver à de nombreux emplacements, que nous allons tenter de lister. 

### Configuration commune

Tout d'abord des fichiers de configuration communs à l'ensemble des interpreteurs de commandes : 
- ```/etc/profile```
- ```/etc/profile.d/*``` 
- ```$HOME/.profile```

### Interpreteur de commandes 

La variable d'environnement ```$SHELL``` vous permet d'identifier l'interpreteur de commande utilisé durant votre session actuelle (ex: ```/bin/bash```, ```/bin/zsh```).
Lors de leur initialisation, chacun d'entre eux exécute un script spécifique : 
- ```/etc/bash.bashrc```, ```$HOME/.bashrc``` pour le shell ```BASH``` ;
- ```/etc/zshrc```, ```$HOME/.zshrc```, ```/etc/zprofile```, ```$HOME/.zprofile```, ```/etc/zshenv```, ```$HOME/.zshenv```, pour le shell ```ZSH```;

J'attire votre attention sur le fait que ces scripts peuvent en exécuter d'autres à leur tour et également implémenter des ```alias``` pour détourner le comportement du système face à vos commandes.

Lors de la fermeture de la session, le shell va également exécuter un script spécifique :
- ```/etc/bash.bash_logout```, ```$HOME/.bash_logout``` pour le shell ```BASH```; 
- ```/etc/zlogout```, ```$HOME/.zlogout``` pour le shell ```ZSH```;


## Journalisation

Chaque interpreteur de commande a son propre fichier de journalisation, souvent défini dans la variable d'environnement ```HISTFILE``` : 
- ```$HOME/.bash_history``` pour le shell ```BASH```
- ```$HOME/.zsh_history```, ```$HOME/.zsh_sessions/*``` pour le shell ```ZSH```


## Références 

- https://pberba.github.io/assets/posts/common/20220201-linux-persistence.pdf