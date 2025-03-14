# Mémo : Protection contre les vulnérabilités XSS

## 🔒 Qu'est-ce qu'une vulnérabilité XSS ?

Une attaque **Cross-Site Scripting (XSS)** permet à un attaquant d'injecter du code malveillant (JavaScript) dans une page web visitée par un utilisateur. Cela peut mener à :
- Le vol de session et l'usurpation d'identité
- L'exécution de scripts nuisibles sur l'appareil de la victime
- L'affichage de faux contenus trompeurs

## 🔗 Types de vulnérabilités XSS

1. **XSS Reflété** : Injection via une URL piégée (ex. lien malveillant dans un email)
2. **XSS Stocké** : L'attaquant injecte du code qui reste stocké sur le serveur (ex. forum, commentaire)
3. **XSS DOM** : Injection exploitant la modification dynamique du DOM côté client

## 🚀 Bonnes pratiques de protection

### ✅ 1. Maîtrise des contextes de composition
- Toujours **encoder** les entrées utilisateur en fonction du contexte (HTML, URL, JS...)
- **Ne pas utiliser** `innerHTML`, `document.write()` ou `insertAdjacentHTML()`
- Privilégier `textContent`, `createTextNode()`, `setAttribute()`

### ✅ 2. Utilisation de Content Security Policy (CSP)
- Implémenter l'en-tête HTTP : `Content-Security-Policy: default-src 'self'; script-src 'self'`
- Empêcher l'exécution de scripts inline (`'unsafe-inline'`) et eval (`'unsafe-eval'`)

### ✅ 3. Séparation des contenus
- **Dissocier** le HTML, CSS, JavaScript et les données JSON
- Charger scripts et styles depuis des fichiers externes
- Envoyer les données en `application/json` plutôt qu'en HTML

### ✅ 4. Validation et échappement des entrées
- Filtrer et valider toutes les entrées utilisateur
- Appliquer un **"escape"** adapté à chaque contexte (ex. `encodeURIComponent()` pour les URLs)

## 🎨 Notion de "Sinks"

Les **sinks** sont des points d'injection dans le DOM qui peuvent exécuter du code malveillant si des données non sécurisées y sont insérées.

**Exemples de sinks dangereux :**
```js
// Vulnérable à XSS
let userInput = "<script>alert('XSS')</script>";
document.innerHTML = userInput; // DANGEREUX
```

**Alternatives sécurisées :**
```js
// Protégé contre XSS
let userInput = "<script>alert('XSS')</script>";
document.textContent = userInput; // Sécurisé
```

## 🚨 Règles à appliquer

### R4 : Utiliser l'API DOM à bon escient
- ✔️ Préférer `textContent` et `createTextNode()` pour insérer du texte
- ✖️ Éviter `innerHTML` et `document.write()`

### R5 : Dissocier les sources de contenu
- HTML pour la structure
- CSS pour le style
- JavaScript pour la logique
- JSON pour les données

### R6 : Spécifier les Content-Type
- Ex. `Content-Type: application/json` pour les API

### R7 : Vérifier l'échappement des contenus inclus
- Utiliser des fonctions d'encodage adaptées à chaque contexte

### R8 : Valider les données externes
- Implémenter des **listes blanches** de valeurs autorisées

## 🔧 Exemple de code sécurisé

```js
async function printUsername(username) {
    try {
        // Encodage URL pour éviter XSS
        const res = await fetch('https://api.com/user/' + encodeURIComponent(username));
        const jsonData = await res.json();
        
        // Encodage HTML
        document.getElementById('username').textContent = jsonData.username;
    } catch (err) {
        console.error("Erreur de récupération", err);
    }
}
```

## 🔒 Conclusion
L'attaque XSS repose sur une mauvaise gestion des entrées utilisateur et de l'encodage des données. Adopter les bonnes pratiques ci-dessus permet de sécuriser efficacement une application web contre ces vulnérabilités.

---

