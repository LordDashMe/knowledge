# Pipelines PHP and Coveralls

Bitbucket pipelines example for PHP with phpunit and xdebug configuration.

Add this yml file in your repo usually the name is ```bitbucket-pipelines.yml```.

```yml
# This is a sample build configuration for PHP.
# Check our guides at https://confluence.atlassian.com/x/e8YWN for more examples.
# Only use spaces to indent your .yml configuration.
# -----
# You can specify a custom docker image from Docker Hub as your build environment.
image: php:7.1.11

pipelines:
  default:
    - step:
        caches:
          - composer
        script:
          - apt-get update --fix-missing -y
          - apt-get update && apt-get install -y unzip git-core
          - pecl install xdebug && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini
          - curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
          - composer self-update
          - composer install
          - composer require php-coveralls/php-coveralls
          - mkdir -p build/logs
          - vendor/bin/phpunit --coverage-clover build/logs/clover.xml
          - export COVERALLS_RUN_LOCALLY=1
          - vendor/bin/php-coveralls -v
```

https://gist.github.com/gaw508/cb9eb10b596ea3783143d1d76159f72c