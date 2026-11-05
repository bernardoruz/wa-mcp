# WA MCP

<img src="assets/logo.png" alt="WA MCP logo" width="96">

Connect your own WhatsApp to your AI. Ask it to catch you up on your chats, find a message, see who's waiting for a reply, or write and send messages for you, all from the conversation.

WA MCP is a hosted [Model Context Protocol](https://modelcontextprotocol.io) server. There is nothing to install or run: add the URL, sign in, and link your WhatsApp number by QR code or pairing code. Website: [wa-mcp.com](https://wa-mcp.com/?utm_source=github&utm_medium=directory).

This repository holds the plugin manifest and docs only. The server itself is not open source.

## Install

**Server URL:** `https://server.wa-mcp.com/mcp` (Streamable HTTP, OAuth)

- **Cursor / Grok Bot:** install WA MCP from the marketplace, or add it to your `mcp.json`:

  ```json
  {
    "mcpServers": {
      "wa-mcp": { "url": "https://server.wa-mcp.com/mcp" }
    }
  }
  ```

- **Any other MCP client:** add the server URL above as a remote (HTTP) MCP server.

## Getting started

1. Add the server. A WA MCP Connect page opens in your browser: click **Connect**.
2. Back in your AI, say **"connect my WhatsApp"**. It shows a QR code to scan (WhatsApp → Settings → Linked devices → Link a device), or gives you a pairing code to enter on your phone.
3. Try it:
   - "Summarize my WhatsApp chats from today"
   - "Who is waiting for a reply from me?"
   - "Search my messages for the address Ana sent"
   - "Reply to Juan that I'll be there at 7"

Your AI shows you a draft and asks before sending anything you didn't dictate.

## Tools

| Tool | What it does |
|---|---|
| `get_recent_chats` | Lists your latest chats |
| `get_unanswered_chats` | Chats where the last message is waiting for your reply |
| `read_chat_history` | Reads the messages of one chat |
| `search_messages` | Searches your messages by text |
| `search_contacts` | Finds people and groups by name or number |
| `download_media` | Opens a photo, voice note or document you received |
| `get_writing_style` | Samples of how you write, so drafts sound like you |
| `send_message` | Sends a text, photo, video, voice note or document |
| `send_poll` | Sends a poll |
| `schedule_message` | Schedules a message, once or repeating |
| `list_scheduled_messages` / `cancel_scheduled_message` | Manages scheduled messages |
| `react_to_message` / `edit_message` / `delete_message` | Reacts to, edits or deletes a message |
| `mark_as_read` / `mark_as_unread` | Marks a chat as read or unread |
| `get_session_status` / `request_pairing_code` / `get_pairing_qr` / `restart_session` | Links WhatsApp and checks the connection |
| `manage_subscription` | Shows your plan |
| `report_feedback` | Sends feedback or a bug report |
| `unlink_whatsapp` / `delete_account` | Unlinks your number or deletes your account |

## Plans

- **Free:** every new number starts with 1 hour of full Pro. After that the Free plan keeps reading, summarizing and searching chats and sending text messages to people who've written to you; messages you send end with "Sent via wa-mcp.com".
- **Pro** (US$9/month, less when billed quarterly or annually): no label, plus files, polls, scheduling, editing, reactions, deleting, and starting new conversations with anti-ban protection. Ask your AI to subscribe; it gives you a Stripe checkout link.

## Privacy and safety

- WA MCP links as a WhatsApp linked device, like WhatsApp Web. You can unlink it any time from your phone or with `unlink_whatsapp`.
- Messages go out at a human pace, and new conversations are protected against WhatsApp's anti-spam rules.
- [Privacy policy](https://wa-mcp.com/privacy) · [Terms](https://wa-mcp.com/terms)

## Support

support@wa-mcp.com

WA MCP is an independent product and is not affiliated with, endorsed by or sponsored by WhatsApp or Meta.
