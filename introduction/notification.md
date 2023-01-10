# Notification

EaseProbe supports notification delivery to the following:

* **Slack**. Using Slack Webhook for notification delivery
* **Discord**. Using Discord Webhook for notification delivery
* **Telegram**. Using Telegram Bot for notification delivery
* **Teams**. Support the [Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-using?tabs=cURL#setting-up-a-custom-incoming-webhook) notification delivery
* **Email**. Support email notification delivery to one or more email addresses
* **AWS SNS**. Support the AWS Simple Notification Service
* **WeChat Work**. Support Enterprise WeChat Work notification delivery
* **DingTalk**. Support the DingTalk notification delivery
* **Lark**. Support the Lark(Feishu) notification delivery
* **SMS**. SMS notification delivery with support for multiple SMS service providers
  * [Twilio](https://www.twilio.com/sms)
  * [Vonage(Nexmo)](https://developer.vonage.com/messaging/sms/overview)
  * [YunPain](https://www.yunpian.com/doc/en/domestic/list.html)
* **Log**. Write the notification into a log file or syslog.
* **Shell**. Run a shell command to deliver the notification (see example)
* **RingCentral**. Using RingCentral Webhook for notification delivery

> **Note**:
>
> 1. The notification are in **Edge-Triggered Mode**, this means that these notifications are triggered when the status changes.
> 2. Windows platforms do not support syslog as notification method.

Check the Notification Configuration sections of the user manual to see configuration details.
