# Next Drop Wheel : téléchargements

Roue du hasard pour DJ : à partir du morceau en cours, Next Drop Wheel propose le suivant en
s'appuyant sur vos analyses rekordbox (tonalité Camelot, tempo, style, énergie). Application de
bureau pour Windows et macOS, éditée par **Kwaku IT**.

Ce dépôt contient uniquement les **versions publiées** et leurs documents : le code source n'y est
pas. Version actuelle : **2.3.0**.

## Télécharger

Sur la page [Releases](https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/latest), choisir :

| Fichier                               | Pour qui                                                                |
| ------------------------------------- | ----------------------------------------------------------------------- |
| `Next-Drop-Wheel-Setup-X.Y.Z.exe`     | Windows, installation classique : menu Démarrer, désinstallation propre |
| `Next-Drop-Wheel-X.Y.Z-portable.exe`  | Windows, fichier unique sans installation (clé USB, PC de soirée)       |
| `Next-Drop-Wheel-X.Y.Z-mac-arm64.dmg` | Mac avec puce Apple (M1 et suivantes)                                   |
| `Next-Drop-Wheel-X.Y.Z-mac-x64.dmg`   | Mac avec processeur Intel                                               |

Les fichiers `latest.yml`, `latest-mac.yml`, `.zip` et `.blockmap` servent à la recherche de mises
à jour : inutile de les télécharger. Les fichiers macOS peuvent arriver sur la page un peu après
ceux de Windows.

**Windows SmartScreen** : tant que l'application n'est pas signée, Windows peut afficher « Windows
a protégé votre ordinateur » au premier lancement. Cliquer sur « Informations complémentaires »
puis « Exécuter quand même ».

**macOS** : ouvrir le `.dmg` et glisser Next Drop Wheel dans le dossier Applications. L'application
n'est pas encore signée par Apple : au premier lancement, macOS refuse de l'ouvrir. Faire un clic
droit (ou Ctrl + clic) sur l'application dans Applications > Ouvrir, puis confirmer « Ouvrir ». Si
macOS ne propose pas ce bouton, aller dans Réglages Système > Confidentialité et sécurité, puis
cliquer sur « Ouvrir quand même » en face de Next Drop Wheel. Les lancements suivants se font
normalement.

## Mises à jour

La recherche de mises à jour est **désactivée par défaut** et proposée une fois au premier
lancement (Réglages > À propos > Mises à jour). Une nouvelle version est seulement **proposée** :
vous choisissez de la télécharger, puis de redémarrer pour l'installer. Rien n'est installé sans
votre accord. Sur macOS, tant que l'application n'est pas signée, elle ne peut pas s'installer
elle-même : elle annonce la nouvelle version et ouvre cette page de téléchargement. Ce qui change à
chaque version : [CHANGELOG.md](CHANGELOG.md).

## Documents

- [Contrat de licence](LICENSE) : logiciel propriétaire, © Kwaku IT, tous droits réservés. Il est
  affiché et à accepter dans l'installateur Windows.
- [Confidentialité](PRIVACY.md) : aucune donnée envoyée sur Internet, hors recherche de mises à jour
  si vous l'activez.
- [Lecture de la bibliothèque rekordbox](docs/REKORDBOX-DATABASE.md) : copie en lecture seule,
  risques et limites.
- [Licences tierces](THIRD_PARTY_NOTICES.md) : bibliothèques et polices embarquées, avec leur
  licence.
- [Sécurité](SECURITY.md) : signaler une faille.

## Signaler un problème

Onglet [Issues](https://github.com/Kwaku-IT/next-drop-wheel-releases/issues/new/choose) > « Signaler un problème ».
Pour une faille de sécurité, suivre [SECURITY.md](SECURITY.md) plutôt qu'un ticket public.

## Marques

rekordbox est une marque d'AlphaTheta Corporation (Pioneer DJ). Camelot est une marque de Mixed In
Key LLC. Next Drop Wheel n'est ni affilié à ces sociétés, ni approuvé ou soutenu par elles.

---

_Fichier mis à jour automatiquement à chaque version : ne pas le modifier ici._

## English

Next Drop Wheel is a DJ "what to play next" wheel for Windows and macOS, built on your rekordbox
analyses. This repository only hosts the published versions and their documents (licence, privacy
policy, third-party notices, changelog); the source code is not here. Download the Windows
installer, the portable version or the macOS disk image (Apple Silicon or Intel) from
[Releases](https://github.com/Kwaku-IT/next-drop-wheel-releases/releases/latest). The macOS app is not signed by Apple
yet: open it the first time with a right-click > Open. Proprietary software, © Kwaku IT, all rights
reserved ([LICENSE](LICENSE)).
