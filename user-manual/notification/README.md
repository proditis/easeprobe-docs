# Notification

EaseProbe supports a variety of notifications. The notifications are **Edge-Triggered**, this means that these notifications are triggered when the status changes.

Each notification is identified by the delivery it supports (eg `slack`), a unique name (across all notifies in the configuration file) and (optionally) the notify specific parameters.

And please be aware that the following configuration:

1.  Setting the environment variables `$HTTP_PROXY` & `$HTTPS_PROXY` allows for configuring the proxy settings for all HTTP related webhook notifications such as discord, slack, telegram etc.

    ```shell
    export HTTPS_PROXY=socks5://127.0.0.1:1080
    ```
2.  All of the notifications support the `dry`, `timeout`, and `retry` optional configuration parameters. For example:

    ```
    notify:
      - name: "slack"
        webhook: "https://hooks.slack.com/services/xxxxxx"
        dry: true # dry notification, print the Discord JSON in log(STDOUT)
        timeout: 20s # the timeout send out notification, default: 30s
        retry: # somehow the network is not good and needs to retry.
          times: 3 # default: 3
          interval: 10s # default: 5s
    ```
3.  We can configure the general notification settings in the `notify` section of the configuration file.

    The following configuration is effective for all notification, unless the notification has its own configuration.

    ```yaml
    settings:
      notify:
        dry: true # Global settings for dry run, default is false
        retry: # the retry setting to send the notification
          times: 5 # retry times, default is 3
          interval: 10s # retry interval, default is 5s
    ```

For a complete list of examples using all the notifications please check the Notification Configuration section.

> **Note**:
>
> 1. Setting the environment variables `$HTTP_PROXY` & `$HTTPS_PROXY` allows for configuring the proxy settings for all HTTP related webhook notifications such as discord, slack, telegram etc.
> 2.  All of the notifications support the following optional configuration parameters.
>
>     ```
>     dry: true # dry notification, print the Discord JSON in log(STDOUT)
>     timeout: 20s # the timeout send out notification, default: 30s
>     retry: # somehow the network is not good and needs to retry.
>       times: 3 # default: 3
>       interval: 10s # default: 5s
>     ```
