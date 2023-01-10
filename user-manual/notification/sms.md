# SMS

Support SMS notification with multiple SMS service providers

* [Twilio](https://www.twilio.com/sms)
* [Vonage(Nexmo)](https://developer.vonage.com/messaging/sms/overview)
* [YunPian](https://www.yunpian.com/doc/en/domestic/list.html)

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `provider`: SMS provider to use: **`yunpian`**, **`twilio`**, **`nexmo`**
* `key`: An API key to use for the SMS service
* `mobile`: The list of mobile numbers, separated by **`,`**, to send the notification
* `sign`: Sign name, needed to register; usually the brand name

Example:

```
# Notification Configuration
notify:
  sms:
    - name: "sms alert service - yunpian"
      provider: "yunpian"
      key: xxxxxxxxxxxx # yunpian apikey
      mobile: 123456789,987654321 # mobile phone number, multi phone number joint by `,`
      sign: "xxxxx" # get this from yunpian
```
