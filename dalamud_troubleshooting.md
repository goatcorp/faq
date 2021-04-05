Put Dalamud and plugin-related FAQs here

### Table of Contents
[How do I install\/enable plugins?](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-how-do-i-installenable-plugins) <br>
[What is the command for \<insert plugin here\>?](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-what-is-the-command-for-insert-plugin-here) <br>
[How do I enable\/disable Dalamud Testing or Plugin Testing](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-how-do-i-enabledisable-dalamud-testing-or-plugin-testing) <br>
[Do not expect XL\/Dalamud\/Plugin updates on patch day releases](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-do-not-expect-xldalamudplugin-updates-on-patch-day-releases) <br>
[I get an error message when trying to install\/update\/disable a plugin](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-i-get-an-error-message-when-trying-to-installupdatedisable-a-plugin) <br>
[Reshade and its variants don't work or Dalamud UI fails](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-reshade-and-its-variants-dont-work-or-dalamud-ui-fails) <br>
[How do I fix plugins that rely on Dalamud provided opcodes?](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-how-do-i-fix-plugins-that-rely-on-dalamud-provided-opcodes) <br>
[Outdated Plugins List](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-outdated-plugins-list) <br>
[All my plugins basically stopped working](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-all-my-plugins-basically-stopped-working) <br>
[Remember the patches, no matter how small, can break plugins](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md#q-remember-the-patches-no-matter-how-small-can-break-plugins) <br>
<hr>

### Q: How do I install\/enable plugins?
Not sure how to install plugins? Just type `/xlplugins` in-game after you see that the in-game hook has loaded.

Note: Disabled plugins are not uninstalled. You'll need to manually delete them if you want to remove all traces of the plugin.
<hr>

### Q: What is the command for \<insert plugin here\>?
While some plugins will list their command from the plugin install window, use `/xlhelp` to list their command and description.

You can also check out the [Plugin Gallery](https://github.com/goatcorp/DalamudPlugins/wiki/Plugin-Gallery) to see if there's some quick documentation, or check the plugin's repo for a readme.
<hr>

### Q: How do I enable\/disable Dalamud Testing or Plugin Testing?
1. Type /xlsettings in game
2. Click on the Experimental tab
3. Select/Unselect the settings as wanted.
4. Click on "Save and Close" to apply.

* Only testing plugins show up in /xlplugins when testing is enabled. They'll still load as normal.
* You may need to relaunch the game to receive another version of Dalamud.
<hr>

### Q: Do not expect XL\/Dalamud\/Plugin updates on patch day releases.

Please remember that many of the developers have school/jobs/both and live across a variety of timezones. Things will be updated when they can be. The notion that "XL could be gone at any time" still exists.
<hr>

### Q: I get an error message when trying to install\/update\/disable a plugin
Please give us more information so we can help troubleshoot why this is happening to you.

1. Which plugin is it?
2. Did a previous version work and do you know what version it was?
3. Does deleting the plugin and trying a fresh install work?
4. Can you please provide your dalamud.txt file?
<hr>

### Q: Reshade and its variants don't work or Dalamud UI fails
It may help to change how you're injecting the hook for Reshade/GShade/etc.

If you're using dgxi, try d3d11.
If you're using d3d11, try dxgi.

You can do this by renaming the hook file in your <ffxiv install>\game folder or by reinstalling your shader injector of choice, typically. (But make sure you don't have both!)
<hr>

### Q: How do I fix plugins that rely on Dalamud provided opcodes?
Certain plugins and features (Universalis updates, PennyPincher, and more), require knowing about the FFXIV client's current opcodes. These change every patch and can sometimes take more time to sort out before a Dalamud update for a new patch is ready.

If you need to refresh your opcode information after it was updated, please relaunch the game. Dalamud will check for updated definitions when it is launched.

<hr>

### Q: Outdated Plugins List
Between patches breaking them, time, and/or interest, these plugins are not currently updated and the developers are aware. If you'd like to help maintain a plugin, we can help you find their repo and contact if they're still active.

Chat Extender:
Broken in: 5.4
Status: Being split into multiple separate plugins that can be maintained separately. (ChatBubbles and Chat Translator are two of these plugins)
<hr>

### Q: All my plugins basically stopped working
Did you have Dalamud test releases enabled? (Currently version 5.2.2.1 as of post)

Don't do that. It's for testing. Specifically for breaking feature changes.

You can still access test plugins on the normal dalamud unless they specifically say they need the test version.

You can turn off Dalamud Testing in /xlsettings if you're still in game.
https://puu.sh/GQuDL.png

Otherwise, please follow these steps:
1. Close the game and xivlauncher if open.
2. Go to %appdata%\xivlauncher\ and open dalamudConfig.json in your text editor of choice.
3. Change the value of DoDalamudTest to false.
<hr>

### Q: Remember the patches, no matter how small, can break plugins
If you're experiencing crashes once Dalamud is whitelisted fora patch, you will want to disable/delete plugins and wait for updates.

Plugins that rely on opcodes may take a little longer than ones ones that rely on hooks in some cases, but it ultimately depends on how much the ffxiv client changed.
<hr>

----
Want to add a new FAQ entry? Please use the temple below
```
### Q: Basic Title
FAQ content
<hr>
```
Then add it to the Table of Contents using `[Name / Title here](Link with anchor here) <br>`

[Return to the top](https://github.com/goatcorp/faq/blob/main/dalamud_troubleshooting.md)<br>
[Return to the main Readme](https://github.com/goatcorp/faq/blob/main/README.md)
