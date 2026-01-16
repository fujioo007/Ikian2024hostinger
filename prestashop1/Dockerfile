# Utilise l'image officielle FrankenPHP + Apache
FROM ghcr.io/dunglas/frankenphp:2.3-apache

# Définir le répertoire de travail
WORKDIR /var/www/html

# Copier le code PrestaShop (optionnel si tu montes un volume)
COPY html/ /var/www/html/

# Installer les extensions PHP nécessaires à PrestaShop
RUN frankenphp-install \
    pdo_mysql \
    gd \
    mbstring \
    intl \
    zip \
    soap \
    xml \
    ctype \
    bcmath \
    json \
    curl \
    iconv

# Permissions
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html

# Exposer le port interne pour Traefik
EXPOSE 8000

# Active le mode DEV (optionnel)
ENV PS_DEV_MODE=1

# Commande par défaut (FrankenPHP gère Apache + PHP-FPM)
CMD ["frankenphp", "run", "--host=0.0.0.0", "--port=8000"]
