FROM alpine:latest

RUN apk update \
     && apk add nginx \
     && adduser -D -g 'ngin' ngin \
     && mkdir -p /var/www \
     && chown -R ngin:ngin /var/lib/nginx \
     && chown -R ngin:ngin /var/www 

RUN rm -rf /etc/nginx/nginx.conf \
    && rm -rf /var/www/index.html

COPY nginx.conf /etc/nginx/nginx.conf 
COPY index.html /var/www/index.html


EXPOSE 80

STOPSIGNAL SIGTERM

CMD ["nginx", "-g", "daemon off;"]


