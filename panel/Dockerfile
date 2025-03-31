FROM ghcr.io/blueprintframework/blueprint:latest

RUN wget https://github.com/JasonHorkles/darkenate/releases/download/v2.0.2/darkenate.blueprint 
RUN blueprint -install darkenate.blueprint
RUN rm darkenate.blueprint

COPY plugins/modpackinstaller.blueprint .
COPY plugins/egg-minecraft--java-edition-modpack-installer.json /app/database/Seeders/eggs/minecraft
RUN blueprint -install modpackinstaller.blueprint
RUN rm modpackinstaller.blueprint

RUN echo "" >> /etc/supervisord.conf && \
    cat >> /etc/supervisord.conf <<'EOF'

[program:user_init]
command=bash -c 'php artisan p:user:make --quiet --no-interaction --email $APP_SERVICE_AUTHOR --name-first "Default" --name-last "User" --password password --username $APP_SERVICE_AUTHOR --admin 1'
user=root
autostart=true
autorestart=false

[program:php_optim]
directory=/app
command=bash -c 'php artisan config:clear && php artisan optimize'
user=root
autostart=true
autorestart=false
EOF