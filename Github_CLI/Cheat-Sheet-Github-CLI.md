# 📋 GitHub CLI Cheat Sheet

## 🔑 Authentification
```bash
gh auth login                    # Connexion interactive
gh auth logout                   # Déconnexion
gh auth status                   # Vérifier le statut de connexion
```

## 📦 Gestion des Dépôts
```bash
gh repo create                   # Créer un nouveau dépôt
gh repo clone USER/REPO         # Cloner un dépôt
gh repo fork                    # Forker le dépôt actuel
gh repo view                    # Voir les infos du dépôt
gh repo list                    # Lister vos dépôts
```

## 🎫 Issues
```bash
gh issue create                 # Créer une issue
gh issue list                   # Lister les issues
gh issue status                # Voir le statut des issues
gh issue view NUMERO           # Voir une issue spécifique
gh issue close NUMERO         # Fermer une issue
```

## 🔄 Pull Requests
```bash
gh pr create                    # Créer une PR
gh pr list                      # Lister les PRs
gh pr checkout NUMERO          # Checkout une PR
gh pr view NUMERO             # Voir une PR
gh pr merge NUMERO            # Merger une PR
```

## 🏃 GitHub Actions
```bash
gh run list                     # Lister les workflows
gh run view                     # Voir un workflow
gh workflow list               # Lister tous les workflows
gh workflow enable             # Activer un workflow
```

## 📢 Gestion des Releases
```bash
gh release create TAG          # Créer une release
gh release list               # Lister les releases
gh release view TAG           # Voir une release
```

## 🔍 Recherche
```bash
gh search repos QUERY         # Rechercher des dépôts
gh search issues QUERY       # Rechercher des issues
gh search prs QUERY         # Rechercher des PRs
```

## 💻 Configuration
```bash
gh config set editor vim     # Définir l'éditeur par défaut
gh config set git_protocol ssh  # Définir le protocole git
gh alias set               # Créer un alias
```

## 🔧 Options Utiles
```bash
--web                      # Ouvrir dans le navigateur
--json                     # Format de sortie JSON
--help                     # Afficher l'aide
-R, --repo OWNER/REPO     # Spécifier un dépôt
```

## 📝 Exemples Pratiques
```bash
# Créer une PR avec titre et description
gh pr create --title "Fix bug" --body "Description du fix"

# Lister les PRs en attente de review
gh pr list --state open --label "needs review"

# Voir les stats d'un dépôt
gh repo view --json stargazers,forks,watchers

# Créer une release avec notes
gh release create v1.0.0 --title "Version 1.0.0" --notes "Notes de version"
```

## 🚀 Astuces Avancées
```bash
# Créer un alias pour une commande fréquente
gh alias set prc 'pr create --title "$1" --body "$2"'

# Utiliser avec jq pour filtrer la sortie JSON
gh pr list --json number,title,author --jq '.[] | select(.author.login == "username")'

# Automatiser la création d'issues
gh issue create --title "Bug Report" --body "$(cat bug_template.md)"
```
