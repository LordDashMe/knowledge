# Setup To Use in PHP Projects

* Steps to setup coveralls
    - http://kizu514.com/blog/setting-up-coveralls-io-with-travis-ci-and-phpunit/
    - https://stackoverflow.com/questions/34980017/travis-ci-works-correctly-but-coveralls-doesnt-see-the-builds/35019765
---
* If the coverage_clover XML file is not readable
    - https://github.com/php-coveralls/php-coveralls/issues/185
    ```xml
    <filter>
        <whitelist processUncoveredFilesFromWhitelist="true">
            <directory suffix=".php">./src</directory>
        </whitelist>
    </filter>
    ```
---
* Files needed to run this and need to apply in the package root dir.
    - ```.coveralls.yml```
    ```yml
    coverage_clover: build/logs/clover.xml
    json_path: build/logs/coveralls-upload.json
    exclude_no_stmt: true
    ```
    - ```.travis.yml```
    ```yml
    # Required to run your project under the correct environment.
    language: php

    # Versions of PHP you want your project run with.
    php:
      - 7.0
      - 7.1

    # Commands to be run before your environment runs.
    before_script:
      - composer require satooshi/php-coveralls:dev-master
      - composer self-update
      - composer install

    # Commands you want to run that will verify your build.
    script: 
      - mkdir -p build/logs
      - vendor/bin/phpunit --coverage-clover build/logs/clover.xml

    after_success:
      - vendor/bin/coveralls -v

    # Customize when the notification emails are sent.
    notifications:
        on_success: never
        on_failure: always
    ```
    - ```phpunit.xml.dist``` - this is needed for the newer version of phpunit
    ```xml
    <logging>
        <log type="coverage-html" 
             target="build/coverage" 
             title="coverage" 
             charset="UTF-8" 
             yui="true" 
             highlight="true" 
             lowUpperBound="35" 
             highLowerBound="70"
        />
        <log type="coverage-clover" target="build/logs/clover.xml"/>
        <log type="junit" target="build/logs/junit.xml" logIncompleteSkipped="false"/>
    </logging>
    ```