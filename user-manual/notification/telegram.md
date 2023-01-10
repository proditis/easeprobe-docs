# Telegram

This notification method utilizes a Telegram Bot to deliver status updates as messages to a Channel or Group.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `token`: The authorization token for the bot
* `chat_id`: The Telegram Channel or Group ID

Example:

```
# Notification Configuration
notify:
  telegram:
    - name: "Group Name"
      token: 1234567890:ABCDEFGHIJKLMNOPQRSTUVWXYZ # Bot Token
      chat_id: -123456789 # Group ID
    - name: "Channel Name"
      token: 1234567890:ABCDEFGHIJKLMNOPQRSTUVWXYZ # Bot Token
      chat_id: -1001234567890 # Channel ID
```
