FROM joshix/caddy:latest

COPY ./Caddyfile /var/www/html/Caddyfile
COPY ./index.html /var/www/html/index.html
COPY ./ssl/private.pem /var/www/html/server.key
COPY ./ssl/public.pem /var/www/html/server.crt

EXPOSE 2015 2378

WORKDIR /var/www/html
CMD ["/bin/caddy"]