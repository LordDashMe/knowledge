# Install the gcloud CLI - Ubuntu

## Commands

```sh
$ sudo apt-get update

$ sudo apt-get install apt-transport-https ca-certificates gnupg curl sudo

$ echo "deb https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

$ curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo tee /usr/share/keyrings/cloud.google.gpg

$ sudo apt-get update && sudo apt-get install google-cloud-cli

$ gcloud init
```
