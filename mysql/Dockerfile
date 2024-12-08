FROM mysql:8.0

RUN ln -sf /usr/share/zoneinfo/Europe/Tallinn /etc/localtime && echo "Europe/Tallinn" > /etc/timezone


ENV MYSQL_ROOT_PASSWORD=123
ENV MYSQL_DATABASE=ads_db
ENV MYSQL_USER=dotskin
ENV MYSQL_PASSWORD=123


COPY create_user.sql /docker-entrypoint-initdb.d/


WORKDIR /var/lib/mysql


EXPOSE 3306