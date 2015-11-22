# Deprecated - current official [HipChat Plugin](https://wiki.jenkins-ci.org/display/JENKINS/HipChat+Plugin) supports HipChat Api V2 also for specific jobs. 

# HipChatNotifier Plugin

Uses HipChat API v2.

What makes it different from other HipChat Jenkins Plugins?

* it works because it uses latest HipChat APIv2 :)
* can specify token created by room owner (no more HipChat admin required!),
* can define token per job (no more global token for all jobs set by Jenkins Administrator!).

## Download plugin

If you don't want to compile plugin yourself, feel free to download [latest pre-compiled version](https://github.com/havramar/hipchat-notifier-plugin/releases/latest) (pick `hipchat-notifier.hpi`) and go to [uploading instructions](#upload-plugin).

## Compile plugin (Ubuntu)

If you want to compile plugin yourself, follow these steps:

```
sudo apt-get install openjdk-7-jdk maven2
git clone git@github.com:havramar/hipchat-notifier-plugin.git
cd hipchat-notifier-plugin
mvn package
```

As a result `target/hipchat-notifier.hpi` should be created. 

## <a name="upload-plugin"></a> Upload plugin to Jenkins

To upload it to Jenkins:
* run Jenkins (assuming it will run as http://localhost:8080),
* visit [Plugins Manager (advanced)](http://localhost:8080/pluginManager/advanced)
* pick path to plugin and submit,
* restart Jenkins.

## Authentication

Token types are described in [the API v2 docs](https://www.hipchat.com/docs/apiv2/auth).

This plugin works with API v2 tokens only! When switching from v1, get new one for v2.

## Configure

### Global Settings

Manage Jenkins -> System Settings -> Hip Chat Notifier (section)
  - your api token - https://{xxxx}.hipchat.com/account/api

### Job Settings

Job Page -> Configure -> Post-build Action (section) -> Add post-build action

### Normal

1. RoomName or RoomID
  - The name or id of the room which to notify
1. Auth token
  - API Access (personal),
  - Room Notification (created by room owner),
1. Message Format (SUCCESS)
1. Message Format (FAILED)
1. Message from file
  - Load notify message from file
  - ignore message format setting

### Advanced

1. post success notification
  - To set whether to notify if the build is successful
1. success notification to notify:true
  - To set whether to notify parameter of success notification to true
1. post failed notification
  - To set whether to notify if the build is failed
1. failed notification to notify:true
  - To set whether to notify parameter of failed notification to true
