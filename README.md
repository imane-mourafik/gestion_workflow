# 📋 Système de Gestion de Workflows d'Entreprise

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2-brightgreen)
![Angular](https://img.shields.io/badge/Angular-17-red)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

> Application web full-stack pour la digitalisation et l'automatisation des processus métier en entreprise

## 📖 Table des matières

- [À propos](#-à-propos)
- [Fonctionnalités](#-fonctionnalités)
- [Technologies utilisées](#-technologies-utilisées)
- [Architecture](#️-architecture)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration](#️-configuration)
- [Utilisation](#-utilisation)
- [Captures d'écran](#-captures-décran)
- [API Documentation](#-api-documentation)
- [Tests](#-tests)
- [Déploiement](#-déploiement)
- [Contribution](#-contribution)
- [Auteurs](#-auteurs)
- [License](#-license)

---

## 🎯 À propos

Ce projet est une **application web de gestion de workflows** développée dans le cadre d'un projet académique. Elle permet aux entreprises de digitaliser leurs processus internes (demandes de congés, achats, validations, etc.) en offrant un système centralisé, sécurisé et traçable.

### Problématique

Les organisations modernes font face à plusieurs défis dans la gestion de leurs processus internes :
- ❌ Manque de traçabilité des demandes
- ❌ Processus de validation lents et manuels
- ❌ Absence de visibilité en temps réel
- ❌ Risques d'erreurs et d'oublis
- ❌ Informations dispersées (emails, papier, Excel)

### Solution

✅ Application web centralisée  
✅ Workflows personnalisables  
✅ Validation multi-niveaux automatisée  
✅ Traçabilité complète  
✅ Tableaux de bord en temps réel  
✅ Sécurité renforcée (JWT + RBAC)

---

## ✨ Fonctionnalités

### 🔐 Authentification & Sécurité
- Connexion sécurisée avec JWT (JSON Web Token)
- Gestion des rôles : **Admin**, **Validateur**, **Employé**
- Protection des routes selon les permissions
- Hachage des mots de passe (BCrypt)

### 👥 Gestion des Utilisateurs
- CRUD complet des employés (Administrateur)
- Affectation des rôles et départements
- Profil utilisateur personnalisable
- Changement de mot de passe

### 🏢 Gestion des Départements
- Création et organisation des départements
- Affectation des employés
- Vue hiérarchique de l'organisation

### 🔄 Gestion des Workflows
- Création de workflows personnalisés
- Définition d'étapes de validation séquentielles
- Affectation des validateurs par étape
- Activation/désactivation des workflows

### 📝 Gestion des Demandes
- Soumission de demandes via formulaires
- Circuit de validation automatique
- Approbation/rejet avec commentaires
- Suivi en temps réel de l'état
- Historique complet et traçabilité

### 📊 Tableaux de Bord
- **Admin** : Vue globale, statistiques, gestion complète
- **Validateur** : Demandes en attente, historique validations
- **Employé** : Mes demandes, soumission, suivi

---

## 🛠️ Technologies utilisées

### Backend
- **Java 17** - Langage de programmation
- **Spring Boot 3.2** - Framework backend
- **Spring Security** - Sécurité et authentification
- **Spring Data JPA** - Accès aux données
- **MySQL 8.0** - Base de données relationnelle
- **JWT** - Authentification stateless
- **Maven** - Gestion des dépendances

### Frontend
- **Angular 17** - Framework frontend
- **TypeScript** - Langage typé
- **Bootstrap 5** - Framework CSS
- **RxJS** - Programmation réactive
- **Angular Router** - Navigation
- **HttpClient** - Communication avec l'API

### Outils
- **IntelliJ IDEA** - IDE Backend
- **Visual Studio Code** - IDE Frontend
- **Postman** - Tests API
- **MySQL Workbench** - Gestion BDD
- **Git** - Versioning
- **GitHub** - Hébergement du code

---

## 🏗️ Architecture

### Architecture 3-tiers

```
┌─────────────────────────────────────────────────────────────┐
│                      FRONTEND (Angular)                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Components   │  │  Services    │  │   Guards     │      │
│  │              │  │              │  │              │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            │ HTTP/REST
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    BACKEND (Spring Boot)                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Controllers  │  │  Services    │  │  Security    │      │
│  │              │  │              │  │              │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            │ JDBC
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                     BASE DE DONNÉES (MySQL)                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Utilisateurs │  │  Workflows   │  │  Demandes    │      │
│  │              │  │              │  │              │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

### Structure du projet

Le projet est organisé en **deux repositories séparés** pour une meilleure séparation des préoccupations et une utilisation optimale des IDE :

#### 🔷 Backend (IntelliJ IDEA)
```
ProjetJavaWorkflowSecurity/          # Projet Spring Boot
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/workflow/
│   │   │       ├── config/          # Configuration (Security, CORS, JWT)
│   │   │       ├── controller/      # REST Controllers
│   │   │       ├── service/         # Business Logic
│   │   │       ├── repository/      # Data Access Layer (JPA)
│   │   │       ├── model/           # Entities (Utilisateur, Workflow, etc.)
│   │   │       ├── dto/             # Data Transfer Objects
│   │   │       └── security/        # JWT Utils, Filters
│   │   └── resources/
│   │       ├── application.properties    # Configuration BDD, JWT
│   │       └── static/              # (optionnel)
│   └── test/                        # Tests unitaires
└── pom.xml                          # Dépendances Maven
```

#### 🔶 Frontend (VS Code)
```
workflow-angular-app/                # Projet Angular
├── src/
│   ├── app/
│   │   ├── components/              # Composants UI
│   │   │   ├── login/
│   │   │   ├── admin/
│   │   │   ├── validateur/
│   │   │   ├── employer/
│   │   │   └── profile/
│   │   ├── services/                # Services HTTP
│   │   │   ├── auth.service.ts
│   │   │   ├── employee.service.ts
│   │   │   ├── workflow.service.ts
│   │   │   └── department.service.ts
│   │   ├── guards/                  # Route Guards (RoleGuard)
│   │   ├── models/                  # Interfaces TypeScript
│   │   ├── interceptors/            # HTTP Interceptors (JWT)
│   │   └── app.routes.ts            # Configuration des routes
│   ├── assets/                      # Images, icônes
│   ├── styles.css                   # Styles globaux
│   └── index.html
├── angular.json                     # Configuration Angular
├── package.json                     # Dépendances npm
└── tsconfig.json                    # Configuration TypeScript
```

#### 📦 Organisation recommandée sur votre machine

```
C:/Users/4B/Downloads/
├── ProjetJavaWorkflowSecurity/      # Backend (ouvert dans IntelliJ)
└── workflow-angular-app/            # Frontend (ouvert dans VS Code)
```

> **Note** : Les deux projets communiquent via API REST sur `http://localhost:8080/api`

---

## 📋 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- **Java JDK 17** ou supérieur - [Télécharger](https://www.oracle.com/java/technologies/downloads/)
- **Node.js 18+** et **npm** - [Télécharger](https://nodejs.org/)
- **MySQL 8.0+** - [Télécharger](https://dev.mysql.com/downloads/)
- **Git** - [Télécharger](https://git-scm.com/)
- **Maven 3.8+** (ou utiliser le wrapper Maven inclus)
- **Angular CLI** : `npm install -g @angular/cli`

Vérifier les installations :
```bash
java -version       # Java 17+
node -version       # Node 18+
npm -version        # npm 9+
mysql --version     # MySQL 8.0+
ng version          # Angular 17+
```

---

## 🚀 Installation

### Organisation des projets

Ce projet est composé de **deux applications séparées** :
- **Backend** : `ProjetJavaWorkflowSecurity` (Spring Boot - IntelliJ IDEA)
- **Frontend** : `workflow-angular-app` (Angular - VS Code)

### 1️⃣ Cloner les repositories

**Option A : Deux repositories GitHub séparés (Recommandé)**
```bash
# Backend
git clone https://github.com/votre-username/workflow-backend.git
cd workflow-backend

# Frontend (dans un autre dossier)
git clone https://github.com/votre-username/workflow-frontend.git
cd workflow-frontend
```

**Option B : Un seul repository avec structure monorepo**
```bash
git clone https://github.com/votre-username/workflow-management-system.git
cd workflow-management-system
```

### 2️⃣ Configuration de la base de données

```bash
# Se connecter à MySQL
mysql -u root -p

# Créer la base de données
CREATE DATABASE projetjavaworkflow CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

# Utiliser la base
USE projetjavaworkflow;

# Exécuter le script de création des tables
source database/schema.sql;

# (Optionnel) Insérer des données de test
source database/data.sql;
```

### 3️⃣ Installation du Backend (Spring Boot - IntelliJ IDEA)

```bash
# Naviguer vers le projet backend
cd ProjetJavaWorkflowSecurity

# Avec Maven wrapper (recommandé)
./mvnw clean install
# Sous Windows :
mvnw.cmd clean install

# Ou avec Maven global
mvn clean install
```

**Ou via IntelliJ IDEA :**
1. Ouvrir IntelliJ IDEA
2. File → Open → Sélectionner le dossier `ProjetJavaWorkflowSecurity`
3. Attendre que Maven télécharge les dépendances
4. Clic droit sur `pom.xml` → Maven → Reload Project

### 4️⃣ Installation du Frontend (Angular - VS Code)

```bash
# Naviguer vers le projet frontend
cd workflow-angular-app

# Installer les dépendances npm
npm install

# Installer Angular CLI globalement (si pas déjà fait)
npm install -g @angular/cli
```

**Ou via VS Code :**
1. Ouvrir VS Code
2. File → Open Folder → Sélectionner le dossier `workflow-angular-app`
3. Ouvrir le terminal intégré (Ctrl + `)
4. Exécuter `npm install`

---

## ⚙️ Configuration

### Backend - `application.properties`

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/projetjavaworkflow
spring.datasource.username=root
spring.datasource.password=votre_mot_de_passe
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# Server
server.port=8080

# JWT
jwt.secret=VotreCleSecreteSecurisee123456
jwt.expiration=86400000
```

### Frontend - `environment.ts`

```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/api'
};
```

---

## 💻 Utilisation

### ⚡ Démarrage rapide

Pour utiliser l'application, vous devez démarrer **les deux projets séparément** :

#### 1️⃣ Démarrer le Backend (IntelliJ IDEA)

**Méthode 1 : Via IntelliJ IDEA (Recommandé)**
1. Ouvrir le projet `ProjetJavaWorkflowSecurity` dans IntelliJ
2. Localiser la classe principale (avec `@SpringBootApplication`)
3. Clic droit → Run 'WorkflowApplication'

**Méthode 2 : Via Maven (Terminal)**
```bash
cd ProjetJavaWorkflowSecurity

# Avec Maven wrapper
./mvnw spring-boot:run

# Windows
mvnw.cmd spring-boot:run

# Ou avec Maven global
mvn spring-boot:run
```

✅ **Backend démarré sur** : `http://localhost:8080`

#### 2️⃣ Démarrer le Frontend (VS Code)

**Méthode 1 : Via VS Code (Recommandé)**
1. Ouvrir le projet `workflow-angular-app` dans VS Code
2. Ouvrir le terminal intégré (Ctrl + `)
3. Exécuter `ng serve`

**Méthode 2 : Via Terminal**
```bash
cd workflow-angular-app

# Mode développement
ng serve

# Avec ouverture automatique du navigateur
ng serve --open

# Sur un port différent (si 4200 occupé)
ng serve --port 4201
```

✅ **Frontend démarré sur** : `http://localhost:4200`

### 🌐 Accéder à l'application

Une fois les deux serveurs démarrés :
1. Ouvrez votre navigateur
2. Allez sur `http://localhost:4200`
3. Connectez-vous avec les identifiants par défaut

### Connexion par défaut

**Administrateur :**
- Email : `admin@test.com`
- Mot de passe : `admin123`

---

## 📸 Captures d'écran

### Page de connexion
<img width="571" height="374" alt="image" src="https://github.com/user-attachments/assets/2e496661-44c2-40df-affe-2e9a20701725" />


### Dashboard Administrateur
<img width="947" height="441" alt="image" src="https://github.com/user-attachments/assets/d1e59212-ef61-43fa-8114-0e13fcc425d3" />


### Dashboard  Validateur
![Workflows](docs/screenshots/workflows.png)

### Dashboard Employe  
<img width="776" height="348" alt="image" src="https://github.com/user-attachments/assets/b3d0a37a-27ea-4540-8516-309ac7ed9044" />


---

## 📚 API Documentation

### Endpoints principaux

#### Authentification
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "motDePasse": "password123"
}
```

#### Utilisateurs
```http
GET    /api/employees          # Liste des employés
GET    /api/employees/{id}     # Détails d'un employé
POST   /api/employees          # Créer un employé
PUT    /api/employees/{id}     # Modifier un employé
DELETE /api/employees/{id}     # Supprimer un employé
```

#### Workflows
```http
GET    /api/workflows          # Liste des workflows
POST   /api/workflows          # Créer un workflow
GET    /api/workflows/{id}     # Détails d'un workflow
PUT    /api/workflows/{id}     # Modifier un workflow
DELETE /api/workflows/{id}     # Supprimer un workflow
```

Documentation complète Swagger disponible sur : `http://localhost:8080/swagger-ui.html`

---

## 🧪 Tests

### Backend (JUnit)

```bash
cd backend

# Exécuter tous les tests
./mvnw test

# Avec couverture de code
./mvnw test jacoco:report
```

### Frontend (Jasmine/Karma)

```bash
cd frontend

# Exécuter les tests
ng test

# Tests en mode CI
ng test --watch=false --code-coverage
```

---

## 🚢 Déploiement

### Backend

```bash
# Build du JAR
cd backend
./mvnw clean package

# Le JAR sera dans target/workflow-backend-1.0.0.jar

# Exécuter le JAR
java -jar target/workflow-backend-1.0.0.jar
```

### Frontend

```bash
# Build pour production
cd frontend
ng build --configuration production

# Les fichiers seront dans dist/
```

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Voici comment contribuer :

1. **Fork** le projet
2. **Créer** une branche (`git checkout -b feature/AmazingFeature`)
3. **Commit** vos changements (`git commit -m 'Add AmazingFeature'`)
4. **Push** vers la branche (`git push origin feature/AmazingFeature`)
5. **Ouvrir** une Pull Request

---

## 👥 Auteurs

- **[Votre Nom]** - *Développement initial* - [GitHub](https://github.com/votre-username)

### Encadrement
- **[Nom du Professeur]** - *Encadrant académique* - [Université/École]

---

## 📄 License

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 🙏 Remerciements

- Professeur **[Nom]** pour l'encadrement et les conseils
- L'équipe Spring Boot pour leur excellent framework
- L'équipe Angular pour leur framework moderne
- La communauté open source

---

## 📞 Contact

Pour toute question ou suggestion :

- **Email** : votre.email@example.com
- **LinkedIn** : [Votre Profil](https://linkedin.com/in/votre-profil)
- **GitHub** : [@votre-username](https://github.com/votre-username)

---

<div align="center">

**⭐ N'oubliez pas de mettre une étoile si ce projet vous a aidé ! ⭐**

Made with ❤️ by [Votre Nom]

</div>
