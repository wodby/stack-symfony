# Symfony application stack for Kubernetes on Wodby

Deploy Symfony applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for Symfony.

<!-- wodby:generated:start -->

## Stack contract

- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a boilerplate

Use one of the compatible boilerplates exposed by this stack's services to
start with Wodby CI build configuration:

- [Symfony on Wodby](https://github.com/wodby/symfony-boilerplate)

## Service definitions

- [PHP (Symfony) service](https://github.com/wodby/service-symfony-php)
- [Nginx (PHP) service](https://github.com/wodby/service-php-nginx)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [Mailpit service](https://github.com/wodby/service-mailpit)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)
- [Cloud PostgreSQL service](https://github.com/wodby/service-cloud-postgres)

## What's included

| Component / service | Default configuration |
| --- | --- |
| PHP<br>`php` | required; enabled by default; links: `db` → `postgres`, `sendmail` → `mailpit` |
| Nginx<br>`nginx` | required; enabled by default; links: `backend` → `php` |
| PostgreSQL<br>`postgres` | required; enabled by default; volumes: `data` 20 GB |
| Mailpit<br>`mailpit` | optional; enabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |
| Cloud PostgreSQL<br>`cloud-postgres` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Start from [Symfony on Wodby](https://github.com/wodby/symfony-boilerplate),
which includes `.wodby/pipeline.yml`, or connect your own compatible source
repository.

The PHP service supports development workspaces: create an environment as a
workspace to edit the code over SSH, with dependencies installed and
migrations applied during setup.

Review service versions, storage, links, and optional components when creating
the application. The same stack can be reused across development, staging, and
production environments.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
