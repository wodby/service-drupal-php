# Drupal PHP services for Wodby

Use Drupal PHP as a reusable component in applications managed by Wodby. This
repository contains the service manifests and referenced files used by the
public Drupal PHP service entries in the Wodby catalog.

- [PHP (Drupal 11) service in the Wodby catalog](https://wodby.com/services/drupal11-php)
- [PHP (Drupal 10) service in the Wodby catalog](https://wodby.com/services/drupal10-php)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Service entries

### PHP (Drupal 11)

| Property | Manifest configuration |
| --- | --- |
| Service name | `drupal11-php` |
| Type | Application service |
| Inherits from | [`php`](https://github.com/wodby/service-php) with version constraint `^1.0.0` |
| Versions | `8.5` by default; also available: `8.3`, `8.4` |
| Workloads | `main` (Deployment), primary |
| Containers | `php` using `wodby/drupal-php`, build target |
| Service links | Files storage (`files`), required, Solr, optional, Redis, optional |
| Volumes | Files, 10 GB, shared, linked through `files` |
| Application build | Git source connection enabled; Dockerfile: `Dockerfile`; starters: Drupal CMS, Vanilla Drupal |
| Configuration | 2 settings, 2 generated or fixed tokens |
| Operations | 3 actions, 1 cron schedules |

Manifest: [`11/service.yml`](11/service.yml)

### PHP (Drupal 10)

| Property | Manifest configuration |
| --- | --- |
| Service name | `drupal10-php` |
| Type | Application service |
| Inherits from | [`php`](https://github.com/wodby/service-php) with version constraint `^1.0.0` |
| Versions | `8.4` by default; also available: `8.1`, `8.2`, `8.3` |
| Workloads | `main` (Deployment), primary |
| Containers | `php` using `wodby/drupal-php`, build target |
| Service links | Files storage (`files`), required, Solr, optional, Redis, optional |
| Volumes | Files, 10 GB, shared, linked through `files` |
| Application build | Git source connection enabled; Dockerfile: `Dockerfile`; starters: Vanilla Drupal |
| Configuration | 2 settings, 2 generated or fixed tokens |
| Operations | 3 actions, 1 cron schedules |

Manifest: [`10/service.yml`](10/service.yml)

## Use this service

A service is a reusable component and does not deploy by itself. Add the public
catalog service to a stack, configure its required links and settings, publish
the stack, and then create or upgrade an app instance.

To maintain your own version of this service:

1. Fork this repository.
2. Edit the service manifest and any files it references.
3. Import the repository as a
   [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference `drupal11-php`, `drupal10-php` from your stack manifest.

Wodby imports the manifest and referenced files from the selected Git branch or
tag and creates a new service revision when the Git-backed service is updated.

## Customize the service

Common changes include adjusting versions, images, Helm chart settings, build
inputs, environment variables, links, storage, resources, and operational
workflows supported by the manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time. These names are part of the contract consumed by
downstream manifests.

Validate customized manifests with the Wodby CLI before importing them:

```bash
wodby service validate-manifest 11/service.yml --org <org-id>
wodby service validate-manifest 10/service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/)
for every supported field and the [managed services
index](https://github.com/wodby/services) for more service examples.
