# AWS SNS

Support AWS Simple Notification Service.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `region`: The region to use
* `arn`: The ARN
* `endpoint`: The endpoint URL
* `credential`: Credential section
  * `id`: The AWS ID
  * `key`: The AWS authorization key

Example:

```
# Notification Configuration
notify:
  aws_sns:
    - name: AWS SNS
      region: us-west-2 # AWS Region
      arn: arn:aws:sns:us-west-2:298305261856:xxxxx # SNS ARN
      endpoint: https://sns.us-west-2.amazonaws.com # SNS Endpoint
      credential: # AWS Access Credential
        id: AWSXXXXXXXID  # AWS Access Key ID
        key: XXXXXXXX/YYYYYYY # AWS Access Key Secret
```
