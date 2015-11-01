# step-slack

A slack notifier written in `bash` and `curl`. Make sure you create a Slack
webhook first (see the Slack integrations page to set one up).

[![wercker status](https://app.wercker.com/status/94f767fe85199d1f7f2dd064f36802bb/s "wercker status")](https://app.wercker.com/project/bykey/94f767fe85199d1f7f2dd064f36802bb)

# Options

- `url` The Slack webhook url
- `username` Username of the notification message
- `channel` (optional) The Slack channel (excluding `#`)
- `icon_url` (optional) A url that specifies an image to use as the avatar icon in Slack
- `notify_on` (optional) If set to `failed`, it will only notify on failed
builds or deploys.
- `branch` (optional) If set, it will only notify on the given branch
- `target` (optional) If set, during deploy it will only notify if deploy targets match
- `passed_msg` (optional) Custom message for passed builds
- `failed_msg` (optional) Custom message for failed builds


# Example

```yaml
build:
    after-steps:
        - slack-notifier:
            url: $SLACK_URL
            channel: notifications
            username: myamazingbotname
            branch: master
```

The `url` parameter is the [slack webhook](https://api.slack.com/incoming-webhooks) that wercker should post to.
You can create an *incoming webhook* on your slack integration page.
This url is then exposed as an environment variable (in this case
`$SLACK_URL`) that you create through the wercker web interface as *deploy pipeline variable*.

# License

The MIT License (MIT)

# Changelog

## 1.3.1

- added `target` option
- added `passed_msg` and `failed_msg` options for custom messages

## 1.2.0

- added `branch` option

## 1.1.0

- `channel` is now optional (wercker/step-slack#5)

## 1.0.0

- Initial release
