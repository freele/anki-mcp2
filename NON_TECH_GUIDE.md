# Anki MCP for Claude on macOS

## Who this is for

People who want to control Anki from Claude without using the terminal.

## Before you start

- Install Anki and open it at least once: [https://apps.ankiweb.net](https://apps.ankiweb.net)
- Install the AnkiConnect plugin (inside Anki: **Tools → Add-ons → Get Add-ons →** code `2055492159`).  
  Guide: [https://ankiweb.net/shared/info/2055492159](https://ankiweb.net/shared/info/2055492159)
- Keep Anki running whenever you want Claude to talk to it.

## Get the bundle

1. Open [https://github.com/freele/anki-mcp2/releases/latest](https://github.com/freele/anki-mcp2/releases/latest)
2. Download the newest file named `anki-mcp.mcpb` and save it somewhere easy to find (for example, Downloads).

## Install in Claude Desktop (Mac)

1. Launch Claude Desktop.
2. In the top menu pick **Claude → Settings**.
3. Go to **Model Context Protocol (MCP)** or **Extensions** (depending on the Claude version).
4. Click **Import bundle** / **Add MCP server**, then choose the `anki-mcp.mcpb` file you just downloaded.
5. When Claude asks for settings, fill in:
   - **AZURE_API_KEY** (only if you want audio generation; leave blank if not).  
     This comes from Microsoft Azure's Speech service—create a free Azure account, add a Speech resource, then copy one of the `KEY` values from the Keys & Endpoint page.
   - **ANKI_MEDIA_DIR** → click **Choose folder**, then select your Anki `collection.media` folder.  
     Default path:  
     ```
     /Users/<your mac username>/Library/Application Support/Anki2/User 1/collection.media
     ```
6. Finish the wizard. Claude now knows how to start the Anki MCP server automatically.

## Try it

1. Open Anki and confirm the AnkiConnect add-on is listed under **Tools → Add-ons** (no special status light is needed).
2. In a browser you can optionally visit [http://localhost:8765](http://localhost:8765) and see the JSON welcome message to confirm AnkiConnect is responding.
3. Open a chat with Claude and type something like:  
   ```
   List my Anki decks
   ```
4. Claude should answer using the new tools. If it says Anki is not reachable, make sure Anki is still running and that the add-on stays enabled.

## Updating later

- Visit the same releases page and download the newest `anki-mcp.mcpb`.
- In Claude settings, remove the old bundle if asked, then import the new one.
