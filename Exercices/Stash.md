# Stash

## dur�e: 10 min

Documentation : <https://git-scm.com/docs/git-stash>

## D�finition

Le stash permet de "remiser" un travail en cours (= non commit�) dans une pile pour pouvoir le reprendre plus tard.
Une fois les modifications stash�es, toutes les op�rations habituelles de git sont possibles.

## En pratique

Depuis master, cr�er et atteindre une branche "stash"

Ajouter un fichier "MiddleWare.cs" dans le r�pertoire de la solution.
Modifier le fichier "Filter.cs" et y ajouter la ligne
`/// Stash comment`

Observer les changements avec un `git status`, et l'historique avec un `git log`.
Les fichiers ne sont actuellement ni commit�s, ni m�me dans l'index git (dans le cas de Middleware.cs).

Jouer la commande `git stash`, et observer � nouveau le statut et l'historique.

Atteindre la branche master. Puis revenir � la branche "stash"
Modifier le fichier Config.cs et y ajouter la ligne
`/// another change`

Observer les changements mis de cot� avec la commande `git stash list` et appliquer ceux-ci avec `git stash apply`

Effectuer � nouveau des modifications sur les fichiers, les stasher � nouveau en utilisant la commande `git stash hello world`
Observer la stash list � nouveau. Observer le diff du stash en jouant un `git stash show`

Cette fois, supprimer le dernier stash avec `git stash drop`

Pour terminer, supprimer le fichier MiddleWare.cs depuis l'explorateur