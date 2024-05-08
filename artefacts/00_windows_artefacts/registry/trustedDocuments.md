# Trusted Documents

Les "Trusted Documents" sont une fonctionnalité de sécurité intégrée aux systèmes d'exploitation Microsoft Windows. Ils sont conçus pour permettre aux utilisateurs de spécifier des fichiers ou des documents en particulier comme étant fiables et sécurisés. Ces fichiers peuvent être des documents provenant de sources connues et sûres, tels que des fichiers internes à l'entreprise ou des documents signés numériquement.

Cet artefact permet de suivre les documents jugés comme de confiance par un utilisateur. Cela va de l'activation des macros, à l'authorisation d'éditer un document.
L'ensemble des données sont stockés au sein de la base de registre dans la clé suivante : 
```
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\<Version><AppName>\Security\Trusted Documents\TrustedRecords

HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\Common\Security\Trusted Documents
```


<br/>

## Emplacement 

Pour rappel, la ruche des comptes utilisateurs ```NTUSER``` est présente dans chacun de leur dossiers personnels: ```%SystemDrive%:\Users\<USERNAME>\NTUSER.dat```.

| Emplacement | 
|-------------|
| NTUSER\SOFTWARE\Microsoft\OFfice<Version><AppName>\Security\Trusted Documents\TrustedRecords | 

| Valeurs attendues | Description | 
|-------------------|-------------|
| 0x01000000 | Autorisation d'édition | 
| 0xFFFFFF7F | Autorisation d'exécution des macros | 

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
| regripper | ```#linux``` | https://github.com/warewolf/regripper/blob/master/plugins/trustrecords.pl |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>

------
## Références :

- https://nk0.gitbook.io/dfir/windows/forensics/evidence-of-execution/office-apps-forensics/trusted-documents