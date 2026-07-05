# PowerBI Parallels MC Setup

This setup allows Claude Code on your Mac to use the **Power BI Modeling MCP Server** running inside a Windows VM to perform tasks like listing tables, creating measures, and documenting your model.

## 1. Prerequisite: Windows VM Setup

- **Install Power BI Desktop** in your Parallels VM.
- **Download the MCP Server:** Download the [Power BI Modeling MCP VS Code Extension](https://marketplace.visualstudio.com/items?itemName=analysis-services.powerbi-modeling-mcp). Extract the `.vsix` (rename to `.zip`) and find the `server` folder.
- **Move the Executable:** Place `powerbi-modeling-mcp.exe` in a stable path, e.g., `C:\MCPServers\PowerBI\powerbi-modeling-mcp.exe`.

## 2. Networking: The SSH Bridge

Windows must be able to accept "silent" commands from your Mac.

1.  **Enable SSH on Windows:** Settings > System > Optional Features > Add **OpenSSH Server**.
2.  **Start the Service:** Open `services.msc`, set **OpenSSH SSH Server** to **Automatic**, and click **Start**.
3.  **Open Firewall:** Run PowerShell as Admin:

    PowerShell

    ```
    New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
    ```

4.  **Passwordless Login (Crucial):**
    - On your **Mac**, generate a dedicated key: `ssh-keygen -t rsa -f ~/.ssh/powerbi_rsa -N ""`
    - Copy the content of `~/.ssh/powerbi_rsa.pub`.
    - On **Windows**, paste that key into `C:\Users\YourUser\.ssh\authorized_keys`.
    - **Admin Fix:** Since you are likely an admin, you **must** also copy that file to the system-wide location: `copy C:\Users\YourUser\.ssh\authorized_keys C:\ProgramData\ssh\administrators_authorized_keys`

## 3. Mac-Side Shortcut

To keep the Claude config clean, add this to your Mac’s `~/.ssh/config` file:

Plaintext

```
Host powerbivm
    HostName 10.211.55.3
    User outstaffer
    IdentityFile ~/.ssh/powerbi_rsa
    IdentitiesOnly yes
```

_(Verify by typing `ssh powerbivm` in your Mac terminal. It should log in instantly without a password)._

## 4. Claude Code Configuration

Create a file named **`.mcp.json`** in the **root directory** of your project. This tells Claude to launch the Windows `.exe` and-critically-silences the background "info" logs that would otherwise crash the connection.

**`.mcp.json` content:**

JSON

```
{
  "mcpServers": {
    "powerbi-parallels": {
      "command": "ssh",
      "args": [
        "-T",
        "-q",
        "powerbivm",
        "cmd.exe /c \"set Logging__LogLevel__Default=Warning && set Logging__Console__LogLevel__Default=Warning && set Logging__LogLevel__Microsoft.Hosting.Lifetime=Warning && C:\\MCPServers\\PowerBI\\powerbi-modeling-mcp.exe --start\""
      ]
    }
  }
}
```

## 5. Running the Workflow

1.  **Windows:** Open your `.pbix` file in Power BI Desktop.
2.  **Mac:** Navigate to your project folder in the terminal.
3.  **Launch:** Run `claude`.
4.  **Verify:** Type `/mcp list`. You should see `powerbi-parallels` as **Connected**.
5.  **Prompt:** _"List all tables and measures in my open Power BI model."_

---

> **Note for the team:** If the connection hangs, ensure the Windows VM hasn't gone to sleep and that the IP address in your SSH config (`10.211.55.3`) still matches the VM's current IP (check with `ipconfig` in Windows).
