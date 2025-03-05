# Guide du .gitignore

## Types de .gitignore

Il existe trois niveaux de .gitignore :

1. **Global (.gitignore_global)**
   - S'applique à tous vos projets Git sur votre machine
   - Emplacement habituel : `~/.gitignore_global`
   - Configuration : `git config --global core.excludesfile ~/.gitignore_global`
   - Idéal pour les fichiers spécifiques à votre système/IDE

2. **Local (par projet)**
   - Fichier `.gitignore` à la racine du projet
   - S'applique uniquement au projet en cours
   - Versionné avec le projet
   - Partagé avec tous les contributeurs

3. **Local personnel (.git/info/exclude)**
   - Dans le dossier `.git` de votre projet
   - Non versionné
   - Uniquement pour vos exclusions personnelles

## Syntaxe de base

```bash
# Ignorer un fichier spécifique
secret.key

# Ignorer tous les fichiers d'un type
*.log
*.tmp

# Ignorer un dossier et son contenu
node_modules/
dist/

# Ignorer un chemin spécifique
builds/debug/

# Ne pas ignorer un fichier spécifique
!important.log

# Ignorer les fichiers dans n'importe quel sous-dossier
**/temp/
```

## Exemples courants par type de projet

### Pour un projet Node.js
```bash
node_modules/
npm-debug.log
.env
.DS_Store
```

### Pour un projet Python
```bash
__pycache__/
*.py[cod]
*$py.class
venv/
.env
```

### Pour un projet C#
```bash
# Fichiers binaires et de compilation
bin/
obj/
*.exe
*.dll
*.pdb
*.cache

# Fichiers Visual Studio
.vs/
*.user
*.suo
*.sln.docstates
*_i.c
*_p.c
*.ncb
*.suo
*.tlb
*.tlh
*.bak
*.cache
*.ilk
*.log
[Bb]in
[Dd]ebug*/
*.lib
*.sbr
*.resharper
packages/
```

## Bonnes pratiques

1. **Commencer tôt**
   - Créez le .gitignore avant votre premier commit
   - Utilisez des modèles existants (disponibles sur github/gitignore)

2. **Être spécifique**
   - Évitez les règles trop générales
   - Commentez les règles complexes
   - Groupez les règles par contexte

3. **Maintenance**
   - Mettez à jour régulièrement
   - Retirez les règles obsolètes
   - Vérifiez avec `git status` que les bonnes choses sont ignorées

## Commandes utiles

```bash
# Vérifier pourquoi un fichier est ignoré
git check-ignore -v nomfichier.txt

# Ajouter de force un fichier ignoré
git add -f fichier.log

# Nettoyer les fichiers ignorés
git clean -Xn  # Simulation
git clean -Xf  # Suppression réelle
```

## Astuce mnémotechnique
> "**G**lobal, **I**n-Project, **T**emporary" (GIT) :
> - **G**lobal : Configuration système (~/.gitignore_global)
> - **I**n-Project : Fichier de projet (.gitignore)
> - **T**emporary : Exclusions personnelles (.git/info/exclude)

## Dépannage courant

1. **Le fichier est toujours suivi malgré .gitignore**
   ```bash
   # Si le fichier était déjà suivi
   git rm --cached fichier
   ```

2. **Règles qui ne fonctionnent pas**
   - Vérifiez que le chemin est relatif à l'emplacement du .gitignore
   - Attention aux espaces en fin de ligne
   - Vérifiez la casse (sensible sous Linux/Mac)

3. **Conflit entre règles**
   - Les règles sont appliquées de haut en bas
   - Une règle d'inclusion (!pattern) l'emporte sur une règle d'exclusion
