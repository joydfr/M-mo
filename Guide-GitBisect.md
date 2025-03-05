# Git Bisect : La chasse aux bugs efficace

## Qu'est-ce que git bisect ?
`git bisect` est un outil puissant qui utilise la recherche dichotomique (ou recherche binaire) pour trouver le commit qui a introduit un bug. Il divise systématiquement l'historique en deux jusqu'à trouver le commit problématique.

## Processus de base

### 1. Démarrer la recherche
```bash
# Démarrer la session bisect
git bisect start

# Marquer le commit actuel comme mauvais (le bug est présent)
git bisect bad

# Marquer un ancien commit connu comme bon (le bug n'était pas présent)
git bisect good <commit-hash>
```

### 2. Processus de recherche
Git va automatiquement :
1. Sélectionner un commit à mi-chemin
2. Vous permettre de tester si le bug est présent
3. Marquer le commit comme "bon" ou "mauvais"
4. Répéter jusqu'à trouver le commit fautif

```bash
# Si le bug est présent dans le commit actuel
git bisect bad

# Si le bug n'est pas présent dans le commit actuel
git bisect good
```

### 3. Terminer la recherche
```bash
# Une fois le commit problématique trouvé
git bisect reset  # Retourne à la branche originale
```

## Exemple pratique

### Scénario : Trouver quand un bug a été introduit
```bash
# 1. Démarrer bisect
git bisect start

# 2. Marquer la version actuelle comme mauvaise
git bisect bad HEAD

# 3. Marquer une ancienne version connue comme bonne
git bisect good v1.0

# 4. Git checkout un commit au milieu
# 5. Testez votre application
# 6. Marquez le résultat
git bisect good  # ou git bisect bad

# 7. Répétez jusqu'à ce que Git trouve le commit fautif
# 8. Une fois terminé
git bisect reset
```

## Automatisation avec git bisect run

### Pour automatiser la recherche avec un script de test
```bash
# Créez un script de test qui retourne :
# 0 : le test passe (good)
# 1-127 (sauf 125) : le test échoue (bad)
# 125 : le commit ne peut pas être testé (skip)

# Lancer bisect avec le script
git bisect start
git bisect bad HEAD
git bisect good v1.0
git bisect run ./test-script.sh
```

### Exemple de script de test simple
```bash
#!/bin/bash
# test-script.sh

# Exécuter les tests
npm test  # ou toute autre commande de test

# Utiliser le code de retour du test
exit $?
```

## Bonnes pratiques

1. **Avant de commencer**
   - Assurez-vous d'avoir un test fiable pour identifier le bug
   - Committez ou stashez vos modifications en cours
   - Identifiez clairement une version "bonne" connue

2. **Pendant la recherche**
   - Testez toujours de la même manière
   - Notez le hash du commit problématique une fois trouvé
   - Documentez le processus de test

3. **Après avoir trouvé le bug**
   - Créez un test de régression
   - Documentez le bug dans le commit de correction
   - Ajoutez le cas de test à votre suite de tests

## Cas d'utilisation courants
- Trouver quand un bug a été introduit
- Identifier quel commit a cassé les tests
- Localiser des changements de performance
- Debugger des problèmes de régression

## Phrase mnémotechnique
"Bisect divise pour mieux régner sur les bugs"

## Commandes utiles supplémentaires
```bash
# Voir l'état actuel de bisect
git bisect log

# Voir les commits restants à tester
git bisect visualize

# Marquer un commit comme non testable
git bisect skip

# Redémarrer depuis le début
git bisect reset
```
