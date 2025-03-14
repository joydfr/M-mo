# 🔐 Mémo Visuel : Content Security Policy (CSP)

## 🛡️ Qu’est-ce que CSP ?
Le **Content Security Policy (CSP)** est une **politique de sécurité** permettant de **limiter les ressources autorisées** sur un site web.

🎯 **Objectif** :
✔ Réduire les risques d’attaques XSS (Cross-Site Scripting) 🚫💻
✔ Restreindre le chargement de scripts et autres ressources 🔍
✔ Ajouter un niveau de protection contre les injections de code malveillant 🏰

---

## ⚙️ Comment configurer CSP ?
CSP est défini **côté serveur** via :
📌 **En-tête HTTP** : `Content-Security-Policy`
📌 **Balise meta** : `<meta http-equiv="Content-Security-Policy">`

---

## 📝 Exemples de stratégies CSP

1️⃣ **Autoriser uniquement les ressources de la même Origin et en HTTPS** 🔒
```csp
Content-Security-Policy: default-src 'self' https:;
```
✅ Sécurisé, limite les ressources externes
❌ Bloque JavaScript inline et les fonctions `eval()`

2️⃣ **Autoriser JavaScript inline et les fonctions d’évaluation de code** ⚠️
```csp
Content-Security-Policy: default-src 'self'; script-src 'unsafe-inline' 'unsafe-eval';
```
🚨 **DANGER** : Expose à des attaques XSS
❌ Mauvaise pratique de sécurité

---

## 🏆 Bonnes Pratiques CSP
✔ **Privilégier `default-src 'self'`** pour limiter les ressources aux mêmes Origins.
✔ **Éviter `unsafe-inline` et `unsafe-eval`** qui peuvent exécuter du code malveillant.
✔ **Utiliser des nonce (`nonce-xxxx`) ou des hashes (`sha256-xxxx`)** pour autoriser du JavaScript spécifique.
✔ **Tester les règles CSP en mode `Content-Security-Policy-Report-Only`** avant mise en production.

🚀 **CSP est un rempart essentiel contre les attaques XSS et les injections de scripts !** 🔥

