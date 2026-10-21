# Sécurité

## Signaler une faille

Merci de **ne pas ouvrir de ticket public** pour une faille de sécurité. Écrire à l'équipe Kwaku IT
via le contact du dépôt GitHub (onglet « Security » > « Report a vulnerability ») en décrivant :

- la version de Next Drop Wheel et du système ;
- les étapes pour reproduire, et ce qu'un attaquant pourrait obtenir ;
- si possible, un fichier d'exemple (export XML, thème `.json`, fichier audio) qui la déclenche.

Une réponse est donnée sous 7 jours ; le correctif est livré dans une nouvelle version publiée.

## Versions maintenues

Seule la dernière version publiée reçoit des correctifs de sécurité.

## Ce que l'application protège déjà

En résumé : fenêtre Electron isolée (sandbox,
`contextIsolation`, CSP stricte, navigation et fenêtres bloquées), toute entrée IPC validée par
zod, chemins de fichiers issus des seules boîtes de dialogue natives et confinés au dossier choisi,
XML sans DTD ni entités et de taille plafonnée, fichiers de thème validés et jamais appliqués comme
du CSS, bibliothèque rekordbox lue sur une copie en lecture seule, aucune donnée envoyée sur le
réseau.
