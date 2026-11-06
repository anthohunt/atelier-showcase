[English](README.md) · **Français**

**Anthony Hunt** · [Fiche du projet sur ingevision.cloud](https://ingevision.cloud/?p=atelier) · [LinkedIn](https://www.linkedin.com/in/anthony-hunt-3948a9196) · [Profil GitHub](https://github.com/anthohunt)

> Dépôt vitrine : le code et les données de ce projet sont privés ; ce README le décrit.

# Atelier

Un portail web qui ouvre, pour chaque projet d'équipe, une session d'agent de programmation partagée par tous ses membres, avec un assistant de réunion intégré.

## Le problème

Dans une équipe de recherche et d'enseignement, tout le monde n'a pas un agent de programmation installé, configuré et relié aux bons fichiers. L'Atelier met cet agent dans un navigateur. Chaque membre d'un projet se connecte et retrouve la même session, le même dossier de travail et la même conversation. Il sert à des collègues qui conçoivent des applications de cours ou rédigent des demandes d'évolution sur une application existante.

## Comment ça marche

- Un projet égale une session. Le serveur la lance dans une session `tmux` placée dans le dossier de travail du projet.
- `ttyd` affiche ce terminal dans le navigateur ; une barre « Message à la session » permet d'écrire à l'agent sans manipuler le terminal.
- Règle d'accès unique : membre du projet ou administrateur.
- Chaque projet a un dossier partagé que l'agent tient à jour au fil du travail.
- Les conversations sont gardées sur disque : après une coupure, la session reprend là où elle s'était arrêtée.
- Les mises à jour se déploient par un rechargement du serveur, sans couper les sessions en cours.

## Ce qui est construit

En service. Fonctions en place :

- Fermeture automatique chaque jour à 20h00 (heure de Paris) : bandeau à 19h45, consigne à 19h50 aux sessions actives de mettre leur dossier à jour, arrêt des sessions à 20h00, conversations conservées. Réouverture sur demande seulement, 24 h au plus. Calcul des heures vérifié sur 13 cas sur 13 (été, hiver, jours de changement d'heure, minuit).
- Assistant de réunion : transcription, synthèse en direct, compte rendu en arbre, panneau pour poser des questions ou donner des consignes à l'agent de réunion, canevas de nœuds et de liens modifiable, une seule réunion active à la fois.
- Console d'administration : comptes, membres, projets rangés par glisser-déposer dans une arborescence de dossiers.
- 15 compétences de la chaîne de conception d'applications web, synchronisées chaque heure vers les sessions.

En août 2026, le serveur a été simplifié : l'idée d'un agent personnel par membre a été abandonnée au profit d'une session par projet (734 lignes ramenées à 549).

## Ce qui est public

Cette fiche est publique. L'outil, son code et les projets de l'équipe restent privés.

## Pile technique

- Node.js (serveur et WebSocket)
- `tmux` et `ttyd`
- Docker
- Traefik
- Interface en HTML et JavaScript
