# Merge

## dur�e: 15 min

Documentation : <https://git-scm.com/docs/git-merge>

## D�finition

Un merge fusionne deux historiques ensemble.

## Avant de d�marrer

Regarder la config de git, et rep�rer la ligne `merge.ff= XXXX` (true ou false)
Si elle est ? false, on va la passer ? true.

`git config merge.ff true`

## En pratique

Cr�er et atteindre une branche 'a-merger' depuis le master.
Modifier le fichier Training.Git\Pages\Index.cshtml en y ajoutant la ligne:
`<!--Index-->`

Commiter ce changement avec le message "Index"

Atteindre le master, et de l? cr�er et atteindre une branche "cible-merge".
V�rifier que la branche ne comporte pas le commit "Index" dans son historique.

Modifier le fichier Error.cshtml en y ajoutant la ligne
`<!--Error-->`

Commiter ce changement avec le message "Error".

On va ? pr�sent merger la branche "a-merger" dans la branche "cible-merge".
Observer l'historique de la branche "cible-merge".

Jouer la commande `git merge a-merger`

Un message apparait. Il s'agit de la d�finition du message d�crivant le commit qui va �tre cr�� par le merge. On ne le changera pas ici.
Appuyer sur Ctrl+c (pour acc�der ? la commande), puis taper 'wq' (write and quit) et valider avec la touche Entr�e.

Le merge cr�e un point de commit qui sera le dernier de l'historique. A observer dans le log.

## Fast Forward

Depuis le master, cr�er une nouvelle branche 'fast-forward' et l'atteindre.

De la m�me fa�on que pr�c�demment, merger la branche 'a-merger' dans la branch 'fast-forward'. Cette fois, aucun commit n'est cr��. Observer le log, on y voit le commit de la branche 'a-merger' qui a �t� directement appliqu�.

Retourner sur la branche master, puis cr�er et atteindre une branche 'no-fast-forward'

Cette fois-ci, on va merger la branche a-merger en pr�cisant qu'on ne fait pas de fast forward.

`git merge --no-ff a-merger`

Git va cette fois cr�er un nouveau commit.

### En quelques mots

Lors d'un merge d'une branche A dans une branche B, Git va comparer les historiques. S'il est possible d'appliquer les commits de B directement sur l'historique de A
(ce qui signifie que ce sont les m�mes historiques) alors Git va faire un Fast-Forward et appliquer les commits directement. La commande --no-ff (ou la config `merge.ff false`)
bloque ce comportement, et force la cr�ation d'un commit de merge.

### Exemples pratiques

Lors d'un merge d'une branche A dans master, on va pr�f�rer bloquer le fast-forward pour avoir un point de commit marquant ce merge.
Lors d'un merge du master dans une branche A, on peut pr�f�rer autoriser le fast forward, car le merge depuis le master n'a pas d'importance dans l'historique de travail.

## Squash

Il est possible lors d'un merge de squasher tous les commits de la branche source en un seul, notamment pour clarifier l'historique.

Cr�er une nouvelle branche 'squash-me' depuis cible-merge, et y faire 2 commits distincts.

Retourner sur 'cible-merge' et jouer la commande `git merge --squash squash-me`. Pr�ciser le message de commit et observer le r�sultat avec un git log