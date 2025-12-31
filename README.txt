---

#   KB-Example : Prototype de Knowledge Base Souveraine

##  Objectif du projet

Valider la faisabilité technique d'une centralisation des procédures clients et techniques sur une infrastructure conteneurisée et souveraine. Ce prototype remplace les solutions SaaS par une stack auto-hébergée, sécurisée, open source (gratuite) et scalable.

## Stack Technique

* **Orchestration :** Docker & Docker Compose.
* **Application :** BookStack (Image LinuxServer).
* **Base de données :** MySQL 5.7.
* **OS Cible :** Déploiement validé sur environnement Linux/Windows via Docker Desktop.

## Sécurisation & Architecture

* **Gestion des Secrets :** Utilisation de variables d'environnement via un fichier `.env` pour l'injection des identifiants BDD et des clés applicatives (APP_KEY).
* **Isolation Réseau :** Le service MySQL n'est pas exposé sur l'hôte, il communique uniquement via le réseau interne Docker avec l'application.
* **Persistance des Données :** Extraction des données SQL et applicatives via des volumes Docker stockés localement dans `./bs-data` et `./bs-db`.

## Déploiement rapide

1. Cloner le dépôt.
2. Créer un fichier `.env` à partir du `.env.example`.
3. Lancer la stack :
```bash
docker-compose up -d

```


4. Accès via : `http://localhost:6875`.
## Évolutions prévues (Roadmap)

* **Identité :** Intégration LDAP/Active Directory pour l'authentification centralisée des collaborateurs.
* **Sécurité :** Mise en place d'un reverse-proxy Nginx avec certificat SSL pour un accès HTTPS.
* **Mise en production :** Migration du prototype local vers un serveur Debian avec IP fixe et DNS dédié.

---