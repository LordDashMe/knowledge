# CodeClimate PHP

- Steps to setup codeclimate
  
  - <https://docs.codeclimate.com/v1.0/docs/test-coverage-php>
  
  - <https://docs.codeclimate.com/docs/finding-your-test-coverage-token>

- Primary Feature of codeclimate is the complexity evaluation or analysis concepts see below link:
  
  - <https://docs.codeclimate.com/v1.0/docs/cognitive-complexity>

---

- Add this lines of code in the Travis CI yml.

```yml
# Required to run your project under the correct environment.
language: php

# Versions of PHP you want your project run with.
php:
  - 7.0
  - 7.1

# Commands to be run before your environment runs.
before_script:
  - composer require codeclimate/php-test-reporter:dev-master --dev
  - composer self-update
  - composer install

# Commands you want to run that will verify your build.
script:
  - mkdir -p build/logs
  - vendor/bin/phpunit --coverage-clover build/logs/clover.xml

# Execute another command after success of the script.
after_success:
  - CODECLIMATE_REPO_TOKEN=195e30dee749fdfe51d7712c1013c7a75b05c6734a89c42fd4bc0a5f787e389f (You can get this in your codeclimate repo setting) vendor/bin/test-reporter

# Customize when the notification emails are sent.
notifications:
  on_success: never
  on_failure: always
```

- Note: this configuration will be soon to be deprecated, we will try the latest copy as soon as possible.