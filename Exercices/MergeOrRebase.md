# MergeOrRebase

Il s'agit d'un sujet tr�s discut� vis-�-vis de Git. Il y a des d�fenseurs des 2 cot�s. Certains d�fendent le merge, d'autres les rebases, certains mixent. Le rebase est r�guli�rement banni de certaines politiques d'entreprise.

Parmi les arguments :

- le rebase change l'historique et oblige � un push --force, donc est potentiellement dangereux. 
- le merge va cr�er un point de commit pas forc�ment d�sir�, surtout dans l'historique de la branche de travail.
- le merge peut se comporter comme un rebase dans le cas d'un fast-forward (mais sans changement d'historique)

Plus de d�tails sur les pours et contre ici : <https://www.atlassian.com/git/articles/git-team-workflows-merge-or-rebase>

## Personnellement

J'ai une pr�f�rence pour l'usage du rebase dans le cadre du travail sur la branche.
Le dev fait ses commits et rebase r�guli�rement sur develop pour �tre � jour.

Il push force sur l'origin de sa branche si besoin, mais il sait (normalement) ce qu'il fait et dispose ainsi de l'historique de son travail.

Une fois qu'il a termin� sa feature, il rebase et squashe son travail en un unique commit qui va �tre review�. (l'historique du travail n'int�resse normalement pas le reviewer)
Cela assure aussi que le dev est reponsable de la mergeabilit� de se branche.

Le reviewer sera par contre responsable de rapatrier la branche dans le d�velop. On va donc pr�f�rer un merge de la branche dans develop, pour disposer d'un historique clair, et ne pas alt�rer l'historique.
