# Lark

Support the Lark (Feishu) notification.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  lark:
    - name: "lark alert service"
      webhook: "https://open.feishu.cn/open-apis/bot/v2/hook/d5366199-xxxx-xxxx-bd81-a57d1dd95de4"
```
