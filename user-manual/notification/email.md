# Email

This notification method utilizes an SMTP server to deliver status updates as mail messages.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `server`: The server hostname or IP and port that accepts SMTP messages
* `username`: A username to authenticate to the remote mail server
* `passord`: The password
* `to`: List of email addresses, separated by **`;`**, for the notification messages to be send

Example:

```
# Notification Configuration
notify:
  email:
    - name: "XXX Mail List"
      server: smtp.email.example.com:465
      username: user@example.com
      password: ********
      to: "user1@example.com;user2@example.com"
      from: "from@example.com" # Optional
      # dry: true # dry notification, print the Email HTML in log(STDOUT)      
```
