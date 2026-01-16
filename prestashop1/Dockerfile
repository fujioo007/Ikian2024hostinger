# FrankenPHP avec PHP 8.4
FROM ghcr.io/fabianmichael/frankenphp:8.4

WORKDIR /var/www/html

# Copier les fichiers PrestaShop téléchargés
COPY html/ /var/www/html/

# Installer les extensions PHP nécessaires pour PrestaShop 9
RUN frankenphp-extension-install mysqli gd intl ctype curl mbstring soap xml zip json opcache pdo_mysql

# Permissions
RUN chown -R www-data:www-data /var/www/html

# Expose le port pour Traefik
EXPOSE 8000

# Lancer FrankenPHP
CMD ["frankenphp", "-S", "0.0.0.0:8000", "-t", "/var/www/html"]
