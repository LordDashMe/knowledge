
## INFO :bulb: ##
1. Creating an HTTPS Server with Node JS.
    - If you've already a Cert and Key just add it somewhere in root folder in the system ex. Linux /etc/...
    then point that files in the node application startup, the pointing will depending on the folder position
    ex. ./../../ to exit the current folder of that node application and point directly to the ssl files.
2. MongoDB.
    - If you want to setup mongoDB you need to have access in the SSH and setup it locally.
    - Or depending on the mongoDB host provider you have you can try to access this using robomongo.
    - Always change the PORT and don't use the default 27001 
    - Add Authentication by creating a user and --authenthication option before starting the mongoDB instance.
    - Install the NodeJS and NPM.
3. This is a simplified steps for setting up mongoDB ready:
    - Step 1 Install
        - [ https://docs.mongodb.com/tutorials/install-mongodb-on-ubuntu/ ]
    - Step 2 Check version
        - [ https://stackoverflow.com/questions/19405791/what-version-of-mongodb-is-installed-on-ubuntu ]
    - Step 3 Add User admin
        - [ https://stackoverflow.com/questions/38921414/mongodb-what-are-the-default-user-and-password ]
        - [ https://docs.mongodb.com/manual/tutorial/enable-authentication/ ]
    - Step 4 Change default Port
        - [ https://stackoverflow.com/questions/9346431/how-can-i-see-what-ports-mongo-is-listening-on-from-mongo-shell ]
        - [ https://stackoverflow.com/questions/41933171/how-to-change-default-port-number-in-mongodb ]
    - Step 5 Restart and do the Step 1 start mongodb again.

## REFERENCES :link: ##
- For ``#1`` Reference:
    - [ https://medium.com/netscape/everything-about-creating-an-https-server-using-node-js-2fc5c48a8d4e ]
- For ``#2`` Reference:
    - [ https://docs.mongodb.com/manual/tutorial/enable-authentication/ ]
    - To verify what PORT mongoDB currently using
        - [ https://stackoverflow.com/questions/9346431/how-can-i-see-what-ports-mongo-is-listening-on-from-mongo-shell ]
    - [ https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/# ]
