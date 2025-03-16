Bien sûr, voici le mémo mis à jour avec les nouvelles informations :

## Introduction à CSP 🚀

- **Définition** : CSP est un standard de sécurité web qui aide à protéger contre les attaques XSS (Cross-Site Scripting) en définissant une liste d'autorisations pour les ressources accessibles par un navigateur 📝.
- **Importance** : Complète les bonnes pratiques de développement, mais ne remplace pas la correction des vulnérabilités 🚫.

## Principe de CSP 📜

- **Liste d'autorisations** : Définit les ressources autorisées (scripts, styles, images) pour un site web, bloquant celles non déclarées 🚫.
- **Moindre privilège** : Restreint les contenus aux ressources fiables pour réduire les risques XSS 🔒.

## Mise en œuvre de CSP 🛠️

1. **En-tête HTTP** :

   - **Avantages** : Permet plus de stratégies (frame-ancestors, sandbox) et une URL de rapport des violations 📊.
   - **Méthodes** : Configuration du reverse-proxy, demande à l'hébergeur, ou via CMS/framework 📈.
   - **Exemple** : Utiliser un plugin comme gd-security-headers pour WordPress 📦.

2. **Balise ``** :
   - **Utilisation** : Si l'en-tête HTTP n'est pas possible, ou pour des cas spécifiques 📝.
   - **Limitation** : Ne s'applique pas aux contenus précédant la balise dans le DOM ⚠️.

## Directives CSP par type de ressource 📚

- **script-src, style-src, img-src, media-src, object-src, font-src** : Origines des JavaScript, CSS, images, audio, vidéo, PDF, et fontes 📊.
- **child-src et frame-ancestors** : Origines des workers et frames enfants et parents 👪.
- **form-action et connect-src** : Origines pour envoyer des formulaires et initier des connexions asynchrones 📨.
- **default-src** : Comportement par défaut pour les ressources sans directive spécifique 📝.
- **upgrade-insecure-requests, block-all-mixed-content, sandbox** : Directives globales pour sécuriser les ressources 🔒.

## Valeurs pour les directives CSP 📝

- **Origine** : Exemple : `https://domaine.fr` ou `*://*.domaine.fr:*` pour sous-domaines 🌐.
- **Mots-clés** : `none`, `self`, `unsafe-inline`, `unsafe-eval`, empreintes (SHA) ou nonces 🔑.
- **Exemple** : `script-src 'self' https://cdn.example.com; object-src 'none';`

## Recommandations 📝

- **Utiliser HTTPS** pour garantir l'intégrité des en-têtes et du corps de la réponse 🔒.
- **Privilégier l'en-tête HTTP** pour une mise en œuvre plus complète et sécurisée 💻.
- **Interdire les contenus inline** : Éviter `unsafe-inline` et `unsafe-eval` pour réduire les risques XSS 🚫.
- **Définir default-src** : Pour un comportement par défaut sécurisé, par exemple `default-src 'self';` 🔒.

## Protection contre le clickjacking 🚫

- **Directive frame-ancestors** : Spécifie les origines autorisées pour charger le site dans une frame 👪.
- **Exemple** : `frame-ancestors 'self';` pour autoriser uniquement l'origine actuelle 📈.

## Collecte des rapports de violation 📊

- **Directive report-uri** : Définit une URL pour collecter les rapports de violations CSP 📨.
- **Exemple** : `report-uri https://csp-report.example.com;` pour envoyer des rapports 📝.
- **Précautions** : Étudier les risques liés à la collecte de rapports, notamment en termes de sécurité et de confidentialité 🔒.

## Stratégies Complémentaires 📈

- **Multiples CSP** : Peuvent être appliquées pour renforcer la stratégie globale 🔒.
- **Ordre d'application** : Les directives les plus strictes sont prises en compte en cas de conflit 📊.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/bcde2a18-8996-458e-969b-a637b107d4b9/paste.txt
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/f0408111-a0e9-4a8e-bb24-fe83d01a258d/paste-2.txt

---

Answer from Perplexity: https://www.perplexity.ai/search/bonsoir-perplexity-je-dois-rea-YLoPy0VYSVKq8ycgEBEJaQ?login-source=sharedThreadLoginGate&login-new=false&utm_source=copy_output
