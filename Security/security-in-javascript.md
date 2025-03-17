## Mémo Sécurité JavaScript

### 1. **Utilisation du Mode Strict** 🚀

- **Principe** : Le mode strict (`"use strict";`) désactive certains comportements trop souples de JavaScript, comme l'assignation de variables non déclarées, et oblige à plus de rigueur dans la syntaxe et le typage.
- **Avantages** : Interrompt le fil d'exécution en cas d'erreurs, désactive les fonctionnalités obsolètes, et peut aider à prévenir certaines vulnérabilités XSS.
- **Inconvénients** :
  - **Compatibilité** : Peut ne pas être compatible avec tout le code JavaScript, surtout celui qui utilise des fonctionnalités obsolètes.
  - **Code plus Verbeux** : Exige une déclaration explicite de toutes les variables, ce qui peut rendre le code plus long et difficile à lire.
- **Prévention des Vulnérabilités** :
  - **Utiliser des Outils de Détection d'Erreurs** : Utiliser des linters pour détecter les erreurs de syntaxe et de compatibilité avant de déployer le code en production.
  - **Test Unitaires** : Effectuer des tests unitaires pour s'assurer que le code fonctionne correctement en mode strict.

#### Exemple de Code

```javascript
// Déclaration au niveau d'un fichier
"use strict";
function chuck(params) {
  // Code ici
}

// Déclaration au niveau d'une fonction
function strictFunc(params) {
  "use strict";
  // Code ici
}
```

### 2. **Utilisation de Tags sur les Template Strings** 📝

- **Principe** : Les Template Strings permettent d'intégrer des expressions dans des chaînes de caractères. Un tag peut être utilisé pour spécifier un comportement lors de l'interprétation.
- **Avantage** : Permet de se protéger contre les vulnérabilités XSS en échappant les caractères spéciaux dans les expressions intégrées.
- **Inconvénients** :
  - **Complexité** : Nécessite une compréhension approfondie des Template Strings et des tags associés.
  - **Maintenance** : Les tags personnalisés doivent être maintenus et mis à jour régulièrement pour rester sécurisés.
- **Prévention des Vulnérabilités** :
  - **Utiliser des Fonctions d'Échappement** : Toujours utiliser des fonctions d'échappement pour les données injectées dans les Template Strings.
  - **Valider les Entrées** : Valider toutes les entrées utilisateur avant de les intégrer dans les templates.

#### Exemple de Code

```javascript
function safeTag(strings, ...values) {
  var out = "";
  for (i in strings) {
    out += strings[i];
    if (values[i]) {
      out += values[i].replace(//g, "&gt;")
                     .replace(/&/g, "&amp;");
    }
  }
  return out;
}

const badVar1 = ' bad';
const myStringTemplate = safeTag`
  Bonjour ${badVar1} !
  Le multiligne est très pratique.
`;
document.body.innerHTML = myStringTemplate;
```

### 3. **Cloisonnement avec les Web Workers** 🚫

- **Principe** : Les Web Workers permettent d'exécuter du code JavaScript en arrière-plan, dans un contexte différent de la page principale, sans accès au DOM.
- **Avantages** : Isolation des traitements sensibles ou non maîtrisés, réduction de la surface d'attaque, et évitement des blocages du fil d'exécution principal.
- **Inconvénients** :
  - **Complexité de Communication** : La communication entre le worker et la page principale peut être complexe à mettre en place.
  - **Limitations de Sécurité** : Les Web Workers ne peuvent pas utiliser SRI pour les ressources chargées via `importScripts`.
- **Prévention des Vulnérabilités** :
  - **Utiliser des Protocoles de Communication Sécurisés** : Utiliser des protocoles sécurisés pour la communication entre le worker et la page principale.
  - **Isoler les Workers Non Fiables** : Utiliser des URLs de type `data:` pour isoler les workers non fiables de l'Origin principale.

#### Exemple de Code

```javascript
var worker = null;
function start() {
  worker = new Worker("worker.js");
  worker.addEventListener("message", (event) => {
    var data = JSON.parse(event.data);
    document.body.style.background = data.color;
    document.getElementById("color").textContent = data.color;
  });
}
```

### 4. **Cloisonnement avec les Iframes** 📺

- **Principe** : Les iframes permettent d'inclure du contenu HTML dans une page, avec un contexte de navigation indépendant.
- **Avantages** : Permettent de présenter des contenus externes tout en contrôlant les interactions avec la page principale.
- **Inconvénients** :
  - **Surface d'Attaque Élargie** : Les iframes peuvent augmenter la surface d'attaque si elles chargent des contenus non fiables.
  - **Complexité de Configuration** : La configuration de l'attribut `sandbox` peut être complexe.
- **Prévention des Vulnérabilités** :
  - **Utiliser l'Attribut Sandbox** : Configurer l'attribut `sandbox` pour limiter les fonctionnalités de l'iframe.
  - **Définir une CSP** : Utiliser une Content Security Policy pour contrôler les origines autorisées à ouvrir des iframes.

#### Exemple de Code

```html

```

### 5. **Risques et Prévention** 🚨

- **Risque XSS** : Utiliser le mode strict et des tags pour les Template Strings pour réduire les risques XSS.
- **Risque CSRF** : Utiliser des tokens anti-CSRF pour protéger contre les attaques CSRF.
- **Risque de Fuite de Données** : Isoler les traitements sensibles dans des Web Workers ou iframes pour limiter l'accès aux données sensibles.
- **Risque d'Inclusion de Code Non Maîtrisé** : Utiliser des Web Workers ou iframes pour isoler les bibliothèques externes et limiter leur accès au DOM.

### 6. **Maîtrise des Composants** 📈

- **Limiter les Composants Tiers** : Utiliser uniquement les composants nécessaires pour réduire la surface d'attaque.
- **Maintenir à Jour les Composants** : Assurer que tous les composants tiers soient à jour pour éviter les vulnérabilités connues.
- **Éviter les Modifications du Cœur** : Ne pas modifier le cœur des composants tiers pour faciliter leur mise à jour.
