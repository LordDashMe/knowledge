# VSCode Setup

## Extensions

- VSCode Great Icons

- GitLens

## Configuration

- To add ruler in the editor view.

    ```text
    "editor.rulers": [
        100
    ],
    ```

- To auto add new line in every save files.

  - [Visual Studio Code — Insert New Line at the End of Files - Stack Overflow](https://stackoverflow.com/questions/44704968/visual-studio-code-insert-new-line-at-the-end-of-files)

  - Add this to the File > Preferences > Settings

   ```text
   "files.insertFinalNewline": true,
   ```

- To adjust the editor font size instead of adjusting the editor zoom level.

  ```text
  "editor.mouseWheelZoom": true,
  "editor.fontSize": 12
  ```

- To adjust terminal font size.

  ```text
  "terminal.integrated.fontSize": 12,
  ```
### How to open User or Workspace settings json file

You can open the settings.json file with the Preferences: Open Settings (JSON) command in the Command Palette (Ctrl+Shift+P) or for Mac (Command+Shift+P).
