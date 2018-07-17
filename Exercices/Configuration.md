# Configuration de Git

## dur�e: 5 min

Avant de d�marrer quoi que ce soit, quelques r�glages � faire pour travailler plus confortablement.
Depuis Git Bash, taper `git config --list` pour voir la liste des configurations existantes dans git.

D�finition de quelques alias pour travailler plus facilement :

- status (st) : `git config --global alias.st status`
- checkout (co) : `git config --global alias.co checkout`
- commit (ci) : `git config --global alias.ci commit`
- see last commit (last) : `git config --global alias.last 'log -1 HEAD'`

Les alias ne sont qu'un raccourci, il est important de ne pas oublier ce qu'ils signifient � la base :)

Refaire un `git config --list` et noter que les alias sont � pr�sent visibles dans les configs.

### Pour en savoir plus

Exemple de configuration plus pouss�e sur git : (paragraphe git-config(1))
<https://nuclearsquid.com/writings/git-tricks-tips-workflows/>