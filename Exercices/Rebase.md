# Rebase

## dur�e: 15/20 min

Documentation : <https://git-scm.com/docs/git-rebase>

## D�finition

Un rebase d'une branche A sur une branche B va appliquer tous les commits de la branche A sur l'historique de la branche B.

Exemple avec 2 historiques :

branche A : A-B-C-X-Y-Z  (X, Y, Z sont les commits qui ont �t� cr��s sur la branche)
branche B : A-B-C-D

depuis la branche A, `git rebase B` va changer l'historique de A par celui de B et appliquer les commits dessus. Elle devient ainsi :

branche A : A-B-C-D-X-Y-Z

## En Pratique

Depuis le master cr�er une branche 'nouvel-historique'

Modifier le fichier Contact.html en y ajoutant la ligne:
`<!--Contact-->`

Commiter ce changement avec le message "Contact"

Atteindre le master, et de l? cr�er et atteindre une branche "cible-rebase".
V�rifier que la branche ne comporte pas le commit "Contact" dans son historique.

Modifier le fichier About.html en y ajoutant la ligne
`<!--About-->`

Commiter ce changement avec le message "About".
Pusher ces changements sur l'origin.

On va ? pr�sent rebaser la branche 'cible-rebase' sur la branche 'nouvel-historique'
Dans la branche courante, jouer la commande `git rebase nouvel-historique`

Observer le r�sultat dans l'historique de la branche.

A noter : aucun nouveau commit n'a �t� cr��.

Observer ? pr�sent le statut dans lequel on se trouve : il y est possible de faire un pull depuis l'origin. Si on pushe, le push va �tre rejet�.
Pourquoi : l'historique de l'origin et celui du local sont diff�rents. Il faut les resynchroniser.
On va donc faire un `push --force` pour forcer le local sur l'origin.

A noter : il est hautement recommand� de v�rifier 2 fois avant de faire un push force, sous peine de perdre son historique de travail.


## En cas de conflit

En changeant l'historique, des conflits peuvent arriver de la m�me fa�on que lors d'un cherry-pick.
Ils se r�solvent aussi de la m�me fa�on.
La diff�rence sera dans les commandes ? jouer apr�s r�solution :

`git rebase --continue` pour poursuivre le rebase
`git rebase --abort` pour revenir ? l'�tat d'avant rebase

## Rebase interactive

Il est possible de profiter du rebase pour regrouper ("squasher") des commits.

Depuis le master cr�er une branche 'rebase-interactive'

Modifier le fichier Contact.html en y ajoutant la ligne:
`<!--Contact-->`

Commiter ce changement avec le message "Contact"

Modifier le fichier About.html en y ajoutant la ligne
`<!--About-->`

Commiter ce changement avec le message "About"

Jouer la commande `git rebase master -i` (-i pour interactive).

Git propose d'abord de s�lectionner les commits qui vont �tre retenus (via le m?me �diteur qu'on a d�j? rencontr�.)

Vocabulaire :
'push' pour conserver le commit (p)
'squash' pour merger le commit avec le pr�c�dent (s)

Point important : __le premier commit de la liste sera toujours ? laiser en push__

Dans notre cas nous allons squasher le 2eme commit.
Aller au d�but de sa ligne avec le curseur, appuyer sur la touche S une fois, puis suppr jusqu'? avoir supprimer le mot 'push'. Taper 'squash' ? la place,
puis ctrl+c, et enfin 'wq'

Git va alors appliquer les commits, puis proposer de d�finir un nouveau message pour celui qui va �tre un nouveau commit (car il est devenu une combinaison de 2 commits)

L'�dition des messages se fait de la m�me fa�on que la s�lection des commits. Sinon il est possible de supprimer une ligne directement en appuyant 2 fois sur 'd'

Une fois le squash termin�, observer l'historique des commits.
