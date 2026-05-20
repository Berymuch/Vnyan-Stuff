# NODEGRAPH ACTION LIST

Welcome to the web page made for listing all of the nodegraphs/actions provided with the Vnyan logic built and maintained by [Berymuch](https://www.twitch.tv/berymuch). All nodegraphs are created by me~ :3

> [!NOTE]
> Many of the actions in this bot are in active development and also update irregularly. Documentation reflects the latest version of Botymuch.

*Current Action count: 129*
PiShock | Commands | Spinning Prizewheel & Chat GPT Integrations | Twitch API
:---: | :---: | :---: | :---:
[PiShock - Twitch Interactions](#PiShock---Twitch-Interactions) | [Broadcaster Commands](#Broadcaster-Commands) | [Spinning Prize Wheel](#Spinning-Prize-Wheel) | [Passive OBS Interactions](#Passive-OBS-Interactions)
[PiShock V2 - Core](#PiShock-V2---Core) | [Chat Command Unit Conversion](#Chat-Command-Unit-Conversion) | [Spinning Prize Wheel - Custom](#Spinning-Prize-Wheel---Custom) | [Redeems](#Redeems)
[PiShock V2 - Examples](#PiShock-V2---Examples) | [Chat Commands](#Chat-Commands) | [Spinning Prize Wheel - User Group](#Spinning-Prize-Wheel---User-Group) | [Twitch interactions](#Twitch-interactions)
[PiShock V2 - Operations](#PiShock-V2---Operations) | [Moderator Commands](#Moderator-Commands) | [Mustached_Maniac ChatGPT](#Mustached_Maniac-ChatGPT) | [𝘼𝙋𝙄𝙓 Logging](#𝘼𝙋𝙄𝙓-Logging)

***

<a name="Broadcaster-Commands"></a>
## Nodegraph Group

Nodegraph Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---:
Disabler/Enabler (Nuts) | 🟩 | 🟥 | This action works as both a chat command (using !non and !noff) and as an action switch button via the Elgato Streamdeck/vnyan logic to toggle chat redeems on and off (streamdeck functions target the default case on the switchcase tree). In order to sync logic states across all three applications, a temp global variable is set when streamerbot is loaded and referenced to determine which state is currently true. The intended default is to have nut interactions "on" when the stream is first launched. The action also integrates a live on-stream display to show more easily to viewers whether the current state is active/inactive. | [Berymuch](https://www.twitch.tv/Berymuch)
Disabler/Enabler (PiShock) | 🟩 | 🟥 | This action works as an action switch button via the Elgato Streamdeck to toggle PiShock functions on and off. In order to sync logic states across the streamdeck and streamerbot, a temp global variable is set when streamerbot is loaded and referenced to determine which state is currently true. The intended default is to have PiShock interactions "on" when the stream is first launched. The action also integrates a live on-stream display to show more easily to viewers whether the current state is active/inactive. | [Berymuch](https://www.twitch.tv/Berymuch)
Disabler/Enabler (Redeems) | 🟩 | 🟥 | This action works as both a chat command (using !ron and !roff) and as an action switch button via the Elgato Streamdeck/vnyan logic to toggle chat redeems on and off (streamdeck functions target the default case on the switchcase tree). In order to sync logic states across all three applications, a temp global variable is set when streamerbot is loaded and referenced to determine which state is currently true. The intended default is to have redeem interactions "on" when the stream is first launched. The action also integrates a live on-stream display to show more easily to viewers whether the current state is active/inactive. | [Berymuch](https://www.twitch.tv/Berymuch)
Disabler/Enabler (Share Browser) | 🟩 | 🟥 | This action works as an action switch button via the Elgato Streamdeck to toggle on-stream browser sharing functions on and off. In order to sync logic states across the streamdeck and streamerbot, a temp global variable is set when streamerbot is loaded and referenced to determine which state is currently true. The intended default is to have browsershare interactions "off" when the stream is first launched. The action also integrates a live on-stream display to show more easily to viewers whether the current state is active/inactive. | [Berymuch](https://www.twitch.tv/Berymuch) | [Berymuch](https://www.twitch.tv/Berymuch)
Disabler/Enabler (Share Screen) | 🟩 | 🟥 | This action works as an action switch button via the Elgato Streamdeck to toggle on-stream screen sharing functions on and off. In order to sync logic states across the streamdeck and streamerbot, a temp global variable is set when streamerbot is loaded and referenced to determine which state is currently true. The intended default is to have screenshare interactions "off" when the stream is first launched. The action also integrates a live on-stream display to show more easily to viewers whether the current state is active/inactive. | [Berymuch](https://www.twitch.tv/Berymuch)
Emergency Mode | 🟩 | 🟥 | A general kill switch to be used in the event of something like a hate raid or other negative channel event. It toggles shield mode/subscriber only mode/stream labels/onstream chat/vtuber/and browser overlays off and on. A confirmation message is also sent to chat. | [Berymuch](https://www.twitch.tv/Berymuch)
Gacha Mode | 🟥 | 🟥 | Controls whether or not the Chat gacha features are enabled or disabled. A general killswitch activated with the associated command. | [ItzApix_](https://www.twitch.tv/ItzApix_)
Nom mode | 🟥 | 🟥 | Controls whether or not the nom command features are enabled or disabled. A general killswitch activated with the associated command. | [ItzApix_](https://www.twitch.tv/ItzApix_)

***
