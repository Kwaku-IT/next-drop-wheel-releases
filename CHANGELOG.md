# Journal des modifications

Les évolutions de Next Drop Wheel visibles dans l'application. Format inspiré de
[Keep a Changelog](https://keepachangelog.com/fr/1.1.0/), versions en
[SemVer](https://semver.org/lang/fr/). Les versions les plus récentes sont en haut.

## [2.0.0] - 2026-10-22

### Bibliothèque sous la roue

- **Modifié** : la **bibliothèque est sous la roue**, dans un panneau qui se replie (sa barre reste
  visible en bas de la fenêtre) ; l'onglet Bibliothèque disparaît. À gauche les sources du vivier,
  en haut les critères, à droite l'explorateur. **Ctrl+B** déplie ou replie le panneau. Il est
  replié au lancement dès que rekordbox ou un dossier fournit des morceaux, et ne s'ouvre seul que
  s'il n'y a rien à tirer.
- **Ajouté** : **toute la bibliothèque rekordbox est reprise**, même sans dossier choisi : ses
  morceaux (avec album, durée, date d'ajout, couleur), ses playlists et dossiers de playlists (pas
  les playlists intelligentes) et ses My Tags. Une grosse collection est lue par paquets, sans
  figer l'application, et relue d'elle-même quand rekordbox change.
- **Ajouté** : choix du **vivier** de la roue, mémorisé : playlists, dossiers et sous-dossiers,
  genre ou famille de genres, plage de BPM, note, couleur, My Tag, ajout récent, morceaux analysés
  seulement ; toute la bibliothèque par défaut. La roue tire dans le vivier dès le tirage suivant,
  et se désactive avec un message s'il est vide. Cocher une playlist, un dossier ou une clé USB y
  remet tous ses morceaux, même ceux décochés un par un.
- **Ajouté** : dans la liste des morceaux, une **case avant la pré-écoute** indique si le morceau
  est dans le vivier ; la cocher l'y ajoute seul (même s'il ne répond pas aux critères), la
  décocher l'en retire.
- **Ajouté** : **clés USB rekordbox** : une clé (ou un disque) préparée par rekordbox pour les
  platines apparaît d'elle-même dans les sources, section « Clés USB », avec ses playlists. Une
  case la met tout entière dans le vivier, ses playlists se cochent une à une. Débranchée, elle
  disparaît et le vivier revient à ce qu'il était sans elle ; rebranchée, elle revient. Ses
  morceaux se pré-écoutent et se glissent comme les autres, et rien n'est jamais écrit sur la clé.
- **Ajouté** : **morceaux introuvables** : un fichier absent est repéré à la première utilisation
  (pré-écoute, glisser-déposer, chargement dans le set, tirage) ; le morceau reste listé mais
  grisé et sort du vivier, et si la roue tombe dessus elle relance seule son tirage. Un nouveau
  scan ou une nouvelle lecture de rekordbox lui redonne sa chance.
- **Modifié** : sans rekordbox, les playlists et les critères propres à rekordbox (note, ajout,
  couleur, My Tags) restent visibles mais grisés, avec la raison ; ajouter un dossier reste
  possible dans tous les cas.
- **Modifié** : le filtre des morceaux à analyser (« Voir seulement ceux-là ») s'affiche au-dessus
  de la liste, avec « Tout afficher », et choisir une source le lève.
- **Modifié** : retirer un dossier garde dans la bibliothèque ses morceaux que rekordbox connaît.
- **Corrigé** : après le retrait d'un dossier, le nombre de morceaux et le résumé du dernier scan
  n'affichent plus les anciennes valeurs.

## [1.1.0] - 2026-10-22

- **Modifié** : mise à jour de composants internes, sans changement visible.

## [1.0.1] - 2026-10-21

Première version publique de Next Drop Wheel, la roue du hasard qui propose au DJ le prochain
morceau à mixer.

### Ce que fait l'application

- **La roue** : chaque tirage révèle trois propositions, à enchaîner d'un clic ; « Choisir
  moi-même » ouvre l'explorateur trié par compatibilité.
- **Des règles à la carte** : harmonie Camelot, tempo (avec half et double time), style et
  énergie, chacune ignorée, préférée ou imposée ; key lock, pitch extrême, curseur Chaos, mode
  Improbable et six ambiances prêtes à l'emploi.
- **rekordbox lu automatiquement** : BPM, tonalité, genre, note et autres analyses sont repris
  directement de rekordbox 6/7, sans export ni import, et relus dès qu'il enregistre une nouvelle
  analyse. Sa bibliothèque n'est jamais modifiée. Les tags des fichiers complètent le reste.
- **Le set** : les morceaux enchaînés sont conservés d'un lancement à l'autre et s'exportent en
  playlist M3U8 ou en XML rekordbox.
- **Pré-écoute** de chaque morceau dans l'application, et **glisser-déposer vers rekordbox** (deck
  ou collection) depuis les cartes, l'explorateur et le set.
- **Morceaux à analyser** : une playlist XML à importer dans rekordbox rassemble ceux qui n'ont
  pas encore de BPM ou de tonalité.
- **Thèmes** : sept thèmes, dont Contraste élevé, et des réglages fins (accent, halos, durée du
  tirage, couleurs de la roue, taille de l'interface), à exporter et importer.
- **Langues** : français et anglais.
- **Aide intégrée**, hors ligne (touche F1, ou « ? » à côté des principaux éléments).
- **Mises à jour** : recherche désactivée par défaut, à activer dans les réglages ; une nouvelle
  version est seulement proposée, et s'installe sur un clic.

### Corrigé

- Une base de données endommagée bloquait tout (« database disk image is malformed » à chaque
  action, ajout de dossier impossible). Elle est maintenant vérifiée à chaque lancement et réparée
  sans rien perdre ; si elle est irréparable, elle est mise de côté (jamais supprimée), une
  nouvelle est créée et rekordbox est relu aussitôt.

[2.0.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.0.0
[1.1.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.1.0
[1.0.1]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.0.1
