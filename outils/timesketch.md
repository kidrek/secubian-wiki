# Timesketch

Timesketch est un outil indispensable permettant d'uploader une timeline au format plaso afin de la parcourir et la confronter à des règles de détection.

L'outil a été intégré au sein de la distribution Secubian.

- Ouvrir un terminal
- Exécuter la commande ```timesketch```
- Ouvrir un navigateur et rendez-vous sur l'url ```http://127.0.0.1``` \
ou en cliquant ici : [instance timesketch](http://127.0.0.1)


Les informations d'authentification par défaut sont les suivantes : 
- Nom d'utilisateur : ```secubian```
- Mot de passe : ```secubian```

Je vous encourage à les changer lors de son utilisation.

- Source : https://timesketch.org/
- Documentation : https://timesketch.org/guides/user/


La solution a pas mal évolué ces derniers mois.
Voici quelques exemples de requêtes pouvant être utilisée : ```data_type:"windows:evtx:record" AND event_identifier:4624 AND xml_string:"/LogonType\"\>3/" AND datetime:[2021-08-29 TO 2021-08-31]```
(source : https://timesketch.org/guides/user/search-query-guide/)


