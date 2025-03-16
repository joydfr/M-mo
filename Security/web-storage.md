Voici un mémo visuel pour la précaution d'usage des bases de données de type Web Storage :

## Introduction aux bases de données Web Storage 📚

- **Définition** : Les bases de données Web Storage incluent `localStorage` et `sessionStorage`, utilisées pour stocker des données côté client 📊.
- **Caractéristiques** : `localStorage` est persistant, tandis que `sessionStorage` est non persistant et expire à la fin de la session 📆.

## Sécurité des bases de données Web Storage 🔒

- **Same-Origin Policy** : Les données sont accessibles uniquement par l'Origin qui les a créées 🚫.
- **Accès par les scripts** : Tous les scripts JavaScript d'une même Origin peuvent accéder aux mêmes données, ce qui peut être un risque si un script malveillant est injecté 🚨.

## Risques associés au stockage de données sensibles 🚫

- **Accès non sécurisé** : Les données sensibles stockées dans `localStorage` ou `sessionStorage` peuvent être accessibles à un attaquant si un script malveillant est injecté 🚫.
- **Recommandations** : Ne stocker que des données non sensibles, comme les préférences utilisateur 📝.

## Précautions pour les bases de données IndexedDB 📈

- **Caractéristiques** : IndexedDB offre un stockage clé/objet persistant avec une API asynchrone et transactionnelle 📊.
- **Risques** : Même contrôle d'accès que Web Storage, donc risques similaires pour les données sensibles 🚨.
- **Recommandations** : Utiliser uniquement pour des données non sensibles, comme le cache d'une application web 📝.

## Recommandations générales 📝

- **Analyse des risques** : Évaluer soigneusement les risques avant de stocker des informations sensibles dans ces bases de données 🔒.
- **Éviter Web SQL Database** : Cette API est obsolète et doit être évitée 🚫.
- **Utiliser des mécanismes sécurisés** pour stocker des informations sensibles, comme des cookies sécurisés ou des solutions serveur 🔒.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/bcde2a18-8996-458e-969b-a637b107d4b9/paste.txt
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/f0408111-a0e9-4a8e-bb24-fe83d01a258d/paste-2.txt

---
