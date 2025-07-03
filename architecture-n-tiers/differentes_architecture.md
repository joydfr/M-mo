# 🧠 Mémo : Les Différents Types d'Architectures Logicielles

Ce mémo t’aide à bien différencier les types d’architectures les plus utilisés dans le développement logiciel.

---

## 1️⃣ Architecture Monolithique 🧱

### 🔍 Description :

Toute l’application est développée dans **un seul bloc déployable** (ex : une seule application `.exe`, `.dll`, `.jar`, etc.).

### 📦 Caractéristiques :

- Toutes les couches (UI, logique métier, accès aux données) sont intégrées dans le **même projet**.
- Une seule base de code, un seul déploiement.

### ✅ Avantages :

- ✅ Facile à développer et déployer au début
- ✅ Bon pour les petites équipes ou MVP

### ❌ Inconvénients :

- ❌ Difficulté à maintenir à grande échelle
- ❌ Un bug peut impacter toute l’app
- ❌ Difficulté de scalabilité partielle

### 📌 Exemple :

Une application ASP.NET MVC classique avec contrôleurs, services, EF Core dans le même projet.

---

## 2️⃣ Architecture N-Tiers 🏗️

### 🔍 Description :

Séparation logique en **couches distinctes** (tiers), chacune avec une **responsabilité spécifique**.

### 📚 Tiers classiques :

- 🎨 **Présentation (UI)** : Interface utilisateur
- 🧠 **Métier (BLL)** : Logique métier
- 🗃️ **Données (DAL)** : Accès aux bases de données

### ✅ Avantages :

- ✅ Bonne séparation des responsabilités
- ✅ Facilite les tests unitaires
- ✅ Scalable verticalement

### ❌ Inconvénients :

- ❌ Communication rigide entre les couches
- ❌ Risque de sur-ingénierie sur de petits projets

### 📌 Exemple :

Projet avec 3 bibliothèques C# : `MonApp.UI`, `MonApp.Business`, `MonApp.Data`.

---

## 3️⃣ Architecture Hexagonale (Ports & Adapters) 🛡️

### 🔍 Description :

Aussi appelée **Architecture "Clean"** ou **"Ports & Adapters"**, elle place la logique métier au **centre**, isolée de la technique.

### 🌀 Structure :

- Noyau métier (core) ne connaît rien de l’extérieur
- Interfaces (ports) vers les **adaptateurs** (DB, UI, API...)

### ✅ Avantages :

- ✅ Testabilité très forte
- ✅ Forte indépendance de la technique (ex : facile de changer de BDD ou UI)
- ✅ Respect du principe **DIP** (Dependency Inversion)

### ❌ Inconvénients :

- ❌ Complexe à mettre en place
- ❌ Peut sembler "trop abstraite" au début

### 📌 Exemple :

- `Domain` (noyau)
- `Application`
- `Infrastructure` (EF Core, API REST, etc.)
- `Presentation`

---

## 4️⃣ Architecture Microservices 🔗

### 🔍 Description :

L’application est **découpée en services indépendants**, chacun gérant un **domaine métier unique**, avec sa **propre base de données**.

### 🚀 Caractéristiques :

- Communication via HTTP/REST, gRPC, Messaging (Kafka, RabbitMQ...)
- Chaque microservice peut être développé, déployé, mis à jour indépendamment

### ✅ Avantages :

- ✅ Haute scalabilité horizontale
- ✅ Tolérance aux pannes
- ✅ Déploiement indépendant par domaine

### ❌ Inconvénients :

- ❌ Complexité technique importante
- ❌ Besoin d'une infrastructure robuste (CI/CD, observabilité, sécurité...)
- ❌ Latence réseau et gestion des transactions distribuées

### 📌 Exemple :

Une app e-commerce avec :

- `Service.Commande`
- `Service.Produit`
- `Service.Paiement`
- Chaque service a sa BDD et son API

---

## 5️⃣ Architecture Orientée Services (SOA) 🧩

### 🔍 Description :

Comme les microservices, mais plus **centralisée**, souvent avec un **Enterprise Service Bus (ESB)**.

### 🎯 Objectif :

Réutiliser des services à travers l’entreprise via un **bus de communication commun**.

### ✅ Avantages :

- ✅ Réutilisabilité des services
- ✅ Bonne pour les entreprises avec de nombreux systèmes

### ❌ Inconvénients :

- ❌ Couplage fort à l’ESB
- ❌ Risque de "goulot d'étranglement"

### 📌 Exemple :

Banque avec services `Client`, `Transaction`, `Crédit`, tous interconnectés via un bus ESB.

---

## 📊 Tableau Comparatif

| Architecture  | 🔧 Complexité  | ⚙️ Scalabilité | 🔬 Testabilité | 🧪 Couplage    | 🧱 Usage Idéal                       |
| ------------- | -------------- | -------------- | -------------- | -------------- | ------------------------------------ |
| Monolithique  | 🔹 Faible      | ⚠️ Faible      | ⚠️ Faible      | 🔗 Fort        | MVP, projets simples ou internes     |
| N-Tiers       | ⚖️ Moyenne     | ✅ Bonne       | ✅ Moyenne     | 🔗 Moyen       | Projets structurés à long terme      |
| Hexagonale    | ⚙️ Élevée      | ✅ Bonne       | ✅ Excellente  | 🔓 Faible      | Projets critiques, testabilité forte |
| Microservices | 🚀 Très élevée | ✅ Excellente  | ✅ Bonne       | 🔓 Très faible | Grands systèmes distribués           |
| SOA           | ⚙️ Élevée      | ✅ Bonne       | ⚠️ Moyenne     | 🔗 Fort        | Grandes entreprises, intégration SI  |

---

## 🎯 À retenir

- **Choisir l'architecture en fonction du contexte** : taille de l'équipe, budget, exigences métier, scalabilité, etc.
- **Tu peux combiner plusieurs architectures** : par exemple, architecture en couches dans chaque microservice.
- **Mieux vaut une architecture simple bien maîtrisée qu’une architecture complexe mal implémentée.**

---
