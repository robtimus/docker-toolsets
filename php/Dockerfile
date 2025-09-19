ARG PHP_VERSION=8.4

FROM php:${PHP_VERSION}-cli-alpine

ARG COMPOSER_HOME=/usr/local/lib/composer
ARG XDEBUG_VERSION=3.4.2
ARG PHPSTAN_VERSION=2.1.28
ARG PHPCS_VERSION=3.13.4

COPY --from=composer:lts /usr/bin/composer /usr/bin/composer

RUN    apk add --no-cache --virtual .build-deps $PHPIZE_DEPS linux-headers \
    && pecl install xdebug-${XDEBUG_VERSION} \
    && apk del -f .build-deps \
    && apk add --no-cache git \
    && docker-php-ext-enable xdebug \
    && COMPOSER_HOME=${COMPOSER_HOME} composer global require phpstan/phpstan ${PHPSTAN_VERSION} \
    && COMPOSER_HOME=${COMPOSER_HOME} composer global require squizlabs/php_codesniffer ${PHPCS_VERSION} \
    ;

ENV PATH=$PATH:${COMPOSER_HOME}/vendor/bin

CMD ["sh"]
