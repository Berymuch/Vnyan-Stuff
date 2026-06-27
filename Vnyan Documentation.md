# NODEGRAPH DOCUMENTATION

A listing of all the nodegraphs/actions provided with the Vnyan logic built and maintained by [Berymuch](https://www.twitch.tv/berymuch).

Startup & Shortcuts | Input Tracking | Avatar | Commands | User Interactions | Animations
:---: | :---: | :---: | :---: | :---: | :---:
[Startup & Shortcuts](#Startup-and-Shortcuts) | [Controller With Button Tracking](#Controller-With-Button-Tracking) | [VTuber Logic](#VTuber-Logic) | [Chat Commands](#Chat-Commands) | [Passive Interactions](#Passive-Interactions) | [Input Animations](#Input-Animations)
| | [Pen and Tablet Tracking](#Pen-and-Tablet-Tracking) | [PNGTuber Logic](#PNGTuber-Logic) | [Nut Command](#Nut-Command) | [Active Interactions](#Active-Interactions) | 

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
Nut Ban & Unban commands | 🟥 | 🟥 | NutBanArray, NutUnbanIndex | This logic allows you to ban and unban specific usernames from engaging with the chat command in the event of abuse. Usernames are case senstive and are entered after the command, and the array of specified usernames is stored in the text file specified. You will need to specify this textfile filepath manually using the 4 nodes below if you want to use this feature. The format is: !nutban username, !nb username, !nutunban username, !nub username
Nut On/Off Command | 🟥 | 🟥 | NutZawarudokillswitch, nutpauseswitch | Used to disable and enable nut commands. Requires my streamerbot logic to function as intended.
Core Logic | 🟩 | 🟩 | NutZawarudokillswitch, VIPNutActive, nutpauseswitch, NutCommandDisplayName, nutforce, nutscale, nuttoss, NutBanArray | The core Nut command is at the start of the chain. Each Parameter filter acts as a numerical gateway for more specific results based off numeric input with the core command.To add a new nut redeem and tie it to a specific number, create a parameter filter and follow the prescribed parameter structure. Once done, connect the gateway parameter filter to the second output in the ordered execution node below. Have fun!
Grifter Nut | 🟩 | 🟩 | nuttoss, wolfstarcooldown, LightFormActive | Triggers an electrocution-like effect by splashing water to simulate sparks, repeatedly flinshing your model, and  using various GFX to give the impression of being zapped by blue electricity! In the event the lightform redeem is currently active when this nut is used, the bloom effect is disabled to prevent eyestrain.
AerialAbhorsen Nut | 🟩 | 🟩 | nuttoss, handbellcounter, Handbellscaling | Triggers a series of bells to be flung at the model with randomized sizes, delay, and sound effect.
Zementh's 360 Nut | 🟩 | 🟩 | nuttoss | Drops the specified object on the model and ragdolls the model while playing the associated SFX.
Krowkaws Nut | 🟩 | 🟩 | nuttoss, PNGberyloaded, BRBstatus, wolfstarcooldown | Launches the model upwards and switches the camera to one itnended to be looking up at the feet to give the illusion of the model flying away perfectly into the center of the sky. Once the model passes the render diistance in vnyan, a sparkle/graphical prop is activated. The model and camera rest to their regular positions afterwards. Works in tandem with me start screen and BRB screen logic to circumvent some graphical issues caused by this interaction.
Fuscus Nut | 🟩 | 🟩 | nuttoss, PNGberyloaded, FuscusNutTimer | Plays a SFX, displays the specified prop over the models head, then plays another SFX and shrinks the model's head bone and ragdolls it to give the illusion of a head shot. The head bone is reset to normal shortly afterwards.
Fist of the North Star Nut | 🟩 | 🟩 | nuttoss, nutpauseswitch, naninutbonescale, naninutbonescale2, naninutbonescale3, naninutbonescale4, naninutbonescale5, naninutbonescale6 | Triggers a Fist of the North star type effect by randomly modifying the sizes of the specified model bones. Also disables other nuts from being activated when in effect.
Win95 Nut | 🟩 | 🟩 | nuttoss, GrizzNutTimer | Displays a prop and activates the associated SFX. If the command is already active, also sends a message to chat informing that no further grizz nuts can be activated until the current one is finished.
Baby Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
Flashbang Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX. Also ragdolls the active model when hit by the thrown item spawned and activates certain graphical effects.
Semphelis Nut | 🟩 | 🟩 | nuttoss, FireworkRaidAmount, RaidFireworksFirefliesRandom, RaidFireworksParam, RaidFireworksTimerRandomizer, FireworkSize, FireworkSoundRandomizer, FireworkWhistleSoundRandomizer | This is a spicy one. The idea is that it launches a specified number of fireworks, with various levels of randomization involved to ensure each firework command is a bit different. can be spammed to fun effect! Requires the specified custom objects to be used in order to run as intended.
Loot Nut | 🟩 | 🟩 | nuttoss, deeznutssacksize | Throws the specified throw items at the active model and plays the specified SFX.
Snow Nut | 🟩 | 🟩 | nuttoss, Nut32Active, EndingSceneSwitch, HypeParticleActive | Throws the specified throw items at the active model and plays the specified SFX. Also triggers particles effect tied to the hypetrain passive interaction and engages various graphical effects.
Protec Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
Spiderverse Nut | 🟩 | 🟩 | nuttoss, Spiderverseactive, EndingSceneSwitch, LightFormActive | Throws the specified throw items at the active model and plays the specified SFX. Also triggers graphical effects tied to the lightform redeem and engages various graphical effects.
Nutella Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
Wolfen_ll Nut | 🟩 | 🟩 | nuttoss, Wolfenlickscycler | Activates the specified prop and plays the specified SFX.
StevenLucario Nut | 🟩 | 🟩 | nuttoss, Stevensuckscycler | Activates the specified prop and plays the specified SFX.
Pickle Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
Nice Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
400 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
402 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
418 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
SwelterDemon Nut | 🟩 | 🟩 | nuttoss, pauseswelterdemonpawdrop, PNGberyloaded, swelterdemonpawdrop | Drops a custom object specified on to the active model by incrementally transforming it's y coordinate location. Also times modelbone modification to coincide with the impact and flatten it, and updates the model position to match the new location.
Noodle Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
Max Damage Nut | 🟩 | 🟩 | nuttoss, nutforce, nutscale | Throws the specified throw items at the active model and plays the specified SFX. Also adjusts parameters of the tossed nut to affect size and impact force.
401 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
403 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
Pi Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
No Clothes Nut | 🟩 | 🟥 | nuttoss, Zawarudokillswitch | Activates the specified blendshape values, throwable prop, and SFX.
Jade Save Nut | 🟩 | 🟩 | nuttoss | Throws the specified throw items at the active model and plays the specified SFX.
RoseEclipz's Nut | 🟩 | 🟩 | nuttoss, roseplapcounter, roseplapcounter2 | A different method of handling countup events to synchronize actions. Tosses 5 of the specified object, then rests a counter, then starts another counter loop for a seperate object that also triggers a SFX and ragdolls the current model.
Nut 42 | 🟩 | 🟩 | nuttoss, LightFormActive | Triggers the specified SFX and also specific GFX.
Nut 666 | 🟩 | 🟩 | nuttoss, LightFormActive | Triggers the specified SFX and also specific GFX, and also interracts with the specified filters in OBS if you have configured them (I use the flame effect from the OBS Shaderfilter plugin). Also toggles the specified blendshapes for the currently active model.
404 Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
Nut 621 | 🟩 | 🟩 | nuttoss, PNGberyloaded, nut621pixeltimer | Triggers the specified SFX and also specific GFX, and also interracts with the vnyan pixelation filter to give a fun censoring effect. Additional logic is present in the eventthe currently active pngtuber is the second one (On my setup, I use this one with a default pixelation effect of it's own).
Grizz Nut 2 (Tornado) | 🟩 | 🟩 | nuttoss, GrizzTornadoActive, HydrateActive | Another fun one! This one works by applying small increments of force to the currently active model to give it the illusion of blowing away in a gust of wind. The effect is slight randomized each time and can be modified by tweaking the add force node values. Also triggers the specified particle effect slot and SFX. In my setup I reuse the particle slot for my hydration redeem, and so additional logic is also included to ensure the two do not conflict.
Tannyk Nut | 🟩 | 🟩 | nuttoss, 1994NutTimerActive | Throw the specified objects and triggers the specified SFX. Also checks to see if the nut is currently running to avoid overlap, and sends an error message to chat if so.
TopHatTig Nut | 🟩 | 🟩 | nuttoss, TigNutTimerActive | This one requires the usage of a specific prop available on my github due to hard coded parameters in the prop file itself. Also checks to see if the command is already running and pauses it if so while sending an error message to chat. When using the appropriate prop, a christmas tree is spawned under the active model after a delay and some SFX which launches the active model off to the left. The lights of the christmas tree prop can be configured to suit your tastes based off the information provided above.
itzApix Nut | 🟩 | 🟩 | nuttoss, ApixNutTimerActive, PreApixColourCyclerCountdown, LightFormActive, ApixNutCountdown, EndingSceneSwitch | This will play the specified SFX, wait, then toggle another SFX and some colour grading changes to replicate an alarm of sorts going off. It also modifies the specified blendshape values for the currently active model. It is also an intelligent command and knows when other logic nodes that modify colour grading are in effect and behaves differently if true. In the case of a lightform redeem or ending scene being active, it will behave slightly differently. 
Lunai Nut | 🟩 | 🟩 | nuttoss | Activates the specified prop and plays the specified SFX.
Sabadar Nut | 🟩 | 🟩 | nuttoss, SabadarNutTimerActive | This will play the specified SFX and props, wait, then play the further specified SFX and end. Also has a built in cooldown and will send a message to chat in the event another instance of the command is issued while it is on cooldown.
TheEarthling Nut | 🟩 | 🟩 | VIPNutActive, nutpauseswitch, NutZawarudokillswitch, PNGberyloaded | This will activate the specified propr and also deactivate it based off of websocket messages sent via my streamerbot logic. This command also relies in my streamerbot logic in order to function as intended and works in tandem with OBS to play and hide a specified source when activated. see streamerbot documentation for more details.
RiccyThicc Nut | 🟩 | 🟩 | | This will play the specified SFX in the rythm determined by the wait nodes and, by design, in sequence with the specified SFX file.Will also ragdoll the currently active model when the throwable generated by this logic node collides with it.
InkEDoodles Nut | 🟩 | 🟩 | | This will drop the specified droppable after the delay and Play an SFX when the object hits. It will also cause the active model to flinch and be thrown forward. This command also relies in my streamerbot logic in order to function as intended and works in tandem with OBS to play and hide a specified source when activated. see streamerbot documentation for more details.

***

<a name="VTuber-Logic"></a>
## VTuber Logic

Nodeblock Name | GFX | SFX | Parameters | Description
:--- | :---: | :---: | :--- | :---
Blendshape Websocket Commands | 🟩 | 🟩 |  | Used to control various aspects of my VTuber using websocket input via my streamdeck.
Avatar Load Commands | 🟩 | 🟥 | FeedMeMoar, FeedMeMoar2, StartingSoonSwitch | Controls logic that triggers whenever an avatar is loaded.
Prop Loading Commands | 🟩 | 🟥 | issmoking | Websocket Commands used to load props and triggered by my streamdeck.
Streamer Mod Alert | 🟩 | 🟥 | PNGberyloaded, Stickybg | Used to toggle an alert asset meant to get my attention (if a mod needs me ASAP for instance). Requires my Streamerbot logic in order to function as intended.
Hat Change | 🟩 | 🟩 | Zawarudokillswitch, HatActive, wereberyloaded, HatText | Controls logic that triggers whenever my hat is activated via chat command. the text following the command is set to a variable on the specified prop and appears visually on the hat. Also triggers different hats based on the currently active model.
Sun Glasses | 🟩 | 🟥 | ShadesActive, wereberyloaded | Controls logic that triggers whenever my shades are activated. Also triggers differently based on the currently active model.
Third Eye | 🟩 | 🟩 | ThirdEyeActive, wereberyloaded | Controls logic that triggers whenever my third eye is activated via chat command. Also triggers different hats based on the currently active model.
Witch Hat | 🟩 | 🟩 | WitchActive, wereberyloaded, EndingSceneSwitch | Controls logic that triggers whenever my witch costume is activated. Also triggers different hats based on the currently active model, and displays slightly different visual effects depending on whether or not the ending scene is currently active.
Teacher Glasses | 🟩 | 🟥 | TeacherGlassesActive, wereberyloaded, GlassesWidth, GlassesArmRotation, GlassesLensSize, GlassesArmLength | Controls logic that triggers whenever my glasses are activated via chat command. You can adjust the dimensions of the glasses using the specified parameter values. Also triggers different glasses based on the currently active model.
VTuber Swaps | 🟩 | 🟩 | PNGberyloaded, wereberyloaded | Controls logic that triggers and interacts with switching models, both PNGTuber and Vtuber. The provided channel point redeem is meant to be used to swap between two different VTuber states and trigger the appropriate versions of props and effects. This logic also allows you to freely swap between an active PNGTuber and VTuber effortlessly when using my PNGTuber Nodegraph logic

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
