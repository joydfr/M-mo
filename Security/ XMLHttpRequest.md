## Mémo Sécurité avec XMLHttpRequest (XHR)

### 1. **Encoder les Réponses XHR** 📝

- **Utiliser des formats non exécutables** comme JSON ou XML pour les réponses XHR.
- **Éviter l'inclusion directe de HTML** pour prévenir les attaques XSS 🚫.

### 2. **Choisir la Méthode HTTP Adaptée** 🚀

- **Méthode GET** : Utiliser uniquement pour des données publiques et non sensibles. Éviter pour les données confidentielles ou les requêtes modifiant l'état du serveur 🚫.
- **Méthode POST** : Préférable pour éviter les fuites de données dans l'URL. Utiliser pour créer de nouvelles ressources 🔒.
- **Méthode PUT** : Utiliser pour mettre à jour ou remplacer des ressources existantes. Idempotent, ce qui réduit les risques liés à des requêtes répétées 🔒.

#### Exemples de Cas

- **Création d'un Compte Utilisateur** : Utiliser **POST** pour créer un nouveau compte.

  ```http
  POST /users HTTP/1.1
  Content-Type: application/json

  {
    "name": "John Doe",
    "email": "john@example.com"
  }
  ```

- **Mise à Jour d'un Compte Utilisateur** : Utiliser **PUT** pour mettre à jour un compte existant.

  ```http
  PUT /users/123 HTTP/1.1
  Content-Type: application/json

  {
    "name": "Jane Doe",
    "email": "jane@example.com"
  }
  ```

### 3. **Protéger contre les Attaques CSRF** 🛡️

- **Utiliser un CSRF-Token** : Générer un token aléatoire avec une entropie minimale de 128 bits pour chaque requête XHR 🔒.
- **Transmettre le Token** : Via un en-tête HTTP dédié ou un meta tag HTML 📝.

### 4. **Mettre en Œuvre une Politique de Sécurité des Contenus (CSP)** 🚫

- **Restreindre les Appels XHR** : Utiliser la directive `connect-src` pour limiter les appels XHR à l'origine du site ou à des domaines autorisés 📈.
- **Exemple de Directive CSP** : `Content-Security-Policy: default-src 'self'; connect-src 'self';` 📝.

En suivant ces recommandations, vous pouvez sécuriser efficacement vos requêtes XHR et protéger votre application contre diverses menaces courantes 😊.

---
