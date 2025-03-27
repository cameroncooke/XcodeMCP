<img src="banner.png" alt="XcodeBuild MCP" width="600"/>

A Model Context Protocol (MCP) server that provides Xcode-related tools for integration with AI assistants and other MCP clients.

## Overview

This project implements an MCP server that exposes Xcode operations as tools that can be invoked by AI agents via the MCP protocol. It enables programmatic interaction with Xcode projects through a standardised interface, optimised for agent-driven development workflows.


https://github.com/user-attachments/assets/2da9d49c-b1d6-47c1-9f1e-ffdf71d8a09a
<caption>Demo showing Claude Code building and launching a macOS app.</caption>

## Why?

The XcodeBuild MCP tool exists primarily to streamline and standardise interaction between AI agents and Xcode projects. By providing dedicated tools for common Xcode operations, it removes reliance on manual or potentially incorrect command-line invocations.

This ensures a reliable and efficient development process, allowing agents to seamlessly leverage Xcode's capabilities while reducing the risk of configuration errors.

Critically, this MCP enables AI agents to independently validate code changes by building projects, inspecting errors, and iterating autonomously. In contrast to user-driven tools like Sweetpad, XcodeBuild MCP empowers agents to automate these workflows effectively.

## Features

The XcodeBuildMCP server provides the following tools:

### Build tools
- **build**: Builds the project using xcodebuild with support for workspaces, projects, schemes, and various platforms (iOS, macOS, watchOS, tvOS, visionOS and their simulator variants).
- **showBuildSettings**: Shows build settings for the project using xcodebuild.
- **getAppPath**: Extracts the app bundle path from build settings, making it easier to find the built app for installation or launching.
- **listSchemes**: Lists all available schemes in an Xcode project or workspace.
- **clean**: Cleans build products using xcodebuild's native clean action.

### Simulator tools
- **listSimulators**: Lists available iOS simulators with their UUIDs.
- **bootSimulator**: Boots an iOS simulator using a specified UUID.
- **openSimulator**: Opens the iOS Simulator app to view the simulator UI.
- **installAppInSimulator**: Installs an app in an iOS simulator.
- **launchAppInSimulator**: Launches an app in an iOS simulator using its bundle ID.

### macOS tools

- **launchMacOSApp**: Launches a macOS app using the open command.

### Bundle ID tools
- **getBundleId**: Extracts the bundle identifier from an app bundle (.app).
- **getiOSBundleId**: Extracts the bundle identifier from an iOS app bundle.
- **getMacOSBundleId**: Extracts the bundle identifier from a macOS app bundle.

## Getting started

### Prerequisites

- Node.js (v16 or later)
- npm
- Xcode command-line tools

### Installation

1. Clone the repository
2. Install dependencies:
   ```
   npm install
   ```
3. Build the project:
   ```
   npm run build
   ```
4. Optionally start the server:
   ```
   node build/index.js
   ```

> [!NOTE]
> You don't need to run the server manually as MCP clients will do this for you.

## Adding to Windsurf/Cursor/Clude Desktop etc.

Create a new custom server configuration and add the following; changing the path to the actual path you cloned the repo to.

```json
{
  "mcpServers": {
    "XcodeBuildMCP": {
      "command": "node",
      "args": [
        "/path_to/XcodeBuildMCP/build/index.js"
      ]
    }
  }
}
```

## Debugging

You can use MCP Inspector via:

```bash
npx @modelcontextprotocol/inspector node build/index.js
```

## Demos

### Building and running iOS app in Cursor
https://github.com/user-attachments/assets/b9d334b5-7f28-47fc-9d66-28061bc701b4


### Building and running iOS app in Claude Code
https://github.com/user-attachments/assets/e3c08d75-8be6-4857-b4d0-9350b26ef086


## Licence

This project is licensed under the MIT License - see the LICENSE file for details.
