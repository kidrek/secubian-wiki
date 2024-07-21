# Tâches planifiées

Les tâches planifiées permettent de réaliser des actions spécifiques à interval de temps régulier.
Elles offrent ainsi un moyen aux acteurs malveillants de maintenir une emprise sur un système compromis.

Référence MITRE : 
- Tactique : ```TA0003 - Persistence```
- Technique : ```T1053.003 - Scheduled Task/Job: Cron```

## AT

### Configuration

Des autorisations d'accès peuvent être définies afin de limiter l'accès aux fonctionnalités de tâches planifiées à certains comptes utilisateurs uniquement : 
- ```/etc/at.allow```
- ```/etc/at.deny```

Les tâches planifiées peuvent être déclarées dans certains cas à ces emplacements : 

- ```/var/spool/cron/atjobs/```


## CRON

### Configuration

Les tâches planifiées peuvent être déclarées à plusieurs emplacements : 

- ```/etc/cron.d```
- ```/etc/crontab```
- ```/var/spool/cron/crontabs/$user/*```

Des répertoires sont également présents au sein du système d'exploitation afin de réaliser des exécutions de tâches à fréquences définies (toutes les heures, jours, semaines, mois) :
- ```/etc/cron.hourly/```
- ```/etc/cron.daily/```
- ```/etc/cron.weekly/```
- ```/etc/cron.monthly/```

### Journalisation

Chaque tâche réalisée est journalisée par défaut au sein des fichiers :
- ```/var/log/cron.log``` pour les systèmes/distributions à base de RedHat
- ```/var/log/syslog```

Il peut être interessant également de valider qu'aucune configuration particulière n'ait été définie dans le répertoire de ```rsyslog``` : ```/etc/rsyslog.d```.

```
# grep -ire "cron.*" /etc/ryslog.d
```

## Systemd timers

Systemd fournit une alternative à cron afin d'exécuter des scripts à fréquence définie.

Pour cela, il est important de rechercher les noms de service ayant une extension de fichier ```.timer```. L'association du fichier ```$service.service``` et ```service.timer``` permettra de comprendre le mode opératoire de l'acteur malveillant.

Voici un exemple, de service exécuté toutes les 6h. Le script exécuté au final correspond à la variable ```ExecStart``` présent dans le fichier ```$service.service``` :

```
[Unit]
Description=NSS cache refresh timer

[Timer]
OnBootSec=5
OnUnitActiveSec=6h

[Install]
WantedBy=timers.target
```


## Références 

- https://pberba.github.io/assets/posts/common/20220201-linux-persistence.pdf
- https://pberba.github.io/security/2022/01/30/linux-threat-hunting-for-persistence-systemd-timers-cron/#7-scheduled-taskjob-cron