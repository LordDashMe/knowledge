# NodeJS and MongoDB Setup

Creating an HTTPS Server with Node JS.

    1. If you've already a Cert and Key just add it somewhere in root folder in the system ex. Linux /etc/...
    then point that files in the node application startup, the pointing will depending on the folder position
    ex. ./../../ to exit the current folder of that node application and point directly to the ssl files.

    https://medium.com/netscape/everything-about-creating-an-https-server-using-node-js-2fc5c48a8d4e

MongoDB.

    1. If you want to setup mongoDB you need to have access in the SSH and setup it locally.

    2. Or depending on the mongoDB host provider you have you can try to access this using robomongo.

    3. Always change the PORT and don't use the default 27001.

    4. Add Authentication by creating a user and --authenthication option before starting the mongoDB instance.

    5. Install the NodeJS and NPM.

    6. To verify what PORT mongoDB currently using
        * https://stackoverflow.com/questions/9346431/how-can-i-see-what-ports-mongo-is-listening-on-from-mongo-shell

    https://docs.mongodb.com/manual/tutorial/enable-authentication/

    https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/#

This is a simplified steps for setting up mongoDB ready.

    1. Install

        https://docs.mongodb.com/tutorials/install-mongodb-on-ubuntu/

    2. Check version

        https://stackoverflow.com/questions/19405791/what-version-of-mongodb-is-installed-on-ubuntu

    3. Add User admin

        https://stackoverflow.com/questions/38921414/mongodb-what-are-the-default-user-and-password

        https://docs.mongodb.com/manual/tutorial/enable-authentication/

    4. Change default Port

        https://stackoverflow.com/questions/9346431/how-can-i-see-what-ports-mongo-is-listening-on-from-mongo-shell

        https://stackoverflow.com/questions/41933171/how-to-change-default-port-number-in-mongodb

    5. Restart and do the Step 1 start mongodb again.

To install this in Ubuntu 17.04 tested.

    http://linuxbsdos.com/2017/06/25/how-to-install-node-js-and-npm-lts-on-ubuntu-17-04-linux-mint-18-2/