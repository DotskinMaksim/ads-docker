# Используем официальный образ MySQL
FROM mysql:latest

# Указываем пароль для root пользователя
ENV MYSQL_ROOT_PASSWORD=123
ENV MYSQL_DATABASE=ads_database

# Копируем dump.sql в директорию, где MySQL ожидает файлы для инициализации
COPY init.sql /docker-entrypoint-initdb.d/

# Если хотите, можно добавить дополнительную настройку MySQL
# COPY my.cnf /etc/mysql/my.cnf

# Устанавливаем рабочую директорию
WORKDIR /docker-entrypoint-initdb.d/

# Все дальнейшие команды для запуска контейнера будут выполняться из этой директории






