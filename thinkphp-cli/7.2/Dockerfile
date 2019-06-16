FROM php:7.2-cli
ENV COMMAND_NAME think

RUN docker-php-ext-install -j$(nproc) iconv pdo_mysql mysqli bcmath mysqli sockets bcmath
#RUN  docker-php-ext-install -j$(nproc) gd

RUN pecl install redis-4.0.1 \
    && docker-php-ext-enable redis\

RUN apt-get update && apt-get install -y --no-install-recommends zlib1g-dev\
    && pecl install memcached-3.1.2 \
    && pecl install memcache-2.2.7 \
    && docker-php-ext-enable memcached memcache

RUN docker-php-source delete

WORKDIR /php/
VOLUME /php/
CMD php ${COMMAND_NAME}
