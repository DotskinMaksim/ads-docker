FROM nginx:latest

# Настройка часового пояса
RUN ln -sf /usr/share/zoneinfo/Europe/Tallinn /etc/localtime && echo "Europe/Tallinn" > /etc/timezone

# Установка зависимостей для composer и npm
RUN apt-get update && apt-get install -y \
    curl \
    unzip \
    git \
    php-fpm \
    php-cli \
    php-mbstring \
    php-xml \
    nodejs \
    npm && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Копирование конфигураций Nginx
COPY nginx.conf /etc/nginx/nginx.conf
COPY ./sites-available /etc/nginx/sites-available

# Настройка Nginx
RUN mkdir -p /etc/nginx/sites-enabled && \
    ln -s /etc/nginx/sites-available/advertisements-service /etc/nginx/sites-enabled/

# Копирование сайта в контейнер
COPY ./site/advertisements-service /var/www/advertisements-service

# Установка прав
RUN chmod -R 755 /var/www/ && \
    chmod -R 755 /etc/nginx/sites-available && \
    chmod -R 755 /etc/nginx/sites-enabled
RUN if [ -f /etc/nginx/sites-enabled/default ]; then rm /etc/nginx/sites-enabled/default; fi
# Выполнение composer install и npm install
WORKDIR /var/www/advertisements-service
RUN composer install

#

# Запуск Nginx
CMD ["nginx", "-g", "daemon off;"]
