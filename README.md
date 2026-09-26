# 🚀 TaskFlow

### Application Full-Stack de gestion de tâches

TaskFlow est une application web moderne de **gestion de tâches** développée dans le cadre d'un projet Full-Stack.

L'application permet à chaque utilisateur de créer un compte, de se connecter de manière sécurisée et de gérer ses propres tâches à travers une interface moderne, responsive et intuitive.

Le projet met en pratique une architecture **MERN**, avec une séparation claire entre le frontend React et le backend Express connecté à MongoDB.

---

## ✨ Aperçu

TaskFlow transforme la gestion quotidienne des tâches en une expérience simple et organisée.

L'utilisateur peut :

* 🔐 créer un compte et se connecter
* 📝 créer des tâches
* ✏️ modifier ses tâches
* 🗑️ supprimer ses tâches
* ✅ marquer une tâche comme terminée
* 🔎 rechercher des tâches
* 🎯 filtrer les tâches
* ↕️ trier les tâches
* 🚦 gérer les priorités
* 📅 définir des dates d'échéance
* 📊 consulter les statistiques de ses tâches

Chaque utilisateur dispose de son propre espace et ne peut accéder qu'à ses propres tâches.

---

# 🎯 Objectifs du projet

Ce projet a été conçu pour mettre en pratique les principales notions du développement Full-Stack moderne :

* développer une application React avec JSX et Vite
* créer des composants React réutilisables
* gérer l'état de l'application
* consommer une API REST
* construire une API avec Express.js
* connecter une application à MongoDB avec Mongoose
* implémenter l'inscription et la connexion
* sécuriser les mots de passe avec bcrypt
* protéger les routes avec JWT
* réaliser un CRUD complet
* gérer l'autorisation et la propriété des ressources
* créer une interface responsive avec Tailwind CSS
* utiliser shadcn/ui pour les composants
* gérer les variables d'environnement
* appliquer des bonnes pratiques de sécurité
* documenter et versionner le projet avec Git et GitHub

---

# 🛠️ Technologies utilisées

## Frontend

| Technologie  | Utilisation                  |
| ------------ | ---------------------------- |
| React        | Interface utilisateur        |
| JSX          | Développement des composants |
| Vite         | Outil de build               |
| React Router | Navigation                   |
| Tailwind CSS | Styling                      |
| shadcn/ui    | Composants UI                |
| Lucide React | Icônes                       |
| Axios        | Communication avec l'API     |

## Backend

| Technologie | Utilisation                    |
| ----------- | ------------------------------ |
| Node.js     | Runtime JavaScript             |
| Express.js  | API REST                       |
| Mongoose    | ODM MongoDB                    |
| MongoDB     | Base de données                |
| JWT         | Authentification               |
| bcrypt      | Hashage des mots de passe      |
| CORS        | Communication frontend/backend |
| dotenv      | Variables d'environnement      |

## Outils

* Git
* GitHub
* VS Code
* MongoDB Atlas / MongoDB local
* npm

---

# 🏗️ Architecture

TaskFlow utilise une architecture Full-Stack séparant clairement le frontend et le backend.

```text
                    ┌─────────────────────┐
                    │       React         │
                    │      + Vite         │
                    │      + Tailwind     │
                    └──────────┬──────────┘
                               │
                               │ HTTP / REST API
                               ▼
                    ┌─────────────────────┐
                    │      Express.js     │
                    │       Server        │
                    └──────────┬──────────┘
                               │
                    ┌──────────┴──────────┐
                    │                     │
                    ▼                     ▼
              JWT Middleware        Controllers
                    │                     │
                    └──────────┬──────────┘
                               ▼
                         ┌───────────┐
                         │ Mongoose  │
                         └─────┬─────┘
                               ▼
                         ┌───────────┐
                         │ MongoDB   │
                         └───────────┘
```

---

# 📁 Structure du projet

```text
taskflow/
│
├── client/
│   ├── public/
│   │   └── logo.svg
│   │
│   ├── src/
│   │   ├── assets/
│   │   │
│   │   ├── components/
│   │   │   ├── ui/
│   │   │   ├── Navbar.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   ├── TaskForm.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   │
│   │   ├── pages/
│   │   │   ├── Landing.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   └── NotFound.jsx
│   │   │
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── authService.js
│   │   │   └── taskService.js
│   │   │
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   │
│   │   ├── hooks/
│   │   ├── lib/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   │
│   ├── .env
│   ├── .env.example
│   ├── package.json
│   └── vite.config.js
│
├── server/
│   ├── config/
│   │   └── db.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   └── taskController.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   ├── errorMiddleware.js
│   │   └── notFoundMiddleware.js
│   │
│   ├── models/
│   │   ├── User.js
│   │   └── Task.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   └── taskRoutes.js
│   │
│   ├── utils/
│   │   └── generateToken.js
│   │
│   ├── .env
│   ├── .env.example
│   ├── server.js
│   └── package.json
│
├── .gitignore
├── README.md
└── package.json
```

---

# 🔐 Authentification

TaskFlow utilise une authentification basée sur **JWT (JSON Web Token)**.

Le fonctionnement est le suivant :

```text
Utilisateur
     │
     ▼
Formulaire Login
     │
     ▼
POST /api/auth/login
     │
     ▼
Express
     │
     ▼
Auth Controller
     │
     ▼
Vérification email/password
     │
     ▼
Comparaison avec bcrypt
     │
     ▼
Génération du JWT
     │
     ▼
React reçoit le token
     │
     ▼
Requêtes protégées
     │
     ▼
JWT Middleware
     │
     ▼
Accès aux ressources
```

Les mots de passe ne sont jamais enregistrés en clair.

Les routes privées nécessitent un token valide.

---

# 👤 Modèle User

```javascript
{
  name: String,
  email: String,
  password: String,
  createdAt: Date,
  updatedAt: Date
}
```

Contraintes :

* email unique
* email normalisé
* mot de passe hashé avec bcrypt
* mot de passe jamais retourné dans les réponses API
* timestamps automatiques

---

# ✅ Modèle Task

```javascript
{
  title: String,
  description: String,
  status: String,
  priority: String,
  dueDate: Date,
  user: ObjectId,
  createdAt: Date,
  updatedAt: Date
}
```

### Statuts disponibles

```text
pending
in-progress
completed
```

### Priorités disponibles

```text
low
medium
high
```

Chaque tâche appartient à exactement un utilisateur.

---

# 📋 Fonctionnalités

## 🔐 Authentification

* Inscription
* Connexion
* Déconnexion
* Récupération du profil utilisateur
* JWT
* Hashage bcrypt
* Protection des routes

## 📝 Gestion des tâches

* Création
* Lecture
* Modification
* Suppression
* Changement de statut
* Changement de priorité
* Date d'échéance
* Marquage comme terminée

## 🔎 Recherche

Recherche par :

* titre
* description

## 🎯 Filtres

* Toutes
* En attente
* En cours
* Terminées
* Priorité faible
* Priorité moyenne
* Priorité élevée

## ↕️ Tri

* Plus récentes
* Plus anciennes
* Date d'échéance
* Priorité

## 📊 Dashboard

Le dashboard affiche notamment :

* nombre total de tâches
* tâches en attente
* tâches en cours
* tâches terminées
* liste des tâches
* recherche
* filtres
* tri

---

# 🌐 Pages

### `/`

Landing Page publique avec :

* navigation
* hero section
* présentation de TaskFlow
* fonctionnalités
* aperçu du dashboard
* call-to-action
* footer responsive

### `/register`

Création d'un compte.

### `/login`

Connexion utilisateur.

### `/dashboard`

Dashboard protégé permettant de gérer les tâches.

### `/404`

Page affichée lorsqu'une route n'existe pas.

---

# 🔌 API REST

Base URL :

```text
http://localhost:5000/api
```

---

## 🔐 Authentication

### Register

```http
POST /api/auth/register
```

Exemple :

```json
{
  "name": "Salma",
  "email": "salma@example.com",
  "password": "password123"
}
```

---

### Login

```http
POST /api/auth/login
```

Exemple :

```json
{
  "email": "salma@example.com",
  "password": "password123"
}
```

---

### Current User

```http
GET /api/auth/me
```

Authentification requise.

---

# 📝 Tasks API

Toutes les routes suivantes nécessitent une authentification.

### Créer une tâche

```http
POST /api/tasks
```

Exemple :

```json
{
  "title": "Préparer le projet React",
  "description": "Finaliser le dashboard",
  "status": "in-progress",
  "priority": "high",
  "dueDate": "2026-10-01"
}
```

---

### Récupérer les tâches

```http
GET /api/tasks
```

Retourne uniquement les tâches de l'utilisateur connecté.

---

### Récupérer une tâche

```http
GET /api/tasks/:id
```

---

### Modifier une tâche

```http
PUT /api/tasks/:id
```

---

### Supprimer une tâche

```http
DELETE /api/tasks/:id
```

---

# 📦 Format des réponses API

Les réponses suivent une structure cohérente.

### Succès

```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "..."
  }
}
```

### Erreur

```json
{
  "success": false,
  "message": "Task not found"
}
```

---

# 🛡️ Sécurité

TaskFlow applique plusieurs bonnes pratiques de sécurité :

* 🔐 mots de passe hashés avec bcrypt
* 🎫 authentification JWT
* 🛡️ routes privées protégées
* 👤 vérification de propriété des tâches
* 🔒 secrets stockés dans les variables d'environnement
* 🚫 fichiers `.env` exclus de Git
* 🧹 validation des données utilisateur
* 🆔 validation des MongoDB ObjectId
* 🌐 CORS configuré pour le frontend
* 🚫 aucune exposition des mots de passe
* 🚫 aucun secret JWT exposé au frontend
* 🚫 aucun `userId` fourni par le frontend utilisé pour déterminer le propriétaire

L'autorisation est vérifiée côté serveur.

Par exemple, une tâche n'est pas récupérée simplement avec :

```javascript
Task.findById(id)
```

Le serveur vérifie également que la tâche appartient à l'utilisateur authentifié.

---

# ⚙️ Variables d'environnement

## Client

Créer :

```text
client/.env
```

```env
VITE_API_URL=http://localhost:5000/api
```

Le fichier exemple :

```text
client/.env.example
```

```env
VITE_API_URL=
```

---

## Server

Créer :

```text
server/.env
```

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/taskflow
JWT_SECRET=change_this_secret
CLIENT_URL=http://localhost:5173
```

Le fichier exemple :

```text
server/.env.example
```

```env
PORT=
MONGO_URI=
JWT_SECRET=
CLIENT_URL=
```

⚠️ **Ne jamais publier les fichiers `.env` sur GitHub.**

---

# 💻 Installation

## Prérequis

Avant de commencer, installer :

* Node.js
* npm
* MongoDB ou un cluster MongoDB Atlas
* Git

Vérifier Node.js :

```bash
node --version
```

Vérifier npm :

```bash
npm --version
```

---

# 📥 Cloner le projet

```bash
git clone https://github.com/YOUR_USERNAME/taskflow.git
```

Puis :

```bash
cd taskflow
```

---

# 🖥️ Installation du Backend

```bash
cd server
npm install
```

Créer ensuite :

```text
server/.env
```

et renseigner les variables d'environnement.

Lancer le serveur :

```bash
npm run dev
```

Le backend sera disponible sur :

```text
http://localhost:5000
```

---

# 🌐 Installation du Frontend

Dans un autre terminal :

```bash
cd client
npm install
```

Créer :

```text
client/.env
```

avec :

```env
VITE_API_URL=http://localhost:5000/api
```

Puis lancer :

```bash
npm run dev
```

Le frontend sera disponible sur :

```text
http://localhost:5173
```

---

# 🗄️ MongoDB

Le projet peut fonctionner avec MongoDB local ou MongoDB Atlas.

### MongoDB local

```env
MONGO_URI=mongodb://localhost:27017/taskflow
```

### MongoDB Atlas

Remplacer la valeur par l'URI de connexion fournie par MongoDB Atlas :

```env
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@cluster.mongodb.net/taskflow
```

⚠️ Cette valeur doit rester uniquement dans le fichier `.env`.

---

# 🧪 Flux utilisateur

```text
Landing Page
      │
      ▼
   Register
      │
      ▼
 Account Created
      │
      ▼
   Dashboard
      │
      ├───────────────┐
      ▼               ▼
 Create Task      Existing Tasks
      │               │
      ▼               ▼
 Task List      Search / Filter / Sort
      │               │
      ├───────────────┤
      ▼               ▼
    Edit          Complete
      │               │
      └───────┬───────┘
              ▼
           Delete
              │
              ▼
           Logout
              │
              ▼
            Login
              │
              ▼
         Dashboard
```

---

# 🎨 Interface utilisateur

TaskFlow utilise une interface moderne basée sur :

* Tailwind CSS
* shadcn/ui
* Lucide React

L'interface met l'accent sur :

* simplicité
* lisibilité
* responsive design
* hiérarchie visuelle
* composants réutilisables
* feedback utilisateur

Des éléments comme les **cards, badges, dialogs, dropdowns, forms, avatars, skeletons et notifications** sont utilisés pour améliorer l'expérience utilisateur.

---

# 📱 Responsive Design

L'application est conçue pour fonctionner sur :

* 💻 Desktop
* 💻 Laptop
* 📱 Tablet
* 📱 Mobile

Le dashboard adapte notamment :

* la navigation
* la sidebar
* les cartes
* la liste des tâches
* les formulaires
* les statistiques

aux différentes tailles d'écran.

---

# 🔔 Gestion des états

L'application gère plusieurs états utilisateur :

### Loading

Pendant :

* connexion
* inscription
* récupération des tâches
* création
* modification
* suppression

### Empty State

Lorsqu'aucune tâche n'existe encore.

### Error State

Lorsqu'une erreur serveur ou réseau survient.

### Success State

Après les actions importantes :

* tâche créée
* tâche modifiée
* tâche supprimée
* connexion réussie

Les notifications sont présentées de manière claire et non intrusive.

---

# 🧩 Architecture Backend

Le backend suit le principe :

```text
HTTP Request
     │
     ▼
   Route
     │
     ▼
 Middleware
     │
     ▼
 Controller
     │
     ▼
   Model
     │
     ▼
 MongoDB
```

### Routes

Responsables de la définition des endpoints.

### Controllers

Contiennent la logique de traitement des requêtes.

### Models

Définissent les schémas Mongoose.

### Middleware

Gèrent notamment :

* authentification
* erreurs
* routes inexistantes

### Config

Contient la configuration MongoDB.

### Utils

Contient les fonctions réutilisables.

---

# 🌱 Git & GitHub

Le projet utilise Git pour suivre l'évolution du développement.

Exemples de commits :

```text
feat: initialize client and server
feat: create MongoDB models
feat: implement authentication
feat: implement JWT middleware
feat: implement task CRUD
feat: create dashboard
feat: add task filters
feat: improve responsive UI
fix: authentication redirect
docs: update README
```

Les fichiers suivants ne doivent jamais être commités :

```text
.env
node_modules/
```

---

# 📸 Screenshots

> Ajoutez ici les captures d'écran de votre application finale.

### Landing Page

```text
screenshots/landing.png
```

### Login

```text
screenshots/login.png
```

### Register

```text
screenshots/register.png
```

### Dashboard

```text
screenshots/dashboard.png
```

### Task Management

```text
screenshots/tasks.png
```

---

# 🚀 Améliorations futures

Plusieurs fonctionnalités peuvent être ajoutées dans de futures versions :

* 🌙 Dark / Light mode
* 🖱️ Drag & Drop des tâches
* 🏷️ Catégories
* 📄 Pagination
* 👤 Page profil
* 🔑 Changement de mot de passe
* 🖼️ Upload d'avatar
* 📊 Graphiques du dashboard
* 📅 Vue calendrier
* 🔔 Notifications de deadline
* 🔄 Tâches récurrentes
* ⚡ mises à jour temps réel avec Socket.IO
* 👥 équipes et espaces de travail
* 🤝 partage de tâches

---

# 📚 Compétences mises en pratique

À travers ce projet, les principales compétences suivantes ont été mises en pratique :

### Frontend

* React
* JSX
* Vite
* React Router
* composants réutilisables
* Context API
* appels API
* gestion des états
* Tailwind CSS
* shadcn/ui

### Backend

* Node.js
* Express.js
* architecture REST
* routes
* controllers
* middleware
* gestion centralisée des erreurs

### Base de données

* MongoDB
* Mongoose
* relations entre documents
* validation des données
* requêtes sécurisées

### Sécurité

* JWT
* bcrypt
* autorisation
* protection des ressources
* variables d'environnement
* CORS

### Outils

* Git
* GitHub
* npm
* VS Code

---

# 🎓 Contexte du projet

**TaskFlow** a été développé dans le cadre d'un exercice étudiant Full-Stack visant à mettre en pratique les concepts fondamentaux du développement d'applications web modernes.

L'objectif n'est pas uniquement de créer un CRUD fonctionnel, mais de construire une application organisée comme un véritable petit produit SaaS, avec une attention particulière portée à :

* l'architecture
* la sécurité
* l'expérience utilisateur
* la maintenabilité
* la séparation des responsabilités
* la documentation

---

# 👩‍💻 Auteur

**Salma EL QADI**

Étudiante en développement d'applications et intelligence artificielle.

* GitHub : `https://github.com/Salma-ELQADI`
* LinkedIn : `https://linkedin.com/in/salma-elqadi/`
