> Showcase repository: the code and data of this project are private; this README describes it. / Dépôt vitrine : le code et les données de ce projet sont privés ; ce README le décrit.

# Atelier

A web portal that opens, for each team project, a coding-agent session shared by all its members, with a built-in meeting assistant.

## The problem

In a research and teaching team, not everyone has a coding agent installed, configured and connected to the right files. Atelier puts that agent in a browser. Each project member logs in and finds the same session, the same working folder and the same conversation. Colleagues use it to design course applications or to write change requests for an existing application.

## How it works

- One project equals one session. The server starts it in a `tmux` session placed in the project's working folder.
- `ttyd` displays that terminal in the browser; a "Message to the session" bar lets users write to the agent without handling the terminal.
- A single access rule: project member or administrator.
- Each project has a shared folder that the agent keeps up to date as work goes on.
- Conversations are kept on disk: after an interruption, the session resumes where it stopped.
- Updates are deployed by reloading the server, without cutting the running sessions.

## What is built

In service. Functions in place:

- Automatic closing every day at 20:00 (Paris time): banner at 19:45, instruction at 19:50 to active sessions to update their folder, sessions stopped at 20:00, conversations kept. Reopening on request only, 24 hours at most. Time calculation checked on 13 cases out of 13 (summer, winter, clock-change days, midnight).
- Meeting assistant: transcription, live summary, tree-shaped minutes, a panel to ask the meeting agent questions or give it instructions, an editable canvas of nodes and links, one active meeting at a time.
- Administration console: accounts, members, projects arranged by drag and drop in a folder tree.
- 15 skills from the web application design pipeline, synchronised every hour to the sessions.

In August 2026, the server was simplified: the idea of a personal agent per member was dropped in favour of one session per project (734 lines reduced to 549).

## What is public

This page is public. The tool, its code and the team's projects remain private.

## Technical stack

- Node.js (server and WebSocket)
- `tmux` and `ttyd`
- Docker
- Traefik
- HTML and JavaScript interface

---

## Version française

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
