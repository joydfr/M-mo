# 🧱 La place des tests E2E dans la pyramide des tests

## 🗼 1. La pyramide des tests, c’est quoi ?

C’est un modèle visuel qui aide à organiser les types de tests selon leur coût, vitesse et portée.  
Voici sa structure :

```
    👤 Tests End-to-End (E2E)
   ⚙️ Tests d’intégration
  🔧 Tests unitaires
```

---

### 🔧 Base : Tests unitaires

- 🧠 Testent une fonction ou méthode isolée.
- ⚡ Très rapides à exécuter.
- 💰 Peu coûteux à maintenir.
- 🧪 Exemple : “La fonction Additionner(2, 3) retourne bien 5 ?”

👉 Ils doivent être les plus nombreux (~70 % des tests).

---

### ⚙️ Milieu : Tests d’intégration

- 🔗 Vérifient que plusieurs modules fonctionnent ensemble (ex : une API qui appelle une base de données).
- 🧪 Exemple : “Quand je crée un utilisateur, est-il bien enregistré en base ?”

👉 En nombre modéré, utiles pour valider les interactions internes (~20 % des tests).

---

### 👤 Sommet : Tests End-to-End (E2E)

- 🧭 Simulent un vrai utilisateur : clics, formulaires, navigation, etc.
- 🐢 Plus lents (car ils testent toute l’application).
- 🔧 Plus fragiles (dépendent de toute la stack technique).
- 💡 Mais cruciaux pour valider les parcours métier !

🧪 Exemple :  
“L’utilisateur s’inscrit → reçoit un mail de confirmation → se connecte → effectue un paiement”

👉 Ils doivent être peu nombreux mais bien choisis (~10 % des tests).

---

## ⚖️ Résumé : Pourquoi limiter les tests E2E ?

| 🟢 Points forts            | 🔴 Limites                |
| -------------------------- | ------------------------- |
| Reproduisent le réel 👤    | Lents à exécuter 🐌       |
| Testent toute l’app 🔄     | Maintenance fragile 🔧    |
| Renforcent la confiance ✅ | Débogage plus complexe 🧩 |

---

## 🧠 À retenir

✔ Les tests E2E sont essentiels pour valider les flux critiques.  
❌ Mais ils ne doivent pas remplacer les tests unitaires et d’intégration.  
📐 Utilise la pyramide pour construire une stratégie de test équilibrée, efficace et durable !
