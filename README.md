# 1Cert_XApps_nginx

Ce projet fournit une configuration Docker pour utiliser Nginx comme serveur reverse-proxy avec Certbot pour gérer les certificats SSL pour plusieurs applications.

## Table des Matières

- [Fonctionnalités](#fonctionnalités)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Configuration](#configuration)
- [Utilisation](#utilisation)
- [Remarques](#remarques)

## Fonctionnalités

- Utilisation de Nginx comme serveur reverse-proxy.
- Gestion automatique des certificats SSL avec Certbot.
- Prise en charge de plusieurs applications sur un seul domaine avec des chemins distincts.
- Configuration SSL sécurisée avec TLSv1.2 et v1.3.

## Prérequis

- Docker et Docker Compose installés sur votre machine.
- Accès à un domaine valide que vous pouvez utiliser pour obtenir des certificats SSL.

Clonez ce dépôt sur votre machine :

   ```bash
   git clone https://github.com/QuentinDerruau/1Cert_XApps_nginx.git
   cd 1Cert_XApps_nginx
   Modifiez les fichiers de configuration selon vos besoins, notamment en remplaçant {your-email} et {your-domain} dans docker-compose.yml et nginx.conf
   docker network create firstApp-network
   docker network create secondApp-network
   docker network create thirdApp-network
  ```

## Configuration
Fichier docker-compose.yml
Ce fichier définit deux services : nginx et certbot.

nginx : Construit à partir du Dockerfile et gère les requêtes HTTP et HTTPS.
certbot : Utilise l'image officielle Certbot pour obtenir et renouveler les certificats SSL.
Fichier Dockerfile
Le Dockerfile définit l'image Nginx personnalisée, en copiant les fichiers de configuration et les certificats nécessaires.

Fichier nginx.conf
Le fichier de configuration Nginx définit comment les requêtes sont gérées, en redirigeant le trafic HTTP vers HTTPS et en configurant les emplacements pour chaque application.

## Utilisation
Pour démarrer le projet, exécutez :

```bash
Copier le code
docker-compose up -d
```
Pour générer et obtenir des certificats SSL pour votre domaine, exécutez :

```bash 
Copier le code
docker-compose run --rm certbot
```
Vérifiez que Nginx est en cours d'exécution et que les certificats SSL sont correctement configurés.

## Remarques
Assurez-vous que votre domaine pointe vers l'adresse IP de votre serveur où Nginx est déployé.
Les certificats SSL sont automatiquement renouvelés. Vérifiez le bon fonctionnement des renouvellements en consultant les logs de Certbot.
