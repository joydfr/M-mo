# Comprendre et utiliser git diff

## Phrase à retenir
> "Git diff compare les **D**ifférences entre **F**ichiers, **S**tages et **C**ommits" (DFSC)

## Utilisation détaillée

### 1. Comparaisons de base
- `git diff` : Affiche les différences entre le répertoire de travail et la zone de staging
- `git diff --staged` : Compare la zone de staging avec le dernier commit
- `git diff HEAD` : Compare le répertoire de travail avec le dernier commit

### 2. Comparaisons spécifiques
- `git diff <commit1> <commit2>` : Compare deux commits
- `git diff <branch1> <branch2>` : Compare deux branches
- `git diff <fichier>` : Limite la comparaison à un fichier spécifique

### 3. Options utiles
- `git diff --word-diff` : Affiche les différences mot par mot
- `git diff --stat` : Résumé statistique des modifications
- `git diff --color-words` : Colorise les différences par mot
- `git diff -w` ou `--ignore-all-space` : Ignore les changements d'espaces

### 4. Lecture des différences
```
diff --git a/fichier1 b/fichier2
index 1234567..89abcdef
--- a/ancien
+++ b/nouveau
@@ -1,3 +1,4 @@
 Ligne inchangée
-Ligne supprimée
+Ligne ajoutée
 Ligne inchangée
```

### 5. Bonnes pratiques
1. Vérifier les modifications avant chaque commit
2. Utiliser `--stat` pour un aperçu rapide
3. Combiner avec `git status` pour une vue d'ensemble
4. Privilégier les comparaisons ciblées sur des fichiers spécifiques

### 6. Cas d'usage courants
- Revue de code avant commit
- Vérification des modifications en attente
- Comparaison entre branches avant merge
- Analyse des différences entre versions

### 7. Astuces avancées
- `git diff master...feature` : Compare la branche feature depuis sa divergence avec master
- `git diff HEAD~3` : Compare avec il y a 3 commits
- `git diff --name-only` : Liste uniquement les fichiers modifiés
- `git diff --check` : Détecte les conflits de fusion potentiels
