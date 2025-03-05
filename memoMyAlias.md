
# Documentation des Alias Oh My Zsh

## Navigation et Commandes Système
| Alias | Commande | Description |
|-------|----------|-------------|
| `..` | `cd ..` | Remonter d'un niveau dans l'arborescence |
| `...` | `cd ../..` | Remonter de deux niveaux |
| `lla` | `ls -la` | Lister tous les fichiers avec détails |
| `la` | `ls -A` | Lister tous les fichiers (incluant cachés) |
| `~` | `cd ~` | Aller au répertoire home |
| `n` | `nano` | Ouvrir l'éditeur nano |

## Git - Commandes de Base
| Alias | Commande | Description |
|-------|----------|-------------|
| `gs` | `git status` | Voir l'état du dépôt |
| `ga` | `git add` | Ajouter des fichiers au staging |
| `gc` | `git commit` | Créer un commit |
| `gp` | `git push` | Pousser les changements |
| `gl` | `git pull` | Tirer les changements |
| `gd` | `git diff` | Voir les différences |
| `gts` | `git stash` | Mettre de côté les changements |
| `gb` | `git branch` | Gérer les branches |
| `lg` | `lazygit` | Ouvrir l'interface Lazygit |

## Git Branch & Switch
```bash
gcbs() {
    if [ -z "$1" ]; then
        echo "Usage: gbs <branch-name>"
        return 1
    fi
    if git show-ref --quiet refs/heads/"$1"; then
        echo "La branche '$1' existe déjà, switching..."
        git switch "$1"
    else
        echo "Création et switch vers la nouvelle branche '$1'..."
        git branch "$1" && git switch "$1"
    fi
}
```
**Usage** : `gbs nouvelle-branche`
- Crée une nouvelle branche si elle n'existe pas
- Switch vers la branche si elle existe déjà

## GitHub CLI
| Alias | Commande | Description |
|-------|----------|-------------|
| `gpl` | `gh pr list` | Lister les pull requests |
| `gpm` | `gh pr list --assignee @me` | Lister mes pull requests |
| `gil` | `gh issue list` | Lister les issues |
| `gim` | `gh issue list --assignee @me` | Lister mes issues |
| `gpc` | `gh pr create --fill --web` | Créer une PR (dans le navigateur) |
| `gpr` | `gh pr review` | Revoir une PR |
| `gpv` | `gh pr view --web` | Voir une PR dans le navigateur |

## Exemples d'Utilisation

### Workflow Git Basique
```bash
gs                  # Vérifier l'état
ga .                # Ajouter tous les fichiers
gc -m "message"     # Créer un commit
gp                  # Pousser les changements
```

### Workflow GitHub CLI
```bash
gpm                 # Vérifier mes PRs
gbs feature/xyz     # Créer/switcher sur une branche
# ... travailler sur le code ...
gpc                 # Créer une PR
```

### Navigation Rapide
```bash
..                  # Remonter d'un niveau
lla                 # Voir tous les fichiers
~                   # Retourner au home
```

## Notes
- Les alias peuvent être combinés avec des arguments additionnels
- Utilisez `--help` après les commandes pour plus d'informations
- Pour recharger les alias après modification : `source ~/.zshrc`
