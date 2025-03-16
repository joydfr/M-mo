Voici un mémo visuel pour la maîtrise des requêtes silencieuses :

## Introduction aux requêtes silencieuses 🚨

- **Définition** : Requêtes initiées par le navigateur sans exécution de JavaScript ou CSS, potentiellement indésirables et risquées 📊.
- **Exemples** : Attribut `ping` dans les balises ``, Resource Hints (`dns-prefetch`, `preconnect`, `prefetch`, `prerender`) 📈.

## Risques associés aux requêtes silencieuses 🚫

- **Fuite d'informations** : Risque d'exploitation de vulnérabilités CSRF ou DDoS 🌪️.
- **Attaques CSRF** : Utilisation de l'attribut `ping` pour envoyer des requêtes sans consentement 🚫.
- **DDoS** : Multiplication des requêtes pour surcharger une cible 🌪️.

## Utilisation de CSP pour limiter les requêtes silencieuses 🔒

- **Directive `connect-src`** : Restreint les origines pour les requêtes silencieuses (ex. `ping`) 📊.
- **Directive `prefetch-src`** : Contrôle les Resource Hints pour éviter des connexions indésirables 📈.
- **Directive `default-src`** : Comportement par défaut pour les ressources non spécifiées, utile pour bloquer les requêtes non autorisées 🔒.

## Exemples de CSP pour limiter les requêtes silencieuses 📝

- **Exemple 1** : `Content-Security-Policy: default-src 'self'; connect-src 'self';`
- **Exemple 2** : `Content-Security-Policy: default-src 'self'; prefetch-src 'self';`

## Recommandations 📝

- **Utiliser CSP par en-tête HTTP** pour une mise en œuvre plus complète et sécurisée 💻.
- **Définir des directives spécifiques** pour limiter les requêtes silencieuses 📊.
- **Étudier les risques liés à chaque fonctionnalité HTML** pour adapter la stratégie CSP 📈.

## Compléments de sécurité 🚀

- **Permissions Policy** : Spécification en cours pour contrôler les permissions des APIs du navigateur, similaire aux permissions des applications mobiles 📱.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/bcde2a18-8996-458e-969b-a637b107d4b9/paste.txt
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/f0408111-a0e9-4a8e-bb24-fe83d01a258d/paste-2.txt

---
