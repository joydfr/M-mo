🛡️ Mémo Sécurité – Menaces sur les Sites et Applications Web
🚨 Menaces principales
Compromission des ressources


Violation de l’intégrité du contenu (défiguration du site).
Objectifs : relayer un message, nuire à l’image du site, démontrer une compétence.
Variante : attaque par point d’eau (piège tendu aux visiteurs).
Vol de données


Atteinte à la confidentialité (authentifiants, infos personnelles, bancaires…).
But lucratif : usurpation d’identité, paiements frauduleux.
Déni de service (DoS/DDoS)


Saturation du site pour le rendre indisponible ou le ralentir.
Impact : déficit d’image et pertes financières.
🎭 Attaques avancées
Attaque par rebond : utiliser un site comme porte d’entrée pour attaquer un autre système ou hébergeur.
Point d’eau (watering hole) : infection discrète des visiteurs habituels (employés, partenaires…) via un site compromis.
📌 Conséquences : Atteinte à la réputation, pertes économiques, risque juridique.
 ✅ Prévention : Sécurisation des accès, mises à jour régulières, surveillance active.

🎨 Mémo Sécurité – Défiguration de Site Web
❌ Qu'est-ce que la défiguration ?
La défiguration (defacement) est une attaque où un pirate modifie l’apparence d’un site web en remplaçant son contenu légitime par un message de son choix.
🎯 Objectifs des attaquants
Propagande : afficher un message politique ou idéologique.
Dénigrement : nuire à l’image du propriétaire du site.
Marquer son exploit : revendication d’une attaque pour démontrer un savoir-faire.
⚠️ Pourquoi c'est un problème ?
Perte de crédibilité et atteinte à la réputation.
Perte de confiance des utilisateurs et clients.
Potentiellement une première étape avant une attaque plus grave (ex. : vol de données).
🛡️ Comment s’en protéger ?
✅ Sécuriser les accès administratifs (mots de passe forts, authentification 2FA).
 ✅ Mettre à jour régulièrement les CMS, plugins et frameworks.
 ✅ Limiter les permissions des utilisateurs et des fichiers critiques.
 ✅ Surveiller les journaux d’accès pour détecter des connexions suspectes.
 ✅ Mettre en place un WAF (Web Application Firewall) pour filtrer les attaques.
🛡️ Mémo Sécurité – Attaque XSS (Cross-Site Scripting)
❌ Qu'est-ce qu'une attaque XSS ?
Une attaque Cross-Site Scripting (XSS) consiste à injecter du code malveillant (ex. : JavaScript, HTML) dans une page web. Ce code est ensuite exécuté par le navigateur des utilisateurs visitant la page compromise.
🎯 Objectifs des attaquants
Voler des informations sensibles : sessions, mots de passe, informations bancaires...
Prendre le contrôle d’un compte utilisateur via un vol de cookies ou de sessions.
Effectuer des actions à l'insu de la victime (ex. : modification de données).
Rediriger vers des sites malveillants ou afficher du contenu frauduleux.
🔍 Les types de XSS
XSS stocké : le code malveillant est sauvegardé sur le serveur (ex. : base de données) et exécuté à chaque visite de la page infectée.
XSS réfléchi : le script est injecté dans un lien piégé et exécuté par le navigateur lorsque la victime le visite.
XSS basé sur le DOM : la modification du code se fait directement via le JavaScript du site (ex. : manipulation du document.location).
⚠️ Pourquoi c’est dangereux ?
Affecte directement les utilisateurs (vol de données, usurpation d'identité…).
Peut servir de tremplin pour des attaques plus graves (CSRF, SQLi…).
Peut compromettre la réputation d’un site et la confiance des utilisateurs.
🛡️ Comment s’en protéger ?
✅ Échapper les entrées utilisateur (htmlspecialchars(), escape(), sanitize()).
 ✅ Mettre en place une politique de sécurité stricte (CSP - Content Security Policy).
 ✅ Limiter l'exécution de scripts non autorisés.
 ✅ Vérifier et filtrer les entrées/sorties côté serveur et client.
 ✅ Utiliser des bibliothèques de sécurité éprouvées (ex. : OWASP ESAPI).
🛡️ Mémo Sécurité – Attaque CSRF (Cross-Site Request Forgery)
❌ Qu'est-ce qu'une attaque CSRF ?
Le Cross-Site Request Forgery (CSRF) est une attaque qui force un utilisateur authentifié à exécuter des actions non souhaitées sur un site web sans son consentement.
🎯 Objectifs des attaquants
Effectuer des actions à la place de la victime (ex. : transfert d’argent, changement de mot de passe…).
Exploiter la session active de l’utilisateur pour contourner l’authentification.
Propager des malwares ou des modifications non autorisées.
🔍 Comment ça fonctionne ?
La victime est connectée à un site légitime (banque, réseau social, messagerie…).
Elle visite un site malveillant ou clique sur un lien piégé.
Une requête est envoyée en arrière-plan vers le site légitime, utilisant la session active de la victime.
Le site légitime exécute l’action demandée sans que la victime ne s’en rende compte.
⚠️ Pourquoi c’est dangereux ?
Exploite la confiance du site légitime envers l’utilisateur.
Ne nécessite aucune interaction spécifique de la victime (juste une visite).
Peut conduire à la prise de contrôle complète d’un compte utilisateur.
🛡️ Comment s’en protéger ?
✅ Utiliser des jetons CSRF (anti-CSRF tokens) pour vérifier l’origine des requêtes.
 ✅ Appliquer la vérification du référent (Referer ou Origin headers).
 ✅ Exiger une authentification forte pour les actions sensibles (ex. : confirmation par mot de passe).
 ✅ Utiliser la directive SameSite pour les cookies afin de restreindre leur envoi aux sites autorisés.
 ✅ Limiter les requêtes aux méthodes sécurisées (ex. : POST plutôt que GET).
🛡️ Mémo Sécurité – Conception et Hébergement d’un Site Web Sécurisé
🚀 1. Sécurité dès la conception
Intégrer la sécurité dès le début du projet pour éviter des corrections coûteuses en fin de développement.
Analyser les risques et besoins en sécurité dès la phase de conception.
Appliquer les principes de sécurité fondamentaux :
 ✅ Moindre privilège (limiter les permissions).
 ✅ Défense en profondeur (multiplier les couches de protection).
 ✅ Maîtrise des dépendances (éviter les bibliothèques obsolètes ou non maintenues).
🖥️ 2. Intégrité du comportement côté client
Les données échangées avec le navigateur doivent être sécurisées.
Attention aux ressources externes utilisées (scripts, API, bibliothèques).
Mettre en place des protections comme :
 ✅ Content Security Policy (CSP) pour limiter l’exécution de scripts malveillants.
 ✅ Sous-ressources validées (Subresource Integrity - SRI) pour éviter les modifications de fichiers distants.
🏢 3. Sécurisation de l’infrastructure d’hébergement
Appliquer les bonnes pratiques de configuration :
 ✅ Sécuriser les échanges (HTTPS obligatoire, certificats SSL/TLS à jour).
 ✅ Durcir les configurations (désactiver les services inutiles, restreindre les accès).
 ✅ Mettre en place une supervision pour identifier les tentatives d’attaques.
🔍 4. Détection et réponse aux incidents
Détecter les vulnérabilités via des audits de sécurité et des tests réguliers.
Journaliser et analyser les événements suspects :
 ✅ Mise en place de logs de sécurité et d’une surveillance des activités.
 ✅ Alertes en cas de comportements anormaux (tentatives de connexion suspectes, injections…).
Vérifier la conformité aux référentiels et normes de sécurité.
🛡️ Mémo Sécurité – Défense en Profondeur
🔎 Qu'est-ce que la défense en profondeur ?
Le principe de défense en profondeur consiste à mettre en place plusieurs couches de sécurité indépendantes pour protéger un système contre les menaces.
🎯 Pourquoi est-ce important ?
Une seule barrière de sécurité peut être contournée en cas de vulnérabilité.
Une architecture cloisonnée et sécurisée limite les dégâts en cas de compromission.
Éviter une approche mono-protection (ex. : tout miser sur un pare-feu, sans sécuriser les applications elles-mêmes).
🏗️ Comment l’appliquer ?
✅ Sécuriser chaque couche du système (serveur, application, base de données, utilisateurs...).
 ✅ Utiliser des contrôles de sécurité à plusieurs niveaux :
Authentification forte (MFA, tokens…).
Filtrage réseau (pare-feu, segmentation, VPN…).
Chiffrement des communications et des données sensibles.
Contrôle des accès et gestion des privilèges minimaux.
Monitoring et détection d’intrusions (SIEM, logs, alertes…).
 ✅ Isoler les composants critiques : chaque brique du système doit avoir ses propres protections.
🚀 Exemple d’application en sécurité web
✔️ Ne pas se fier uniquement au pare-feu pour bloquer les attaques.
 ✔️ Protéger l’application avec une validation stricte des entrées utilisateur (contre XSS, SQLi…).
 ✔️ Chiffrer les données en base pour éviter les fuites en cas de compromission.
 ✔️ Mettre en place des journaux d’activité pour détecter les comportements suspects.

🔐 Mémo Sécurité – Réduction de la Surface d’Attaque
🔎 Définition
La réduction de la surface d’attaque consiste à minimiser l’exposition d’un système en limitant les services, accès et composants au strict nécessaire. Moins il y a de points d’entrée accessibles, plus il est difficile pour un attaquant d’exploiter une vulnérabilité.
🎯 Pourquoi est-ce important ?
✔️ Réduction des risques d’attaques en limitant les portes d’entrée pour les attaquants.
 ✔️ Moins de vulnérabilités possibles grâce à une exposition minimale des services et applications.
 ✔️ Meilleure gestion de la sécurité en simplifiant l’administration et la surveillance.
🚀 Comment réduire la surface d’attaque ?
✔️ Au niveau du réseau
Restreindre l’accès aux ports ouverts (ex. : fermer les ports inutiles).
Mettre en place des pare-feu et limiter les connexions entrantes/sortantes aux stricts besoins.
✔️ Au niveau du système
Supprimer les logiciels, services et composants non utilisés (ex. : désinstaller les paquets inutiles).
Désactiver les protocoles et fonctionnalités non essentiels (ex. : désactiver Telnet si non utilisé).
Utiliser des systèmes d’exploitation et logiciels à jour, sans composants obsolètes.
✔️ Au niveau de l’application
Supprimer les modules et fonctionnalités inutilisés (ex. : désactiver WebDAV si non utilisé).
Restreindre les API aux seules actions strictement nécessaires.
Appliquer le principe du moindre privilège aux utilisateurs et services.
🔐 Sécurisation des échanges de données
🔎 Définition
La sécurisation des échanges de données vise à garantir que les informations envoyées et reçues sur un site ou une application web ne puissent pas être interceptées, modifiées ou usurpées par un attaquant.
🎯 Pourquoi est-ce important ?
✔ Confidentialité : Protection des données sensibles (mots de passe, données bancaires, informations personnelles) contre les interceptions.
 ✔ Intégrité : Empêcher la modification des données en transit par des attaquants.
 ✔ Authenticité : Vérification que les données proviennent bien de la source prévue et ne sont pas altérées.
 ✔ Conformité légale : Respect du RGPD et des régulations sur la protection des données.
🛡️ Moyens de protection
✔ Utilisation du protocole HTTPS avec un certificat TLS valide pour chiffrer les échanges.
 ✔ HSTS (HTTP Strict Transport Security) : Obligation d’utiliser uniquement HTTPS pour éviter toute attaque de type downgrade.
 ✔ Validation des données reçues : éviter l’injection de contenu malveillant.
 ✔ Utilisation de headers HTTP de sécurité (ex. : Content Security Policy, X-Frame-Options).
📌 À retenir : Sans chiffrement et validation, les données sont vulnérables aux interceptions, aux modifications et aux attaques de type "Man-in-the-Middle" (MITM). Le chiffrement avec TLS et l’application de politiques de sécurité web sont essentiels pour garantir la confidentialité et l’intégrité des échanges.
🛠️ Bonnes Pratiques de Conception et de Sécurité
✅ Actions à mener pour sécuriser une application web
🔹 Mesures manuelles
Analyser les risques dès la conception.
Appliquer des principes de sécurité dès le début (ex. : moindre privilège, défense en profondeur).
S’assurer de l’utilisation de dépendances sécurisées et maintenues.
Vérifier les configurations des infrastructures et serveurs d’hébergement (durcissement, gestion des accès).
🔹 Mesures automatisées
Intégrer des outils d’analyse de code source pour détecter les vulnérabilités et mauvaises pratiques.
Automatiser l’analyse des dépendances logicielles pour identifier les composants obsolètes ou vulnérables.
Mettre en place des mécanismes de détection d’anomalies et de journalisation des activités suspectes.
🔹 Stratégie d’audit et bug bounty
Définir un plan d’audit de sécurité pour chaque phase du projet.
Faire appel à des auditeurs externes PASSI pour évaluer la conformité aux standards de sécurité.
Mettre en place un Bug Bounty, qui permet à des hackers éthiques de signaler des vulnérabilités et de renforcer la sécurité de l’application de manière continue.
🛡️ À retenir : La sécurité ne s’improvise pas, elle doit être intégrée dès la conception et maintenue tout au long de la vie de l’application à l’aide d’audits réguliers et de tests de sécurité (analyse de code, bug bounty, détection d’attaques).
📜 Mémo : L'importance de la Journalisation en Sécurité Web
🔍 Pourquoi la journalisation est essentielle ?
La journalisation est un élément clé de la sécurité des systèmes d’information. Elle permet :
 ✅ Détection d’incidents de sécurité : Identification rapide des comportements suspects.
 ✅ Analyse des événements : Compréhension des actions et des accès effectués sur le système.
 ✅ Audit et conformité : Respect des réglementations de sécurité (ex. : RGPD).
🛡️ Bonnes Pratiques de Journalisation
📌 En phase de conception
Déterminer quels événements doivent être enregistrés (authentifications, changements de privilèges, accès aux ressources sensibles, etc.).
Configurer la synchronisation des horloges entre tous les composants pour une traçabilité cohérente.
📌 En phase d’exploitation
Assurer un stockage sécurisé des journaux pour éviter leur falsification ou destruction.
Appliquer des règles de conservation et d’archivage adaptées aux obligations légales et à la criticité des données.
Mettre en place des outils d’analyse et d’alertes pour identifier les comportements suspects (SIEM, SOC).
Éviter l’inclusion de données sensibles dans les logs pour limiter les risques d’exfiltration d’informations confidentielles.
Prévoir un mécanisme de protection contre la saturation des fichiers journaux pour prévenir les attaques par déni de service.
🛠️ Outils recommandés : SIEM (Splunk, ELK Stack), alertes de logs (Fail2ban, OSSEC, Wazuh), surveillance de la synchronisation temporelle (NTP).
🔔 Pourquoi c’est important ?
 L’application web est souvent exposée à des menaces constantes. Un bon système de journalisation bien sécurisé permet de réagir rapidement aux incidents, de comprendre les attaques et de respecter les obligations réglementaires en matière de sécurité des données.
➡ En résumé : La journalisation ne doit pas être négligée, mais elle doit être sécurisée pour ne pas devenir une faille exploitée par les attaquants !

🔐 Mémo : Mise en place de HTTPS sur un site web
✅ Pourquoi utiliser HTTPS ?
La mise en place de HTTPS (HyperText Transfer Protocol Secure) est essentielle pour garantir la sécurité des données échangées entre un site web et ses utilisateurs. Elle permet de :
 ✔ Sécuriser les échanges : Protection contre l’écoute, l’interception et la modification des données en transit.
 ✔ Garantir l’authenticité du site : Vérification de l’identité du site web par un certificat SSL/TLS.
 ✔ Empêcher les attaques de type Man-in-the-Middle (MITM) : Bloque l’interception et la modification des communications.
 ✔ Prévenir les altérations de contenu : Empêche l’injection de publicités ou de codes malveillants par des tiers (ex. : hotspots Wi-Fi publics).
 ✔ Améliorer le référencement SEO et la confiance des utilisateurs : Les navigateurs comme Chrome affichent des mises en garde pour les sites sans HTTPS.
✅ Recommandations pour mettre en place HTTPS correctement :
🔹 Utilisation de TLS 1.2 ou TLS 1.3 : Les versions antérieures comme SSL et TLS 1.0/1.1 sont obsolètes et vulnérables.
 🔹 Utilisation d’un certificat SSL/TLS valide : Privilégier les certificats de Let’s Encrypt (gratuits) ou achetés auprès d’une autorité de certification (CA) reconnue.
 🔹 Activation du HSTS (HTTP Strict Transport Security) : Éviter le downgrade vers HTTP en forçant l’utilisation de HTTPS.
 🔹 Protection contre les attaques de type Man-in-the-Middle (MITM) : Empêcher l’interception et la modification des communications.
 🔹 Désactivation des protocoles obsolètes : Éviter l’utilisation des versions non sécurisées comme SSLv2, SSLv3, et TLS 1.0 / 1.1.
 🔹 Chiffrement fort : Utilisation de chiffrement AES-GCM et des suites de chiffrement modernes pour assurer une protection optimale des données.
 🔹 Configuration des certificats et sécurité renforcée :
 ✔ Activer HSTS (HTTP Strict Transport Security) pour forcer l’utilisation de HTTPS.
 ✔ Utiliser Certbot pour générer et renouveler automatiquement les certificats SSL gratuits.
 ✔ Éviter les certificats autofinancés et privilégier ceux émis par des autorités de certification reconnues.
 ✔ Configurer les en-têtes HTTP de sécurité : Content Security Policy (CSP), X-Content-Type-Options, et Referrer-Policy.
⚠️ Attention !
 ❌ Évitez les certificats SSL/TLS auto-signés pour les sites publics.
 ❌ N’utilisez plus TLS 1.0 ou TLS 1.1 (obsolètes et vulnérables).
 ❌ Assurez-vous de renouveler les certificats à temps pour éviter toute coupure du service.
En mettant en place un HTTPS sécurisé avec TLS 1.2 ou TLS 1.3, votre site bénéficie d’un chiffrement et d’une authentification des échanges, réduisant ainsi les risques liés aux attaques MITM et aux manipulations malveillantes du trafic. Un site sécurisé inspire également plus de confiance aux utilisateurs et améliore son référencement sur les moteurs de recherche. 🚀
🔹 Le Man-in-the-Middle (MitM) : Une Menace Courante
Le Man-in-the-Middle (MitM) est une attaque informatique où un tiers malveillant intercepte et manipule discrètement les communications entre deux parties qui pensent communiquer directement entre elles.
Comment fonctionne une attaque MitM ?
Interception des communications
L’attaquant se positionne entre deux parties (ex. : un utilisateur et un site web, ou un client et un serveur).
Il intercepte les données échangées entre eux sans qu’ils s’en rendent compte.
Manipulation ou vol des données
L’attaquant peut modifier les données envoyées entre les deux parties ou voler des informations sensibles (mots de passe, numéros de carte bancaire).
Types d’attaques Man-in-the-Middle
🔸 Ecoute passive : L’attaquant intercepte les communications sans modifier leur contenu.
 🔸 Interception active : L’attaquant modifie les messages en transit, par exemple, en changeant un numéro de compte bancaire dans un transfert d’argent.
 🔸 Faux points d’accès Wi-Fi : Un cybercriminel peut créer un faux réseau Wi-Fi public (ex. : dans un café ou un aéroport) et intercepter tout le trafic des utilisateurs connectés.
 🔸 DNS Spoofing : L’attaquant redirige la connexion vers un faux site imitant celui d’un service légitime (ex. : fausse banque en ligne) pour voler des identifiants.
Comment se protéger d’un MitM ?
✔ Utiliser HTTPS partout (protocole sécurisé avec chiffrement TLS 1.2 ou TLS 1.3)
 ✔ Vérifier les certificats SSL des sites web (icône de cadenas dans la barre d’adresse)
 ✔ Ne pas se connecter à des sites sensibles (banque, email) via des Wi-Fi publics non sécurisés
 ✔ Activer l’option "HSTS" pour forcer HTTPS sur votre site web
 ✔ Utiliser un VPN sur les réseaux Wi-Fi publics pour sécuriser votre connexion

🔹 La Sécurisation de l’Infrastructure d’Hébergement
Le site web repose sur une infrastructure qui doit être correctement configurée et sécurisée pour éviter les attaques informatiques.
Les éléments essentiels de la sécurité de l’hébergement
🔹 Configuration sécurisée des serveurs
 ✔ Désactiver les services inutiles (ex. : Telnet, FTP, HTTP si HTTPS est activé)
 ✔ Sécuriser les connexions SSH avec une authentification par clé SSH au lieu des mots de passe
 ✔ Restreindre les accès aux services selon le principe du moindre privilège
🔹 Supervision et détection des attaques
 ✔ Activer des logs de connexion pour surveiller les accès suspects
 ✔ Configurer des systèmes de détection et prévention d’intrusion (IDS/IPS)
 ✔ Analyser régulièrement les logs pour identifier des comportements anormaux
🔹 Réduction de la surface d’attaque
 ✔ Bloquer tous les ports et services inutiles
 ✔ Supprimer les composants logiciels inutilisés ou obsolètes
 ✔ Utiliser des pare-feu (firewalls) pour filtrer le trafic réseau
 ✔ Restreindre les autorisations des fichiers et des applications

MÉMO : HTTP Strict Transport Security (HSTS)
Problème :
Sites acceptant HTTP puis redirigeant vers HTTPS
Vulnérabilité : attaquants peuvent intercepter la communication initiale
Solution - HSTS :
Force le navigateur à utiliser HTTPS automatiquement
Empêche l'utilisateur d'ignorer les alertes de sécurité (certificats invalides)
Élimine la fenêtre d'opportunité pour les attaques "man-in-the-middle"
Bénéfice sécurité :
Protection complète du canal de communication dès la première requête
MÉMO : Mise en œuvre de HSTS
Objectif :
Limiter les risques d'attaques Man-In-The-Middle
Nécessité :
Protéger contre les accès non sécurisés générés par:
Les utilisateurs (omission du HTTPS)
Les attaquants (tentatives de dégradation de connexion)
Implémentation :
Obligatoire pour une sécurisation complète du site
Élimine la phase vulnérable de connexion initiale


MÉMO : Certificate Transparency (CT)
Contexte :
Création suite aux difficultés techniques/organisationnelles des autorités de certification
Fonctionnement :
Système de surveillance des certificats délivrés
Utilise des registres (CT logs) où sont ajoutés les certificats lors de leur signature
Les registres ont des propriétés cryptographiques résistantes à la falsification
Avantages :
Permet de vérifier la légitimité des certificats
Facilite une réaction rapide en cas de problème
Fournit des preuves cumulatives de l'émission légitime d'un certificat
Bénéfices pour les acteurs du Web :
Prise de décision éclairée sur les autorités de certification fiables
Détection rapide des certificats illégitimes (absents ou incohérents avec le registre)
