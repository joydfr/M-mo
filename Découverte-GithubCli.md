# Guide Complet de GitHub CLI (gh)

## Introduction
GitHub CLI est un outil en ligne de commande qui permet d'utiliser GitHub directement depuis votre terminal. Il simplifie de nombreuses tâches courantes liées à GitHub sans avoir besoin d'utiliser l'interface web.

## Installation

### Sur macOS
```bash
brew install gh
```

### Sur Windows
```bash
winget install --id GitHub.cli
```

### Sur Linux (Ubuntu/Debian)
```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

## Configuration initiale
```bash
gh auth login
```
Cette commande lance le processus d'authentification interactif.

## Commandes essentielles

### Gestion des dépôts

1. **Créer un nouveau dépôt**
```bash
gh repo create mon-projet --public
```

2. **Cloner un dépôt**
```bash
gh repo clone proprietaire/depot
```

3. **Voir les informations d'un dépôt**
```bash
gh repo view proprietaire/depot
```

### Gestion des issues

1. **Créer une issue**
```bash
gh issue create --title "Titre de l'issue" --body "Description de l'issue"
```

2. **Lister les issues**
```bash
gh issue list
```

3. **Voir une issue spécifique**
```bash
gh issue view NUMERO
```

### Gestion des Pull Requests

1. **Créer une pull request**
```bash
gh pr create --title "Titre de la PR" --body "Description de la PR"
```

2. **Lister les pull requests**
```bash
gh pr list
```

3. **Examiner une pull request**
```bash
gh pr checkout NUMERO
```

4. **Fusionner une pull request**
```bash
gh pr merge NUMERO
```

## Fonctionnalités avancées

### Gestion des workflows

1. **Voir les actions en cours**
```bash
gh run list
```

2. **Voir les logs d'une action**
```bash
gh run view NUMERO_RUN
```

### Gestion des releases

1. **Créer une release**
```bash
gh release create v1.0.0 --title "Version 1.0.0" --notes "Notes de version"
```

2. **Lister les releases**
```bash
gh release list
```

## Astuces et bonnes pratiques

1. **Alias personnalisés**
   - Créez des alias pour vos commandes fréquentes :
   ```bash
   gh alias set prc 'pr create --title "$1" --body "$2"'
   ```

2. **Configuration du format de sortie**
   - Utilisez --json pour obtenir une sortie formatée :
   ```bash
   gh issue list --json number,title,assignees
   ```

3. **Utilisation des filtres**
   - Filtrez les PRs par statut :
   ```bash
   gh pr list --state merged
   ```

## Extensions

GitHub CLI supporte les extensions qui étendent ses fonctionnalités :

1. **Installation d'une extension**
```bash
gh extension install PROPRIETAIRE/NOM_EXTENSION
```

2. **Liste des extensions installées**
```bash
gh extension list
```

## Intégration avec d'autres outils

1. **VS Code**
```bash
gh pr checkout NUMERO --web
```

2. **Scripts shell**
```bash
gh api repos/:owner/:repo/issues --jq '.[].title'
```

## Conclusion

GitHub CLI est un outil puissant qui peut considérablement améliorer votre workflow de développement. En maîtrisant ces commandes, vous pouvez :
- Gagner du temps en évitant les allers-retours vers l'interface web
- Automatiser des tâches répétitives
- Intégrer GitHub dans vos scripts et votre workflow de développement
- Améliorer votre productivité globale avec Git et GitHub
