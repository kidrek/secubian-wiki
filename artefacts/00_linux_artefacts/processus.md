# Les processus

Il est crucial d'analyser les processus Linux lors d'une investigation numérique, car ils fournissent de nombreux indices et artefacts permettant de comprendre les activités suspectes ou malveillantes sur le système. 
Voici quelques emplacements recensant les processus en cours d'exécution.


| Emplacement | Description |
|-------------|-------------|
|/proc/\$PID/cmdline| Contient la commande exécutée |
|/proc/\$PID/comm| |
|/proc/\$PID/cwd| Contient un lien symbolic vers le répertoire courant utilisé pour l'exécution du processus|
|/proc/\$PID/environ| Contient l'ensemble des variables d'environnement utilisées par le processus |
|/proc/\$PID/exe| Contient un lien symbolic vers le binaire exécuté|
|/proc/\$PID/exe \| grep 'deleted'| Contient un lien symbolic vers le binaire exécuté même si ce dernier n'est plus présent au sein du système de fichiers|
|/proc/\$PID/fd/*| Contient l'ensemble des "file descriptors" du processus|
|/proc/\$PID/fd/* \| grep 'memfd'| Contient l'ensemble des "file descriptors" anonymes présents dans la mémoire vive |
|/proc/\$PID/fd/* \| grep 'bpf-map'| Contient l'ensemble des "file descriptors" ayant pour type "bpf-map". Les bpf-map sont des structures de données clés/valeurs résidant dans l'espace noyau qui permettent de stocker et partager des informations entre les programmes BPF et l'espace utilisateur.  |
|/proc/\$PID/fd/* \| grep 'bpf-prog'| Contient l'ensemble des "file descriptors" ayant poru type "bpf-prog" Les bpf-prog sont des programmes eBPF (Extended Berkeley Packet Filter) chargés et exécutés dans l'espace noyau Linux. Les bpf-prog sont chargés depuis l'espace utilisateur via l'appel système bpf() avec les commandes ```BPF_PROG_LOAD``` ou ```BPF_PROG_TYPE```. Ils peuvent être chargés à partir de fichiers objets ELF ou à partir du code assembleur BPF. |
|/proc/\$PID/fdinfo| Contient une entrée pour chacun des fichiers ouverts par le processus |
|/proc/\$PID/map_files/*| Contient des entrées correspondant à des fichiers en mémoire|
|/proc/\$PID/maps| Contient une liste de tous les fichiers du processus présents en mémoire|
|/proc/\$PID/maps \| grep '(deleted)'| Contient une liste de tous les fichiers supprimés du processus qui étaient présents en mémoir (ex: librairies partagées supprimées)|
|/proc/\$PID/stack| Trace symbolique des appels de fonction dans la pile du noyau de ce processus|
|/proc/\$PID/status| Informations sur l'état du processus utilisé par ```ps```|
|/proc/\$PID/task/\$TID/children| Liste séparée dans l'espace des tâches filles de cette tâche|
|/proc/\$PID/unix| Contient une liste des sockets UNIX ouvertes/accédées par le processus|


