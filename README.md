# 🐳 Projet DevOps : Pipeline CI/CD avec Jenkins & Docker

## 📝 Description du projet

Ce projet consiste en la mise en place d'une chaîne d'automatisation complète (CI/CD) pour une application web statique basée sur un serveur **Nginx**. L'objectif est de passer d'un mode de gestion manuel à une infrastructure pilotée par le code (**Pipeline as Code**) permettant de minimiser les interventions humaines et les erreurs de déploiement.

## 🛠️ Technologies utilisées

* 
**Serveur Web** : Nginx (via Docker).


* 
**Gestionnaire de version** : GitHub.


* 
**Orchestrateur CI/CD** : Jenkins.


* 
**Conteneurisation** : Docker Engine.


* 
**Registre d'images** : Docker Hub.



---

## 🏗️ Étapes de réalisation

### 1. Préparation de l'application

* Création d'une page `index.html` affichant le message "Welcome BDCC".


* Rédaction d'un `dockerfile` configuré pour copier cette page dans le répertoire de diffusion de Nginx (`/usr/share/nginx/html`) et exposer le port 80.



### 2. Automatisation (CI - Intégration Continue)

* 
**Gestion du code** : Initialisation d'un dépôt Git et push du code vers un répertoire GitHub public.


* 
**Déclenchement automatique** : Configuration de Jenkins pour surveiller le dépôt via la méthode **Poll SCM** (`* * * * *`), permettant de détecter tout changement de code chaque minute.


* 
**Construction et Publication** : Automatisation de la commande `docker build` pour générer l'image et de `docker push` pour l'archiver sur Docker Hub avec des tags dynamiques (numéros de build).



### 3. Pipeline as Code (CD - Déploiement Continu)

* 
**Scripting** : Remplacement de la configuration manuelle par un fichier **`jenkinsfile`** déclaratif.


* 
**Cycle de vie du conteneur** : Intégration de commandes batch pour automatiser l'arrêt (`docker stop`), la suppression (`docker rm`) de l'ancienne version, et le lancement (`docker run`) du nouveau conteneur sur le port local **8081**.



---

## 📋 Étapes du Jenkinsfile

Le pipeline final exécute les cinq stages suivants de manière séquentielle:

1. 
**Cloning Git** : Téléchargement sécurisé de la dernière version du code.


2. 
**Building Image** : Création d'une nouvelle image Docker isolée.


3. 
**Test Image** : Étape de validation (vérification de la disponibilité du service).


4. 
**Publish Image** : Envoi de l'image vérifiée vers le registre distant Docker Hub.


5. 
**Deploy Image** : Mise à jour automatique de l'application en production locale.



---

## 👨‍💻 Auteur

**Abdelaaly**


*Étudiant en Master II Big Data et Cloud Computing (BDCC)* *ENSET Mohammedia* 
