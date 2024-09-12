# Djangoly Conventions
This document tracks all the validation and convention rules enforced by Djangoly. Each rule has a unique code, a description, and any additional relevant information.

## Security-related Rules (SEC)

| Rule Code | Rule Name | Description |
| --- | --- | --- |
| SEC01 | DEBUG_TRUE | DEBUG is set to True. Ensure it is False in production. |
| SEC02 | HARDCODED_SECRET_KEY | SECRET_KEY appears to be hardcoded. It is strongly recommended to store it in an environment variable. |
| SEC03 | EMPTY_ALLOWED_HOSTS | ALLOWED_HOSTS is empty. This is not secure for production. |
| SEC04 | WILDCARD_ALLOWED_HOSTS | ALLOWED_HOSTS contains a wildcard '*'. This is not recommended for production. |
| SEC05 | CSRF_COOKIE_SECURE_FALSE | CSRF_COOKIE_SECURE is False. Set this to True to avoid transmitting the CSRF cookie over HTTP accidentally. |
| SEC06 | SESSION_COOKIE_SECURE_FALSE | SESSION_COOKIE_SECURE is False. Set this to True to avoid transmitting the session cookie over HTTP accidentally. |
| SEC07 | SECURE_SSL_REDIRECT_FALSE | SECURE_SSL_REDIRECT is set to False. It should be True in production to enforce HTTPS. |
| SEC08 | X_FRAME_OPTIONS_NOT_SET | X_FRAME_OPTIONS is not set to a valid value. It should be either 'DENY' or 'SAMEORIGIN' to prevent clickjacking. |
| SEC09 | X_FRAME_OPTIONS_MISSING_MIDDLEWARE | X_FRAME_OPTIONS is set, but the XFrameOptionsMiddleware is missing from the MIDDLEWARE list. |
| SEC10 | SECURE_HSTS_SECONDS_NOT_SET | SECURE_HSTS_SECONDS is set to 0. Set it to a positive value to enforce HTTPS. |
| SEC11 | SECURE_HSTS_INCLUDE_SUBDOMAINS_IGNORED | SECURE_HSTS_INCLUDE_SUBDOMAINS is True, but it has no effect because SECURE_HSTS_SECONDS is 0. |
| SEC12 | SECURE_HSTS_INCLUDE_SUBDOMAINS_FALSE | SECURE_HSTS_INCLUDE_SUBDOMAINS is set to False. Set it to True for better security. |
| SEC13 | RAW_SQL_USAGE | Avoid using 'raw' queries to execute SQL directly, bypassing Django's ORM protections. |
| SEC14 | RAW_SQL_USAGE_WITH_CURSOR | Avoid using 'connection.cursor()' to execute SQL directly, bypassing Django's ORM protections. |

## Complexity-related Rules (CMP)

| Rule Code | Rule Name | Description | Additional Info |
| --- | --- | --- | --- |
| CMP01 | COMPLEX_VIEW | Identifies overly complex views. | - |
| CMP02 | FUNCTION_COMPLEXITY | Checks if function complexity exceeds a defined threshold. | - |

## Code Quality-related Rules (CDQ)

| Rule Code | Rule Name | Description | Additional Info |
| --- | --- | --- | --- |
| CDQ01 | NO_EXCEPTION_HANDLER | Checks for the presence of exception handlers in views. | - |
| CDQ02 | NAME_TOO_SHORT | Names (variables, functions, object properties) should be at least 3 characters long (excluding leading underscores). | Applies to all variables, function names, object properties, etc. Excludes 'id' for object properties. |
| CDQ03 | FUNCTION_NAME_NO_VERB | Function names should include a verb to describe the action. | Applies to regular functions, Django model methods, serializer methods, view methods, and testcase methods |
| CDQ04 | FUNCTION_TOO_LONG | Functions should not exceed a specified number of lines. | The maximum allowed length is configurable |
| CDQ05 | CLASS_NAME_CONVENTION | Class names should follow specific naming conventions. | - |
| CDQ06 | LIST_NAME_CONVENTION | List names should follow specific naming conventions. | - |
| CDQ07 | DICTIONARY_VALIDATION | Dictionaries should follow specific validation rules. | - |
| CDQ08 | FOR_LOOP_TARGET_VALIDATION | For loop targets should follow specific validation rules. | - |
| CDQ09 | DJANGO_MODEL_FIELD_NAMING | Django model fields should follow variable naming conventions. | - |
| CDQ10 | DJANGO_SERIALIZER_FIELD_NAMING | Django serializer fields should follow variable naming conventions. | - |
| CDQ11 | DJANGO_FIELD_CONVENTIONS | Django fields should follow specific conventions. | - |
| CDQ12 | COMMENT_VALIDATION | Processes and validates leading comments. | - |
| CDQ13 | CELERY_TASK_VALIDATION | Performs checks related to Celery tasks. | - |
| CDQ14 | REDUNDANT_QUERY_METHODS | Identifies redundant QuerySet method chains, such as `all().filter()` or `filter().all()`. These chains are unnecessary because the final method in the chain provides the desired result. Simplified queries avoid redundant operations, resulting in cleaner and easier-to-maintain code. | Refer to Django's [QuerySet API documentation](https://docs.djangoproject.com/en/stable/ref/models/querysets/) for more information. |

## Style-related Rules (STY)

| Rule Code | Rule Name | Description | Additional Info |
| --- | --- | --- | --- |
| STY01 | BOOLEAN_VARIABLE_PREFIX | Boolean variables should use required prefixes. | Prefixes are configurable in settings |
| STY02 | BOOLEAN_VARIABLE_POSITIVE_NAMING | Boolean variables should use positive naming (avoid negative patterns). | - |
| STY03 | BOOLEAN_PROPERTY_PREFIX | Boolean object properties should use required prefixes. | Prefixes are configurable in settings |
| STY04 | BOOLEAN_PROPERTY_POSITIVE_NAMING | Boolean object properties should use positive naming (avoid negative patterns). | - |

## Configuration-related Rules (CFG)

| Rule Code | Rule Name | Description | Additional Info |
| --- | --- | --- | --- |
| CFG01 | RESERVED_SYMBOL_HANDLING | Skips validation for symbols marked as reserved. | - |
