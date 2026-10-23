# Sécurité

## Signaler une faille

Merci de **ne pas ouvrir de ticket public** pour une faille de sécurité. Écrire à l'équipe Kwaku IT
via le contact du dépôt GitHub (onglet « Security » > « Report a vulnerability ») en décrivant :

- la version de Next Drop Wheel et du système ;
- les étapes pour reproduire, et ce qu'un attaquant pourrait obtenir ;
- si possible, un fichier d'exemple (export XML, thème `.json`, fichier audio) qui la déclenche.

Une réponse est donnée sous 7 jours ; le correctif est livré dans une nouvelle version publiée.

Pour un bug ordinaire (sans enjeu de sécurité), l'application propose **Signaler un problème**
(**Réglages > À propos**, ou après une erreur ; cette proposition se désactive). Sur demande
seulement, elle ouvre le navigateur sur un signalement prérempli du dépôt public (visible de tous,
compte GitHub nécessaire) ou la messagerie, avec un mail pour `contact@kwaku-it.com`. Elle n'envoie
rien elle-même. Le rapport joint est montré en entier avant tout envoi : version de l'application et
du système, réglages d'interface, état des sources sans détail, dernières lignes du journal
masquées ; ni chemin, ni nom de fichier audio, ni titre, ni nom d'utilisateur. La description
saisie est envoyée telle quelle : n'y décrivez pas une faille, utilisez le canal privé ci-dessus.

## Versions maintenues

Seule la dernière version publiée reçoit des correctifs de sécurité.

## Ce que l'application protège déjà

En résumé : fenêtre Electron isolée (sandbox,
`contextIsolation`, CSP stricte, navigation et fenêtres bloquées), toute entrée IPC validée par
zod, chemins de fichiers issus des seules boîtes de dialogue natives et confinés au dossier choisi,
XML sans DTD ni entités et de taille plafonnée, fichiers de thème validés et jamais appliqués comme
du CSS, bibliothèque rekordbox lue sur une copie en lecture seule, chemins de partages réseau listés par
un import rekordbox jamais ouverts, aucune donnée envoyée sur le réseau.
