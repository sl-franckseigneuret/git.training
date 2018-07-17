# Working with Git

## dur�e: 20 / 30 min

Cr�er une branche "work", et l'atteindre.

Tout d'abord regardons l'�tat de la branche avec un `git status`
Ou avec un alias `git st`

Et l'historique existant avec un `git log`.
Documentation : <https://git-scm.com/docs/git-log>
Pour creuser un peu le log : <https://www.atlassian.com/git/tutorials/git-log>)

## Changements dans les fichiers

### Modifications

Ouvrir le fichier Program.cs avec un �diteur, et supprimer les lignes suivantes :

`using System;`
`using System.Collections.Generic;`
`using System.IO;`
`using System.Linq;`
`using System.Threading.Tasks;`

Sauvegarder et fermer le fichier.

Ouvrir le fichier Startup.cs avec un �diteur, et ajouter la ligne suivante :

`services.AddMemoryCache();`

Juste avant : `services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);`

Sauvegarder et fermer le fichier.

### Status, log et diff

Observer les changements avec un `git status`, et l'historique avec un `git log`.

Pour voir ce qui a �t� fait, et qui va �tre commit�, on va faire un `git diff` (pour voir l'int�gralit� des changements) ou un `git diff FILENAME` pour voir les changements sur un fichier sp�cifique.
IMPORTANT : cela ne marchera pas si les fichiers ont d�j� �t� ajout�s ou commit�s. Il faut donc le faire avant d'engager quoi que ce soit. 
A noter : ce n'est pas la solution la plus esth�tique. En g�n�ral on pr�f�rera utiliser un logiciel avec une interface qui pr�sente cela de fa�on plus esth�tique.

Les fichiers sont modifi�s, mais non commit�s encore. On va corriger cela en faisant un `git commit -am "Mon premier commit"`

-a marque tous les fichiers qui ont �t� modifi�s ou effac�s en pr�t � �tre commit� (staged for commit) SAUF ceux qui ne sont pas dans l'index de git (qu'il faut ajouter avec un git add)
-m "mon message" indique le message de commit

-am est la concat�nation des 2 commandes.

Observer les changements avec un `git status`, et l'historique avec un `git log`.
Afficher le dernier commit avec un `git last`

Pusher les fichiers sur l'origin (cr�er l'upstream si besoin).

## Ajouts de fichiers

Dans le r�pertoire de travail, ajouter les fichiers vides suivants (? cot� de Startup.cs et Program.cs):
`Config.cs`
`Settings.cs`
`Filter.cs`

Observer les changements avec un `git status`, et l'historique avec un `git log`.

Commiter les fichiers et observer le statut avec un `git status`. Les fichiers ajout�s ne sont pas encore inclus dans l'index git!
On va donc devoir les y ajouter. Faire un `git add Training.Git/Config.cs`et observer les changements avec un `git status`.

Il est aussi possible, et plus pratique, d'ajouter les fichiers par lot avec un `git add .`. Le git add ajoute les fichiers � l'index git et les stage pour commit dans la foul�e.

Maintenant que les fichiers sont ajout�s, on peut les commiter.
Faire un `git status` et noter qu'il est pr�cis� que le local est "1 commit ahead of origin".

Regarder le log de l'origin avec `git log origin/master` et le comparer avec le log local

Pusher les fichiers sur l'origin.

### Comprendre le cycle de vie des fichiers

![Lifecyle](https://git-scm.com/figures/18333fig0201-tn.png)

## Retour au master

__La partie se d�roulant sur github n'est pas d�velopp�e ici.__
Atteindre la page <https://github.com/YOURUSERNAME/git-training/branches>
Cliquer sur le bouton "New Pull request" ? cot� du nom de la branch r�cemment push�e, puis "Create Pull Request"
Enfin Merger la pull request depuis l'onglet "Conversation".

Retourner sur Git bash, et atteindre le master.

Faire un `git pull`. Puis faire un `git log` pour observer les changements.
A noter : un 'git pull' est la combinaison de 2 commandes : 'git fetch', suivi de 'git merge origin'

Retourner sur <https://github.com/YOURUSERNAME/git-training> et cr�er une branche.  
Depuis git bash, faire un `git fetch` pour voir apparaitre la nouvelle branche.
A noter : le 'git fetch' r�cup�re les nouvelles branches cr��es sur l'origin mais elles n'apparaitront pas avec un git branch. Par contre il est possible de les checkout-er.