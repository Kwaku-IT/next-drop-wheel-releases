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
