ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

ARG COPY_FROM
COPY --chown=wodby:wodby ${COPY_FROM} /var/www/html

ARG DOCROOT_SUBDIR
ARG DRUPAL_SITE
ARG DRUPAL_VERSION

RUN make init-drupal -f /usr/local/bin/actions.mk
