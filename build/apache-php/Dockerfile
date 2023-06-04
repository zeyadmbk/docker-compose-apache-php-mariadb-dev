FROM shinsenter/php:8.2-fpm-apache

ENV TZ=Europe/Amsterdam

RUN apt-get update -y
RUN apt-get install -y vim
RUN apt-get install -y git
RUN apt-get install -y curl
# Any other package needed for the app can be added here

# Install PHP Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install nodejs 18 and NPM
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
RUN apt-get install -y nodejs

# copy the custom Apache config/vhosts to the docker image
COPY vhosts.apache.conf /etc/apache2/sites-available/apache-custom.conf
# Disable the default vhost
RUN a2dissite 000-default
# Enable the new copied vhost config
RUN a2ensite apache-custom

# Change the owner of the source code directory
ADD --chown=webuser:webgroup . /var/www/html/src