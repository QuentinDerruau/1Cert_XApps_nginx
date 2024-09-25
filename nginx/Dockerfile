FROM nginx:latest

COPY nginx.conf /etc/nginx/nginx.conf

COPY ./data/certbot/conf /etc/letsencrypt
COPY ./data/certbot/www /var/www/certbot

EXPOSE 80
EXPOSE 443