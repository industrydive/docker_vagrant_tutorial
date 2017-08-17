FROM nginx:1.12.1


# remove the default conf file
RUN rm /etc/nginx/conf.d/default.conf
COPY tutorial.conf /etc/nginx/conf.d/tutorial.conf

VOLUME /srv/www
WORKDIR /srv/www
