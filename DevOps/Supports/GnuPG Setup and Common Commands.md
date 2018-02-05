# GnuPG

- To install GnuPGv2.
    - Download files here: https://www.gnupg.org/download/index.html
        - GnuPG
        - Libgpg-error
        - Libgcrypt
        - Libksba
        - Libassuan
        - nPth
        - Pinetry
    - Install libgpg-error 1.27
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/libgpg-error/libgpg-error-1.27.tar.gz && \
        wget -c https://www.gnupg.org/ftp/gcrypt/libgpg-error/libgpg-error-1.27.tar.gz.sig && \
        gpg --verify libgpg-error-1.27.tar.gz.sig && tar -xzf libgpg-error-1.27.tar.gz && \
        cd libgpg-error-1.27/ && ./configure && make && make install && cd ../
        ```
    - Install libgcrypt 1.8.2
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/libgcrypt/libgcrypt-1.8.2.tar.gz && \
        wget -c https://www.gnupg.org/ftp/gcrypt/libgcrypt/libgcrypt-1.8.2.tar.gz.sig && \
        gpg --verify libgcrypt-1.8.2.tar.gz.sig && tar -xzf libgcrypt-1.8.2.tar.gz && \
        cd libgcrypt-1.8.2 && ./configure && make && make install && cd ../
        ```
    - Install libassuan 2.5.1
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/libassuan/libassuan-2.5.1.tar.bz2 && \
        wget -c https://www.gnupg.org/ftp/gcrypt/libassuan/libassuan-2.5.1.tar.bz2.sig && \
        gpg --verify libassuan-2.5.1.tar.bz2.sig && tar -xjf libassuan-2.5.1.tar.bz2 && \
        cd libassuan-2.5.1 && ./configure && make && make install && cd ../
        ```
    - Install libksba 1.3.5
        ```
        wget -c  https://www.gnupg.org/ftp/gcrypt/libksba/libksba-1.3.5.tar.bz2 && \
        wget -c https://www.gnupg.org/ftp/gcrypt/libksba/libksba-1.3.5.tar.bz2.sig && \
        gpg --verify libksba-1.3.5.tar.bz2.sig && tar -xjf libksba-1.3.5.tar.bz2 && \
        cd libksba-1.3.5 && ./configure && make && make install && cd ../
        ```
    - Install npth 1.5
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/npth/npth-1.5.tar.bz2 && \
        wget -c https://www.gnupg.org/ftp/gcrypt/npth/npth-1.5.tar.bz2.sig && \
        gpg --verify npth-1.5.tar.bz2.sig && tar -xjf npth-1.5.tar.bz2 && \
        cd npth-1.5 && ./configure && make && make install && cd ../
        ```
    - Install pinetry 1.1.0
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/pinentry/pinentry-1.1.0.tar.bz2 && \
        wget -c https://www.gnupg.org/ftp/gcrypt/pinentry/pinentry-1.1.0.tar.bz2.sig && \
        gpg --verify pinentry-1.1.0.tar.bz2.sig && tar -xjf pinentry-1.1.0.tar.bz2 && \
        cd pinentry-1.1.0 && ./configure --enable-pinentry-curses --disable-pinentry-qt4 && \
        make && make install && cd ../
        ```
    - Install GnuPG 2.2.4
        ```
        wget -c https://www.gnupg.org/ftp/gcrypt/gnupg/gnupg-2.2.4.tar.bz2 && \
        wget -c https://www.gnupg.org/ftp/gcrypt/gnupg/gnupg-2.2.4.tar.bz2.sig && \
        gpg --verify gnupg-2.2.4.tar.bz2.sig && tar -xjf gnupg-2.2.4.tar.bz2 && \
        cd gnupg-2.2.4 && ./configure && make && make install
        ```
    - Finishing the build
        ```
        echo "/usr/local/lib" > /etc/ld.so.conf.d/gpg2.conf && ldconfig -v
        ```

- To create key gen in gpg.
```
$ gpg --full-key-gen (for gpg v2.2.4 and for lower just use "gpg --key-gen")
    
    - Please select what kind of key you want:
            (1) RSA and RSA (default)
            (2) DSA and Elgamal
            (3) DSA (sign only)
            (4) RSA (sign only)
            Your selection? "1"
            
    - RSA keys may be between 1024 and 4096 bits log.
            What keysize do you want? (2048) "4096"
            
    - Please specify how long the key should be valid.
            0 = key does not expire
          <n> = key expires in n days
         <n>w = key expires in n weeks
         <n>m = key expires in n months
         <n>y = key expires in n years
         Key is valid for? "1y"
         
    - Real name: "your/recipient full name"

    - Email address: "you active email address"

    - Comment: "Your comment or remarks"

    - Change (N)ame, (C)omment, (E)mail, or (O)kay/(Q)uit? "O"

    - You need a Passphrase to protect your secret key.
        Enter passphrase: "This will recommend a string, number and special character atleast 1" 
        
$ gpg --list-secret-keys (This will show the list of created key gen)
```

- To encrypt file in gpg.
```
$ gpg --encrypt --output <TheEncryptedContentFilename.gpg> --recipient <TheListedEmail@email.com> <TheFilenameToEncrypt.extension>
```

- To decrypt gpg file.
```
(Note: Important that the recipient generated key must imported first before decrypting the selected file to other device.)
$ gpg --decrypt --output <DecryptedFilename.extension> <TheEncryptedContentFilename.gpg>
```

- To export gpg public key.
```
$ gpg --export "Real Name" > file.gpg.pub.key
$ gpg --output file.gpg.pub.key --export "The Email"
```

- To export gpg secret key.
```
$ gpg --export-secret-key "Real Name" > file.gpg.secret.key
$ gpg --output file.gpg.secret.key --export-secret-key "The Email"
```

- To import gpg public key.
```
$ gpg --import file.gpg.pub.key
```

- To import gpg secret key.
```
$ gpg --import file.gpg.secret.key
```

- Reference: 
    - https://gist.github.com/vt0r/a2f8c0bcb1400131ff51
    - https://www.youtube.com/watch?v=kVhq3bhQdSs
    - https://www.youtube.com/watch?v=cUZMIP8z1T0&t=45s
    - http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html