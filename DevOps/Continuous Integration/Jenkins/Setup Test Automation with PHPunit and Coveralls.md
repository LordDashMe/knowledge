# Setup Test Automation with PHPunit and Coveralls

- To setup jenkins for PHP automation testing using phpunit follow the simplified steps below:
    1. Create a "Folder" in Jenkins and name it related to your project name.
    2. After creation of folder above you need to CD to that folder.
    3. Inside the project folder you create you need to create a "Freestyle Project"
       this free style project will name related to the branch of you repository ex. master.
    4. After creating freestyle project the configuration will show.
        - Configuration:
            - Source Code Management:
                - Type: GIT
                - Repositories.
                    - URL.
                    - Credentials.
                - Branches to build.
            - Build Triggers:
                - Check the "Build when a change is pushed to Bitbucket".
            - Build:
                ```
                ~/bin/composer install
                vendor/bin/phpunit
                ```
    5. For the case you use Coveralls to show the code coverage after phpunit execute.
        - Configuration:
            - Build:
                ```
                ~/bin/composer install
                ~/bin/composer require php-coveralls/php-coveralls
                vendor/bin/phpunit
                export CI_NAME=$JOB_NAME
                export CI_BUILD_NUMBER=$BUILD_NUMBER
                export CI_BUILD_URL=$BUILD_URL
                export CI_BRANCH="master"
                export COVERALLS_RUN_LOCALLY=1
                vendor/bin/php-coveralls -v
                ```
- Other files need to add in you project root:
    - ```.coveralls.yml```
    ```yml
    coverage_clover: build/logs/clover.xml
    repo_token: gjdQNf3QGFGVNpff6qjzuOs67AFEl96FF (You can get this in your coveralls repo setting)
    json_path: build/logs/coveralls-upload.json
    exclude_no_stmt: true
    ```
    - ```phpunit.xml.dist or phpunit.xml```
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <phpunit 
        backupGlobals="false"
        backupStaticAttributes="false"
        beStrictAboutTestsThatDoNotTestAnything="false"
        bootstrap="tests/bootstrap.php"
        colors="true"
        convertErrorsToExceptions="true"
        convertNoticesToExceptions="true"
        convertWarningsToExceptions="true"
        processIsolation="false"
        stopOnError="false"
        stopOnFailure="false"
        syntaxCheck="true"
        verbose="true"
    >
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
        </logging>

        <filter>
            <whitelist processUncoveredFilesFromWhitelist="true">
                <directory suffix=".php">./src</directory>
            </whitelist>
        </filter>
        
        <testsuites>
            <testsuite name="Hasher">
                <directory suffix="Test.php">./tests</directory>
            </testsuite>
        </testsuites>
        
    </phpunit>
    ```
    - ```composer.json```
    ```json
    {
        "name": "joshuareyes16/jenkins-build-testing-automation",
        "description": "Salt it.",
        "version": "1.0.0",
        "keywords": ["Hide", "Hash"],
        "license": "MIT",
        "authors": [
            {
                "name": "Joshua Clifford Reyes",
                "email": "joshua.reyes@nuworks.ph"
            }
        ],
        "require": {
            "php": ">=7.0"
        },
        "require-dev": {
            "mockery/mockery": "~1.0",
            "phpunit/phpunit": "~6.0"
        },
        "autoload": {
            "psr-4": {
                "LordDashMe\\Hasher\\": "src/"
            }
        }
    }
    ```
- That's all my config to run coveralls and phpunit using jenkins.
- Reference: https://alexbilbie.com/2015/04/setting-up-jenkins/