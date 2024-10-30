
## Présentation de l'Application

Tree Learning est une application de cours en ligne qui permet aux utilisateurs de se connecter, d'accéder à des modules de formation et de suivre leur progression. L'application est divisée en deux parties principales : un frontend développé en React avec TypeScript et un backend construit avec Symfony et PHP.

## Stacks Techniques

### Frontend
- React
- TypeScript
- Redux Toolkit pour la gestion d'état
- RTK Query pour les appels API
- Tailwind CSS pour le styling

### Backend
- Symfony 6
- PHP 8.1
- PostgreSQL 13
- Doctrine ORM

### Outils de Développement
- Docker pour la conteneurisation
- Git pour le contrôle de version

## Installation

1. Cloner le dépôt :
   ```
   git clone https://github.com/Elvi-2202/application-de-bureau
   cd APPLICATION DE BUREAU
   ```

2. Configuration du Backend :
   ```
   cd api-modules
   composer install
   cp .env .env.local
   # Configurez la base de données dans .env.local
   php bin/console doctrine:database:create
   php bin/console doctrine:migrations:migrate
   php bin/console doctrine:fixtures:load
   symfony server:start
   ```

3. Configuration du Frontend :
   ```
   cd cours-en-ligne
   npm install
   cp .env.example .env.local
   # Configurez l'URL de l'API dans .env.local
   npm start
   ```

4. Lancement de la base de données :
   ```
   cd db
   docker-compose up -d
   ```

## Structure de la Base de Données

La base de données comprend les tables suivantes :

- `users` : Stocke les informations des utilisateurs
- `modules` : Contient les détails des modules de formation
- `lessons` : Stocke les leçons individuelles au sein des modules
- `progress` : Suit la progression des utilisateurs dans les modules

## Sécurité

- Authentification basée sur JWT pour sécuriser l'accès à l'API
- Hachage des mots de passe avec bcrypt
- Validation des entrées côté serveur et côté client
- Protection CSRF dans les formulaires Symfony
- Utilisation de HTTPS pour toutes les communications

## Fonctionnalités

### Wireframes et Intégration

Les wireframes de l'application ont été conçus pour offrir une expérience utilisateur intuitive. L'intégration frontend suit fidèlement ces wireframes, en utilisant Tailwind CSS pour un design responsive et moderne.

### Authentification JWT

L'authentification utilise des tokens JWT (JSON Web Tokens) pour sécuriser l'accès à l'API. Le processus comprend :

1. Connexion de l'utilisateur avec email et mot de passe
2. Génération d'un token JWT côté serveur
3. Stockage du token côté client (localStorage)
4. Envoi du token dans le header Authorization pour chaque requête API

### Récupération des Modules

Les modules de formation sont récupérés via l'API une fois l'utilisateur authentifié. Le processus est le suivant :

1. Appel à l'endpoint `/api/modules` avec le token JWT
2. Récupération et affichage des modules disponibles
3. Mise à jour dynamique de l'interface utilisateur avec les données des modules

