# ntfy MCP Server

A [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server that enables AI assistants to send push notifications through [ntfy.sh](https://ntfy.sh/). This server provides a simple way to integrate real-time notifications into your AI workflows, allowing you to receive alerts on your phone, desktop, or any device that supports ntfy.sh.

## What is ntfy.sh?

[ntfy.sh](https://ntfy.sh/) is a simple HTTP-based pub-sub notification service that allows you to send push notifications to your devices. It's particularly useful for:
- Getting notified when long-running tasks complete
- Receiving alerts from automated workflows
- Staying informed about important events in your applications

## Features

- Send messages to any ntfy.sh channel
- Support for message titles, priorities (1-5), and tags
- Simple integration with MCP-compatible AI assistants
- No authentication required for public channels

## Installation

1. **Install dependencies:**

```bash
npm install --save-dev typescript @types/node ts-node
```

2. **Build the TypeScript code:**

```bash
npm run build
```

3. **The MCP server is now available at `./build/index.js`**

## Usage

### Running the Server

After building, you can run the server directly:

```bash
npm start
```

Or point your MCP client to the built server at `./build/index.js`.

### Available Tools

The server provides one tool:

#### `send_message`

Sends a message to a specified ntfy.sh channel.

**Parameters:**
- `channel` (required): The ntfy.sh channel name to send the message to
- `message` (required): The message content to send
- `title` (optional): A title for the notification
- `priority` (optional): Priority level from 1-5 (5 being highest priority)
- `tags` (optional): Array of tags to categorize the message

**Example usage in an MCP client:**
```json
{
  "tool": "send_message",
  "arguments": {
    "channel": "my-notifications",
    "message": "Task completed successfully!",
    "title": "Workflow Update",
    "priority": 4,
    "tags": ["automation", "success"]
  }
}
```

## Configuration

No additional configuration is required. The server uses the public ntfy.sh service at `https://ntfy.sh/`.

### Channel Names

- Channel names can be any string, but should be unique to avoid conflicts
- Consider using descriptive names like `my-project-alerts` or `personal-notifications`
- Anyone who knows your channel name can send messages to it, so choose wisely

## Development

### Build Scripts

- `npm run build` - Compile TypeScript to JavaScript
- `npm run build:linux` - Build and make executable on Linux
- `npm run build:windows` - Build for Windows
- `npm start` - Run the compiled server

### Project Structure

- [`src/index.ts`](src/index.ts) - Main server implementation
- [`build/index.js`](build/index.js) - Compiled JavaScript output (after build)

## License

See [LICENSE](LICENSE) file for details.

