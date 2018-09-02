# Creating Alias Bash Command

## Open user .bashrc

```text
$ vim ~/.bashrc
...
```

## Go to the end of the file

Using <kbd>vim</kbd>, hitting <kbd>G</kbd> or <kbd>shift + G</kbd>

## Add the alias

```text
alias custom-command='execute other command'
```

## Save the edited file

Using <kbd>vim</kbd>, press <kbd>Escape</kbd> then type the characters below.

```text
:wq
```

## Install the new .bashrc cotent

```text
$ source ~/.bashrc
...
```

## Reference

http://www.hostingadvice.com/how-to/set-command-aliases-linuxubuntudebian/