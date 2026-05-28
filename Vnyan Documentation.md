# NODEGRAPH ACTION LIST

Welcome to the web page made for listing all of the nodegraphs/actions provided with the Vnyan logic built and maintained by [Berymuch](https://www.twitch.tv/berymuch). All nodegraphs are created by me~ :3

> [!NOTE]
> This is a work in progress

User Interactions | Input Tracking | Avatar | Commands
:---: | :---: | :---: | :---:
[Startup & Shortcuts](#Startup-and-Shortcuts) | [Controller With Button Tracking](#Controller-With-Button-Tracking) | [VTuber Logic](#VTuber-Logic) | [Chat Commands](#Chat-Commands)
[Passive Interactions](#Passive-Interactions) | [Pen and Tablet Tracking](#Pen-and-Tablet-Tracking) | [PNGTuber Logic](#PNGTuber-Logic) | [Nut Command](#Nut-Command)
[Active Interactions](#Active-Interactions) | [Input Animations](#Input-Animations) |  | 

***

<a name="Startup-and-Shortcuts"></a>
## Startup and Shortcuts

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Application Start Commands | 🟩 | 🟥 | Various | Runs logic that configures aspects of the VNyan setup when the application is started. These include things such as: setting window resolution, loads a specific avatar model file, sets blendshape values, and a plays a looping default idle animation, and configures camera parameters. The biggest aspect of this nodegraph is the parameter values it sets near the bottom. All of these are referenced by various other nodegraphs in my setup, and assume these parameter values as a baseline when Vnyan is launched.
BRB Backrooms | 🟩 | 🟩 | ScreenshotActive, BRBStatus, BRBstatusShout, CameraZoomBRB, TFtransitiontime, CameraFocalLengthBRB | Uses input from a websocket message to swap to a "BRB Screen" type layout. The initial message calls a parameter that is used to switch on/off states for the nodegraph. When on, the logic will load the specified world file, engage looping randomized camera behaviors, send a confirmation message to chat, and toggle various graphical effects and props. When off, these settings are then reverted to the baseline.
BRB Clip Shoutouts | 🟩 | 🟥 | BRBstatusShout, BRBstatus, wereberyloaded | Uses input from a websocket message to configure a BRB screen tailored shoutout display. The "start" websocket message engages the changes, while the "end" websocket message reverts to the base BRB screen configuration. Locks the camera to a set position while active, and uses a modified camera when the specified vtuber model is active. the starting soon trigger will adapt the current camera to suit whatever model is currently active if the mdoel is changed while the brb player is currently playing. Relies on a spout2 projection prop from a clip player in OBS in order to function.
Starting Soon & Ending Screen Scene Swaps | 🟩 | 🟥 | StartingSoonSwitch, EndingSceneSwitch | Uses input from a websocket message to swap to a "starting" and/or "ending" type layout. The initial message calls a parameter that is used to switch on/off states for the nodegraph. When on, the logic will load the specified world file, engage camera behaviors, and toggle various graphical effects and props. When off, these settings are then reverted to the baseline.
Camera Websocket Commands | 🟩 | 🟥 | PNGZoom, pngcamerazoompause | Uses various websocket messages to toggle particularly cameras in vnyan.

***

<a name="Active-Interactions"></a>
## Active Interactions

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Amazon'd | 🟩 | 🟩 | Zawarudokillswitch | When the channel point redeem is used, this logic will drop the specified items and play specified SFX only if the killswitch is not currently active. If it is, the signal is dropped. Also contains generalized logic to trigger a SFX when an item with the itemtag "box" collides with the vtuber model.
Anvil Drop | 🟩 | 🟩 | Zawarudokillswitch, StunnedExec | Used to drop the specified props on the vtuber model, as well as engage behaviors via baked in parameters on these props. Also modifies bone scaling of specified bones as well as ragdolling the mode and triggering specified SFX.
Za Warudo Timer | 🟩 | 🟩 | Zawarudokillswitch, NutZawarudokillswitch | When used, this command acts as a general killswitch for all other redeems and various other nodegraph logic trees. Functions include taking a screenshot when the za warudo redeem is engaged and toggling various other GFX and SFX in vnyan. This command also can have aspects of it triggered via websocket messages.
The Beans | 🟩 | 🟩 | Zawarudokillswitch, CameraLock, StartingSoonSwitch, PNGberyloaded, LightFormActive | Used to engage logic for the beans redeem. When active, it will modify the camera, lock it in place, trigger various GFX and SFX, reset bone scaling to the default value, and toggle various props. Also checks to see if the Starting soon scene is currently active. If so, it will adjust behavior to ensure that the props in that scene are not put into conflict with the logic in either graph.
Run an Ad! | 🟩 | 🟩 | Zawarudokillswitch | Used to play the specified SFX and GFX when the specified redeem is triggered and if the killswitch is not currently active. Works in tandem with my Redeem logic in StreamerBot.
Nom | 🟩 | 🟩 | Zawarudokillswitch, PNGberyloaded, wereberyloaded | Used to trigger the specified GFX and SF when the specified channel point redeem is triggered. If a PNGTuber is currently active, the food item will not be spawned and only the SFX will play. If the specified VTuber is active, a larger form of the food wil be spawned instead.
Build a Nut | 🟩 | 🟩 | VIPNutActive | Used to engage the specified GFX and SFX when the specified channel point redeem is used. This command also integrates with the specified OBS sources and text files to engage further functionality.
Destroy | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Pets | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Throw | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
No Horny | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Munch Speaks! | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Love | 🟩 | 🟥 | Zawarudokillswitch, redeemer | Used to trigger logic that toggles the specified GFX and SFX if the killswitch is not enabled. Also uses the "redeemer" parameter to set the user's username as part of the dropped chatBlob object.
Hydrate | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Goo | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Lightform | 🟩 | 🟩 | Zawarudokillswitch, LightFormActive, LightFormBloom, LightFormBloomTransition | Used to trigger the lightform effect when the specified channel point redeem is triggered and activates specified GFX, SFX, and sources in OBS. When activated, the logic triggers a timer loop that increments the LightFormBloomVariable by the specified amount every 100ms. That parameter gradually icnreases the intensity of the bloom effect, and resets to zero/disables once the value of the parameter hits the threshold specified by the LightFormBloomTransitions parameter. Also activates the specified blendshape parameters when used.
Fuzzy Fact | 🟩 | 🟥 | Zawarudokillswitch | Used to take user input when redeemed and share it via Squawk TTS in chat when set up as an OBS audio source. This command will play the specified SFX, add the user input received when redeemed as a line to the specified file, will read/modify/save the specified array to that file, and is intended to work in tandom with my !fuzzyfact command in streamerbot.The !fuzzyfact command in streamerbot will need to have its execute code modified with any additional lines as they are not automatically appended to the code logic.
Plap | 🟩 | 🟩 | Zawarudokillswitch, TongueTimer, wereberyloaded | Used to trigger behavior that extends the vtuber's tongue via blendshape value modification, automatically retracts it based on that randomized interval, allows for variation between active vtubers, and can be interfaced with via the "!itsout" chat command in my streamerbot logic through the websocket trigger. Also plays the specified SFX.
Xerox | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Tummy Timeout Redeem | 🟩 | 🟩 | Zawarudokillswitch | Placeholder
Workout Gacha | 🟩 | 🟥 | Zawarudokillswitch | Placeholder
Question | 🟩 | 🟥 | Zawarudokillswitch | Placeholder

***

<a name="Passive-Interactions"></a>
## Passive Interactions

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Sub/Chat Message Indicator | 🟩 | 🟩 | Placeholder | Placeholder
Feed Me Effect | 🟩 | 🟩 | Placeholder | Placeholder
Walkons | 🟩 | 🟩 | Placeholder | Placeholder
Headpat | 🟩 | 🟩 | Placeholder | Placeholder
On Hypetrain | 🟩 | 🟥 | Placeholder | Placeholder
Goal Celebration | 🟩 | 🟥 | Placeholder | Placeholder
On Subscription | 🟩 | 🟥 | Placeholder | Placeholder
Hype Train Events | 🟩 | 🟩 | Placeholder | Placeholder
Raid & Shoutout Events | 🟩 | 🟩 | Placeholder | Placeholder
Horny Jail & Bonk | 🟥 | 🟩 | Placeholder | Placeholder
Wolf Kisser | 🟥 | 🟩 | Placeholder | Placeholder
Ban User | 🟥 | 🟩 | Placeholder | Placeholder
Yarr | 🟥 | 🟩 | Placeholder | Placeholder
Deer Command | 🟩 | 🟩 | Placeholder | Placeholder
Edge Command | 🟥 | 🟩 | Placeholder | Placeholder
Scene Lighting Activated | 🟥 | 🟩 | Placeholder | Placeholder
Emote Dropper | 🟩 | 🟥 | Placeholder | Placeholder
On Ad Break | 🟩 | 🟩 | Placeholder | Placeholder
On Follow | 🟩 | 🟥 | Placeholder | Placeholder
Pyramid 5 Or Higher | 🟩 | 🟥 | Placeholder | Placeholder
Bits Multiples Effects| 🟩 | 🟩 | Placeholder | Placeholder
Compare Multiples On Bits Donation | 🟩 | 🟩 | Placeholder | Placeholder

***

<a name="Chat-Commands"></a>
## Chat Commands

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Roll Dice Command (Subscribers & Regular) | 🟩 | 🟩 | Placeholder | Placeholder
Pool's Opened & Closed | 🟩 | 🟥 | Placeholder | Placeholder

***

<a name="Nut-Command"></a>
## Nut Command

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Nut Ban & Unban commands | 🟥 | 🟥 | Placeholder | Placeholder
Nut On/Off Command | 🟥 | 🟥 | Placeholder | Placeholder
Core Logic | 🟩 | 🟩 | Placeholder | Placeholder
Grifter Nut | 🟩 | 🟩 | Placeholder | Placeholder
AerialAbhorsen Nut | 🟩 | 🟩 | Placeholder | Placeholder
Zementh's 360 Nut | 🟩 | 🟩 | Placeholder | Placeholder
Krowkaws Nut | 🟩 | 🟩 | Placeholder | Placeholder
Fuscus Nut | 🟩 | 🟩 | Placeholder | Placeholder
Fist of the North Star Nut | 🟩 | 🟩 | Placeholder | Placeholder
Win95 Nut | 🟩 | 🟩 | Placeholder | Placeholder
Baby Nut | 🟩 | 🟩 | Placeholder | Placeholder
Flashbang Nut | 🟩 | 🟩 | Placeholder | Placeholder
Semphelis Nut | 🟩 | 🟩 | Placeholder | Placeholder
Loot Nut | 🟩 | 🟩 | Placeholder | Placeholder
Snow Nut | 🟩 | 🟩 | Placeholder | Placeholder
Protec Nut | 🟩 | 🟩 | Placeholder | Placeholder
Spiderverse Nut | 🟩 | 🟩 | Placeholder | Placeholder
Nutella Nut | 🟩 | 🟩 | Placeholder | Placeholder
Wolfen_ll Nut | 🟩 | 🟩 | Placeholder | Placeholder
StevenLucario Nut | 🟩 | 🟩 | Placeholder | Placeholder
Pickle Nut | 🟩 | 🟩 | Placeholder | Placeholder
Nice Nut | 🟩 | 🟩 | Placeholder | Placeholder
400 Nut | 🟩 | 🟩 | Placeholder | Placeholder
402 Nut | 🟩 | 🟩 | Placeholder | Placeholder
418 Nut | 🟩 | 🟩 | Placeholder | Placeholder
SwelterDemon Nut | 🟩 | 🟩 | Placeholder | Placeholder
Noodle Nut | 🟩 | 🟩 | Placeholder | Placeholder
Max Damage Nut | 🟩 | 🟩 | Placeholder | Placeholder
401 Nut | 🟩 | 🟩 | Placeholder | Placeholder
403 Nut | 🟩 | 🟩 | Placeholder | Placeholder
Pi Nut | 🟩 | 🟩 | Placeholder | Placeholder
No Clothes Nut | 🟩 | 🟥 | Placeholder | Placeholder
Jade Save Nut | 🟩 | 🟩 | Placeholder | Placeholder
RoseEclipz's Nut | 🟩 | 🟩 | Placeholder | Placeholder
Nut 42 | 🟩 | 🟩 | Placeholder | Placeholder
Nut 666 | 🟩 | 🟩 | Placeholder | Placeholder
404 Nut | 🟩 | 🟩 | Placeholder | Placeholder
Nut 621 | 🟩 | 🟩 | Placeholder | Placeholder
Grizz Nut 2 (Tornado) | 🟩 | 🟩 | Placeholder | Placeholder
Tannyk Nut | 🟩 | 🟩 | Placeholder | Placeholder
TopHatTig Nut | 🟩 | 🟩 | Placeholder | Placeholder
itzApix Nut | 🟩 | 🟩 | Placeholder | Placeholder
Lunai Nut | 🟩 | 🟩 | Placeholder | Placeholder
Sabadar Nut | 🟩 | 🟩 | Placeholder | Placeholder
TheEarthling Nut | 🟩 | 🟩 | Placeholder | Placeholder
RiccyThicc Nut | 🟩 | 🟩 | Placeholder | Placeholder
InkEDoodles Nut | 🟩 | 🟩 | Placeholder | Placeholder

***

<a name="VTuber-Logic"></a>
## VTuber Logic

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Blendshape Websocket Commands | 🟩 | 🟩 | Placeholder | Placeholder
Avatar Load Commands | 🟩 | 🟥 | Placeholder | Placeholder
Prop Loading Commands | 🟩 | 🟥 | Placeholder | Placeholder
Streamer Mod Alert | 🟩 | 🟥 | Placeholder | Placeholder
Volume Based Autofocus | 🟥 | 🟥 | Placeholder | Placeholder
Hat Change | 🟩 | 🟩 | Placeholder | Placeholder
Sun Glasses | 🟩 | 🟥 | Placeholder | Placeholder
Third Eye | 🟩 | 🟩 | Placeholder | Placeholder
Witch Hat | 🟩 | 🟩 | Placeholder | Placeholder
Teacher Glasses | 🟩 | 🟥 | Placeholder | Placeholder
VTuber Swaps | 🟩 | 🟩 | Placeholder | Placeholder

***

<a name="PNGTuber-Logic"></a>
## PNGTuber Logic

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Bery Specific Mods/Personalization | 🟩 | 🟥 | Placeholder | Placeholder
PNGTuber Core Logic (No Touchy) | 🟥 | 🟥 | Placeholder | Placeholder
Instructions & Setup | 🟥 | 🟥 | Placeholder | Placeholder
Websocket Triggers | 🟥 | 🟥 | Placeholder | Placeholder
Transformation Effect | 🟩 | 🟩 | Placeholder | Placeholder
Specific PNGTuber Effects | 🟩 | 🟩 | Placeholder | Placeholder
1PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder
2PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder
3PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder
4PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder
5PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder
6PNGTuber Graphic States | 🟩 | 🟥 | Placeholder | Placeholder

***

<a name="Pen-and-Tablet-Tracking"></a>
## Pen and Tablet Tracking

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Pen/Mouse Tracking for Drawing Streams | 🟩 | 🟥 | Placeholder | Placeholder
Pen Tracking (Right Hand Enabled) | 🟥 | 🟥 | Placeholder | Placeholder
Pen Tracking (Left Hand Enabled) | 🟥 | 🟥 | Placeholder | Placeholder

***

<a name="Controller-With-Button-Tracking"></a>
## Controller With Button Tracking

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Controller Pose | 🟩 | 🟥 | Placeholder | Placeholder
Controller Tracking (Right Hand) | 🟥 | 🟥 | Placeholder | Placeholder
Controller Tracking (Left Hand) | 🟥 | 🟥 | Placeholder | Placeholder

***

<a name="Input-Animations"></a>
## Input Animations

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Input Animations | 🟩 | 🟥 | Placeholder | Placeholder
Bery Specific Mods/Personalization | 🟩 | 🟥 | Placeholder | Placeholder


***
