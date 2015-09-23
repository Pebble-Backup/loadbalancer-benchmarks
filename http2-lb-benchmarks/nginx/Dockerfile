FROM nginx:1.9.5
RUN mkdir -p /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./index.html /usr/share/nginx/html/index.html
COPY ./ssl/private.pem /etc/nginx/server.key
COPY ./ssl/public.pem /etc/nginx/server.crt

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]