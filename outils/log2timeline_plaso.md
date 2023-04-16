# Log2timeline et Plaso


Pour faciliter les investigations et les mises à jour de ces outils, il a été décidé de les intégrer en tant que docker.

Ils sont disponibles via les alias : 
- dockerl2t
- dockerplaso


!! Il est important que le prélévement soit copié dans le répertoire dédié à cet effet : ```/home/secubian/Documents/Cases```. 
De plus il est nécessaire de se positionner dans le répertoire : ```/home/secubian/Documents/``` pour exécuter ces outils. En effet, le répertoire courant sera mappé sur le docker. Il est donc indispensable que le prélévement et les règles de détection soient accessible à partir du répertoire courant.


## Génération du bodyfile relatif à une image disque

La commande par défaut utilisée, est la suivante. 
Elle a besoin de deux arguments, le chemin où se trouve le prélévement ```evidence.dump``` et le chemin du fichier de sortie 'bodyfile' ```output_file.plaso```. 

L'argument ```-z``` permet d'homogéniser et faciliter l'investigation future en privilégiant le timezone UTC dans le fichier de sortie.

```
dockerl2t -z UTC --partitions all --storage_file ./Cases/{output_file.plaso} ./Cases/{evidence.dump}
```

Une fois ce traitement terminé, le fichier de sortie ```{output_file.plaso}``` pourra être intégré dans la solution [Timesketch](timesketch) pour son analyse.

### Les filtres

Il est possible de restreindre l'analyse de log2timeline à des fichiers/répertoires spécifiques en lui passant en argument un fichier texte. Cette action permet de réduire considérablement le temps de traitement. !! Attention, car cette option restreint le champ d'action de log2timeline et vous risquez de passer à coté d'artefact.

```
dockerl2t -z UTC -f ./Tools/DFIR/log2timeline/filter_windows.txt --storage_file ./Cases/{output_file.plaso} ./Cases/{evidence.dump}
```

### Les règles Yara

Il est tout à fait possible de soumettre durant la génération du "bodyfile" un fichier contenant des règles YARA.

```
dockerl2t -z UTC --yara_rules {yara_file.yar} --storage_file ./Cases/{output_file.plaso} ./Cases/{evidence.dump}
```

Pour faciliter le traitement, une majorité des dépôts Github contenant des règles YARA ont été téléchargés en amont et sont présents dans le répertoire : ```/home/secubian/Documents/Tools/DETECTION/rules/yara```.
Un script a également été intégré pour faciliter le regroupement de toutes ces règles en un seul et unique fichier (ref: Andrea FORTUNA).

```
dockerl2t -z UTC --yara_rules ./Tools/DETECTION/rules/yara/malware_rules.yar --storage_file ./Cases/{output_file.plaso} ./Cases/{evidence.dump}
```

!! L'export des résultats via Psort devra intégrer l'argument ```--additional_fields yara_match``` pour intégrer les détections éventuelles faites par log2timeline.