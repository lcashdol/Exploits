FROM ubuntu:latest

# Install apache, PHP
RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -y install \
    apache2 php7.2 libapache2-mod-php7.2 wget tar unzip git

# Enable apache mods.
RUN a2enmod php7.2
RUN a2enmod rewrite
RUN a2enmod headers

# Update the PHP.ini file, enable <? ?> tags and quieten logging.
RUN sed -i "s/short_open_tag = Off/short_open_tag = On/" /etc/php/7.2/apache2/php.ini
RUN sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.2/apache2/php.ini

# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Expose apache.
EXPOSE 80

# Install releases
RUN cd /var/www/html && \
     git clone https://github.com/hayageek/jquery-upload-file && mkdir -p /var/www/html/jquery-upload-file/php/uploads

    
RUN chown -R www-data:www-data /var/www/html

# By default start up apache in the foreground, override with /bin/bash for interative.
CMD /usr/sbin/apache2ctl -D FOREGROUND
