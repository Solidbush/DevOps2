# образ Alpine
FROM alpine:latest

# необходимые пакеты
RUN apk add --no-cache nginx

# пользователь
RUN addgroup -S nginxgroup && adduser -S nginxuser -G nginxgroup

# необходимые директории и права
RUN mkdir -p /var/lib/nginx/tmp/client_body \
    /var/lib/nginx/tmp/proxy \
    /var/lib/nginx/tmp/fastcgi \
    /var/lib/nginx/tmp/uwsgi \
    /var/lib/nginx/tmp/scgi \
    /var/log/nginx \
    /run/nginx \
    && chown -R nginxuser:nginxgroup /var/lib/nginx /var/log/nginx /run/nginx

# конфигурация nginx из внешнего источника
COPY nginx.conf /etc/nginx/nginx.conf

# каталог для статических файлов
RUN mkdir -p /var/www/html && chown -R nginxuser:nginxgroup /var/www/html

# порт
EXPOSE 8080

USER nginxuser

CMD ["nginx", "-g", "daemon off;"]