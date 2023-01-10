# WeChat Work

Support Enterprise WeChat Work notification.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `webhook`: The URL for the webhook

Example:

```
# Notification Configuration
notify:
  wecom:
    - name: "wecom alert service"
      webhook: "https://qyapi.weixin.qq.com/cgi-bin/webhook/send?key=589f9674-a2aa-xxxxxxxx-16bb6c43034a" # wecom robot webhook
```
