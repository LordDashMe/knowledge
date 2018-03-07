# Creating Alias Bash Command

#### Open user .bashrc
```
$ vim ~/.bashrc
```

#### Go to the end of the file
Using <kbd>vim</kbd>, hitting <kbd>G</kbd> or <kbd>shift + G</kbd>

#### Add the alias
```
alias custom-command='execute other command'
```

#### Save the edited file
Using <kbd>vim</kbd>, press <kbd>Escape</kbd> then type the characters below.
```
:wq
```

#### Install the new .bashrc cotent
```
$ source ~/.bashrc
```

#### Reference
- http://www.hostingadvice.com/how-to/set-command-aliases-linuxubuntudebian/