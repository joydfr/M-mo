## Introduction aux Termes Techniques et Recommandations

### 1. **FIDO U2F et FIDO 2** 📈

- **Définition** : FIDO U2F (Universal 2nd Factor) et FIDO 2 sont des normes d'authentification multifacteur développées par la FIDO Alliance. Elles visent à simplifier l'utilisation de l'authentification multifacteur en utilisant des clés physiques ou des applications pour sécuriser les accès.
- **Fonctionnement** : Ces normes utilisent des clés sécurisées pour générer des signatures uniques à chaque connexion, rendant difficile l'usurpation d'identité 😊.

### 2. **OTP (One-Time Password)** 📝

- **Définition** : Un mot de passe à usage unique, utilisé une seule fois pour une authentification.
- **Types** :
  - **HOTP (HMAC-based OTP)** : Utilise un algorithme basé sur le code d'authentification de message (HMAC) pour générer des mots de passe à usage unique 🤔.
  - **TOTP (Time-based OTP)** : Utilise la synchronisation de l'heure pour générer des mots de passe à usage unique ⏰.
  - **OCRA (OATH Challenge-Response Algorithm)** : Utilise un défi pour générer une réponse unique à chaque authentification 📊.

### 3. **Kerberos** 🐒

- **Définition** : Protocole d'authentification qui utilise des tickets pour vérifier l'identité des utilisateurs.
- **Fonctionnement** : Un utilisateur se connecte avec son nom d'utilisateur et mot de passe, puis reçoit un ticket d'authentification qui lui permet d'accéder à des ressources sans avoir à ressaisir ses informations 📝.

### 4. **PAKE (Password-Authenticated Key Agreement)** 🔑

- **Définition** : Protocole qui permet à deux parties de s'authentifier mutuellement et d'établir une clé secrète partagée sans révéler le mot de passe.
- **Exemples** :
  - **SPAKE2 (Secure Password-Authenticated Key Exchange)** : Une version sécurisée de l'échange de clés authentifié par mot de passe 🚀.
  - **OPAQUE** : Un protocole qui permet une authentification sécurisée tout en protégeant le mot de passe même en cas de compromission du serveur 🛡️.

### Recommandations de l'ANSSI

#### Objectifs du Guide 📚

- **Authentification** : Vérifier l'identité des utilisateurs pour garantir la sécurité des systèmes d'information.
- **Public visé** : Développeurs, administrateurs, RSSI, DSI, utilisateurs 👥.

#### Principales Recommandations

1. **Analyse de Risque** : Effectuer une analyse de risque avant de mettre en place des moyens d'authentification 📊.
2. **Authentification Multifacteur** : Privilégier l'authentification multifacteur 🚫.
3. **Facteur de Possession** : Utiliser un facteur de possession pour renforcer la sécurité 🔒.
4. **Robustesse des Mots de Passe** : Adapter la robustesse des mots de passe au contexte 🔑.
5. **Coffre-fort de Mots de Passe** : Utiliser un coffre-fort pour stocker les mots de passe 🗝️.

#### Types de Facteurs d'Authentification

- **Facteur de Connaissance** : Ce que je sais (ex : mot de passe) 🤔.
- **Facteur de Possession** : Ce que je possède (ex : carte à puce) 📈.
- **Facteur Inhérent** : Ce que je suis (ex : empreinte digitale) 👍.

#### Recommandations pour les Mots de Passe

- **Longueur** : Privilégier des mots de passe longs 📏.
- **Complexité** : Utiliser des règles de complexité adaptées 🔒.
- **Expiration** : Définir un délai d'expiration raisonnable ⏰.
- **Stockage** : Stocker les mots de passe de manière sécurisée 🗝️.
