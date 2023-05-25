# VMware ESXi / Workstation / Fusion

Plutôt que d'utiliser les outils traditionnels sur les systèmes d'exploitations tels que Microsoft Windows, Linux, la solution de virtualisation VMware ESXi permet de réaliser très rapidement un prélèvement de la **mémoire vive** ainsi que du **disque dur** via un simple **snapshot**.

Une fois cette action réalisée, l'équipe sécurité aura toute latitude pour récupérer les fichiers **".vmdk", ".vmsn", ".vmss" et ".vmem"** au sein du laboratoire d'analyse.

## Prélèvements 

### 1. Prélèvement de l'ensemble de la machine virtuelle

Voici les actions à réaliser :

1. Connexion au VCenter avec un utilisateur bénéficiant des permissions pour réaliser un snapshot.
2. VCENTER> Sélectionner la machine virtuelle incriminée
3. VCENTER> Réaliser un snapshot dont le nom porte l'identifiant de l'incident en cours "**INCIDENT_202x-xxx-**"
4. VCENTER> Accéder au datastore ou sont stockés les fichiers de la machine virtuelle incriminéeIl est possible d'identifier les datastores au sein du fichier de configuration de la machine virtuelle **".vmx"**
5. VCENTER> Télécharger l'ensemble des fichiers **".vmdk", ".vmsn", ".vmss" et ".vmem"** correspondant à la machine virtuelle sur un disque dur dédié à leur analyse
6. Réaliser sur le disque dur d'analyse, un hash de l'ensemble des fichiers de la machine virtuelle afin de valider leur intégrité durant chaque étape de l'analyse
7. Réaliser une copie de l'ensemble des fichiers sur un disque dur BACKUP, ce dernier ne sera pas impacté par les diverses analyses réalisées durant l'investigation numériques

### 2. Prélèvement de la mémoire vive de la machine virtuelle

Voici les actions à réaliser :

1. Connexion au VCenter avec un utilisateur bénéficiant des permissions pour réaliser un snapshot.
2. VCENTER> Sélectionner la machine virtuelle incriminée
3. VCENTER> Réaliser un snapshot dont le nom porte l'identifiant de l'incident en cours **"INCIDENT_202x-xxx-"**
4. VCENTER> Accéder au datastore ou sont stockés les fichiers de la machine virtuelle incriminéeIl est possible d'identifier les datastores au sein du fichier de configuration de la machine virtuelle **".vmx"**
5. VCENTER> Télécharger les fichiers **".vmsn", ".vmem", ".vmss"** correspondant à la machine virtuelle sur un disque dur dédié à leur analyse
6. Réaliser sur le disque dur d'analyse, un hash de l'ensemble des fichiers de la machine virtuelle afin de valider leur intégrité durant chaque étape de l'analyse
7. Réaliser une copie de l'ensemble des fichiers sur un disque dur BACKUP, ce dernier ne sera pas impacté par les diverses analyses réalisées durant l'investigation numériques

## Analyses

### Accéder aux données d'un fichier VMDK sur Linux 

```bash
# 1ere solution
--
losetup /dev/loop0 myfile.vmdk
fdisk -l /dev/loop0    # Identification de l'offset de départ de la partition à monter, multiplier par le nombre de byte par secteur (ex: 32256 * 512)
mount -o loop, offset=$((512*32256)) /dev/loop0 /mnt/evidence

# 2nde solution
--
apt install libguestfs-tools
guestmount -a myfile.vmdk -i --ro /mnt/evidence

# 3eme solution 
--
modprobe nbd
qemu-nbd -r -c /dev/nbd1 myfile.vmdk
fdisk -l /dev/nbd1     # Identification de l'offset de départ de la partition à monter, multiplier par le nombre de byte par secteur (ex: 32256 * 512)
mount -o loop, offset=$((512*32256)) /dev/nbd1/mnt/evidence

# 4e solution
--
Il est tout à fait possible d'accèder aux données d'un fichier vmdk via l'application 7zip - Open an archive --> myfile.vmdk
```

### Génération d'une timeline

Il est tout à fait possible de lancer un traitement du fichier VMDK avec l'outil log2timeline.