# Mémo Vim - Guide des commandes essentielles

## Modes
- `i` : Mode insertion (avant le curseur)
- `a` : Mode insertion (après le curseur)
- `Esc` : Retour au mode normal
- `v` : Mode visuel (sélection)
- `V` : Mode visuel ligne
- `o` : Nouvelle ligne en dessous + mode insertion
- `O` : Nouvelle ligne au dessus + mode insertion

## Navigation
### Déplacements basiques
- `h j k l` : Gauche, bas, haut, droite
- `w` : Début du mot suivant
- `b` : Début du mot précédent
- `e` : Fin du mot
- `0` : Début de ligne
- `$` : Fin de ligne
- `^` : Premier caractère non-blanc de la ligne

### Déplacements avancés
- `gg` : Début du fichier
- `G` : Fin du fichier
- `:{numero}` : Aller à la ligne {numero}
- `%` : Aller à la parenthèse/accolade correspondante
- `Ctrl+u` : Remonter d'une demi-page
- `Ctrl+d` : Descendre d'une demi-page
- `{` : Paragraphe précédent
- `}` : Paragraphe suivant

## Édition
### Actions basiques
- `x` : Supprimer caractère sous le curseur
- `dd` : Couper la ligne
- `yy` : Copier la ligne
- `p` : Coller après
- `P` : Coller avant
- `u` : Annuler
- `Ctrl+r` : Refaire

### Actions avancées
- `ciw` : Changer le mot sous le curseur
- `ci"` : Changer le texte entre guillemets
- `ci(` : Changer le texte entre parenthèses
- `dd` : Supprimer la ligne
- `D` : Supprimer jusqu'à la fin de la ligne
- `cc` : Changer toute la ligne
- `>>` : Indenter la ligne
- `<<` : Désindenter la ligne

## Recherche et remplacement
- `/motif` : Rechercher 'motif' vers l'avant
- `?motif` : Rechercher 'motif' vers l'arrière
- `n` : Occurrence suivante
- `N` : Occurrence précédente
- `:%s/ancien/nouveau/g` : Remplacer toutes les occurrences
- `:%s/ancien/nouveau/gc` : Remplacer avec confirmation

## Commandes importantes
- `:w` : Sauvegarder
- `:q` : Quitter
- `:wq` ou `ZZ` : Sauvegarder et quitter
- `:q!` : Quitter sans sauvegarder
- `:help` : Aide
- `:set number` : Afficher les numéros de ligne
- `:set relativenumber` : Numéros de ligne relatifs

## Copier/Coller multi-registres
- `"ayy` : Copier la ligne dans le registre 'a'
- `"ap` : Coller le contenu du registre 'a'

## Multi-fichiers
- `:e fichier` : Ouvrir un fichier
- `:bn` : Buffer suivant
- `:bp` : Buffer précédent
- `:ls` : Lister les buffers
- `:sp` : Split horizontal
- `:vsp` : Split vertical
- `Ctrl+w` puis `h j k l` : Naviguer entre les fenêtres

## Astuces
1. Combiner les commandes :
   - `3dd` : Supprimer 3 lignes
   - `2yy` : Copier 2 lignes
   - `5j` : Descendre de 5 lignes

2. La commande "." répète la dernière modification

3. Pour sélectionner du texte entre délimiteurs :
   - `vi"` : Sélectionner entre guillemets
   - `vi(` : Sélectionner entre parenthèses
   - `vi{` : Sélectionner entre accolades

## Configuration recommandée (~/.vimrc)
```vim
set number          " Affiche les numéros de ligne
set relativenumber  " Numéros de ligne relatifs
set autoindent     " Auto-indentation
set smartindent    " Indentation intelligente
set expandtab      " Tabs en espaces
set tabstop=4      " Largeur de tab = 4 espaces
set shiftwidth=4   " Indentation = 4 espaces
syntax on          " Coloration syntaxique
```
