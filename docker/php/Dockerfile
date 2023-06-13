FROM php:8.1-fpm

# 必要なパッケージや拡張機能をインストール
RUN apt-get update \
    && apt-get install -y zlib1g-dev libzip-dev gnupg unzip git wget libfreetype6-dev libjpeg62-turbo-dev libpng-dev tzdata\
    && docker-php-ext-install zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# タイムゾーン設定
ENV TZ=Asia/Tokyo

# SQL SERVER 必須コンポーネントのインストール
#RUN apt-get update \
#    && apt-get install -y curl apt-transport-https \
#    && curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
#    && curl https://packages.microsoft.com/config/debian/10/prod.list > /etc/apt/sources.list.d/mssql-release.list \
#    && apt-get update \
#    && ACCEPT_EULA=Y apt-get install -y msodbcsql17 unixodbc-dev

# Microsoft SQL Server 用 PHP ドライバーのインストール
#RUN pecl install sqlsrv-5.11.0 pdo_sqlsrv-5.11.0 \
#    && docker-php-ext-enable sqlsrv pdo_sqlsrv

# Node.js , npm のインストール
#RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
#RUN apt-get install -y nodejs npm

# composer 2.4.4 インストール
COPY --from=composer:2.4.4 /usr/bin/composer /usr/bin/composer

WORKDIR "/var/www/html"

EXPOSE 8000
EXPOSE 8080
