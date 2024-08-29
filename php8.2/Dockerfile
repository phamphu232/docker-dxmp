# Stage 1: Build
FROM docker.io/php:8.2.20-fpm-alpine3.20 AS build
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod 0755 /usr/local/bin/install-php-extensions
RUN install-php-extensions bcmath gd intl imap odbc opcache pdo_mysql pdo_sqlsrv sockets zip

# # Stage 2: Final
# FROM docker.io/php:8.2.20-fpm-alpine3.20
# COPY --from=build /usr/local/etc/php /usr/local/etc/php
# COPY --from=build /usr/local/lib/php/extensions /usr/local/lib/php/extensions
# COPY --from=build /usr/local/bin/install-php-extensions /usr/local/bin/install-php-extensions
# COPY --from=build /usr/lib /usr/lib
RUN docker-php-ext-enable bcmath gd intl imap odbc opcache pdo_mysql pdo_sqlsrv sockets zip
ARG UID=1000
ARG GID=1000
RUN deluser www-data 2>/dev/null || true
RUN addgroup -g ${GID} www-data \
    && adduser -u ${UID} -G www-data -h /home/www-data -s /sbin/nologin -D www-data
EXPOSE 9000
CMD ["php-fpm"]