# Github SSH Keys

## Steps

### Generate SSH Keys Local

- Generate ssh keys with the email

  ```sh
  ssh-keygen -t rsa -b 4096 -C "john.doe@example.com"
  ```

- Enter to accept the default file location.

  - If required to change the file name, it needs to properly setup on `~/.ssh/config`
 
    ```sh
    Host github.com
      AddKeysToAgent yes
      # IdentityFile ~/.ssh/<file-name-gen-key>
      IdentityFile ~/.ssh/id_rsa
    ```

  - (Optional) For multiple ssh key that's available for single host, you can use this format
 
    ```sh
    Host host1.github.com
      HostName github.com
      User git
      PreferredAuthentications publickey
      IdentityFile ~/.ssh/id_rsa
      IdentitiesOnly yes
    ```

- Enter a secure passphrase.

- Enter this command to display the contents of your **public key**.

  ```sh
  cat .ssh/id_rsa.pub
  ```
- Copy the contents (we will need it later).

### Add SSH Keys in Github Account

- Log into your GitHub account.

- Go to Settings.

- Find SSH and GPG keys.

- New SSH key.

- Provide a title in the field (i.e Local Device SSH Keys, ...).

- Provide the **public key** (content of `.ssh/id_rsa.pub`) into the Key field.

### Test SSH Connection with Github

- Run the following

  ```sh
  $ ssh -vT git@github.com
  ```

- You may see a warning like this:

  ```text
  > The authenticity of host 'github.com (IP ADDRESS)' can't be established.
  > ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
  > Are you sure you want to continue connecting (yes/no)?
  ```

- Verify that the fingerprint in the message you see matches GitHub's public key fingerprint. If it does, then type `yes`:

  ```text
  > Hi USERNAME! You've successfully authenticated, but GitHub does not
  > provide shell access.
  ```

## Reference

- <https://www.inmotionhosting.com/support/server/ssh/how-to-add-ssh-keys-to-your-github-account/>

- <https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection>
