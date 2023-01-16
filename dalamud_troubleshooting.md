# Dalamud FAQ

## Table of Contents

### Info

- [How do I install/enable plugins?](#q-how-do-i-installenable-plugins)
- [How do I enable plugin test builds?](#q-how-do-i-enable-plugin-test-builds)
- [What is the command for \<insert plugin here\>?](#q-what-is-the-command-for-insert-plugin-here)
- [How do I turn Dalamud Staging on or off?](#q-how-do-i-turn-dalamud-staging-on-or-off)
- [How do I reset dalamud/plugin window locations?](#q-how-do-i-reset-dalamudplugin-window-locations)
- [How do I manually delete plugins?](#q-how-do-i-manually-delete-plugins)
- [Why can't I find a plugin?](#q-why-cant-i-find-a-plugin)

### Troubleshooting

- [I get an error message when trying to install/update/disable a plugin](#q-i-get-an-error-message-when-trying-to-installupdatedisable-a-plugin)
- [Reshade and its variants don't work or Dalamud UI fails](#q-reshade-and-its-variants-dont-work-or-dalamud-ui-fails)
- [How do I fix plugins that rely on Dalamud provided opcodes?](#q-how-do-i-fix-plugins-that-rely-on-dalamud-provided-opcodes)
- [All my plugins basically stopped working](#q-all-my-plugins-basically-stopped-working)

### Misc

- [Do not expect XL/Dalamud/Plugin updates on patch day releases](#do-not-expect-xldalamudplugin-updates-on-patch-day-releases)
- [Remember the patches, no matter how small, can break plugins](#remember-the-patches-no-matter-how-small-can-break-plugins)

---

### Q: How do I install/enable plugins?

Not sure how to install plugins? Just type `/xlplugins` in-game after you see that the in-game hook has loaded.

---

### Q: How do I enable plugin test builds?

1. Type `/xlsettings` in game.
2. Go to the `Experimental` tab.
3. Click the checkbox for `Get plugin testing builds`.
4. Click `Save` / `Save and Close`.

- **NOTE: Testing plugins will have bugs, issues, crashes, and may even change dramatically before final release.**

For troubleshooting, please keep questions/comments/issues in the [plugin-testing](https://discord.com/channels/581875019861328007/719513457988337724) channel on our [Discord server](https://goat.place/).

---

### Q: What is the command for \<insert plugin here\>?

Plugins will list their command(s) from the plugin installer window (`/xlplugins`). The command `/xlhelp` will print all commands in your chat.

---

### Q: How do I turn Dalamud Staging on or off?

#### In game (if you can still launch)

1. Type `/xldev` in game.
2. Click on the Dalamud menu on the top of the screen.
3. Select/unselect the settings as wanted.
4. Relaunch the game.

#### Out of game (when you get crashes)

1. Close the game.
2. Go to `%AppData%\XIVLauncher\` and open `dalamudConfig.json` in your text editor of choice.
3. Go to the line that says `"DalamudBetaKey":`. Change the value to `"BETAKEYHERE"` to enable Dalamud Staging, and **`null`** (no quotes) to disable Dalamud Staging.
4. Save the file.
5. Launch the game.

- This is for developers, not users. Plugin testers should only use it when specifically stated. You should expect to encounter issues and crash more often on staging builds. **Use with caution.**
- NOTE: After enabling Dalamud Staging, you may have to wait for Dalamud to be redownloaded.
- NOTE 2: You should replace the `BETAKEYHERE` entry with a real beta key. **It requires the quotes**.
- NOTE 3: Make sure there are no quotes when setting `DalamudBetaKey` to null.

---

### Q: How do I reset dalamud/plugin window locations?

1. Close the game.
2. Go to `%AppData%\XIVLauncher\`.
3. Delete `dalamudUI.ini`.
4. Start the game.

---

### Q: How do I manually delete plugins?

1. Close the game and XIVLauncher.
2. Go to `%AppData%\XIVLauncher\installedPlugins`.
3. Remove the folder\[s\] for the plugin\[s\].
4. Go to `%AppData%\XIVLauncher\devPlugins`.
5. Remove all manually installed plugins. (Check if they have a third party repo, or reinstall them later.)
6. Start the game.

- NOTE: You may not have any manually installed plugins. That's fine.

---

### Q: Why can't I find a plugin?

Plugins often have to be updated for new patches. Please be patient if it's only been a few days or weeks - the plugin will often return. There are no estimates nor SLAs, and are subject to the developer's time/interest/motivation. You can view this [site](https://tommadness.github.io/Plugin-Browser/) to see which plugins are currently available.

---

### Q: I get an error message when trying to install/update/disable a plugin

Please give us more information so we can help troubleshoot why this is happening to you.

- Which plugin is it?
- Did a previous version work, and do you know what version it was?
- Does deleting the plugin and trying a fresh install work?
- Can you please provide your dalamud.txt file?

---

### Q: Reshade and its variants don't work or Dalamud UI fails

1. Go to `(your game installation folder)\game`.
2. Make sure the game is closed.
3. If there is a file called `d3d11.dll` or `dinput8.dll`, **rename it** to `dxgi.dll`.
4. Relaunch the game.

If this doesn't help, please contact us in our [Discord server](https://goat.place/).

---

### Q: How do I fix plugins that rely on Dalamud provided opcodes?

Certain plugins and features (Universalis updates, PennyPincher, and more) require knowing about the FFXIV client's current opcodes. These change every patch and can sometimes take more time to sort out before a Dalamud update for a new patch is ready.

If you need to refresh your opcode information after it was updated, please relaunch the game. Dalamud will check for updated definitions when it is launched.

---

### Q: All my plugins basically stopped working

There can be a number of things causing this, and we'll need to get more information from you!

If possible, please join our [Discord server](https://goat.place/) and ask in our support channels. We'll probably need your `output.log` and/or `dalamud.log` file to investigate the cause.

It is also helpful to know if you have any additional addons/injectors/mods such as ReShade/GShade, RivaTuner/RTSS/MSI Afterburner, any on-screen-displays/overlays, or mods installed via TexTools, as these can also contribute to crashing or conflicts.

---

### Do not expect XL/Dalamud/Plugin updates on patch day releases

Please remember that many of the developers have school/jobs/both and live across a variety of time zones. Things will be updated when they can be. The notion that "XL could be gone at any time" still exists.

---

### Remember the patches, no matter how small, can break plugins

If you're experiencing crashes once Dalamud is whitelisted for a patch, you will want to disable/delete plugins and wait for updates.

Plugins that rely on opcodes may take a little longer than ones ones that rely on hooks in some cases, but it ultimately depends on how much the FFXIV client changed.

---

Want to add a new FAQ entry? Please use the template below and PR to the main [FAQ repo](https://github.com/goatcorp/faq):

```md
### Q: Basic Title

(FAQ content)

---
```

Then add it to the Table of Contents using `- [Name / Title here](#anchor here)`.

[Return to the top](#table-of-contents)\
<a href="{{ site.github.baseurl }}/">Return to the main FAQ</a>
