# Journal des modifications

Les évolutions de Next Drop Wheel visibles dans l'application. Format inspiré de
[Keep a Changelog](https://keepachangelog.com/fr/1.1.0/), versions en
[SemVer](https://semver.org/lang/fr/). Les versions les plus récentes sont en haut.

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

[1.1.0]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.1.0
[1.0.1]: https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/tag/v1.0.1
