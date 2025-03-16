## Introduction aux cookies 🍪

- **Définition** : Cookies sont des informations stockées côté client pour maintenir un état entre le client et le serveur 📊.
- **Risques** : Cibles des attaquants pour modifier ou récupérer des informations sensibles 🚫.

## Sécurité des cookies 🔒

- **Attributs de sécurité** :
  - **HttpOnly** : Empêche l'accès JavaScript aux cookies 🚫.
  - **Secure** : Cookies envoyés uniquement via HTTPS 🔒.
  - **SameSite** : Protège contre les attaques CSRF en contrôlant l'envoi des cookies en cross-site 🚫.
- **Recommandations** : Utiliser ces attributs pour protéger les cookies sensibles 📝.

## Directives CSP pour la sécurité 📈

- **Types de directives** :
  - **script-src, style-src, img-src, etc.** : Contrôlent les origines des ressources 📊.
  - **child-src et frame-ancestors** : Gèrent les frames et workers 👪.
  - **form-action et connect-src** : Origines pour les formulaires et connexions asynchrones 📨.
  - **default-src** : Comportement par défaut pour les ressources non spécifiées 🔒.
- **Mots-clés** :
  - **'self'** : Origine actuelle 📈.
  - **'unsafe-inline' et 'unsafe-eval'** : À éviter pour réduire les risques XSS 🚫.
  - **Hash et nonce** : Autorisations spécifiques pour les contenus inline de confiance 🔒.

## Recommandations pour CSP 📝

- **Définir `default-src`** pour un comportement par défaut sécurisé 🔒.
- **Éviter les contenus inline** pour réduire la surface d'attaque 🚫.
- **Utiliser des empreintes ou nonces** pour autoriser des contenus inline de confiance 🔒.
- **Mettre en œuvre une stratégie de reporting** pour détecter les violations CSP 📊.

## Protection contre le clickjacking 🚫

- **Directive `frame-ancestors`** : Contrôle l'inclusion du site dans des frames 👪.
- **En-tête `X-Frame-Options`** : Obsolète, mais peut être utilisé pour la compatibilité 📈.

## Collecte des rapports CSP 📊

- **Directive `report-uri`** : Définit une URL pour collecter les rapports de violations CSP 📨.
- **Précautions** : Étudier les risques liés à la collecte de rapports, notamment en termes de sécurité et de confidentialité 🔒.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/bcde2a18-8996-458e-969b-a637b107d4b9/paste.txt
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/f0408111-a0e9-4a8e-bb24-fe83d01a258d/paste-2.txt
[3] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/ac2ba864-f1ee-4d1a-b626-eea401eb887d/paste-3.txt

---
