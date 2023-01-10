# Discord

This notification method utilizes the Discord webhooks to deliver status updates as messages.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  discord:
    - name: "Server #Alert"
      webhook: "https://discord.com/api/webhooks/...../....../"
      # the avatar and thumbnail setting for notify block
      avatar: "https://img.icons8.com/ios/72/appointment-reminders--v1.png"
      thumbnail: "https://freeiconshop.com/wp-content/uploads/edd/notification-flat.png"
      # dry: true # dry notification, print the Discord JSON in log(STDOUT)
      retry: # something the network is not good need to retry.
        times: 3
        interval: 10s
```

For more details you can visit the [Discord Intro to Webhooks](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks)
