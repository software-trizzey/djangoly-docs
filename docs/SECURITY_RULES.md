# Djangoly Security Rules

This document tracks all the security rules enforced by Djangoly. Each rule has a unique code, a description, and a link to relevant documentation.

## Settings-Related Security Rules

| Rule Code | Rule Name                        | Description                                                                                                     | Documentation Link                                                                                  |
|-----------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| SEC01     | DEBUG_TRUE                        | DEBUG is set to True. Ensure it is False in production.                                                          | [Django Debug Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#debug)                   |
| SEC02     | HARDCODED_SECRET_KEY              | SECRET_KEY appears to be hardcoded. It is strongly recommended to store it in an environment variable.           | [Django Secret Key Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#secret-key)         |
| SEC03     | EMPTY_ALLOWED_HOSTS               | ALLOWED_HOSTS is empty. This is not secure for production.                                                       | [Django Allowed Hosts](https://docs.djangoproject.com/en/5.0/ref/settings/#allowed-hosts)            |
| SEC04     | WILDCARD_ALLOWED_HOSTS            | ALLOWED_HOSTS contains a wildcard '*'. This is not recommended for production.                                   | [Django Allowed Hosts](https://docs.djangoproject.com/en/5.0/ref/settings/#allowed-hosts)            |

## Cookie and Session Security Rules

| Rule Code | Rule Name                        | Description                                                                                                     | Documentation Link                                                                                  |
|-----------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| SEC05     | CSRF_COOKIE_SECURE_FALSE          | CSRF_COOKIE_SECURE is False. Set this to True to avoid transmitting the CSRF cookie over HTTP accidentally.      | [Django CSRF Cookie Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#csrf-cookie-secure)|
| SEC06     | SESSION_COOKIE_SECURE_FALSE       | SESSION_COOKIE_SECURE is False. Set this to True to avoid transmitting the session cookie over HTTP accidentally.| [Django Session Cookie Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#session-cookie-secure) |

## HSTS and HTTPS Security Rules

| Rule Code | Rule Name                            | Description                                                                                             | Documentation Link                                                                              |
|-----------|---------------------------------------|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| SEC07     | SECURE_SSL_REDIRECT_FALSE             | SECURE_SSL_REDIRECT is set to False. It should be True in production to enforce HTTPS.                   | [Django SSL Redirect](https://docs.djangoproject.com/en/5.0/ref/settings/#secure-ssl-redirect)   |
| SEC10     | SECURE_HSTS_SECONDS_NOT_SET           | SECURE_HSTS_SECONDS is set to 0. Set it to a positive value to enforce HTTPS.                            | [Django HSTS Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#secure-hsts-seconds)  |
| SEC11     | SECURE_HSTS_INCLUDE_SUBDOMAINS_IGNORED| SECURE_HSTS_INCLUDE_SUBDOMAINS is True, but it has no effect because SECURE_HSTS_SECONDS is 0.            | [Django HSTS Settings](https://docs.djangoproject.com/en/5.0/ref/settings/#secure-hsts-include-subdomains) |

## Raw SQL Security Rules

| Rule Code | Rule Name                        | Description                                                                                                     | Documentation Link                                                                                  |
|-----------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| SEC13     | RAW_SQL_USAGE                     | Avoid using 'raw' queries to execute raw SQL queries directly. This can bypass Django's ORM protections.         | [Django Raw SQL Usage](https://docs.djangoproject.com/en/5.0/topics/db/sql/#performing-raw-queries) |
| SEC14     | RAW_SQL_USAGE_WITH_CURSOR         | Avoid using 'connection.cursor()' to execute raw SQL queries directly.                                           | [Django Raw SQL Usage](https://docs.djangoproject.com/en/5.0/topics/db/sql/#performing-raw-queries) |

