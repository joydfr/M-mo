# Fonctionnalités clés de GitHub - Guide de référence rapide

## Pull Requests (Demandes de tirage)
- **Objectif** : Proposer des modifications de code et demander leur fusion dans une autre branche
- **Fonctions principales** :
  - Mécanisme de révision de code
  - Fil de discussion pour les modifications proposées
  - Peut être lié aux "issues" qu'il résout
  - Possibilité d'exiger des approbations avant la fusion
- **Quand l'utiliser** : Lorsque vous avez terminé le travail dans une branche de fonctionnalité et souhaitez la fusionner dans la branche principale

## Branches
- **Objectif** : Créer des versions parallèles de votre code
- **Fonctions principales** :
  - Isoler le travail de développement sans affecter le code principal
  - Prendre en charge le développement parallèle par plusieurs contributeurs
  - Peuvent être protégées pour empêcher les modifications directes
- **Types courants** :
  - `main`/`master` : Branche principale avec le code de production
  - Branches de fonctionnalités : Branches temporaires pour les nouvelles fonctionnalités
  - Branches de correctifs : Corrections rapides pour les problèmes de production

## Issues (Problèmes)
- **Objectif** : Suivre les bugs, les améliorations et les tâches
- **Fonctions principales** :
  - Organiser le travail avec des étiquettes, des jalons et des assignations
  - Forum de discussion pour des problèmes ou fonctionnalités spécifiques
  - Peut être référencé dans les commits et les pull requests
  - Historique consultable des défis du projet
- **Bonne pratique** : Créer des issues détaillées avec les étapes pour reproduire les bugs ou des exigences claires pour les fonctionnalités

## Settings (Paramètres de projet)
- **Objectif** : Configurer les options spécifiques au dépôt
- **Fonctions principales** :
  - Gérer les permissions d'accès
  - Configurer les règles de protection des branches
  - Mettre en place des webhooks et des intégrations
  - Activer/désactiver les fonctionnalités GitHub (Wiki, Issues, etc.)
  - Configurer GitHub Pages
- **Paramètres importants** : Règles de protection des branches, accès des collaborateurs

## Settings (Paramètres de profil)
- **Objectif** : Gérer votre présence personnelle et la sécurité sur GitHub
- **Fonctions principales** :
  - Modifier les informations de profil (photo, bio, statut)
  - Gérer les tokens d'accès personnels
  - Configurer les préférences de notification
  - Configurer les clés SSH et GPG
  - Configurer l'authentification à deux facteurs
- **Bonne pratique de sécurité** : Examiner régulièrement les tokens d'accès et activer l'authentification à deux facteurs

---

**À retenir** : Les flux de travail GitHub efficaces impliquent généralement la création d'une issue, la création d'une branche pour cette issue, la création d'une pull request une fois terminé, et la fusion après révision.
