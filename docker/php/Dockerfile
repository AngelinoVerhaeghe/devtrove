# Dockerfile voor de PHP container
FROM php:8.3-fpm

# Installeer systeemafhankelijkheden
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libzip-dev \
    unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql zip

# Stel de werkdirectory in
WORKDIR /var/www

# Kopieer de bestaande code naar de container
COPY . .

# Installeer Composer (optioneel)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Expose de poort
EXPOSE 9000

CMD ["php-fpm"]
