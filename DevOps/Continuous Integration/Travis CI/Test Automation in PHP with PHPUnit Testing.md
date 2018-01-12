# Test Automation in PHP with PHPUnit Testing

* Core Concepts.
    - Travis CI can be use for multi support unit testing for PHP because it's creating vitual environment.
* Handson.
    - Tried the Travis CI for building but not on actual deployment.
    - It's easy to learn, easy to integrate with Github repo.
* Learn the default config file of Travis for PHP, add this config file to your root project.
    ```yml
    # Required to run your project under the correct environment.
    language: php

    # Versions of PHP you want your project run with.
    php:
      - 5.6
      - 7.0
      - 7.1

    # Commands to be run before your environment runs.
    before_script:
      - composer self-update
      - composer install

    # Commands you want to run that will verify your build.
    script: 
      - mkdir -p build/logs
      - vendor/bin/phpunit --coverage-clover build/logs/clover.xml

    # Customize when the notification emails are sent.
    notifications:
      on_success: never
      on_failure: always
    ```