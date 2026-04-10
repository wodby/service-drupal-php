ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

ARG COPY_FROM
COPY --chown=wodby:wodby ${COPY_FROM} /var/www/html

ARG DOCROOT_SUBDIR
ARG DRUPAL_SITE
ARG DRUPAL_VERSION

ENV COMPOSER_CACHE_DIR=/home/wodby/.composer/cache

RUN --mount=type=cache,target=/home/wodby/.composer/cache \
    composer install -n --no-ansi --prefer-dist

RUN make init-drupal -f /usr/local/bin/actions.mk
