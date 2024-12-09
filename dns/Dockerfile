FROM ubuntu:latest

# Устанавливаем необходимые зависимости и BIND9
RUN apt-get clean && apt-get update && apt-get install -y bind9

# Настройка часового пояса
RUN ln -sf /usr/share/zoneinfo/Europe/Tallinn /etc/localtime && echo "Europe/Tallinn" > /etc/timezone

# Копируем конфигурационные файлы BIND9
COPY ./bind9 /etc/bind/

# Открываем порты для DNS (53/tcp и 53/udp)
EXPOSE 53/udp 53/tcp

# Запускаем процесс BIND9
CMD ["/usr/sbin/named", "-g"]
