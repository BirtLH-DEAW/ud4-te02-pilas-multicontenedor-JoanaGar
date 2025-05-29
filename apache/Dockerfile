FROM ubuntu:22.04

RUN apt-get update && apt-get -y install apache2 libapache2-mod-fcgid \
    && a2enmod proxy_fcgi \
    && apt-get install -y git \
    && GIT_SSL_NO_VERIFY=true git clone https://github.com/deaw-birt/UD4-despliegue-PHP.git /apache/UD4-despliegue-PHP \
    && cp -r /apache/UD4-despliegue-PHP/* /var/www/html/ \
    && rm -R /apache/UD4-despliegue-PHP

COPY 000-default.conf /etc/apache2/sites-available
COPY index.php dwes.css /var/www/html/

EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]