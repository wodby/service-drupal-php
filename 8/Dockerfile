ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

FROM wodby/ci-cache as cache
COPY --from=cache --chown=wodby:wodby /cache/.composer/cache $HOME/.composer/cache

ARG COPY_FROM
COPY --chown=wodby:wodby ${COPY_FROM} /var/www/html

## COMMANDS

## INIT

ARG DOCROOT_SUBDIR
ARG DRUPAL_FILES_SYNC_SALT
ARG DRUPAL_SITE
ARG DRUPAL_VERSION

RUN make init-drupal
