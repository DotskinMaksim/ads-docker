FROM nginx:latest

RUN ln -sf /usr/share/zoneinfo/Europe/Tallinn /etc/localtime && echo "Europe/Tallinn" > /etc/timezone


COPY nginx.conf /etc/nginx/nginx.conf
COPY ./sites-available /etc/nginx/sites-available

RUN mkdir -p /etc/nginx/sites-enabled && \
    ln -s /etc/nginx/sites-available/advertisements-service /etc/nginx/sites-enabled/

RUN git clone https://github.com/DotskinMaksim/advertisements-service.git  ./site/
COPY ./site/advertisements-service /var/www/advertisements-service
RUN chmod -R 755 /var/www/ && \
    chmod -R 755 /etc/nginx/sites-available && \
    chmod -R 755 /etc/nginx/sites-enabled

RUN if [ -f /etc/nginx/sites-enabled/default ]; then rm /etc/nginx/sites-enabled/default; fi

CMD ["nginx", "-g", "daemon off;"]