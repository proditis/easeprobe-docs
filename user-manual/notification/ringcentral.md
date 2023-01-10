# RingCentral

This notification method utilizes the RingCentral webhooks to deliver status updates as messages.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  ringcentral:
    - name: "MegaEase#Alert"
      webhook: "https://hooks.ringcentral.com/webhook/v2/.........."
```
