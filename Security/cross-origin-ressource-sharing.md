## Mémo Sécurité avec CORS

### 1. **Principe de CORS** 🚀

- **CORS** permet de dépasser la **Same-Origin Policy** en établissant un contrat entre le serveur de destination et le navigateur via des en-têtes HTTP.
- Remplace les techniques risquées comme JSON-P et la proxyfication XHR par le serveur 🚫.

### 2. **Types de Requêtes CORS** 📝

- **Requêtes Simples** : Utilisent des méthodes et en-têtes "safelisted" (GET, HEAD, POST avec certains en-têtes). Ne nécessitent pas de preflight.
- **Requêtes Preflighted** : Utilisent des méthodes ou en-têtes non standard. Un preflight est envoyé avant la requête réelle pour vérifier les permissions 📝.

### 3. **Preflight Request** 🚫

- **Méthode OPTIONS** : Envoyée avant la requête réelle pour vérifier si elle est autorisée.
- **En-têtes** : `Access-Control-Request-Method` et `Access-Control-Request-Headers` indiquent les méthodes et en-têtes à utiliser.
- **Réponse** : Le serveur répond avec des en-têtes comme `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, et `Access-Control-Allow-Headers` pour autoriser ou refuser la requête 📝.

#### Exemple de Preflight

```http
// Requête Preflight
OPTIONS /resource HTTP/1.1
Origin: http://example.com
Access-Control-Request-Method: PUT
Access-Control-Request-Headers: Content-Type

// Réponse du Serveur
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: http://example.com
Access-Control-Allow-Methods: PUT, GET, POST
Access-Control-Allow-Headers: Content-Type
```

### 4. **Menaces Évitées par CORS** 🛡️

- **Attaques XSS** : CORS réduit les risques de Cross-Site Scripting en limitant l'accès aux ressources à des origines autorisées[2].
- **Attaques CSRF** : En contrôlant les origines autorisées, CORS aide à prévenir les attaques de type Cross-Site Request Forgery[4].

### 5. **Risques Associés à CORS** 🚨

- **Misconfigurations** : Utilisation de wildcards (`*`) dans `Access-Control-Allow-Origin` ou autorisation de sites non fiables peuvent exposer les données sensibles[1][4].
- **Fuites de Données** : Configurations trop permissives peuvent permettre l'accès non autorisé aux informations utilisateur[4].

### 6. **Prévention des Risques CORS** 🔒

- **Spécifier les Origines Autorisées** : Utiliser des valeurs spécifiques dans `Access-Control-Allow-Origin` au lieu de wildcards[1][5].
- **Autoriser Seulement les Sites Fiables** : Ne pas autoriser des sites non fiables à accéder aux ressources sensibles[2][5].
- **Éviter l'Usage de `null`** : Ne pas utiliser `Access-Control-Allow-Origin: null`, car cela peut être exploité par des requêtes internes ou sandboxées[5].
- **Mettre en Place un Preflight pour les Données Sensibles** : Forcer un preflight pour les requêtes sensibles pour limiter les risques de fuite d'informations[1].
