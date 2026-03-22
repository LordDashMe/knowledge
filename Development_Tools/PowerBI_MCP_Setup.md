# Power BI MCP Setup

## Install MCP

### Manual install

This MCP Server can also be configured across other IDEs, CLIs, and MCP clients:

1.  Download the VSIX package for the version you want using the URL below:
    -   Template:  `https://marketplace.visualstudio.com/_apis/public/gallery/publishers/analysis-services/vsextensions/powerbi-modeling-mcp/[version]/vspackage?targetPlatform=[platform]`
    -   Example (version  `0.1.9`, platform  `win32-x64`):  `https://marketplace.visualstudio.com/_apis/public/gallery/publishers/analysis-services/vsextensions/powerbi-modeling-mcp/0.1.9/vspackage?targetPlatform=win32-x64`
2.  Rename the downloaded  `.visx`  file to  `.zip`
3.  Unzip the contents to a folder of your choice, for example:  `C:\MCPServers\PowerBIModelingMCP`
4.  Run  `\extension\server\powerbi-modeling-mcp.exe`
5.  Copy the MCP JSON registration from the console and register it in your preferred MCP client tool.

## Preparation

### Step 1: Prepare the Windows VM

First, we need to set up the Windows environment to host the server and prevent it from dropping the connection.

1.  **Configure Parallels Settings:** Open the configuration for your Windows VM. Go to Options > Startup and Routing, and ensure the VM is set to **never sleep** while running.
    
2.  **Get Your VM's IP Address:** Start the Windows VM. Open the Command Prompt, type `ipconfig`, and hit Enter. Look for the "IPv4 Address" and write it down.
    
3.  **Install the Tools:** Ensure Power BI Desktop is installed. Download and extract the Power BI MCP server executable (`.exe`) to a simple, permanent directory on your C: drive, such as `C:\MCP\powerbi-mcp.exe`.
    

### Step 2: Enable OpenSSH on Windows

This creates the secure tunnel your Mac will use to talk to the Windows executable.

1.  **Install OpenSSH Server:** In Windows, go to Settings > System > Optional Features. Click "View features" next to "Add an optional feature". Search for **OpenSSH Server**, check the box, and install it.
    
2.  **Start the Service:** Open the Windows Start Menu, type `services.msc`, and hit Enter. Scroll down to **OpenSSH SSH Server**. Right-click it, go to Properties, change the "Startup type" to **Automatic**, and click **Start**.
    
3.  **Test the Connection:** Open the Terminal on your macOS host and type: `ssh your_windows_username@<your-vm-ip>`. Accept the security prompt and enter your Windows password. If you see a Windows command prompt appear in your Mac terminal, the bridge is working. Type `exit` to close it.
    

_(Note: To avoid typing your password every time Claude Code runs, it is highly recommended to set up SSH keys between your Mac and Windows VM)._

### Step 3: Configure Claude Code on macOS

Now, tell Claude Code on your Mac how to use that SSH tunnel to launch the MCP server.

1.  **Edit the MCP Config:** Open your Mac Terminal. If you use the standard Claude Code config, open `~/.claude.json` (or the specific configuration file for your current directory).
    
2.  **Add the Server Details:** Add the Power BI server configuration using the SSH command. Your JSON file should look like this:
    

JSON

```
{
  "mcpServers": {
    "powerbi-parallels": {
      "command": "ssh",
      "args": [
        "your_windows_username@<your-vm-ip>",
        "C:\\MCP\\powerbi-mcp.exe"
      ]
    }
  }
}

```

### Step 4: Run the Workflow

With the bridge built, you can now use the setup.

1.  **Open Power BI:** Inside your Parallels Windows VM, open Power BI Desktop and load the `.pbix` file you want to work on. The local MCP server needs Power BI to be running and a file open to interact with it.
    
2.  **Start Claude Code:** On your Mac, open your Terminal and launch Claude Code.
    
3.  **Test the Integration:** Ask Claude Code a prompt like, "Use the Power BI MCP server to list the tables in my currently open dataset."
    

Claude Code will reach through the SSH tunnel, launch the executable in Windows, interact with the open Power BI file, and stream the results right back to your Mac terminal!

## Reference

- [PowerBI Modeling MCP](https://github.com/microsoft/powerbi-modeling-mcp)
