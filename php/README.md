# php-toolset

A Docker image containing PHP, composer and a small set of tools:

* git
* [xdebug](https://xdebug.org/)
* [phpstan](https://github.com/phpstan/phpstan) (not for PHP 5.x)
* [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)

To run the image, call Docker as follows:

```
docker run -v <local-project-dir>:<project-dir> -w <project-dir> robtimus/php-toolset
```

This will open a shell at `<project-dir>`, that allows you to execute your standard set of commands like `composer install`, `phpstan`  and `phpcs`.

## ApiGen

[ApiGen](https://github.com/apigen/apigen) is not included because no stable version is available for PHP 8.x at the time of writing. Use [apigen/apigen](https://hub.docker.com/r/apigen/apigen) instead.
