# CoffeeShop

![PHP](https://img.shields.io/badge/PHP-%3E%3D%208.4-777BB4?logo=php&logoColor=white)
![Symfony](https://img.shields.io/badge/Symfony-8.1-black?logo=symfony&logoColor=white)
![Twig](https://img.shields.io/badge/Twig-3.x-8BC34A?logo=twig&logoColor=white)
![Doctrine ORM](https://img.shields.io/badge/Doctrine%20ORM-3.x-FC6A31)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql&logoColor=white)
![Stimulus](https://img.shields.io/badge/Stimulus-3.x-77E8B9?logo=stimulus&logoColor=black)
![Turbo](https://img.shields.io/badge/Hotwire%20Turbo-8.x-4A4A4A)
![Docker Compose](https://img.shields.io/badge/Docker%20Compose-configured-2496ED?logo=docker&logoColor=white)
![Licence](https://img.shields.io/badge/Licence-propri%C3%A9taire-lightgrey)

Projet pédagogique de BTS consacré à la création d’un site vitrine de vente de café avec Symfony. Le site a vocation à présenter un catalogue de cafés, sans permettre leur achat en ligne.

> **État du projet :** le dépôt contient actuellement le socle Symfony et sa configuration. Les pages et fonctionnalités métier décrites ci-dessous constituent les objectifs du projet ; elles ne sont pas encore implémentées dans cette version.

## Sommaire

- [Parties et objectifs](#parties-et-objectifs)
- [Fonctionnalités visées](#fonctionnalités-visées)
- [Technologies](#technologies)
- [Prérequis](#prérequis)
- [Installation et lancement](#installation-et-lancement)
- [Structure du dépôt](#structure-du-dépôt)
- [Tests](#tests)

## Parties et objectifs

### Partie 1 — Structure et intégration

Cette première partie porte sur la mise en place du projet Symfony, la découverte de Twig, la création des templates et des assets, ainsi que le routage et la navigation entre les pages.

Le design s’inspire du thème [Coffee Seven](https://coffee-seven-ivory.vercel.app/), à adapter avec une identité visuelle propre au projet et à l’univers du café.

### Suite du projet

Le socle doit ensuite accueillir les pages et comportements du site décrits dans les spécifications fonctionnelles. Leur implémentation est à suivre dans le dépôt.

## Fonctionnalités visées

- **Accueil** : bannière ou slider avec titre, description et bouton ; présentation de la boutique ; cafés tendance ; témoignages clients ; pied de page avec les coordonnées.
- **Nos produits** : présentation des cafés et formulaire de filtrage par marque, catégorie et prix.
- **Nous contacter** : formulaire avec nom, prénom, e-mail, téléphone et message.
- **Pas de vente en ligne** : le catalogue présente les produits, sans panier ni paiement.

## Technologies

- **PHP 8.4 ou supérieur** et **Symfony 8.1** pour l’application.
- **Twig** pour le rendu des pages côté serveur.
- **Doctrine ORM 3** et **Doctrine Migrations** sont installés pour la persistance et les évolutions de schéma.
- **PostgreSQL 16** comme base de données de développement via Docker Compose.
- **AssetMapper**, **Stimulus** et **Turbo** pour la gestion des assets et les interactions côté navigateur.
- **PHPUnit 13** pour les tests.
- **Mailpit** est également déclaré dans la configuration Docker Compose pour le développement local du courrier.

## Prérequis

- PHP **8.4+** avec les extensions `ctype` et `iconv`.
- [Composer](https://getcomposer.org/).
- [Docker Compose](https://docs.docker.com/compose/).
- [Symfony CLI](https://symfony.com/download) pour lancer le serveur de développement avec `symfony serve`.

## Installation et lancement

Depuis la racine du dépôt :

1. Installer les dépendances PHP :

   ```bash
   composer install
   ```

2. Démarrer les services de développement :

   ```bash
   docker compose up -d
   ```

   La configuration démarre PostgreSQL et Mailpit. Les ports hôte peuvent être attribués automatiquement ; consultez-les avec :

   ```bash
   docker compose ps
   ```

3. Vérifier la variable `DATABASE_URL` dans `.env`. Si le port PostgreSQL publié sur votre machine n’est pas `5432`, créez un fichier `.env.local` à la racine et ajustez-y cette variable. Exemple pour un port hôte `5432` :

   ```dotenv
   DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"
   ```

   Les identifiants par défaut sont réservés au développement local : configurez des identifiants sûrs pour tout autre environnement. Ne versionnez pas `.env.local`.

4. Lancer le serveur Symfony :

   ```bash
   symfony serve
   ```

   Le terminal indique l’adresse locale à ouvrir dans le navigateur. À ce stade du dépôt, les pages métier ne sont pas encore présentes.

## Structure du dépôt

```text
assets/       JavaScript, CSS et contrôleurs Stimulus
bin/          Points d’entrée des commandes Symfony et PHPUnit
config/       Configuration Symfony et des bundles
migrations/   Migrations Doctrine (à ajouter avec l’évolution du schéma)
public/       Point d’entrée HTTP de l’application
src/          Code PHP de l’application
templates/    Templates Twig
tests/        Configuration et futurs tests du projet
translations/ Fichiers de traduction
compose.yaml  Services de développement (PostgreSQL, Mailpit)
```

## Tests

Lancer la suite PHPUnit avec :

```bash
php bin/phpunit
```

Le répertoire `tests/` ne contient pour l’instant que le bootstrap de test ; les tests fonctionnels et unitaires restent à écrire au fur et à mesure de l’implémentation.
