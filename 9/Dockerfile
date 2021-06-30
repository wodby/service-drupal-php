ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

ARG COPY_FROM
COPY --chown=wodby:wodby ${COPY_FROM} /var/www/html

ARG DOCROOT_SUBDIR
ARG DRUPAL_FILES_SYNC_SALT
ARG DRUPAL_SITE
ARG DRUPAL_VERSION

# @todo return after docker update
#RUN make init-drupal -f /usr/local/bin/actions.mk
RUN if [[ -z "${DOCROOT_SUBDIR}" ]]; then export DRUPAL_ROOT="${APP_ROOT}"; else export DRUPAL_ROOT="${APP_ROOT}/${DOCROOT_SUBDIR}"; fi; \
    export DRUPAL_SITE_DIR="${DRUPAL_ROOT}/sites/${DRUPAL_SITE}"; \
    init_drupal
