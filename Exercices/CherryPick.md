# Cherry-pick

## dur�e: 15 / 20 min

Documentation : <https://git-scm.com/docs/git-cherry-pick>

## D�finition

Le cherry-pick permet de r�cup�rer un commit sp�cifique depuis une branch pour l'appliquer en tant que dernier commit d'une autre.


## En pratique

Depuis master, cr�er et atteindre une branche 'cherry-pick-me'

A l'aide d'un �diteur de fichier, ins�rer dans Config.cs :
`/// a config file`

Commiter ce changement avec le message "Modif Config.cs".

A pr�sent modifier le contenu du fichier Settings.cs et y ins�rer en haut du fichier
`/// settings 1`

Commiter ce changement avec le message "Modif Settings.cs". __2 commits distincts doivent �tre visibles dans l'historique__

Afficher le log de la branche et rep�rer les lignes d�crivant les commits. Elles doivent ressembler � ceci :

`commit 433411e842d6c46658982b74625b1ff5f64e7da2
Author: Yann TERRAILLON <yann.terraillon@seloger.com>
Date:   Mon Jun 11 18:20:39 2018 +0200
Modif Config.cs
`

Double-cliquer sur le hash du commit "Modif Config.cs" (en gras dans l'exemple pr�c�dent) pour le copier.

Retourner sur la branche master et afficher l'historique avec un `git log`.

Jouer la commande `git cherry-pick 433411e842d6c46658982b74625b1ff5f64e7da2`

Regarder � nouveau l'historique du master.

## En cas de conflit

Depuis master cr�er et atteindre une branche 'cherry-pick-issue'

Modifier le contenu du fichier Settings.cs et y ins�rer en haut du fichier
`/// settings 2`

Commiter ce changement avec le message "Modif Settings.cs for conflict".

Cherry-picker le commit "Modif Settings.cs" depuis la branche 'cherry-pick-me'

Un message similaire � celui-ci apparait :

`$ git cherry-pick 33db9aed04b88e26f464ad06e47ef97d495f1964`
`error: could not apply 33db9ae... temp`
`hint: after resolving the conflicts, mark the corrected paths`
`hint: with 'git add <paths>' or 'git rm <paths>'`
`hint: and commit the result with 'git commit'`

Les modifications sont en conflit, car le m�me fichier est modifi� par 2 commits incompatibles. Afficher le statut nous donne plus d'informations :

`On branch cherry-pick-issue`
`You are currently cherry-picking commit 33db9ae.`
`(fix conflicts and run "git cherry-pick --continue")`
`(use "git cherry-pick --abort" to cancel the cherry-pick operation)`

`Unmerged paths:`
`(use "git add <file>..." to mark resolution)`

`both modified:   Training.Git/Settings.cs`

`no changes added to commit (use "git add" and/or "git commit -a")`

Pour r�soudre le conflit, plusieurs fa�ons sont possibles. Nous le ferons � la main dans le cadre de cet exercice.

Ouvrir le fichier Settings.cs. Les lignes conflictuelles sont marqu�es par des chevrons : <<<<<<< et >>>>>>>>

`<<<<<<< HEAD`
`/// settings 2`
`=======`
`/// settings 1`
`>>>>>>> 33db9ae... cherry-pick-me`

Dans le cadre de cet exercice nous allons conserver les 2 modifications. Editer le fichier pour supprimer les lignes suivantes :
`<<<<<<< HEAD`
`=======`
`>>>>>>> 33db9ae... cherry-pick-me`

Dans git bash marquer le conflit comme r�solu en faisant un `git add Training.Git/Settings.cs` ou un `git add`. __Attention__ le git add . va marquer tous les fichiers comme r�solus.
Il faut donc s'assurer que les conflits sont effectivement bien r�solus avant.

Une fois les conflits marqu�s comme r�solus, on va continuer le cherry-pick (qui s'�tait mis en pause pour la r�solution du conflit.)

`git cherry-pick --continue`

A noter que l'on peut aussi arr�ter l'op�ration et revenir � l'�tat d'avant d'avoir d�marr� le cherry-pick en faisant un `git cherry-pick --abort`

## Le HEAD

Le HEAD d�signe le point de commit le plus avanc� de la branche courante. Il change en m�me temps que l'on change de branche. 