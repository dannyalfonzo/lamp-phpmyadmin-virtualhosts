FROM php:7.1-apache	
# or php:7.0-apache, php:5.6-apache @see https://github.com/docker-library/php

RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/ssl-cert-snakeoil.key -out /etc/ssl/certs/ssl-cert-snakeoil.pem -subj "/C=AT/ST=Vienna/L=Vienna/O=Security/OU=Development/CN=example.com"
RUN a2enmod ssl

RUN a2enmod rewrite

RUN apt-get update

RUN apt-get install libcurl3-dev libpng-dev libmcrypt-dev libxml2-dev libgd-dev libfreetype6-dev libldap2-dev libjpeg62-turbo-dev cron nano -y

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install mysqli pdo pdo_mysql curl gd mbstring gettext mcrypt xmlrpc soap intl zip xml

## para magento 2
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install ctype
RUN docker-php-ext-install dom
RUN docker-php-ext-install hash
RUN docker-php-ext-install simplexml
##RUN docker-php-ext-install spl

# Install XSL
RUN apt-get install -y libxslt-dev
RUN docker-php-ext-install xsl

RUN docker-php-ext-install json
RUN docker-php-ext-install iconv

# enable mail sending for php with sendmail
#RUN apt-get update && apt-get upgrade -y sendmail && rm -rf /var/lib/apt/lists/* && \
#    echo 'sendmail_path = "/usr/sbin/sendmail -t -i"' > /usr/local/etc/php/conf.d/mail.ini

#RUN echo "$(hostname)" >> /etc/mail/relay-domains
#RUN m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
#RUN echo "127.0.0.1 noreply.domain.com $(hostname)" >> /etc/hosts
#RUN service sendmail restart
