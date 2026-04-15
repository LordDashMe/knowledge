# Cmder

This is like a Terminal in linux and can be utilize in windows environment. cmder can be by default provided by Laragon.

- How to change the command alias of the terminal: [How do you create an alias? · Issue #421 · cmderdev/cmder · GitHub](https://github.com/cmderdev/cmder/issues/421)

  - Find ```user-alias.cmd``` in the ```config/``` folder.

  - To change the default ```ll``` command and use the ```ls -al``` like in the linux:

    ```bash
    ll=ls -al --show-control-chars -F --color $*
    ```

- How to change the default startup of the terminal: 

  - [windows - Start up cmder ConEmu console in a specific folder - Stack Overflow](https://stackoverflow.com/questions/31933766/start-up-cmder-conemu-console-in-a-specific-folder)

- To modify the CLI style, ex. removing the lambda character and break line. Just follow the step in the reference.

  - [Is it possible to show the current folder in front of cursor on the current line? · Issue #338 · cmderdev/cmder · GitHub](https://github.com/cmderdev/cmder/issues/338)

  ```lua
  -- local cmder_prompt = "\x1b[1;32;40m{cwd} {git}{hg}{svn} \n\x1b[1;39;40m{lamb} \x1b[0m"
  local cmder_prompt = "\x1b[1;00;40m{cwd}{git}{hg}{svn}\x1b[1;39;40m{lamb}"
  -- local lambda = "λ"
  local lambda = "$ "
  ```
