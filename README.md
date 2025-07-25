# Cpanel MCP Server

This MCP Server plugin provides seamless integration between AI assistants and cPanel hosting control panels, enabling natural language management of web hosting accounts. The plugin connects directly to cPanel's API, allowing users to perform common hosting tasks through conversational commands rather than navigating the traditional cPanel interface.

## Features

- **Advanced File Operations:** Create, list, edit, and delete files.
- **Disk Usage:** Check your account's disk space consumption.
- **Database Management:** Create and delete databases and database users, and manage user privileges.
- **Email Management:** Create and delete email accounts.
- **Subdomain Management:** Create and delete subdomains.
- **FTP Management:** Create and delete FTP accounts.
- **Backups:** Initiate a full account backup.
- **SSL Management:** Install SSL certificates.

## Installation and Configuration

This server is designed to be run as a Model Context Protocol (MCP) server. To use it, you need to configure it in your MCP settings file.

1.  **Build the server:**
    ```bash
    npm install
    npm run build
    ```

2.  **Configure the server:**
    Add the following configuration to your `cline_mcp_settings.json` file. This file is typically located in the user settings directory of your code editor.

    ```json
    {
      "mcpServers": {
        "cpanel": {
          "command": "node",
          "args": ["/path/to/Cpanel-MCP-Server/build/index.js"],
          "env": {
            "CPANEL_USERNAME": "your_cpanel_username",
            "CPANEL_API_TOKEN": "your_cpanel_api_token",
            "CPANEL_SERVER_URL": "https://your_cpanel_domain.com:2083"
          },
          "disabled": false,
          "autoApprove": []
        }
      }
    }
    ```

    **Important:** Replace the placeholder values for `CPANEL_USERNAME`, `CPANEL_API_TOKEN`, and `CPANEL_SERVER_URL` with your actual cPanel credentials. The `/path/to/Cpanel-MCP-Server/build/index.js` should also be replaced with the absolute path to the built `index.js` file on your system.

## Security

Your cPanel credentials are not stored in this repository. They are loaded from your local MCP settings file as environment variables at runtime. This ensures that your sensitive information is kept separate from the server's source code and is not exposed if you choose to share or publish the code.
