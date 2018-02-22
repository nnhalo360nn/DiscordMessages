## Introduction

This plugin is for those who are unable to setup real discord bots or do not have the hardware for it. DiscordMessages makes use of the webhook function of Discord therefore you do not need any dependencies to get up and running!

## Features

All of these features can be enabled/disabled via the config.
- Ban - (/ban) - Allows a player with permission to ban another player and have the message announced to the server and sent to discord, this replaces the vanilla ban command but works better in the way that it lets you ban offline players with simplicity.
- Report - (/report) - Allows a player with permission to report another player and have their message sent to discord.
- Mute Messages - (Requires BetterChatMute) - When a player is muted via BetterChatMute a message is sent to Discord.
- Message - (/message) - Allows a player with permission to send a message to Discord.
- Server Chat - Posts to discord once a player types in chat with the option to enable TTS (Text To Speech) 

## Dependencies

### Optional

- [Better Chat Mute](https://umod.org/plugins/betterchatmute)

## Commands

() = Required - {} = Optional
- /report (player) (message) - This will send a report to the discord channel.
- /ban (player) {message} - This will ban the player and send it to the specified discord channel.
- /message (message) - Sends a message to discord.

## Permissions

- discordmessages.report
- discordmessages.ban
- discordmessages.message


## API

There are two API methods. API_SendFancyMessage will send an Embedded message while API_SendTextMessage will send a generic text message.
```cs
DiscordMessages?.Call("API_SendFancyMessage", (string)WebhookURL, (string)EmbedTitle, (int)EmbedColor, (JSON)Fields);
DiscordMessages?.Call("API_SendTextMessage", (string)WebhookURL, (string)Message);
 ```
 
 In order to create the fields required for an Embedded message you simply create an fields object with an array of fields as follows.
 
```cs
object fields = new[]
{
  new {
    name = "Field1 Title", value = "Field1 Value", inline = true
  },
  new {
    name = "Field2 Title", value = "Field2 Value", inline = false
  }
};
string json = JsonConvert.SerializeObject(fields);
DiscordMessages?.Call("API_SendFancyMessage", (string)WebhookURL, (string)EmbedTitle, (int)EmbedColor, json);
```
