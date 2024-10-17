# Mozilla Firefox

L'analyse de l'historique de navigation web/téléchargement peut apporter des informations précieuses durant une investigation numérique.

## Emplacement des artefacts

Le profil du navigateur utilisé se trouve dans le profil de l'utilisateur : 

* Microsoft Windows : ```%Rootdrive%:\Users\{utilisateur}\AppData\Roaming\Mozilla\Firefox\Profiles\{profil}```
* MacOS : ```~/Library/Application Support/Firefox/Profiles/<ProfileName>```
* Linux: ```~/.mozilla/firefox/<ProfileName>```

| Artefacts | Fichiers |
|----|----|
| Historique de navigation (table:moz_places) / Téléchargement (table: moz_annos) |```places.sqlite``` | 
| Information d'authentification | ```logins.json```  |
| Cookies de navigation | ```cookies.sqlite``` |
| Liste des extensions installées | ```extensions.json``` | 
| Informations relatives aux favicons correspondant aux sites visités | ```favicons.sqlite``` |
| Informations relatives aux données saisies dans les formulaires de pages web | ```formhistory.sqlite``` |
| List des préférences associées aux sites visités | ```permissions.sqlite\|content-prefs.sqlite``` |


Quelques informations supplémentaires peuvent être utiles pour interpreter correctement les données contenues dans la base de données ```places.sqlite```.

```
--- Magic numbers
-- moz_historyvisits.visit_type:
-- https://dxr.mozilla.org/mozilla-esr60/source/toolkit/components/places/nsINavHistoryService.idl#1185
-- 1	TRANSITION_LINK                 The user followed a link and got a new toplevel window.
-- 2	TRANSITION_TYPED	        The user typed the page's URL in the URL bar or selected it from URL bar autocomplete results, clicked on it from a history query (from the History sidebar, History menu, or history query in the personal toolbar or Places organizer.
-- 3	TRANSITION_BOOKMARK	        The user followed a bookmark to get to the page.
-- 4	TRANSITION_EMBED	        Set when some inner content is loaded. This is true of all images on a page, and the contents of the iframe. It is also true of any content in a frame, regardless of whether or not the user clicked something to get there.
-- 5	TRANSITION_REDIRECT_PERMANENT	The transition was a permanent redirect.
-- 6	TRANSITION_REDIRECT_TEMPORARY	The transition was a temporary redirect.
-- 7	TRANSITION_DOWNLOAD	        The transition is a download.
-- 8    TRANSITION_FRAMED_LINK          The user followed a link and got a visit in a frame.
-- 9    TRANSITION_RELOAD               The page has been reloaded.


```

Sources :
- https://gist.github.com/olejorgenb/9418bef65c65cd1f489557cfc08dde96

## Outil de collecte 

| Nom | OS | Références |
|-----|-------------|------------|
| Velociraptor | ```#windows``` | https://docs.velociraptor.app/artifact_references/pages/windows.kapefiles.targets/ |

<br/>

## Outil de traitement 

| Nom | OS | Références |
|-----|-------------|------------|
| Nirsoft MZCacheView | ```#Windows``` | https://www.nirsoft.net/utils/mozilla_cache_viewer.html |
| Nirsoft PasswordFox | ```#windows``` | https://www.nirsoft.net/utils/passwordfox.html |
| Plaso / Log2timeline | ```#linux```  | https://plaso.readthedocs.io/en/latest/sources/user/Parsers-and-plugins.html |

<br/>

## Outil d'analyse

| Nom | OS | Références |
|-----|-------------|------------|
| .. |  | |

<br/>



Sources : 
- https://medium.com/@laurent.mandine/browser-forensics-89429fe0749f
- https://medium.com/@jsaxena017/web-browser-forensics-part-2-firefox-browser-3dc6ef104607