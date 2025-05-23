# Model Context Protocol

As highlighted previously, there's more to writing code than just writing code. We need to interact with deployment tools, find information, and create issues just to name a few tasks. Model Context Protocol (MCP) allows for external services to be introduced to Copilot (and other AI tools), which can then be used to query or perform tasks.

## Scenario

Being the good developers that we are, we want to create an issue for the work we've created. We don't want to open a website, but do this right through Copilot Chat.

## Demo background

There are numerous MCP servers available. This one uses the [GitHub MCP Server](https://github.com/github/github-mcp-server). The server has already been configured, but you will need to [generate a key](./0-setup.md#start-the-mcp-server-for-a-later-demo) **OFF CAMERA** to setup this demo.

## Demo overview

1. Walk everyone through the **mcp.json** file, where the server is created.
2. Return to Copilot Chat, start a new query, and ask for an issue to be created.
3. Showoff the newly created issue.

## Demo steps

### Configuration walkthrough

MCP servers can be defined for a user in their setting file, or at the project level in **.vscode/mcp.json**. Let's start by walking through the configuration.

1. Return to your codespace.
2. Open **.vscode/mcp.json**.
3. Highlight the `servers` section first, which has just the one: GitHub.
4. Highlight that it can perform tasks on your behalf, like creating issues and pull requests. This of course requires a token. This can be a [personal access token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) or, since we're using a codespace, the GITHUB_TOKEN generated by the codespace.

> [!IMPORTANT]
> Highlight the importance of keeping this token a secret like a password, because that's what it is.

4. Highlight the `inputs` section, and how you'll be prompted for the token when you first start the server. VS Code will protect the key, keeping it from being read except for these operations.
5. Highlight the **Start** button (or **Stop**) just above the server. If **Start** is displayed, start the server.
6. Finally, highlight the **Add Server** button. Show off the list of [available servers](https://github.com/modelcontextprotocol/servers).

### Send a query to MCP

Let's send a query to the MCP server through Copilot Chat.

1. Open Copilot Chat.
2. Select the **+** to start a **New Chat**.
3. Ensure **Agent** is selected from mode, and **Claude 3.7 Sonnet** is selected from the model.
4. Select the **Select Tools** icon to show the available tools or commands available through the MCP server. Highlight that Copilot will automatically determine what command needs to be run, so we don't need to choose them individually.
5. Select <kbd>Esc</kbd> to close the window.
6. Send the following prompt to create an issue, replacing <YOUR_REPO_NAME> with the **org/name** of your repository.

    ```plaintext
    Create a new issue on <YOUR_REPO_NAME> for adding filtering to the website. The filter should allow someone to choose the publisher and/or category. Add a todo list to the issue to ensure the proper tasks have been completed, like unit tests passing and code review completed.
    ```

7. Agent Mode will detect the desire to create an issue, and generate a prompt to call `create_issue`.
8. Expand the section to highlight the JSON body Copilot wants to send.
9. Highlight the **Continue** button, and the dropdown which allows you to choose to **Always** approve these commands.

> [!IMPORTANT]
> Be **very cautious** about enabling Copilot to always have permission to perform tasks like creating issues or other operations.

10. Press **Continue** to let Copilot create the issue.
11. Open your repository and the **Issues** tab.
12. Open the newly created issue.
13. Highlight how the text has been expanded by Copilot through the magic of generative AI.

## Summary

MCP allows Copilot and other AI services to access external services to locate information or perform more robust tasks.

## Next demo

That's it! You're done!!
