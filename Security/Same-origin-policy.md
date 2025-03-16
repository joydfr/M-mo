# 🛡️ Mémo Visuel : Same-Origin Policy (SOP)

## 🌐 Définition de l'Origin
L'**Origin** d'une page est définie par **3 éléments** :
📌 **Protocole** (HTTP/HTTPS)  
📌 **Domaine** (exemple.org)  
📌 **Port** (ex : 80, 443, 8080)  

**Exemple :**  
🔹 `https://www.exemple.org:443/accueil.html` → **Origin :** `https://www.exemple.org`

---

## 🎯 Objectif de la SOP
**Limiter les interactions entre différentes Origins** pour **éviter les attaques** (XSS, CSRF, vol de données, etc.).

✅ **Même Origin** → Accès complet autorisé 🔓  
🚫 **Origines différentes** → Accès restreint 🔐  

---

## ⚠️ Restrictions selon la ressource

| 🏷️ **Ressource** | ⛔ **Restrictions SOP** |
|----------------|-----------------|
| **🖼️ iframe** | Une page A ne peut pas interagir avec une iframe d’Origin B. |
| **🔗 Fetch / AJAX** | Les requêtes vers une autre Origin sont bloquées. |
| **💾 Web Storage** | Chaque Origin a son propre stockage (LocalStorage, IndexedDB). |
| **🍪 Cookies** | Partage limité aux sous-domaines du même domaine. |
| **📜 JavaScript** | Peut être exécuté depuis une autre Origin mais avec accès limité aux données. |
| **🎨 CSS** | Peut modifier le style de la page, même s’il provient d’une autre Origin. |
| **📷 Médias** | Chargement autorisé, mais accès (lecture/écriture) restreint en Cross-Origin. |

---

## 🔓 Comment contourner la SOP ?

✔ **CORS (Cross-Origin Resource Sharing)** : Permet aux serveurs d'autoriser certaines requêtes Cross-Origin.
✔ **Web Messaging (postMessage)** : Permet une communication sécurisée entre Origins différentes (ex : iframes, popups).

---

## 🚨 Risques de Sécurité
❗ **JavaScript Cross-Origin** → Un script malveillant peut interagir avec la page.
❗ **CSS Cross-Origin** → Une feuille de style externe peut injecter du contenu non souhaité.
❗ **Attaques XSS / CSRF** → La SOP aide à prévenir mais ne protège pas totalement.

🔒 **Respecter la SOP est essentiel pour la sécurité web !** 🔒

