Voici un mémo visuel pour la mise en œuvre de Referrer-Policy :

## Introduction à Referrer-Policy 🚀

- **Définition** : Stratégie pour contrôler l'en-tête Referer, qui indique l'URL de la page précédente lors d'une requête 📊.
- **Importance** : Protège la confidentialité en limitant les informations transmises via l'en-tête Referer 🔒.

## Risques liés à l'en-tête Referer 🚫

- **Fuite d'informations** : L'URL complète peut être transmise, incluant des données sensibles comme des paramètres de requête 📝.
- **Problèmes de confidentialité** : Particulièrement préoccupant pour les Capability URLs ou les informations personnelles 🚫.

## Stratégies de Referrer-Policy 📈

- **Options** :
  - **no-referrer** : Aucune information n'est transmise.
  - **no-referrer-when-downgrade** : Comportement par défaut, l'URL complète est utilisée sauf lors du passage de HTTPS à HTTP.
  - **origin** : Seule l'Origin est transmise.
  - **same-origin** : Aucune information n'est transmise sauf pour les accès au même site.
  - **strict-origin** : L'Origin est utilisée uniquement vers des destinations sécurisées.
  - **origin-when-cross-origin** : L'URL complète pour le site courant, l'Origin pour les autres.
  - **strict-origin-when-cross-origin** : Comme précédent, mais avec vérification de sécurité.
  - **unsafe-url** : URL complète toujours transmise, y compris de HTTPS à HTTP (à éviter) 🚫.

## Mise en œuvre de Referrer-Policy 🛠️

1. **En-tête HTTP** : Définition via l'en-tête Referrer-Policy pour une stratégie globale 💻.
2. **Balise ``** : Utilisation de la balise HTML pour une stratégie par page 📝.
3. **Attribut `referrerpolicy`** : Modification ponctuelle sur des éléments spécifiques (, , etc.) pour des stratégies personnalisées 📈.

## Recommandations 📝

- **Utiliser HTTPS** pour éviter la transmission d'informations sensibles 🔒.
- **Éviter `unsafe-url`** pour protéger la confidentialité 🚫.
- **Définir une stratégie** via l'en-tête HTTP ou la balise `` pour contrôler l'en-tête Referer 💻.
- **Utiliser l'attribut `referrerpolicy`** pour des ajustements ponctuels sur des éléments spécifiques 📈.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/bcde2a18-8996-458e-969b-a637b107d4b9/paste.txt
[2] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/58399061/f0408111-a0e9-4a8e-bb24-fe83d01a258d/paste-2.txt

---

Answer from Perplexity: https://www.perplexity.ai/search/bonsoir-perplexity-je-dois-rea-YLoPy0VYSVKq8ycgEBEJaQ?login-source=sharedThreadLoginGate&login-new=false&utm_source=copy_output
