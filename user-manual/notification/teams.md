# Teams

This notification method utilizes the Microsoft Teams connectors to deliver status updates as messages.

Support the notification.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  teams:
      - name: "teams alert service"
        webhook: "https://outlook.office365.com/webhook/a1269812-6d10-44b1-abc5-b84f93580ba0@9e7b80c7-d1eb-4b52-8582-76f921e416d9/IncomingWebhook/3fdd6767bae44ac58e5995547d66a4e4/f332c8d9-3397-4ac5-957b-b8e3fc465a8c"
```

For more details you can visit:

* [Microsoft Teams Create and send messages](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-using?tabs=cURL#setting-up-a-custom-incoming-webhook)
* [Microsoft Teams actionable messages](https://docs.microsoft.com/en-us/outlook/actionable-messages/send-via-connectors)
