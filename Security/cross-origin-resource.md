# 🔄 Mémo Visuel : Cross-Origin Resource Sharing (CORS)

## 🌍 Pourquoi utiliser CORS ?
Le **CORS** permet de contourner la **Same-Origin Policy (SOP)** afin d'autoriser les échanges entre différentes Origins. 

🎯 **Exemple d’usage** : 
- Accéder à une API météo depuis un site web
- Afficher des actualités d’un autre domaine

📌 **CORS remplace des méthodes obsolètes et risquées** comme :
✔ **Proxyfication** : Technique où un serveur intermédiaire récupère les données pour contourner la SOP, souvent vulnérable aux attaques.
✔ **JSON-P (JSON with Padding)** : Ancienne technique exploitant `<script>` pour charger des données, mais avec des risques de sécurité.

---

## 🔄 Comment fonctionne CORS ?
CORS est un **contrat** entre le serveur et le navigateur basé sur des **en-têtes HTTP**. Voici le processus :

1️⃣ **Requête Cross-Origin envoyée par le navigateur** 📤
   - L’en-tête `Origin` est inclus pour indiquer l'origine du site appelant.

2️⃣ **Réponse du serveur** 📩
   - L’en-tête `Access-Control-Allow-Origin` précise si l'origine est autorisée.
   - Exemple : `Access-Control-Allow-Origin: https://mon-site.com`
   - Pour autoriser toutes les origines : `Access-Control-Allow-Origin: *`

3️⃣ **Décision du navigateur** 🤖
   - Si l’origine est autorisée → ✅ **Réponse acceptée**
   - Si l’origine n’est pas autorisée → ❌ **Requête bloquée** + **Erreur de sécurité**

---

## 🔐 Cas particulier : Requêtes Authentifiées
Les requêtes envoyant des **Cookies** ou un **Jeton d’authentification** nécessitent des en-têtes supplémentaires.
✔ `Access-Control-Allow-Credentials: true` → Indique que les identifiants peuvent être envoyés.

📌 **Important** : `Access-Control-Allow-Origin: *` **ne fonctionne pas** avec des requêtes authentifiées !

---

## 🚀 CORS en résumé
✅ Permet d’accéder à des ressources externes de manière sécurisée.
✅ Nécessite une configuration correcte côté serveur.
❌ Ne doit pas être utilisé à la légère pour éviter des failles de sécurité.

🔒 **Bien configurer CORS est essentiel pour éviter les attaques Cross-Origin !**

