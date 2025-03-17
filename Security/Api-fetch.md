## Mémo Sécurité avec l'API Fetch

### 1. **Présentation de l'API Fetch** 🚀

- **Alternative à XMLHttpRequest (XHR)** : Fetch est une API moderne qui utilise des promesses (Promises) pour une meilleure flexibilité et simplicité.
- **Avantages** : Meilleure séparation des usages avec des objets distincts (`Headers`, `Request`, `Response`), manipulation facilitée des données de bas niveau (blobs), et intégration avec des API comme Cache, Referrer Policy, ou SRI.

### 2. **Options de Configuration Fetch** 📝

- **Mode** :
  - **no-cors** : Contrôle que la requête est simple (GET, HEAD) et non CORS.
  - **cors** : Active le preflight si nécessaire.
  - **same-origin** : Contrôle que la requête est effectuée sur la même Origin.
- **Credentials** :
  - **omit** : Ne pas envoyer les cookies ou données d'authentification.
  - **same-origin** (par défaut) : Envoyer les cookies uniquement pour la même Origin.
  - **include** : Envoyer les cookies et données d'authentification pour toutes les requêtes.
- **Redirect** : Contrôle le comportement en cas de redirection (301, 302, 303, 307, 308).

#### Exemple de Code Fetch

```javascript
const url = "/api/ville/Paris";
const params = {
  method: "GET",
  mode: "same-origin",
  credentials: "omit",
  cache: "default",
  referrerPolicy: "no-referrer",
  redirect: "error",
  integrity: "sha256-abcdef1234567890",
};

fetch(url, params)
  .then((res) => res.json())
  .then((data) => handleMeteoData(data));

// Avec async/await
(async () => {
  const meteoDataRaw = await fetch(url, params);
  const meteoDataJson = await meteoDataRaw.json();
  handleMeteoData(meteoDataJson);
})();
```

---

### 3. **Avantages de Fetch par rapport à XMLHttpRequest (XHR)** ✅

- **Simplicité et Modernité** : Fetch est plus simple à utiliser grâce aux promesses et à la syntaxe `async/await`.
- **Gestion des Erreurs** : Les erreurs sont gérées via des promesses (`catch`), ce qui rend le code plus lisible.
- **Annulation des Requêtes** : Fetch permet d'annuler une requête en cours grâce à l'API `AbortController`.
- **Meilleure Séparation des Usages** : Les objets distincts (`Headers`, `Request`, `Response`) permettent une gestion plus claire des éléments HTTP.
- **Intégration avec d'autres API** : Compatible avec Cache API, Referrer Policy, Subresource Integrity (SRI), etc.

---

### 4. **Limites de Fetch** 🚨

- **Manque de Progress Bar Intégrée** : Contrairement à XHR, Fetch ne fournit pas directement une barre de progression pour les téléchargements. Il faut utiliser un `ReadableStream` pour cela.
- **Pas de Timeout Intégré** : Fetch ne permet pas de définir un délai par défaut pour les requêtes. Il faut utiliser un mécanisme externe comme `AbortController`.
- **Manuel Stringification des Données JSON** : Contrairement à certaines bibliothèques qui automatisent cette tâche.

---

### 5. **Menaces Possibles avec Fetch** 🛡️

#### Menaces Courantes :

1. **Cross-Site Scripting (XSS)** :
   - Si les données reçues via Fetch sont directement injectées dans le DOM sans être sanitizées, cela peut permettre l'exécution de scripts malveillants.
2. **Cross-Site Request Forgery (CSRF)** :
   - Les requêtes Fetch peuvent être utilisées par un attaquant pour effectuer des actions malveillantes sur une application sans que l'utilisateur en soit conscient.
3. **Transmission Insecure** :
   - Utiliser Fetch sans HTTPS expose les données en transit à des attaques de type "man-in-the-middle".

#### Risques Spécifiques à CORS :

- Une mauvaise configuration CORS peut exposer l'application à des fuites de données sensibles ou permettre l'accès non autorisé depuis des origines externes.

---

### 6. **Prévention des Menaces avec Fetch** 🔒

#### Recommandations Générales :

1. **Utiliser HTTPS** :
   - Toutes les requêtes Fetch doivent être effectuées sur HTTPS pour chiffrer les données en transit et éviter leur interception.
2. **Valider et Sanitizer les Entrées Utilisateur** :
   - Toujours valider et nettoyer les données reçues avant de les utiliser dans le DOM ou dans la logique applicative.
3. **Implémenter des Tokens Anti-CSRF** :
   - Utiliser un CSRF-token pour protéger contre les attaques CSRF.
4. **Mettre en Place une Politique de Sécurité des Contenus (CSP)** :
   - Restreindre les sources autorisées via une CSP pour prévenir les attaques XSS.

#### Recommandations Spécifiques à CORS :

1. **Spécifier les Origines Autorisées dans CORS** :
   - Éviter d'utiliser `Access-Control-Allow-Origin: *` pour limiter l'accès aux ressources sensibles uniquement aux origines fiables.
2. **Forcer le Preflight pour les Données Sensibles** :
   - Configurer le serveur pour exiger un preflight avant toute requête contenant des informations sensibles afin de réduire le risque de fuite.
3. **Contrôler l’En-tête Origin** :
   - Vérifier systématiquement l’en-tête `Origin` pour s'assurer que seuls les domaines autorisés peuvent accéder aux ressources.

---
