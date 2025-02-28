# Mémo : Conventions de nommage pour les commits Git

## Structure générale d'un commit
- **Titre** : ~50 caractères, impératif, précis
- **Ligne vide**
- **Description détaillée** (optionnelle) : explications, contexte, etc.

## Format Angular (plus strict et structuré)
```
<type>(<scope>): <description>
<LIGNE VIDE>
<body>
<LIGNE VIDE>
<footer>
```

### Types de commit Angular
| Type       | Utilisation                                      |
|------------|--------------------------------------------------|
| `feat`     | Une nouvelle fonctionnalité                      |
| `fix`      | Correction d'un bug                              |
| `docs`     | Changements dans la documentation                |
| `style`    | Formatage, point-virgules manquants, etc. (pas de changement de code) |
| `refactor` | Refactorisation du code (ni bug, ni fonctionnalité) |
| `perf`     | Amélioration des performances                    |
| `test`     | Ajout ou correction de tests                     |
| `build`    | Changements affectant le système de build ou les dépendances externes |
| `ci`       | Changements aux fichiers/scripts CI              |
| `chore`    | Autres changements ne modifiant pas src ou test  |
| `revert`   | Annule un commit précédent                       |

### Scope
- Nom du module affecté (optionnel)
- Exemples : `animations`, `core`, `compiler`, etc.

### Description
- Description courte en impératif présent
- Première lettre en minuscule
- Pas de point final

### Body (Corps)
- Motivation pour le changement
- Contraste avec le comportement précédent

### Footer (Pied de page)
- Références aux issues fermées : `Closes #123, #456`
- Breaking changes (changements majeurs) avec la description et migration

## Commits Breaking Changes
- Doivent inclure `BREAKING CHANGE:` dans le footer
- Description détaillée du changement, justification et migration

## Exemples de commits format Angular
```
feat(shopping-cart): ajouter le bouton de confirmation d'achat

Le bouton simplifie le processus d'achat et réduit les abandons de panier.

Closes #123
```

```
fix(auth): corriger la validation du jeton d'authentification

BREAKING CHANGE: La structure du jeton d'authentification a changé.
Avant: { token: string }
Après: { accessToken: string, refreshToken: string }

Migration: Mettez à jour les clients pour utiliser accessToken au lieu de token.
```

## Règles d'or générales
1. **Utiliser l'impératif** : "Ajoute", "Corrige", "Supprime" 
2. **Être spécifique** : Indiquez clairement ce qui a changé
3. **Un commit, une unité logique** : Chaque commit = une modification cohérente
4. **Séparer le titre et la description** par une ligne vide

## À éviter
- ❌ Messages vagues : "Fix bugs", "WIP", "Updates"
- ❌ Messages trop longs en première ligne
- ❌ Informations personnelles : "J'ai enfin résolu ce problème"
- ❌ Langage inapproprié
- ❌ Mélanger plusieurs modifications non liées
Sources
https://www.conventionalcommits.org/fr/v1.0.0/
https://github.com/angular/angular/blob/main/CONTRIBUTING.md#-commit-message-format
