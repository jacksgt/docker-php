FROM php:7.2-fpm-stretch

# Install OS dependencies
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get install --no-install-recommends -y \
    libldap2-dev \
    zlib1g-dev \
    libc-client-dev \
    libkrb5-dev \
    libpng-dev \
    libpq-dev \
    && apt-get autoclean; apt-get autoremove && \
    rm -rf /var/lib/apt/lists/*

# Link LDAP library for PHP ldap extension
RUN ln -fs /usr/lib/x86_64-linux-gnu/libldap.so /usr/lib/

RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl

# Install PHP Plugins
RUN docker-php-ext-install \
    gd \
    imap \
    ldap \
    mbstring \
    pdo \
    pdo_mysql \
    pdo_pgsql \
    pgsql \
    zip
