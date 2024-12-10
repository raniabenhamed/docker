# Projet Docker et WSL

## Description
Ce projet a pour but de mettre en place un environnement Docker et WSL (Windows Subsystem for Linux) pour apprendre et tester la conteneurisation. Il inclut plusieurs étapes pour configurer, utiliser et expérimenter avec Docker et WSL.

## Fonctionnalités principales
1. Activation de WSL et installation de Docker.
2. Test de Docker avec des images simples.
3. Création de conteneurs personnalisés avec Dockerfile.
4. Utilisation et gestion des volumes Docker pour la persistance des données.
5. Ajout d'alias pratiques pour faciliter l'utilisation de Docker.

## Prérequis
- **Windows 10/11**
- WSL (Windows Subsystem for Linux)
- Docker installé et fonctionnel

## Installation et configuration rapide
Consultez le [guide d'installation](docs/guide_installation.md) pour une procédure détaillée.

## Utilisation
Après l'installation, vous pouvez consulter le [guide d'utilisation](docs/guide_utilisation.md) pour explorer les différentes fonctionnalités du projet.

## Structure du projet
```plaintext
MonProjet/
├── README.md          # Description et guide du projet
├── Dockerfile         # Fichier Docker pour les conteneurs personnalisés
├── scripts/           # Scripts Bash pour automatiser certaines tâches
├── docs/              # Documentation détaillée
│   ├── guide_installation.md
│   └── guide_utilisation.md
├── config/            # Fichiers de configuration (ex. .bashrc modifié)
└── .gitignore         # Fichiers à ignorer pour le versioning



