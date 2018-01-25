# Installation

1. First follow the steps provided by digital ocean, this is tested in 16.04 Ubuntu LTS.
    - https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-16-04
2. After completing all the steps above you can now proceed to change the default port of jenkins.
    - https://stackoverflow.com/questions/28340877/how-to-change-port-number-for-jenkins-installation-in-ubuntu-12-04
    ```
    HTTP_PORT="XXXX"
    JENKINS_ARGS="--httpPort=XXXX"
    ```
3. Then if you're using bitbucket for repositories if you want to add bitbucket push as trigger build use the below plugin for jenkins.
    - https://wiki.jenkins.io/display/JENKINS/BitBucket+Plugin
4. After installing the plugin in your bitbucket you must add the hook for you jenkins domain. (Note that you need to have a live domain for your jenkins server).
    ```
    http://jenkins.domain.com:8089/bitbucket-hook/
    ```
5. If you want to use ssh access in the build shell script in jenkins it's easy to add rsa key of jenkins to the specific server.
    - https://help.ubuntu.com/community/SSH/OpenSSH/Keys
    - Add the Jenkins ``` cat id_rsa.pub ``` to the ``` authorized_keys ```