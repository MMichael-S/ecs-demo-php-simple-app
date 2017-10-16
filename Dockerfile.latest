# Amazon ECS PHP Simple Demo App
# Dockerfile for latest apache & php version
FROM ubuntu

# Install dependencies
RUN apt-get update -y
RUN apt-get install -y git curl apache2 php libapache2-mod-php php-mcrypt php-mysql

# Install app
RUN rm -rf /var/www/*

# Update /var/www to /var/www/html
ADD src /var/www/html

# Configure apache
RUN a2enmod rewrite
RUN chown -R www-data:www-data /var/www

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

# env add by fshi from apache env file --> /etc/apache2/envvars
ENV APACHE_PID_FILE /var/run/apache2/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2

EXPOSE 80

CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]
