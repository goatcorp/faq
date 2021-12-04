# Dalamud FAQ

### Table of Contents
[How do I install/enable plugins?](#q-how-do-i-installenable-plugins) <br>
[How do I enable plugin test builds?](#q-how-do-i-enable-plugin-test-builds) <br>
[What is the command for \<insert plugin here\>?](#q-what-is-the-command-for-insert-plugin-here) <br>
[How do I turn Dalamud Staging on or off?](#q-how-do-i-turn-dalamud-staging-on-or-off) <br>
[Do not expect XL/Dalamud/Plugin updates on patch day releases](#q-do-not-expect-xldalamudplugin-updates-on-patch-day-releases) <br>
[I get an error message when trying to install/update/disable a plugin](#q-i-get-an-error-message-when-trying-to-installupdatedisable-a-plugin) <br>
[Reshade and its variants don't work or Dalamud UI fails](#q-reshade-and-its-variants-dont-work-or-dalamud-ui-fails) <br>
[How do I fix plugins that rely on Dalamud provided opcodes?](#q-how-do-i-fix-plugins-that-rely-on-dalamud-provided-opcodes) <br>
[Outdated Plugins List](#q-outdated-plugins-list) <br>
[All my plugins basically stopped working](#q-all-my-plugins-basically-stopped-working) <br>
[Remember the patches, no matter how small, can break plugins](#q-remember-the-patches-no-matter-how-small-can-break-plugins) <br>
[How do I reset dalamud/plugin window locations?](#q-how-do-i-reset-dalamudplugin-window-locations) <br>
<hr>

### Q: How do I install/enable plugins?
Not sure how to install plugins? Just type `/xlplugins` in-game after you see that the in-game hook has loaded.

<hr>

### Q: How do I enable plugin test builds?
1. Type `/xlsettings` in game.
2. Go to the `Experimental` tab
3. Click the checkbox for `Get plugin testing builds`
4. Click `Save` / `Save and Close`

**Please note that testing plugins can/will have bugs and may change dramatically before final release. Especially on newer plugins, they could crash your game. **

For troubleshooting, please keep questions/comments/issues in the [plugin-testing](https://discord.com/channels/581875019861328007/719513457988337724) channel on our discord server..

<hr>

### Q: What is the command for \<insert plugin here\>?
While some plugins will list their command from the plugin install window, use `/xlhelp` to list their command and description.

You can also check out the [Plugin Gallery](https://github.com/goatcorp/DalamudPlugins/wiki/Plugin-Gallery) to see if there's some quick documentation, or check the plugin's repo for a readme.
<hr>

### Q: How do I turn Dalamud Staging on or off?
#### In game (if you can still launch)
1. Type `/xldev` in game.
2. Click on the Dalamud menu on the top of the screen.
3. Select/Unselect the settings as wanted.
4. Relaunch the game

#### Out of game (when you get crashes)
1. Close the game
2. Go to `%appdata%\XIVLauncher\` and open `dalamudConfig.json` in your text editor of choice
3. Change the line that says `"DoDalamudTest": true,` to `"DoDalamudTest": false,`
4. Save
5. Launch the game. NOTE: You may have to wait for Dalamud to be redownloaded.

* Only enable this if you absolutely need to. It is for developers, not users or plugin testers unless specifically stated. 
<hr>

### Q: Do not expect XL/Dalamud/Plugin updates on patch day releases.

Please remember that many of the developers have school/jobs/both and live across a variety of time zones. Things will be updated when they can be. The notion that "XL could be gone at any time" still exists.
<hr>

### Q: I get an error message when trying to install/update/disable a plugin
Please give us more information so we can help troubleshoot why this is happening to you.

1. Which plugin is it?
2. Did a previous version work and do you know what version it was?
3. Does deleting the plugin and trying a fresh install work?
4. Can you please provide your dalamud.txt file?
<hr>

### Q: Reshade and its variants don't work or Dalamud UI fails
1. Go to `<your game installation folder>\FINAL FANTASY XIV - A Realm Reborn\game`
2. Make sure the game is closed
3. If there is a file called `d3d11.dll` or `dinput8.dll` **rename it** to `dxgi.dll`
4. Relaunch.

If this doesn't help, please contact us in our Discord server.

<hr>

### Q: How do I fix plugins that rely on Dalamud provided opcodes?
Certain plugins and features (Universalis updates, PennyPincher, and more), require knowing about the FFXIV client's current opcodes. These change every patch and can sometimes take more time to sort out before a Dalamud update for a new patch is ready.

If you need to refresh your opcode information after it was updated, please relaunch the game. Dalamud will check for updated definitions when it is launched.

<hr>

### Q: Outdated Plugins List
Between patches breaking them, time, and/or interest, these plugins are not currently updated and the developers are aware. If you'd like to help maintain a plugin, we can help you find their repo and contact if they're still active.

**Chat Extender** <br>
Broken in: 5.3 <br>
Status: Being split into multiple separate plugins that can be maintained separately. (ChatBubbles and Chat Translator are two of these plugins) <br>

**VoidList** <br>
Broken in 5.4 <br>
Status: Replaced completely with Visibility by SheepGoMeh. Install that instead using the /xlplugins command ingame. <br>
<hr>

### Q: All my plugins basically stopped working
There can be a number of things causing this, and we'll need to get more information from you!
  
If possible, please join our [Discord Server](https://discord.gg/3NMcUV5) and ask in the #xivlauncher_issues channel for support.
  
We'll probably need your `output.log` and/or `dalamud.log` file to investigate the cause. 
  
It is also helpful to know if you have any additional addons/injectors/mods such as reshade/gshade, rivatuner/rtss/msi afterburner, any on-screen-displays/overlays, or mods installed via Textools, as these can also contribute to crashing or conflicts.
<hr>

### Q: Remember the patches, no matter how small, can break plugins
If you're experiencing crashes once Dalamud is whitelisted fora patch, you will want to disable/delete plugins and wait for updates.

Plugins that rely on opcodes may take a little longer than ones ones that rely on hooks in some cases, but it ultimately depends on how much the ffxiv client changed.
<hr>


### Q: How do I reset dalamud/plugin window locations?
1. Close the game 
2. Go to %appdata%\xivlauncher
3. Delete dalamudUI.ini
4. Start the game

<hr>

Want to add a new FAQ entry? Please use the template below and PR to the main [FAQ repo](https://github.com/goatcorp/faq)
```
### Q: Basic Title
FAQ content
<hr>
```
Then add it to the Table of Contents using `[Name / Title here](#anchor here) <br>`

[Return to the top](#table-of-contents)<br>
[Return to the main Readme](https://goatcorp.github.io/faq)
