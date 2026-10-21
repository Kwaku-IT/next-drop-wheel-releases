# Lecture directe de la bibliothèque rekordbox

Next Drop Wheel lit **tout seul** les analyses de rekordbox 6 et 7 (BPM, tonalité, genre,
artiste, année, note, commentaire) dans sa base `master.db`. Le DJ n'a rien à exporter ni à
importer : il ouvre son dossier de musique, et les morceaux que rekordbox connaît arrivent avec
leurs analyses.

## Comment ça marche

| Étape    | Ce que fait l'app                                                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trouver  | `%APPDATA%\Pioneer\rekordbox\master.db` (Windows) ou `~/Library/Pioneer/rekordbox/master.db` (macOS). Emplacement fixe, jamais un chemin venu de l'interface.        |
| Copier   | `master.db` et ses fichiers `-wal` / `-shm` sont **copiés** dans un dossier temporaire privé.                                                                        |
| Lire     | La **copie** est ouverte en **lecture seule** avec SQLCipher (`better-sqlite3-multiple-ciphers`), puis `djmdContent` est lu avec l'artiste, le genre et la tonalité. |
| Nettoyer | Le dossier temporaire est supprimé, même en cas d'erreur.                                                                                                            |
| Relier   | Chaque morceau est relié aux fichiers scannés par son **chemin réel** (jonctions, liens et noms courts 8.3 compris), comme pour un export XML.                       |

Quand : au lancement, après chaque scan, et dès que rekordbox enregistre sa bibliothèque (date de
`master.db` / `-wal` vérifiée toutes les 15 secondes). La ligne d'état du panneau Bibliothèque dit
ce qui a été lu.

Code : rekordbox-database-reader.ts,
sync-rekordbox.ts,
rekordbox-watcher.ts.

## Risques et parades

| Risque                                                                                                                                             | Gravité   | Parade                                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Format non documenté** : AlphaTheta (Pioneer DJ) ne publie ni le schéma ni la clé ; une mise à jour peut les changer.                            | Moyenne   | Lecture refusée proprement (état « illisible »), les tags restent utilisés, et l'**import d'un export XML** réapparaît en secours dans le panneau Bibliothèque. Vérifié sur une base chiffrée de même schéma.                                                                                                                                  |
| **Clé de chiffrement** : c'est celle publiée par le projet open source pyrekordbox, identique pour toutes les installations rekordbox 6/7 connues. | Moyenne   | Si elle change, même parade que ci-dessus ; mettre à jour la constante `DATABASE_KEY` après vérification.                                                                                                                                                                                                                                      |
| **Corruption de la bibliothèque rekordbox**                                                                                                        | Écartée   | L'app n'ouvre **jamais** les fichiers de rekordbox : elle n'en lit qu'une copie, en lecture seule. Il est vérifié avant chaque version que l'original reste identique octet pour octet.                                                                                                                                                        |
| **Copie incohérente** pendant que rekordbox écrit                                                                                                  | Faible    | Le `-wal` est copié avec la base ; au pire une lecture voit l'état d'avant, et la suivante (15 s plus tard) rattrape.                                                                                                                                                                                                                          |
| **Module natif** : premier binaire natif du projet.                                                                                                | Faible    | Binaires précompilés Node-API (pas de recompilation, compatibles Electron 45), décompressés hors de l'`asar`, seuls ceux de la plateforme cible sont livrés. Vérifié dans une version empaquetée.                                                                                                                                              |
| **Données personnelles** : la base contient aussi l'historique, les playlists, les cue points.                                                     | Faible    | Sont lus : `djmdContent` (+ artiste, genre, tonalité, album, couleur), les playlists classiques et leurs dossiers (`djmdPlaylist`, `djmdSongPlaylist`, sans les playlists intelligentes) et les My Tags (`djmdMyTag`, `djmdSongMyTag`) ; ni l'historique ni les cue points. Rien n'est envoyé sur le réseau ; la copie temporaire est effacée. |
| **Aspect juridique** : lire un format propriétaire chiffré.                                                                                        | À évaluer | L'app ne lit que les données de **l'utilisateur, sur son propre ordinateur**, sans les modifier ni les redistribuer (interopérabilité). Les conditions d'utilisation de rekordbox sont à relire avant une diffusion publique.                                                                                                                  |
| **rekordbox 5** (base `.edb`, autre format)                                                                                                        | Connu     | Non lu : état « rekordbox introuvable », l'import XML reste proposé.                                                                                                                                                                                                                                                                           |

## Clés USB exportées par rekordbox

Une clé (ou un disque) préparée par rekordbox pour les platines devient une **source du vivier**
dès qu'elle est branchée : rien à exporter ni à importer.

| Étape    | Ce que fait l'app                                                                                                                                                                                                                                                                                                |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trouver  | Toutes les 3 secondes, simple `stat` de `<X>:\PIONEER\rekordbox\exportLibrary.db` et `export.pdb` pour les lettres C à Z (Windows), ou de `/Volumes/*/PIONEER/rekordbox/` (macOS). Aucun réseau, aucun chemin venu de l'interface. Une clé est relue seulement quand elle apparaît ou que ses fichiers changent. |
| Choisir  | **`exportLibrary.db` d'abord** (« OneLibrary » / Device Library Plus, rekordbox 6.8+ et 7) ; **`export.pdb`** (+ `exportExt.pdb` pour les My Tags, format DeviceSQL historique) seulement si OneLibrary manque ou ne s'ouvre pas. Un seul des deux est lu : les identifiants de chaque fichier lui sont propres. |
| Copier   | `exportLibrary.db` et ses `-wal` / `-shm` sont **copiés** dans un dossier temporaire privé, la copie est ouverte en **lecture seule** puis effacée. `export.pdb` est lu en mémoire (64 Mo au plus) par un parseur maison borné.                                                                                  |
| Confiner | Les chemins de la clé (`/Contents/...`, relatifs à sa racine) sont résolus sous la racine de la clé ; un chemin qui en sortirait est ignoré. Pré-écoute et glisser-déposer vérifient à nouveau le fichier réel (liens résolus) sous cette racine.                                                                |
| Ranger   | Tables à part (`device`, `device_track`, `device_playlist`...), jamais mêlées à la collection : un morceau de la clé, ses playlists (identifiants préfixés `usb:<clé>:`) et ses analyses partent avec elle quand elle est débranchée.                                                                            |

Ce qui est lu : morceaux (titre, artiste, album, genre, tonalité, BPM, note, couleur, année,
durée, date d'ajout, commentaire, chemin), playlists et dossiers de playlists (pas les playlists
intelligentes). Les My Tags de la clé sont lus mais pas encore proposés comme critère.
L'historique, les cue points et les fichiers d'analyse (`USBANLZ`) ne sont pas lus.

**Clé de OneLibrary** : `exportLibrary.db` est chiffrée avec SQLCipher (paramètres SQLCipher 4).
La phrase de passe, identique pour toutes les clés, est celle publiée (sous forme obscurcie) par
pyrekordbox, `pyrekordbox/onelibrary/database.py` ; constante `DATABASE_KEY` de
device-library-reader.ts.

Code : device-library-reader.ts,
pdb-parser.ts,
device-detector.ts,
device-service.ts,
device-repository.ts.

| Risque                                                                                            | Gravité | Parade                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Écriture sur la clé**                                                                           | Écartée | Rien n'est jamais ouvert en écriture sur la clé : la base est copiée, `export.pdb` est lu en mémoire. Il est vérifié avant chaque version que rien n'apparaît à côté de l'export.              |
| **Formats non documentés** (`exportLibrary.db`, `export.pdb`) qui changent avec rekordbox         | Moyenne | Clé affichée « illisible », le reste de l'app continue ; elle n'est pas relue tant que ses fichiers ne changent pas. OneLibrary illisible : `export.pdb` prend le relais.                      |
| **Fichier hostile ou abîmé** (`export.pdb`)                                                       | Faible  | Taille plafonnée, tailles de page connues seulement, chaque lecture vérifiée dans sa page, parcours des pages sans boucle possible, types de chaîne validés ; une ligne illisible est ignorée. |
| **Chemin qui sortirait de la clé** (`/../...`)                                                    | Faible  | Refusé à la lecture (`confineToDrive`) puis revérifié sur le fichier réel avant toute pré-écoute ou tout glisser-déposer. Un nom contenant `..` (`Vol..2`) reste accepté.                      |
| **Clé retirée pendant la lecture**                                                                | Faible  | La lecture échoue, la clé disparaît au sondage suivant ; un import interrompu est refait (sa signature n'est enregistrée qu'à la fin).                                                         |
| **Les deux exports divergent** (écrits à quelques minutes d'écart, cas observé sur une vraie clé) | Faible  | Un seul est lu (OneLibrary en priorité), jamais un mélange.                                                                                                                                    |
| **Même fichier listé deux fois** par l'export (observé : 34 lignes sur 2 380)                     | Faible  | Un seul morceau par chemin résolu ; les entrées de playlist du doublon pointent vers le morceau gardé.                                                                                         |

## Ce qui n'est pas fait

- Aucune écriture dans rekordbox (playlists, analyses) : hors périmètre, risque de corruption.
- Aucune écriture sur une clé USB.
- Les cue points et la structure des morceaux (fichiers ANLZ) ne sont pas lus.
