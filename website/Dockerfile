FROM ubuntu:12.04

MAINTAINER Sai sz281234@dal.ca

RUN apt-get update && apt-get install -y apache2 && apt-get clean 

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

EXPOSE 80/tcp

COPY index.html /var/www/

CMD ["usr/sbin/apache2","-D","FOREGROUND"]
