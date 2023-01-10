# DingTalk

Support the DingTalk notification.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook
* `secret`: Optionally a secret key to use

Example:

```
# Notification Configuration
notify:
  dingtalk:
    - name: "dingtalk alert service"
      webhook: "https://oapi.dingtalk.com/robot/send?access_token=xxxx"
      secret: "" # sign secret if set
```
