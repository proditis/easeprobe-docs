# Slack

This notification method utilizes the Slack webhooks to deliver status updates as messages.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  slack:
    - name: "Organization #Alert"
      webhook: "https://hooks.slack.com/services/........../....../....../"
      # dry: true   # dry notification, print the Slack JSON in log(STDOUT)      
```

For more details you can visit the [Slack Webhooks API](https://api.slack.com/messaging/webhooks)
