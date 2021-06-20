FROM php:7.2
RUN docker-php-ext-install pdo_mysql
RUN apt-get update
RUN apt-get install -y git unzip mariadb-client 
WORKDIR /app
COPY ./composer.json ./
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN composer install
EXPOSE 8000
CMD wait 10; ./webapp/sql/init.sh; cd /app/webapp/php; composer start
