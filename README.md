
# 🐳 Projet DevOps : Pipeline CI/CD avec Jenkins & Docker

## 📝 Description du projet

Ce projet réalise une usine logicielle complète (**CI/CD**) pour une application web statique basée sur un serveur **Nginx**. L'objectif est de passer d'une gestion manuelle à une infrastructure pilotée par le code (**Pipeline as Code**), garantissant un déploiement rapide, fiable et automatisé.

---

## 🏗️ Architecture du Pipeline

Le cycle de vie du logiciel est automatisé via un **Jenkinsfile** structuré en 5 étapes clés :

### 1. Suivi des Builds (Job History)

Chaque modification du code sur GitHub déclenche automatiquement une nouvelle exécution. L'historique permet de suivre la stabilité du projet au fil du temps.

> 
![Historique des exécutions réussies](screenShots\jobs)

### 2. Visualisation du Pipeline (Stage View)

Le pipeline traite le code par étapes successives. Si une étape échoue, le processus s'arrête pour garantir la qualité.


![Vue détaillée des 5 stages (Cloning, Building, Testing, Publishing, Deploying).](screenShots\pipeline.png)

### 3. Archivage sur le Registre (Docker Hub)

Une fois validée, l'image est versionnée et stockée sur Docker Hub. L'utilisation du tag `$BUILD_NUMBER` permet une traçabilité parfaite de chaque version.


![épertoire Docker Hub montrant les images taguées par numéro de build et le tag 'latest' mis à jour.](screenShots\dockerHub.png)
---

## 🛠️ Détails Techniques

### Configuration Docker

L'application est conteneurisée à l'aide d'un `dockerfile` optimisé :

```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html
EXPOSE 80

```

### Automatisation du Déploiement

Le déploiement local (CD) assure la continuité du service en nettoyant les anciennes instances avant de lancer la nouvelle version sur le port **8081** :

```cmd
docker stop tp5-container || ver > nul
docker rm tp5-container || ver > nul
docker run -d -p 8081:80 --name tp5-container abdelaaly/tp5:latest

```

---

## 🎓 Auteur

**Abdelaaly** *Étudiant en Master II Big Data et Cloud Computing (BDCC)* *ENSET Mohammedia*

