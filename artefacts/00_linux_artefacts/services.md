# Les services

Les services sous Linux sont des programmes qui s'exécutent en arrière-plan et fournissent des fonctionnalités spécifiques au système ou aux utilisateurs. Historiquement, les services étaient gérés par le système d'initialisation ```SystemV```. Cependant, de nombreuses distributions modernes utilisent désormais ```systemd``` comme gestionnaire de services principal. Ces derniers sont très souvent utilisés par les acteurs malveillants pour y déployer des mécanismes de persistences. 

L'ensemble de ces scripts sont exécutés au démarrage du système mais également lors du rechargement de la configuration.

L'objectif de ce post est de guider l'investigation numérique afin d'identifier l'exécution de binaire malveillant, via l'analyse notamment de la variable ```ExecStart```.

## Configuration
Il est possible de définir ces services à plusieurs endroits au sein du système d'exploitation.

Voici les principaux emplacements :
- ```/etc/systemd/system.conf```
- ```/etc/init.d/*```
- ```/etc/rc.local```

## Emplacement des scripts de lancement

### Scripts du système
Les scripts de lancement de ces services sont présents à de multiples emplacements : 

- ```/etc/systemd/system/*```
- ```/lib/systemd/system/*```
- ```...```

L'exhaustivité de ces chemins est accessible via la commande : ```systemd-analyze unit-paths``` 

```
# systemd-analyze unit-paths |sort
-
/etc/systemd/system
/etc/systemd/system.attached
/etc/systemd/system.control
/lib/systemd/system
/run/systemd/generator
/run/systemd/generator.early
/run/systemd/generator.late
/run/systemd/system
/run/systemd/system.attached
/run/systemd/system.control
/run/systemd/transient
/usr/lib/systemd/system
/usr/local/lib/systemd/system
```

### Scripts utilisateurs

Les scripts de lancement de ces services sont présents à de multiples emplacements : 

- ```/etc/systemd/user/*```
- ```/lib/systemd/user/*```
- ```...```

L'exhaustivité de ces chemins est accessible via la commande : ```systemd-analyze unit-paths --user``` 

```
# systemd-analyze unit-paths --user |sort
-
/etc/systemd/user
/etc/xdg/systemd/user
/home/kidrek/.config/systemd/user
/home/kidrek/.config/systemd/user.control
/home/kidrek/.local/share/systemd/user
/run/systemd/user
/run/user/501/systemd/generator
/run/user/501/systemd/generator.early
/run/user/501/systemd/generator.late
/run/user/501/systemd/transient
/run/user/501/systemd/user
/run/user/501/systemd/user.control
/usr/lib/systemd/user
/usr/local/lib/systemd/user
/usr/local/share/systemd/user
/usr/share/systemd/user
```


## Exemple de script malveillant

Voici un exemple de service exéuctant un beacon au démarrage du système.

```
# vi /usr/lib/systemd/system-generators/sysmon.service
-
[Unit]
Description=networking.service

[Service]
ExecStart=/opt/beacon.sh

[Install]
WantedBy=multi-user.target
```

## Journalisation 

- ```rc-local``` : son exécution peut être identifié au sein du fichier ```/var/log/syslog```.

```
# cat /var/log/syslog | egrep "rc-local.service|/etc/rc.local Compatibility"
```


## Réferences 

- https://pberba.github.io/security/2022/02/07/linux-threat-hunting-for-persistence-systemd-generators/
- https://pberba.github.io/security/2022/02/06/linux-threat-hunting-for-persistence-initialization-scripts-and-shell-configuration/#81-isnt-rclocal-deprecated