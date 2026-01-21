# FrankenPHP avec PHP 8.2
FROM ghcr.io/fabianmichael/frankenphp:8.2

# Dossier de travail
WORKDIR /var/www/html

# Variables PrestaShop (install auto)
ENV PS_DEV_MODE=1 \
    PS_INSTALL_AUTO=1 \
    PS_ERASE_DB=0 \
    PS_DOMAIN=shop1.dev.local \
    PS_FOLDER_ADMIN=admin \
    PS_FOLDER_INSTALL=install \
    ADMIN_MAIL=admin@shop1.dev.local \
    ADMIN_PASSWD=admin123

# Copier les fichiers PrestaShop
COPY html/ /var/www/html/

# Extensions PHP requises par PrestaShop 9
RUN frankenphp-extension-install \
    mysqli \
    pdo_mysql \
    gd \
    intl \
    curl \
    mbstring \
    soap \
    xml \
    zip \
    json \
    opcache

# Permissions nécessaires à PrestaShop
RUN chown -R www-data:www-data /var/www/html \
 && chmod -R 755 /var/www/html

# Port exposé pour Traefik
EXPOSE 8000

# Lancer FrankenPHP
CMD ["frankenphp", "-S", "0.0.0.0:8000", "-t", "/var/www/html"]
