# VSCode Setup

## Extensions

### Main

- VSCode Great Icons

- GitLens

- Docker

- Prettier - Code formatter

### Optional

- Edit csv

- Markdown All in One

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
  "editor.fontSize": 12,
  "editor.tabSize": 2
  ```

- To adjust terminal font size.

  ```text
  "terminal.integrated.fontSize": 12,
  ```

### How to open User or Workspace settings json file

You can open the settings.json file with the Preferences: Open Settings (JSON) command in the Command Palette (Ctrl+Shift+P) or for Mac (Command+Shift+P).

## Default Settings.json

```json
{
  "security.workspace.trust.untrustedFiles": "open",
  "workbench.colorTheme": "Monokai",
  "workbench.iconTheme": "vscode-great-icons",
  "editor.codeActionsOnSave": {},
  "editor.rulers": [100],
  "files.insertFinalNewline": true,
  "editor.mouseWheelZoom": true,
  "editor.fontSize": 12,
  "terminal.integrated.fontSize": 12,
  "editor.tabSize": 2,
  "diffEditor.ignoreTrimWhitespace": false,
  "typescript.updateImportsOnFileMove.enabled": "never",
  "editor.formatOnSave": true,
  "files.associations": {
    ".prettierrc": "json"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[json]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[markdown]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

## Useful Shortcut Keys

- Command Palette: `Shift + Cmd + P`

- Show settings: `Cmd + ,`

- Show files: `Cmd + P`

- Exit project view: `Cmd + K + F`
