# Journal des modifications

Les évolutions de Next Drop Wheel visibles dans l'application. Format inspiré de
[Keep a Changelog](https://keepachangelog.com/fr/1.1.0/), versions en
[SemVer](https://semver.org/lang/fr/). Les versions les plus récentes sont en haut.

## [2.4.0] - 2026-10-23

- **Ajouté** : Next Drop Wheel existe aussi pour **macOS**, pour les Mac à puce Apple comme pour
  les Mac Intel, en image disque `.dmg` à glisser dans Applications. L'application n'étant pas
  encore signée par Apple, la première ouverture se fait par clic droit > Ouvrir.
- **Ajouté** : sur macOS, une nouvelle version est annoncée comme sous Windows, et le bouton ouvre
  la page de téléchargement (elle ne s'installe pas d'elle-même).
- **Ajouté** : « Signaler un problème », dans Réglages > À propos et dans l'aide. Décrivez ce qui
  s'est passé, relisez le rapport de diagnostic joint, montré en entier, puis envoyez-le sur GitHub
  (un compte GitHub est nécessaire) ou par mail, ou copiez-le ou enregistrez-le pour le joindre
  vous-même. Le rapport ne contient ni vos chemins de fichiers, ni les noms de vos fichiers audio, ni
  votre nom d'utilisateur, et l'application n'envoie toujours rien elle-même : c'est vous qui
  l'envoyez.
- **Ajouté** : après une erreur, ou au lancement si la session précédente s'est mal terminée, un
  bandeau discret propose d'envoyer un rapport. Il n'apparaît jamais pendant un tirage ni en mode
  compact, au plus une fois par session, et se désactive par « Ne plus proposer » ou dans
  Réglages > À propos.
- **Ajouté** : l'écran affiché quand l'interface rencontre un problème propose de le signaler.
- **Ajouté** : l'aide a une rubrique « Signaler un problème », et la section Confidentialité
  d'À propos explique ce que contient un signalement et qui l'envoie.

## [2.3.0] - 2026-10-23

- **Amélioré** : les étiquettes de la roue (tonalité, tempo, titre) sont lisibles sur toutes les
  parts et dans tous les thèmes, et les textes secondaires et les tonalités ont un meilleur
  contraste. Les couleurs vives se concentrent sur la roue et sur « Enchaîner » : l'onglet actif, la
  valeur de Chaos et le morceau en cours du set sont plus sobres.
- **Amélioré** : navigation au clavier. Les flèches changent de proposition même quand le focus est
  sur le bouton de la roue, deux boutons précédent et suivant encadrent la proposition affichée,
  les modes de jeu se parcourent aux flèches, le curseur Chaos est annoncé correctement par les
  lecteurs d'écran, et Ctrl+, ouvre les réglages.
- **Amélioré** : la barre du haut tient sur la fenêtre à sa taille minimale, la liste du set défile
  quand elle est longue, le « ? » d'aide de la roue rejoint les boutons sous la roue, et
  l'application respecte les réglages de contraste élevé du système.
- **Amélioré** : en mode compact, la roue est un peu plus petite pour laisser le titre du morceau
  proposé lisible, « Enchaîner » passe en dessous, et la proposition se pré-écoute aussi, comme dans
  la fenêtre principale.
- **Modifié** : le journal de l'application (gardé sur l'ordinateur, pour un rapport de bug)
  n'enregistre plus les chemins de vos fichiers.
- **Corrigé** : une clé USB dont la bibliothèque rekordbox est anormalement volumineuse (ou
  abîmée) n'est plus copiée sur le disque de l'ordinateur : elle est signalée illisible, sans
  remplir le disque ni bloquer l'application.
- **Corrigé** : la recherche des clés USB ne regarde plus que les clés USB et cartes mémoire.
  Un lecteur réseau (surtout déconnecté) ne ralentit plus l'application, et n'est plus jamais
  interrogé.

## [2.2.0] - 2026-10-22

- **Corrigé** : la roue et ses propositions ne disparaissent plus quelques secondes après un
  glisser-déposer vers rekordbox, ou simplement pendant que rekordbox joue (en mode compact
  surtout) : « Enchaîner » reste disponible.

## [2.1.0] - 2026-10-22

### Interface allégée

- **Modifié** : le morceau **en cours** n'a plus sa carte à droite de la roue : il ouvre le
  panneau « Set en cours », mis en avant (badge « En cours », tonalité en couleur, artiste),
  au-dessus des morceaux déjà joués. Ce panneau passe **au-dessus du « Mode de jeu »
  (anciennement « Règles du jeu »)**, qui se **replie** : il est fermé à chaque lancement, son
  en-tête garde l'ambiance active sur une ligne, et un bouton à gauche du titre le déplie.
- **Ajouté** : dans « Set en cours », **survoler un morceau** (ou y placer le focus au clavier)
  affiche une petite carte flottante, dense : tonalité Camelot en couleur, titre, artiste, BPM,
  style, énergie, année et durée. Échap la referme ; elle reste toujours entière dans la fenêtre.
- **Modifié** : le **carrousel des propositions** disparaît, **la roue en tient lieu**. Après un
  tirage, les parts proposées restent entourées de pointillés et toutes les autres passent en
  gris ; la molette ou les flèches du clavier sur la roue, ou un clic sur une part en pointillés,
  changent de proposition, et la roue tourne pour l'amener sous le repère. Une part en
  pointillés se glisse aussi sur un deck rekordbox, comme une ligne du set. La proposition
  affichée tient sur une seule ligne sous la roue (tonalité, titre, BPM, compatibilité et son
  bouton de pré-écoute), suivie de « Enchaîner », qui la garde et relance aussitôt la roue pour
  la suite ; la survoler montre la même petite carte que le set, avec en plus ses chances d'être
  tirée et le pourquoi de chaque règle. « Choisir moi-même » reste sous la roue.
- **Ajouté** : **mode compact**, pour garder la roue à côté de rekordbox sans le cacher : le
  bouton à droite des onglets (ou Ctrl+Maj+M) réduit la fenêtre à la roue seule, petite et
  toujours au premier plan, déplaçable par sa barre de titre. Le bouton central lance la roue,
  la proposition affichée tient sur une ligne avec « Enchaîner », une part en pointillés se
  glisse directement sur un deck rekordbox, et le bouton en haut à gauche (ou Ctrl+Maj+M) rend
  la fenêtre complète à sa taille et à sa place d'avant. Le mode et l'emplacement de la petite
  fenêtre sont retrouvés au lancement suivant.
- **Modifié** : dans Réglages > Apparence, les **réglages fins** passent en haut et le choix du
  thème en bas.
- **Modifié** : **aide mise à jour** : nouvelles rubriques « Le set », « La bibliothèque et le
  vivier », « Mode compact » et « Réglages » (thèmes, réglages fins, langue, mises à jour), chaque
  ambiance expliquée, tous les raccourcis clavier et plus de cas de dépannage. Un « ? » ouvre
  aussi l'aide depuis le set et l'apparence.

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

[2.4.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.4.0
[2.3.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.3.0
[2.2.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.2.0
[2.1.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.1.0
[2.0.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v2.0.0
[1.1.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.1.0
[1.0.1]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.0.1
