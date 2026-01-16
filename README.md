
# Ikian2024hostinger

**ONLY for DEV, not for production**

A very simple Docker-compose to discover Symfony 6 with PHP 8.0.13 in 5 minutes
## Run Locally

Lister les réseaux Docker existants
```bash
gdocker network ls
```
ou Tu peux filtrer pour le réseau web :
```bash
docker network ls | grep web
```

Créer le réseau si nécessaire
```bash
docker network create web
```

Se connecter au git 
```bash
git remote set-url origin git@github.com:fujioo007/Ikian2024hostinger.git
```

Mettre à jour le git d'apres le dossier local
```bash
git add .
git commit -m "Description des changements"
git push

```
Générer le certificat auto-signé (DEV)

```bash
mkdir -p traefik/certs
```
Puis :
```bash
openssl req -x509 -nodes -days 365 \
  -newkey rsa:2048 \
  -keyout traefik/certs/dev.key \
  -out traefik/certs/dev.crt \
  -subj "/CN=dev.local"
```
Tu obtiens :

dev.crt

dev.key


Clone the project

```bash
  git@github.com:yoanbernabeu/symfony6-php8-in-docker-compose.git
```

Run the docker-compose

```bash
  docker-compose build
  docker-compose up -d
```

Log into the PHP container

```bash
  docker exec -it php8-sf6 bash
```

Create your Symfony application and launch the internal server

```bash
  symfony new new-project --full
  cd new-project
  symfony serve -d
```

Create an account (identical to your local session)

```bash
  adduser username
  chown username:username -R .
```

*Your application is available at http://127.0.0.1:9000*

If you need a database, modify the .env file like this example:

```yaml
  DATABASE_URL="postgresql://symfony:ChangeMe@database:5432/app?serverVersion=13&charset=utf8"
```

## Ready to use with

This docker-compose provides you :

- PHP-8.0.13-cli (Debian)
    - Composer
    - Symfony CLI
    - and some other php extentions
    - nodejs, npm, yarn
- postgres:13-alpine
- mailcatcher


## Requirements

Out of the box, this docker-compose is designed for a Linux operating system, provide adaptations for a Mac or Windows environment.

- Linux (Ubuntu 20.04 or other)
- Docker
- Docker-compose
## Author

- [@fujioo007](https://github.com/fujioo007)
