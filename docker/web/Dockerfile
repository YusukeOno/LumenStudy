FROM ubuntu:18.04

LABEL maintainer "YusukeOno <y-ono@nswt.co.jp>"

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -yq --no-install-recommends \
    apt-utils \
    curl \
    vim \
    # Install git
    git \
    # Install apache
    apache2 \
    # Install php 7.2
    libapache2-mod-php7.2 \
    php7.2-cli \
    php7.2-json \
    php7.2-curl \
    php7.2-fpm \
    php7.2-gd \
    php7.2-ldap \
    php7.2-mbstring \
    php7.2-mysql \
    php7.2-soap \
    php7.2-sqlite3 \
    php7.2-xml \
    php7.2-zip \
    php7.2-intl \
    # Install tools
    openssl \
    locales \
    unzip \
    ca-certificates \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set locales
RUN locale-gen ja_JP.UTF-8

EXPOSE 80 443

WORKDIR /app

COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf

CMD apachectl -D FOREGROUND 
