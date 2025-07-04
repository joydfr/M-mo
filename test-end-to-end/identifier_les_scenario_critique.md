# 🎯 Identifier les scénarios critiques pour les tests End-to-End (E2E)

---

## 🧠 Pourquoi choisir seulement certains scénarios ?

Les tests E2E sont :

- 🐢 **Lents** à exécuter
- 🔧 **Fragiles** en cas de changement d’interface
- 💰 **Coûteux** à maintenir

👉 Il faut donc choisir avec soin ce qu’on teste en priorité.

---

## 🔍 Comment identifier un scénario critique ?

Pose-toi ces questions :

1. **Ce scénario est-il vital pour le métier ?**  
   → Sans lui, l’application n’a plus de valeur 📉  
   _Exemple : le paiement, la connexion utilisateur…_
2. **Ce scénario est-il fréquent ?**  
   → Plus il est utilisé, plus il doit être testé régulièrement 🔁
3. **Y a-t-il des points d’intégration sensibles ?**  
   → Plusieurs modules / services communiquent ensemble ? 🧩
4. **Des régressions sont-elles déjà survenues ici ?**  
   → L’historique de bugs guide souvent les tests à ajouter 🐞

---

## 🧭 Exemples de scénarios E2E critiques

| 🌐 Type d’application        | ✅ Scénarios à tester en E2E                                                           |
| ---------------------------- | -------------------------------------------------------------------------------------- |
| 🛒 **E-commerce**            | Connexion 🔐, recherche 🔎, ajout panier 🛒, paiement 💳, confirmation d’achat 📧      |
| 📩 **Application SaaS**      | Création de compte 👤, onboarding 🧭, modification de profil 📝, gestion des droits 🔐 |
| 🎓 **Plateforme e-learning** | Inscription à un cours 📚, progression utilisateur 🧩, validation d’un quiz ✅         |
| 🧾 **Portail administratif** | Téléversement de pièce 📄, soumission de formulaire 📝, suivi de dossier 🔍            |

---

## 🧼 Astuce : catégoriser les scénarios

- 🎯 **Parcours critique métier**  
  L’utilisateur accomplit une action essentielle au service (ex. acheter, réserver, signaler).
- 🔄 **Parcours technique à forte intégration**  
  L’action fait appel à plusieurs couches techniques (base, API, back + front).
- 📉 **Parcours à risque ou historique de bugs**  
  Instables ou ayant déjà causé des régressions.

---

## 🛠️ Outils pour t’aider à identifier les bons scénarios

- 🔄 Analyse des logs utilisateurs (Hotjar, Matomo, Analytics)
- 🧩 Carte de parcours client (User Journey)
- 🐞 Historique des bugs dans l’outil de suivi (Jira, GitLab, etc.)

---

## 🧠 À retenir

✔ Cible les scénarios critiques, fréquents et sensibles  
✔ Reste pragmatique : peu de scénarios E2E, mais bien choisis  
✔ Combine avec tests unitaires + intégration pour une couverture complète 🧱
