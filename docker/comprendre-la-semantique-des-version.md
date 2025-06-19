# 🧠 Mémo – Gestion sémantique des versions (SemVer)

## 📌 Définition

La gestion sémantique des versions suit la convention suivante :

```
MAJOR.MINOR.PATCH
```

Exemple : `2.4.1`

| Partie | Signification                                                           |
| ------ | ----------------------------------------------------------------------- |
| MAJOR  | Rupture de compatibilité (breaking change)                              |
| MINOR  | Nouvelles fonctionnalités, mais compatibles avec les anciennes versions |
| PATCH  | Corrections de bugs, aucune nouvelle fonctionnalité                     |

---

## 🔁 Exemples d’évolution

| Avant | Changement                             | Après | Pourquoi ? |
| ----- | -------------------------------------- | ----- | ---------- |
| 1.0.0 | Correction d’un bug                    | 1.0.1 | PATCH      |
| 1.0.1 | Ajout d’une nouvelle API compatible    | 1.1.0 | MINOR      |
| 1.1.0 | Modification d’une méthode (signature) | 2.0.0 | MAJOR      |

---

## 🐳 Avec Docker

Tu peux taguer tes images comme suit :

```sh
docker build -t monapp:1.2.3 .
docker build -t monapp:latest .
```

**Bonnes pratiques Docker :**

- Toujours versionner (`monapp:1.2.3`)
- Ne pas uniquement utiliser `latest` (trop vague)
- Possibilité de multitaguer :

```sh
docker build -t monapp:1.2.3 -t monapp:1.2 -t monapp:1 -t monapp:latest .
```

---

## 📦 Avec .NET et C#

Dans un `.csproj` :

```xml
<PropertyGroup>
    <Version>2.1.0</Version>
    <AssemblyVersion>2.1.0</AssemblyVersion>
    <FileVersion>2.1.0</FileVersion>
</PropertyGroup>
```

Tu peux automatiser l’incrémentation avec un outil comme **GitVersion**, **Nerdbank.GitVersioning**, ou simplement via Git tags.

---

## ✅ Résumé

| Règle                       | Exemple                        |
| --------------------------- | ------------------------------ |
| PATCH = bugfix              | 1.0.1                          |
| MINOR = nouvelles features  | 1.1.0                          |
| MAJOR = rupture API         | 2.0.0                          |
| Toujours taguer dans Docker | monapp:1.2.3, pas juste latest |

---

## 🧩 Explication progressive de 1.2.3

### 🔢 Comment on passe à une version 1.2.3 ?

On découpe chaque chiffre :

```
1.2.3
│ │ └── PATCH : correction de bug (fix)
│ └──── MINOR : nouvelle fonctionnalité sans casser l’existant
└────── MAJOR : gros changement qui casse la compatibilité
```

---

### 🎯 Exemple concret

Imaginons que tu développes une application `monapp` :

| Version | Ce que tu fais                               | Pourquoi ce numéro |
| ------- | -------------------------------------------- | ------------------ |
| 1.0.0   | Première version stable                      | Point de départ    |
| 1.0.1   | Tu corriges un bug                           | ✅ PATCH           |
| 1.1.0   | Tu ajoutes une nouvelle commande CLI         | ✅ MINOR           |
| 1.1.1   | Tu corriges un bug dans la nouvelle commande | ✅ PATCH           |
| 2.0.0   | Tu supprimes une commande existante          | ❗ MAJOR : rupture |
| 2.1.0   | Tu ajoutes une fonctionnalité (ex. export)   | ✅ MINOR           |
| 2.1.1   | Tu corriges un bug dans l’export             | ✅ PATCH           |

Donc : **1.2.3** signifie :

- C’est la 1ère version stable (MAJOR = 1)
- Avec 2 ajouts de fonctionnalités mineures
- Et 3 corrections de bugs

---

### 📦 Pour tes projets C# ou Docker

Quand tu publies une nouvelle version :

- Si tu as corrigé un bug → tu augmentes **PATCH**
- Si tu as ajouté une nouvelle fonctionnalité sans casser l’existant → tu augmentes **MINOR**, tu remets PATCH à 0
- Si tu as cassé des anciennes fonctionnalités (ex : renommé une méthode publique) → tu augmentes **MAJOR**, tu remets MINOR et PATCH à 0

---

### ⚙️ Gestion manuelle

Avec Docker :

```sh
docker build -t monapp:1.2.3 .
```

Avec un `.csproj` :

```xml
<Version>1.2.3</Version>
```

---

### 🛠 Automatisation

Pour éviter de le faire à la main :

- Utilise les tags Git : `git tag v1.2.3`
- Ou des outils comme :
  - **GitVersion**
  - **Nerdbank.GitVersioning**
  - Ou un Makefile/script bash qui incrémente la version

---

## 🛠️ Script Bash pour automatiser le bump de version

Voici un exemple de script Bash simple pour incrémenter la version dans un fichier `VERSION` :

```bash
#!/bin/bash

# Usage: ./bump.sh [major|minor|patch]
set -e

PART=${1:-patch}

if [ ! -f VERSION ]; then
    echo "0.0.0" > VERSION
fi

VERSION=$(cat VERSION)
IFS='.' read -r MAJOR MINOR PATCH <<< "$VERSION"

case "$PART" in
    major)
        MAJOR=$((MAJOR + 1))
        MINOR=0
        PATCH=0
        ;;
    minor)
        MINOR=$((MINOR + 1))
        PATCH=0
        ;;
    patch)
        PATCH=$((PATCH + 1))
        ;;
    *)
        echo "Usage: $0 [major|minor|patch]"
        exit 1
        ;;
esac

NEW_VERSION="$MAJOR.$MINOR.$PATCH"
echo "$NEW_VERSION" > VERSION
echo "Version bumped to $NEW_VERSION"
```

**Utilisation :**

- `./bump.sh patch` → incrémente le patch (par défaut)
- `./bump.sh minor` → incrémente le minor
- `./bump.sh major` → incrémente le major

N’oublie pas d’ajouter, committer et taguer la nouvelle version dans Git !

---
