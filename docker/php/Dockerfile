FROM php:8.0-fpm
SHELL ["/bin/bash", "-c"]
RUN  apt update
RUN apt install p7zip-full -y
RUN apt install git -y
RUN apt install nano -y
RUN apt install unzip -y
RUN apt install libzip-dev -y
RUN apt install libmcrypt-dev -y
RUN apt install wget -y
RUN pecl install mcrypt-1.0.4 
RUN docker-php-ext-enable mcrypt
RUN docker-php-ext-install \pdo_mysql
ENV docker-php-ext-configure zip --with-libzip
RUN docker-php-ext-install \zip
#RUN docker-php-ext-install \mcrypt 
RUN cd /usr/local/bin
RUN curl -sS https://getcomposer.org/installer | php -- \
--install-dir=/usr/bin --filename=composer.phar
RUN mv /usr/bin/composer.phar /usr/local/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN cd /var/www/ && composer create-project laravel/laravel laravelproject
#RUN composer config -g allow-plugins.kylekatarnls/update-helper true
#RUN composer create-project laravel/laravel /var/www/inventory 4.2.* --prefer-dist
#ENV PATH=$PATH:$HOME:~/.composer/vendor/bin
#RUN cd /var/www/ && curl -OL https://github.com/laravel/laravel/archive/v4.2.11.zip && unzip *.zip -d temp && mkdir /var/www/inventory 
#&& mv /var/www/temp/* /var/www/123/
#COPY ./ /var/www/temp  
#RUN ./vendor/bin/upgrade-carbon
#RUN cd /var/www/ && wget full_url_to_raw_file_on_github https://github.com/laravel/laravel/archive/v4.2.11.zip 
