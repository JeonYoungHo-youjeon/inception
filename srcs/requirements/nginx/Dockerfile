FROM alpine:3.16.4

RUN apk update && apk upgrade
RUN apk add nginx openssl

RUN openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj "/C=KR/ST=Seoul/L=Seoul/O=42Seoul/OU=Gon/CN=localhost" -out /etc/ssl/certs/youjeon.42.fr.crt -keyout /etc/ssl/private/youjeon.42.fr.key

RUN mkdir -p /var/www/html

COPY ./conf/default.conf /etc/nginx/http.d/default.conf
COPY ./tools/index.html /var/www/html/index.html

EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
