# Confidentialité

Même texte que dans l'application (**Réglages > À propos**).

- **Aucune donnée n'est envoyée sur Internet** (hors recherche de mises à jour, si elle est activée) : pas de compte, pas de statistiques d'usage, pas de
  publicité, pas de télémétrie. L'application ne charge aucune ressource distante.
- **Tout reste sur l'ordinateur** : la bibliothèque, les réglages et le set sont enregistrés dans
  `%APPDATA%\Next Drop Wheel` (Windows) ou `~/Library/Application Support/Next Drop Wheel`
  (macOS), avec un journal technique local (`logs\main.log` : démarrage, mises à jour, erreurs ;
  aucun envoi). Pour tout effacer, quitter l'application puis supprimer ce dossier.
- **Fichiers lus** : uniquement les dossiers de musique choisis par l'utilisateur, et une copie en
  lecture seule de la bibliothèque rekordbox de cet ordinateur
  ([docs/REKORDBOX-DATABASE.md](docs/REKORDBOX-DATABASE.md)). Rien n'est modifié dans ces fichiers.
- **Fichiers écrits** : seulement ceux que l'utilisateur demande (export d'un set, playlist « À
  analyser », thème), à l'endroit qu'il choisit.
- **Mises à jour** : la recherche de mises à jour est **désactivée par défaut** et proposée une
  fois au premier lancement. Activée, elle lit seulement la liste des versions publiées sur GitHub
  (au lancement et une fois par jour), sans aucun identifiant ; rien n'est téléchargé ni installé
  sans l'accord de l'utilisateur. C'est la seule connexion réseau de l'application.
- **Signaler un problème** : uniquement à la demande de l'utilisateur, l'application ouvre son
  navigateur sur un signalement prérempli du dépôt public
  [Kwaku-IT/next-drop-wheel-releases](https://github.com/Kwaku-IT/next-drop-wheel-releases/issues)
  (signalement public, compte GitHub nécessaire) ou sa messagerie, avec un mail prérempli pour
  `contact@kwaku-it.com`. L'application n'envoie rien elle-même : c'est l'utilisateur qui envoie,
  depuis son navigateur ou sa messagerie. Le rapport joint lui est montré en entier avant : version
  de l'application et du système, réglages d'interface (langue, thème), état des sources sans
  détail (rekordbox trouvé ou non, nombre de morceaux, clé USB branchée ou non), dernières lignes
  du journal, masquées. Il ne contient ni chemin de dossier, ni nom de fichier audio, ni titre de
  morceau, ni nom d'utilisateur. La description saisie par l'utilisateur est envoyée telle qu'il
  l'a écrite. La proposition d'envoyer un rapport après une erreur se désactive (« Ne plus
  proposer », ou **Réglages > À propos**).
