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
Camera Websocket Commands | 🟩 | 🟥 | PNGZoom, pngcamerazoompause | Uses various websocket messages to toggle specified cameras in vnyan.

***

<a name="Active-Interactions"></a>
## Active Interactions

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Amazon'd | 🟩 | 🟩 | Zawarudokillswitch | When the channel point redeem is used, this logic will drop the specified items and play specified SFX only if the killswitch is not currently active. If it is, the signal is dropped. Also contains generalized logic to trigger a SFX when an item with the itemtag "box" collides with the vtuber model.
Anvil Drop | 🟩 | 🟩 | Zawarudokillswitch, StunnedExec | Used to drop the specified props on the vtuber model, as well as engage behaviors via baked in parameters on these props. Also modifies bone scaling of specified bones as well as ragdolling the mode and triggering specified SFX.
Za Warudo Timer | 🟩 | 🟩 | Zawarudokillswitch, NutZawarudokillswitch, nutpauseswitch, ScreenshotActive | When used, this command acts as a general killswitch for all other redeems and various other nodegraph logic trees. Functions include taking a screenshot when the za warudo redeem is engaged and toggling various other GFX and SFX in vnyan. This command also can have aspects of it triggered via websocket messages.
The Beans | 🟩 | 🟩 | Zawarudokillswitch, CameraLock, StartingSoonSwitch, PNGberyloaded, LightFormActive | Used to engage logic for the beans redeem. When active, it will modify the camera, lock it in place, trigger various GFX and SFX, reset bone scaling to the default value, and toggle various props. Also checks to see if the Starting soon scene is currently active. If so, it will adjust behavior to ensure that the props in that scene are not put into conflict with the logic in either graph.
Run an Ad! | 🟩 | 🟩 | Zawarudokillswitch | Used to play the specified SFX and GFX when the specified redeem is triggered and if the killswitch is not currently active. Works in tandem with my Redeem logic in StreamerBot. In order for this action to function as intended, it must be pointed towards the "surprise expressions.txt" file stored to your preference on your PC. You can download this file from my vnyan github repository under "Text Files".
Nom | 🟩 | 🟩 | Zawarudokillswitch, PNGberyloaded, wereberyloaded | Used to trigger the specified GFX and SF when the specified channel point redeem is triggered. If a PNGTuber is currently active, the food item will not be spawned and only the SFX will play. If the specified VTuber is active, a larger form of the food wil be spawned instead.
Build a Nut | 🟩 | 🟩 | VIPNutActive | Used to engage the specified GFX and SFX when the specified channel point redeem is used. This command also integrates with the specified OBS sources and text files to engage further functionality.
Destroy | 🟩 | 🟩 | Zawarudokillswitch, PNGCamerZoomPause, CameraLock, PNGberyloaded, EndingSceneSwitch, ScreenshotActive | This action ragdolls your VTuber and PNGTuber (if using my logic) and dsiplays a dark souls style overlay to signify your demise. Colour grading is also applied to the PNGTuber to really put emphasis on the whole thing!
Pets | 🟩 | 🟩 | Zawarudokillswitch, PNGberyloaded, petsongplaying | Randomizes pets for a headpat redeem. Includes logic for both PNGTubers and Vtubers, and chooses a random pet based off configured props each time it is redeemed.
Throw | 🟩 | 🟩 | Zawarudokillswitch | Throws the specified amount of specified objects at the currently active model.
No Horny | 🟩 | 🟩 | Zawarudokillswitch | Tosses the specified amount of teh specified object at the currently active model and toggles the specified prop. Also sends a message to chat.
Munch Speaks! | 🟩 | 🟩 | Zawarudokillswitch | Triggers the Squawk TTS and reads out whatever the user has entered into the redeem text field.
Love | 🟩 | 🟥 | Zawarudokillswitch, redeemer | Used to trigger logic that toggles the specified GFX and SFX if the killswitch is not enabled. Also uses the "redeemer" parameter to set the user's username as part of the dropped chatBlob object.
Hydrate | 🟩 | 🟩 | Zawarudokillswitch, PNGberyloaded, HydrateActive, GrizzTornadoActive, wolfstarcooldown | This nut triggers GFX and SFX meant to represent a hydration effect. It works by using both Vnyan and OBS sources. Due to sharing particle effect slots with other commands, logic is included to check and see what is active when and respond accordingly. If a PNGTuber is active, it performs a simplified version of the logic.
Goo | 🟩 | 🟩 | Zawarudokillswitch, EndingSceneSwitch | Drops goo on the currently PNGTuber or Vtuber, and allows for the colour of the goo to be specified by th user via hex value or standard colour names. Also sets blendshapes to an expression of dread and engages colour grading FX if the ending scene is not currently active.
Lightform | 🟩 | 🟩 | Zawarudokillswitch, LightFormActive, LightFormBloom, LightFormBloomTransition | Used to trigger the lightform effect when the specified channel point redeem is triggered and activates specified GFX, SFX, and sources in OBS. When activated, the logic triggers a timer loop that increments the LightFormBloomVariable by the specified amount every 100ms. That parameter gradually icnreases the intensity of the bloom effect, and resets to zero/disables once the value of the parameter hits the threshold specified by the LightFormBloomTransitions parameter. Also activates the specified blendshape parameters when used.
Fuzzy Fact | 🟩 | 🟥 | Zawarudokillswitch | Used to take user input when redeemed and share it via Squawk TTS in chat when set up as an OBS audio source. This command will play the specified SFX, add the user input received when redeemed as a line to the specified file, will read/modify/save the specified array to that file, and is intended to work in tandom with my !fuzzyfact command in streamerbot. In order for this action to function as intended, it must be pointed towards the "Fuzzyfact responses.txt" file stored to your preference on your PC. You can download this file from my vnyan github repository under "Text Files". The !fuzzyfact command in streamerbot will need to have its execute code modified with any additional lines as they are not automatically appended to the code logic.
Plap | 🟩 | 🟩 | Zawarudokillswitch, TongueTimer, wereberyloaded | Used to trigger behavior that extends the vtuber's tongue via blendshape value modification, automatically retracts it based on that randomized interval, allows for variation between active vtubers, and can be interfaced with via the "!itsout" chat command in my streamerbot logic through the websocket trigger. Also plays the specified SFX.
Xerox | 🟩 | 🟩 | Zawarudokillswitch, TimeWarpCooldown | Triggers timewarp scan effect in OBS if the plugin is configured and randomizes the direction the scan progresses based off preconfigured timewarp filter settings (each OBS filter used is a seperately configured timewarp filter). It also zooms in on the model to do the scan, the resets the active camera to default once the scan has been completed. A screenshot of the scan is also saved to the local OBS recording directory as configured under settings in OBS. If an animation effect is active, it is paused until the timelpase scan is completed and then reengaged based off the specified animation file.
Tummy Timeout Redeem | 🟩 | 🟩 | Zawarudokillswitch, wereberyloaded, VoreFoodCheck, <HC_Text_Name_1>, <HC_Text_Secondary_1>, Twitchuservore | This one is complex. It work across both Vnayn, OBS, and Streamerbot in order to function. The OBS side is used to display/project spout2 proprs into vnyan of the redeemers twitch PFP. The Streamerbot side is used to time the redeemer out once they have been vored, and the Vnyan side is used to control the staging of the entire logic tree. The Streamerbot & vnyan logic also allow for the broadcaster to vore specific people using the !vore command! Please see the streamerbot documentation on github and action logic for further directions on how to set up this command. 
Workout Gacha | 🟩 | 🟥 | Zawarudokillswitch, WorkoutGachaArrayRange, workoutgachachoice, workoutgachaReps, WorkoutGachaArray | Enqueues an array populated with various workouts and randomly selects one and the number of reps, and outputs the result to chat. Will also save the resulting workout to the specified text file for record keeping and is configured to integrate with Squawk TTS if configured.
Question | 🟩 | 🟥 | Zawarudokillswitch, QuestionArrayRange | This command reads a specified text file, creates and populates an array using values on each seperate line of that text file as seperate indexes, randomly chooses one of those indexes to pass as a chat message to twitch and to the locally hosted Squawk TTS service if configured. It will also unmute the TTS source if muted and set certain OBS Filters to match.

***

<a name="Passive-Interactions"></a>
## Passive Interactions

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Sub/Chat Message Indicator | 🟩 | 🟩 | bubblelogicgate | A simple bubble shooter that randomizes the direction and type of bubble generated when a VIP user sends a message in chat. Helps to get your attention.
Feed Me Effect | 🟩 | 🟩 | Zawarudokillswitch, FeedMeMoar, FeedMeMoar2 | This node group will increment the FeedMeMoar parameter used to increase bone size. It is activated each time your avatar collides with (or eats) a food item. You can link up more bones if you'd like by connecting them to the lower "Param to Decimal" node as shown. Change the value 2 number to be bigger or smaller to increase or decrease the growth increments! You could even use different action nodes to trigger the growth effect, like subs/bits/cheers/etc. (just connect them in place of the food collision node to the right of this message). The FeedMeMoar parameter is automatically set to the default value when you launch Vnyan. It can also be reset using the !bodyreset command while streaming if things glitch/get out of hand. The randomizer plays one of 1 fart effects when this node graph is triggered by anything except for the application startup X3.
Walkons | 🟩 | 🟩 | ItzapixFanfare, GranethFanfare, TopHatTigFanfare | Triggers a walkon fanfar once when the specified user creates a twitch chat message. There's lots of ways to handle this, and this serves as an example of how to do so in vnyan. The parameters used are set to 0 when vnyan is launched.
Golden and Treasure Hype Train Events | 🟩 | 🟥 | goldensparkleswitch, randomizegoldenkappa | This triggers special effects in the event a golden hypetrain or treasure train are activated on the channel. This requires my streamerbot logic in order to function as intended.
Goal Celebration | 🟩 | 🟥 |  | Triggers a series of confetti explosions when a goal is completed. Requires my Streamer Bot logic in order to function as intended.
On Subscription | 🟩 | 🟥 | SubscriptionRainActive | Triggers a screenwide particle effect when a sub is recieved. Disables it after the specified amount of time has passed.
Hype Train Events | 🟩 | 🟩 | HypeParticleActive | Triggers a screenwide particle effect when a hype train is active. Disables it when the hypetrain ends.
Raid & Shoutout Events | 🟩 | 🟩 | RaidersNumber, ShoutoutRaidName | This is a fun one. When you are raided, this logic takes the amount of raiders and plays that many instances of the specified SFX. It also takes the raid leaders name and saves it to a variable that is then used to populate a logic string that sends a clip shoutout message to chat via hand gesture (that's right, no typing required). In order for this to function as intended my streamerbot logic is required. You must also set up the hand gestures desired via vnyan Menu > Gestures. It even supports noclip versions of the shoutout command if configured!
Subscriber Enhanced Commands | 🟩 | 🟩 | Zawarudokillswitch | Controls playback of specified SFX when subscriber enhanced commands are triggered. Requires my streamerbot logic in order to function as intended.
Yarr | 🟥 | 🟩 | Zawarudokillswitch | Triggers the specified SFX when the websocket message is activated. Requires my Streamerbot logic to function as intended.
Deer Command | 🟩 | 🟩 | Zawarudokillswitch, PNGberyloaded | Triggers the specified SFX and GFX when the websocket message is activated. Requires my Streamerbot logic to function as intended.
Edge Command | 🟥 | 🟩 | Zawarudokillswitch | Triggers the specified SFX when the websocket message is activated. Requires my Streamerbot logic to function as intended.
Scene Lighting Activated | 🟥 | 🟩 |  | Plays the specified SFX when the websocket message is triggered.
Emote Dropper | 🟩 | 🟥 |  | A simple emote dropper that activates whenever an emote is sent in twitch chat.
On Follow | 🟩 | 🟥 | LightFormActive, RHDrawActive, LHDrawActive, wereberyloaded | Triggers a dancing animation, sets the specified blendshape values, swaps cameras, triggers a particle effect, and toggles certain props if active based off the current vtuber in use when a follow event occurs.
Pyramid 5 Or Higher | 🟩 | 🟥 |  | Triggers the specified sound effect and prop when an emote pyramid of 5 or higher is triggered. Requires my Streamer Bot logic in order to function.
Bits Multiples Effects| 🟩 | 🟩 |  | Tosses the specified amount of bits donated at the currently active model with the specified throwable. Also factors the amount up to 9 and plays a certain SFX for each valid factor. Bits thrown also have limiter logic in place to help situations where large amounts of bits are cheered and the throwables last an absurd amount of time.
Compare Multiples On Bits Donation | 🟩 | 🟩 |  | Tosses the specified amount of bits donated at the currently active model with the specified throwable. Also factors the amount up to 9 and plays a certain SFX for each valid factor. Bits thrown also have limiter logic in place to help situations where large amounts of bits are cheered and the throwables last an absurd amount of time.

***

<a name="Chat-Commands"></a>
## Chat Commands

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Roll Dice Command (Subscribers & Regular) | 🟩 | 🟩 | Zawarudokillswitch, DiceFaces, DiceAmount, RollDiceResult, RollDiceValue, RollDiceMultiple, ThrowDiceAmount, ThrowDiceFaces, BasicDiceFaces, BasicDiceAmount, BasicRollDiceResult, BasicRollDiceValue | The basic dice roll command randomizes output between 1 and the range defined by: [BasicDiceAmount] x [BasicDiceFaces]. This simplification can result in impossible results and functions as an approximation. The premium command randomizes and adds together dice of the specified type until the input amount is reached and returns a far more accurate result (while also including logic to allow for thrown objects).
Pool's Opened & Closed | 🟩 | 🟥 |  | Triggers the specified assets when the command is triggered by the broadcaster.

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
Bery Specific Mods/Personalization | 🟩 | 🟥 | EndingSceneSwitch, PNGberyloaded, wereberyloaded | A bit of example logic to show how you can modify the nodegraph to achieve various things. 
PNGTuber Core Logic (No Touchy) | 🟥 | 🟥 | PNGZoom, PNGberyloaded, isspeaking, isblinking, DuplicateCheck, ScreenshotActive, TFtransitiontime, PNGCameraZoomPause | This is the brains of the entire PNGTuber nodegraph and is responsible for running the various calculations. See nodegraph comments for more details and additional setup instructions.
Instructions & Setup | 🟥 | 🟥 | PNGberyloaded, PNGTuberBlinksRandomizer | This is required in order to perform the initial setup of the PNGTuber Logic. See nodegraph comments for more details and additional setup instructions.
Websocket Triggers (PNGTubers 1-6) | 🟥 | 🟥 | PNGberyloaded | Controls specific effects when PNGTubers 1-6 are currently active. See nodegraph comments for more details and additional setup instructions.
Websocket Triggers (PNGTubers 7-12) | 🟥 | 🟥 | PNGberyloaded | Controls specific effects when PNGTubers 7-12 are currently active. See nodegraph comments for more details and additional setup instructions.
Transformation Effect | 🟩 | 🟩 | TFtransitiontime | Controls the animation effect triggered when swapping PNGTubers and models. See nodegraph comments for more details and additional setup instructions.
Specific PNGTuber Effects (PNGTubers 1-6) | 🟩 | 🟩 | PNGberyloaded | Controls specific effects when PNGTubers 1-6 are currently active. See nodegraph comments for more details and additional setup instructions.
Specific PNGTuber Effects (PNGTubers 7-12) | 🟩 | 🟩 | PNGberyloaded | Controls specific effects when PNGTubers 7-12 are currently active. See nodegraph comments for more details and additional setup instructions.
1PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
2PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
3PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
4PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
5PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
6PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
7PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.
8PNGTuber Graphic States | 🟩 | 🟥 | PNGberyloaded | See nodegraph comments for more details and additional setup instructions.

***

<a name="Pen-and-Tablet-Tracking"></a>
## Pen and Tablet Tracking

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Pen/Mouse Tracking for Drawing Streams | 🟩 | 🟥 | RHDrawActive, LMRightDrawActive, MouseX, RightDrawActive, RHLeapMotionPause, LHDrawActive, LMLeftDrawActive, MouseY, LHLeapMotionPause | This allows your model's hand and arm to track your tablet strokes as you draw, supports both left and right handed drawing setups, AND also allows you to still use leap motion hand tracking! See nodegraph comments for more details and additional setup instructions.
Pen Tracking (Right Hand Enabled) | 🟥 | 🟥 | RHDrawActive, RightDrawActive, [RHLeapMotionPause], [MouseY], [MouseX], RUpperX, RUpperY, RUpperZ, RShoulderX, RshoulderY, RshoulderZ | This part of the nodegraph logic will be active with a right handed drawing setup.
Pen Tracking (Left Hand Enabled) | 🟥 | 🟥 | LHDrawActive, LeftDrawActive, [LHLeapMotionPause], [MouseY], [MouseX], LUpperX, LUpperY, LUpperZ, LShoulderX, LshoulderY, LshoulderZ | This part of the nodegraph logic will be active with a left handed drawing setup.
Vtuber Model Check Module | 🟩 | 🟥 | RHDrawActive, wereberyloaded, LHDrawActive | This is used to activate/deactivate different props based on the currently active model.

***

<a name="Controller-With-Button-Tracking"></a>
## Controller With Button Tracking

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Controller Pose | 🟩 | 🟥 | RHControllerActive, LHControllerActive, RightControllerActive, LeftControllerActive, LMRightControllerActive, LMLeftControllerActive, RHControllerLeapMotionPause, LHControllerLeapMotionPause | Controls how the nodegraph logic translates button presses tino hand animations. Requires a controller connected to your PC in order to use and also requires the vnyan controller tracking service to be running in the background (you need to turn this on in settings). See nodegraph comments for more details and additional setup instructions.
Controller Tracking (Right Hand) | 🟥 | 🟥 | RHControllerActive, [RHControllerLeapMotionPause] | This part of the nodegraph logic controls activity on the right side of your controller.
Controller Tracking (Left Hand) | 🟥 | 🟥 | LHControllerActive, [LHControllerLeapMotionPause] | This part of the nodegraph logic controls activity on the left side of your controller.

***

<a name="Input-Animations"></a>
## Input Animations

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Input Animations | 🟩 | 🟥 | [_gamepadleftx], [_gamepadlefty], [_gamepadrightx], [_gamepadrighty], ActivateControls, AnimActive, IsRunning, RunningInterrupt, [AvatarMovementX], [AvatarRotationX], [AvatarMovementY], [AvatarRotationY]| Controls how the nodegraph logic calculates and translates your button presses into animations. See nodegraph comments for more details and additional setup instructions.
Bery Specific Mods/Personalization | 🟩 | 🟥 | PNGberyloaded | A bit of example logic to show how you can modify the nodegraph to achieve various things. 

***
