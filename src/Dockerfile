FROM alpine:latest

RUN apk update \
     && apk add nginx \
     && adduser -D -g 'www' www \
     && mkdir /www \
     && chown -R www:www /var/lib/nginx \
     && chown -R www:www /var/www 

RUN rm -rf /etc/nginx/nginx.conf \
    && rm -rf /var/www/index.html

COPY nginx.conf /etc/nginx/nginx.conf 
COPY index.html /www/index.html


EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]


