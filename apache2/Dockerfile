FROM docker.io/httpd:2.4.59-alpine3.20

# Argument definitions
ARG UID=1000
ARG GID=1000

# Install shadow package for deluser and addgroup
# RUN apk add --no-cache shadow

# Remove the existing www-data user, if it exists
RUN deluser www-data 2>/dev/null || true

# Create group and user with specified UID and GID
RUN addgroup -g ${GID} www-data \
    && adduser -u ${UID} -G www-data -h /home/www-data -s /sbin/nologin -D www-data

# Set permissions for the Apache directory
RUN chown -R www-data:www-data /usr/local/apache2 && \
    chmod -R 755 /usr/local/apache2

# Set the user to www-data
USER www-data

# Expose ports 80 and 443
EXPOSE 80 443

# Run Apache in the foreground
CMD ["httpd-foreground"]
