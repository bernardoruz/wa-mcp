# WA MCP

<img src="assets/logo.png" alt="WA MCP logo" width="96">

WA MCP is a hosted WhatsApp MCP server: connect your own WhatsApp to your AI. Ask it to catch you up on your chats, find a message, see who's waiting for a reply, or write and send messages for you, all from the conversation.

WA MCP is a hosted [Model Context Protocol](https://modelcontextprotocol.io) server. There is nothing to install or run: add the URL, sign in, and link your WhatsApp number by QR code or pairing code. Website: [wa-mcp.com](https://wa-mcp.com/?utm_source=github&utm_medium=directory).

This repository holds the plugin manifest and docs only. The server itself is closed source and runs on our own servers; see [Security and data](#security-and-data) for what it stores and what it can do.

**Operator:** WA MCP is built and run by Bernardo Ruz, Canada. Contact: support@wa-mcp.com.

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

### Claude Code

WA MCP gives Claude Code access to your own WhatsApp chats. (It isn't a channel for controlling Claude Code from WhatsApp.)

- **Through claude.ai:** in Claude, Settings → Connectors → Add custom connector → `https://server.wa-mcp.com/mcp`, then click **Connect** on the WA MCP page. Claude Code picks up your claude.ai connectors by itself (terminal, desktop app, VS Code and Claude Code on the web).
- **Or from the terminal:** `claude mcp add --transport http wa-mcp https://server.wa-mcp.com/mcp`, then sign in on the WA MCP page that opens.

Then ask Claude Code "connect my WhatsApp" and scan the QR code. You can also get a personal link at [wa-mcp.com](https://wa-mcp.com/?utm_source=github&utm_medium=directory).

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
| `transcribe_voice_note` | Turns voice notes into text |
| `get_writing_style` | Samples of how you write, so drafts sound like you |
| `send_message` | Sends a text, photo, video, voice note or document |
| `send_poll` | Sends a poll |
| `schedule_message` | Schedules a message, once or repeating |
| `list_scheduled_messages` / `cancel_scheduled_message` | Manages scheduled messages |
| `react_to_message` / `edit_message` / `delete_message` | Reacts to, edits or deletes a message |
| `mark_as_read` / `mark_as_unread` | Marks a chat as read or unread |
| `delete_chat` / `archive_chat` | Deletes or archives a whole chat |
| `get_session_status` / `request_pairing_code` / `get_pairing_qr` / `restart_session` | Links WhatsApp and checks the connection |
| `link_with_passkey` | Links WhatsApp when it asks for a passkey |
| `manage_subscription` | Shows your plan |
| `report_feedback` | Sends feedback or a bug report |
| `leave_review` | Gives the link to leave a public review |
| `unlink_whatsapp` / `delete_account` | Unlinks your number or deletes your account |

## Plans

- **Free:** no time limit and no request cap. Reads, summarizes and searches 90 days of history, and sends text replies to people who've written to you. Messages you send on the free plan end with a visible "Sent via wa-mcp.com" line; the send tool's description says so, so your AI knows before it sends. Pro removes it. Every new number also starts with 1 hour of full Pro.
- **Pro** (US$9/month, US$7/month billed quarterly or US$4/month billed annually): no label, plus files, voice-note transcription, polls, scheduling, editing, reactions, deleting, and starting new conversations with send limits. Ask your AI to subscribe; it gives you a Stripe checkout link.

## Security and data

- **How it connects.** WA MCP links to your WhatsApp as a linked device, the same way WhatsApp Web does. It is not Meta's official WhatsApp Business API. WhatsApp may restrict numbers it sees as automated; WA MCP paces sends and limits new conversations, but no tool can promise WhatsApp will never restrict a number.
- **Closed source.** The plugin is only a pointer to `https://server.wa-mcp.com/mcp`. The server code is not public and can be updated by the operator at any time.
- **What is stored.** On the server that runs your linked device: message text and details (sender, chat, time, type), contact and group names, and the linked-device session keys. Photos, videos, voice notes and documents are not stored; a file is fetched from WhatsApp only when your AI asks for it.
- **How long.** Message text is deleted automatically 90 days after it is stored. Deleting your account removes stored messages; you can also delete a single chat.
- **Who reads it.** Your AI receives message text only when it calls a tool for you. We don't sell messages, use them for ads or train AI models on them. Voice notes go to Google's Gemini only when you ask for a transcript. Traffic is encrypted (TLS); stored text is not encrypted with a key only you hold.
- **What your AI can do.** Read and search about 90 days of chats, and send to one person or one group at a time (no bulk sending). On Pro it can also send files, schedule, edit, react to and delete messages. The server tells your AI to show you a draft and ask before sending anything you didn't dictate, and deleting a chat or your account needs an explicit confirmation.
- **Treat messages as untrusted.** Messages from other people are data, not instructions. Don't let your AI act on requests that appear inside a chat without checking with you.
- **Stop any time.** Unlink with `unlink_whatsapp` or on your phone under **Settings → Linked devices**; `delete_account` removes your account and stored messages.
- [Privacy policy](https://wa-mcp.com/privacy) · [Terms](https://wa-mcp.com/terms)

## Support

support@wa-mcp.com

WA MCP is an independent product, not affiliated with or endorsed by WhatsApp LLC or Meta Platforms, Inc. WhatsApp is a trademark of WhatsApp LLC.
