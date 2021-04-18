Put XIVLauncher related FAQs here

### Table of Contents
[How come the in-game addon \(Dalamud\) doesn't work and/or plugins don't display?](#q-how-come-the-in-game-addon-dalamud-doesnt-work-andor-plugins-dont-display) <br>
[How do I uninstall XIV Launcher?](#q-how-do-i-uninstall-xiv-launcher) <br>
[How do I fix plugins that rely on Dalamud provided opcodes?](#q-how-do-i-fix-plugins-that-rely-on-dalamud-provided-opcodes) <br>
[How do I whitelist XIVLauncher and Dalamud so my Antivirus leaves them alone](#q-how-do-i-whitelist-xivlauncher-and-dalamud-so-my-antivirus-leaves-them-alone) <br>
[XIV isn't saving my new password / how do I clear my saved password?](#q-xiv-isnt-saving-my-new-password--how-do-i-clear-my-saved-password) <br>
[I think XIVLauncher is giving me a Blue Screen of Death. What information would help narrow this down?](#q-i-think-xivlauncher-is-giving-me-a-blue-screen-of-death-what-information-would-help-narrow-this-down) <br>
[How can I fix crashes on startup?](#q-how-can-i-fix-crashes-on-startup) <br>
[Do not expect XL/Dalamud/Plugin updates on patch day releases.](#q-do-not-expect-xldalamudplugin-updates-on-patch-day-releases) <br>
[CAN I LOGIN EARLY TO TITLESCREEN BEFORE PATCH LIVE????](#q-can-i-login-early-to-titlescreen-before-patch-live) <br>
[XL Environment Variables](#q-xl-environment-variables) <br>
[Outdated Plugins List](#q-outdated-plugins-list) <br>
[The launcher shows a red world icon and an error message when trying to log in, and the official launcher doesn't open](#q-the-launcher-shows-a-red-world-icon-and-an-error-message-when-trying-to-log-in-and-the-official-launcher-doesnt-open) <br>
[WTFast Config](#q-wtfast-config) <br>
[NVIDIA Driver issue \(7th of January\)](#q-nvidia-driver-issue-7th-of-january) <br>
[How to set an an injection delay in rivaTuner/RTSS](#q-how-to-set-an-an-injection-delay-in-rivatunerrtss) <br>
[Where can I find my FFXIV Installation?](#q-where-can-i-find-my-ffxiv-installation) <br>
[How do I migrate ffxiv and/or xivlauncher files from an old Wine prefix to a new one? \[Linux\]](#q-how-do-i-migrate-ffxiv-andor-xivlauncher-files-from-an-old-wine-prefix-to-a-new-one-linux) <br>
[How do I migrate ffxiv and\\or xivlauncher files from an old installation to a new one? \[Windows\]](#q-how-do-i-migrate-ffxiv-andor-xivlauncher-files-from-an-old-installation-to-a-new-one-windows) <br>
[I'm on Linux and I keep getting \"XIVLauncher failed to update\" errors](#q-im-on-linux-and-i-keep-getting-xivlauncher-failed-to-update-errors) <br>
[How do I get started with development?](#q-how-do-i-get-started-with-development) <br>
[Why do people keep asking about Steam so much?](#q-why-do-people-keep-asking-about-steam-so-much) <br>
[Can I repair my FFXIV installion?](#q-can-i-repair-my-ffxiv-installion) <br>
[How do I fix a version check error when trying to update FFXIV?](#q-how-do-i-fix-a-version-check-error-when-trying-to-update-ffxiv) <br>
[I updated my game with TexTools mods installed. How do I fix crashes?](#q-i-updated-my-game-with-textools-mods-installed-how-do-i-fix-crashes) <br>
<hr>

### Q: How come the in-game addon (Dalamud) doesn't work and/or plugins don't display?

Like many other game tools, Dalamud works by injecting into the FFXIV process and hooking DirectX. Occasionally, it conflicts with other tools or can't work because of them.

Some of the more common ones that may cause issues are:
- **Common Third-Party Antivirus** programs. See the dedicated FAQ for this using `f!faq av`
- **MacType** makes no changes to FFXIV because it doesn't use normal fonts anyways. Block it from hooking to FFXIV and you'll be fine.
- **MSI Afterburner** contains RTSS. See below.
-  **OBS** Some of the streaming modes involve hooking directx for better capture. This can cause plugins to render in streams or to not render at all. You may need to change your capture methods.
- **RivaTuner**/**RTSS** see if disabling the RTSS overlay helps. If not, blacklist FFXIV from automatic hooking. RTSS can be used after Dalamud loads without issues. You may also have luck with [Setting an RTSS delay](#q-how-to-set-an-an-injection-delay-in-rivatunerrtss)
<hr>

### Q: How do I uninstall XIV Launcher?

You can uninstall XIVLauncher like any normal windows program though the control panel or windows 10 setting app. If you want to purge any trace of it, check for and remove these folders.

Program installation and old versions:
`%localappdata%\XIVLauncher`
`%localappdata%\goatsoft`

Settings/plugins and other user config
`%appdata%\XIVLauncher`
<hr>

### Q: How do I fix plugins that rely on Dalamud provided opcodes?
Certain plugins and features (Universalis updates, PennyPincher, and more), require knowing about the FFXIV client's current opcodes. These change every patch and can sometimes take more time to sort out before a Dalamud update for a new patch is ready.

If you need to refresh your opcode information after it was updated, please relaunch the game. Dalamud will check for updated definitions when it is launched.
<hr>

### Q: How do I whitelist XIVLauncher and Dalamud so my Antivirus leaves them alone?

Please make exceptions (or whitelist) the following folders:
 - `%localappdata%\XIVLauncher`
 - `%localappdata%\goatsoft`
 - `%appdata%\XIVLauncher`
 - `Your FFXIV game installation folder`

## Please also restart your computer afterwards

#### You may also need to reset Dalamud (the plugin system)
To reset dalamud, remove your `%appdata%\XIVLauncher\addon\Hooks` folder. Or type `f!faq delete dalamud` in the XIVLauncher discord and Franzbot will guide you through.

Want to help us out? If your antivirus complains about XIVLauncher or Dalamud, please submit the files it complains about on the whitelist link. Include "this is not harmful" and the type of malware your Av program flagged it as.

**Avast**
<https://support.avast.com/en-ww/article/Antivirus-scan-exclusions> <br>
Whitelist form: <https://www.avast.com/en-us/false-positive-file-form.php>

**AVG**
<https://support.avg.com/SupportArticleView?l=en&urlname=AVG-Antivirus-scan-exclusions> <br>
Whitelist form: <https://www.avg.com/en-us/false-positive-file-form>

**Bitdefender**
<https://www.bitdefender.com/consumer/support/answer/8886/> <br>
Whitelist form: <https://www.bitdefender.com/submit>
**NOTE**: BitDefender users may also need to whitelist xivlauncher's program files (local appdata stuff) through the BitDefender firewall. You'll know this is the case if it fails to check for updates/open.

**McAfee**
NOTE: McAfee doesn't allow you to whitelist folders. Instead, you'll need to whitelist files, which is more annoying and also version-specific. We'd recommend switching back to Windows Defender if you're on a free version, as it's less headache for all involved.

You should try to whitelist the following files if possible:
1. `<your ffxiv installation>\game\ffxiv_dx11.exe`
2. `%localappdata%\XIVLauncher\XIVLauncher.exe`
3. `%localappdata%\XIVLauncher\app-X.Y.Z\XIVLauncher.exe` NOTE: replace X.Y.Z with the latest version available. **This changes with every launcher update**
4. `%appdata%\XIVLauncher\addon\Hooks\W.X.Y.Z\Dalamud.Injector.exe` NOTE: replace W.X.Y.Z with the latest version available. **This changes with every dalamud update**
5. `%appdata%\XIVLauncher\addon\Hooks\W.X.Y.Z\Dalamud.dll` NOTE: replace W.X.Y.Z with the latest version available. **This changes with every dalamud update**

<https://service.mcafee.com/webcenter/portal/cp/home/articleview?articleId=TS102056> <br>
Whitelist steps: <https://service.mcafee.com/webcenter/portal/cp/home/articleview?articleId=TS103032>
**Norton**
<https://support.norton.com/sp/en/us/home/current/solutions/v3672136> <br>
Whitelist form: <https://submit.norton.com/>

**Windows Defender**
<https://support.microsoft.com/en-us/help/4028485/windows-10-add-an-exclusion-to-windows-security> <br>
Whitelist form: <https://www.microsoft.com/en-us/wdsi/filesubmission>

(**PLEASE PROCEED WITH CAUTION**. If you're installing dev plugins, third-party plugins, or something outside of the normal /xlplugins method, we cannot be sure that the plugins will work, be undetected in-game, and not cause harm to your computer)
<hr>

### Q: XIV isn't saving my new password / how do I clear my saved password?

XIV Launcher saves user credentials in the Windows Credential Manager. They will be appropriately labelled so you can find the exact one you want to edit/remove.

1. Open the Windows Credential Manager application. The fastest method is to just start typing its name in the start menu.
2. Select button for Windows Credentials
3. Scroll down until you see an entry like FINAL FANTASY XIV-username and expand the entry
4. Delete the entry. XIVLauncher will no longer be able to load it.
5. Now open xivlauncher and try to login.

If you need more help, a basic guide can be found on <https://pureinfotech.com/credential-manager-windows-10/>
<hr>

### Q: I think XIVLauncher is giving me a Blue Screen of Death. What information would help narrow this down?
(NOTE: It's probably not XIV Launcher, but the following information will help us verify that)

1. What stop code are you getting?
2. What is the faulting application or driver?
3. When did this start happening for you?
4. Which plugins do you have installed? Does it still happen if you disable them and selectively re-enable them one by one?
5. Have you done a full uninstall of XIVLauncher and reinstall? (see a few posts above for details)

If unsure about some of those details or if the Windows Event Viewer doesn't tell you, [Bluescreenview](https://www.nirsoft.net/utils/blue_screen_view.html) can read the memory dump (please let the computer finish it without hitting the reset button while it dumps your memory to hard drive)
<hr>

### Q: How can I fix crashes on startup?
Please try to install the VC Redist from Microsoft at <https://github.com/abbodi1406/vcredist/releases/latest>, as well as the .NET 4.8 Runtime <https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net48-web-installer>.
If you are still facing issues, please message us in #xivlauncher_issues
<hr>

### Q: Do not expect XL\/Dalamud\/Plugin updates on patch day releases.
Please remember that many of the developers have school/jobs/both and live across a variety of timezones. Things will be updated when they can be. The notion that "XL could be gone at any time" still exists.
<hr>

### Q: CAN I LOGIN EARLY TO TITLESCREEN BEFORE PATCH LIVE????
In theory, yes. But you'll probably have expired authorization and have to login again anyways.

Like every patch maintenance, the lobby server will likely be taken offline as usual. Even assuming you get the patch downloaded and applied mid-mainteance, your authorization will almost assuredly be expired before things are back up.  **Especially for housing patches as SE never ends those early.**

You can make use of XL's "wait for maintenance to be over" features to sit and check for boot patches (no login required) and then prompt you to login for game patches as soon as they are generally available.

The "wait for maintenance to be over" feature can also check for servers to be live every ~15 seconds to get you logged in as soon as things are live.

As with any patch, **in-game addons will be automatically disabled until Dalamud is updated for new patch content**. Do not manually inject Dalamud as a startup application unless you'd like to crash your client  
<hr>

### Q: XL Environment Variables

You can set `XL_PRERELEASE=true` for testing a new release of xivlauncher if applicable.

**If you set this on without knowing what it does, we will not help you if something breaks**

Don't use the wine env var anymore. Just use the properly working Lutris scripts that work with SquirrelSetup.

 **Support will not be provided if you are not on the current version of XL, Dalamud, and plugins. Use with caution as outdated versions will likely crash.**
<hr>

### Q: Outdated Plugins List
Between patches breaking them, time, and/or interest, these plugins are not currently updated and the developers are aware. If you'd like to help maintain a plugin, we can help you find their repo and contact if they're still active.

#### Chat Extender:
Broken in: 5.4
Status: Being split into multiple separate plugins that can be maintained separately. (ChatBubbles and Chat Translator are two of these plugins)
<hr>

### Q: The launcher shows a red world icon and an error message when trying to log in, and the official launcher doesn't open
This is an issue with Square Enix servers that has been affecting players in the US for a while now, being caused by the login servers being hosted directly by SE in Japan and not taking care of their routes to players.

To remedy it, you can either wait a while and try again then, or set your VPN to Japan until you are on the title screen. Then you should be able to play normally without a VPN. DNS changes have also been said to help.

We can recommend mudfish as a VPN for FFXIV as it's cheap and seems to work reliably.
To troubleshoot, you can ping frontier.ffxiv.com, SE's Japanese login server.
<hr>

### Q: WTFast Config
![wtfast config settings](images/wtfastconfig.png)
<hr>

### Q: NVIDIA Driver issue (7th of January)
If you experience crashes with the Nvidia driver from the 7th of January, please try rolling back to the last release before the holidays from the 15th of December.

The release from the 7th seemingly introduced a change or bug that will cause FFXIV to crash under certain conditions when XL is loaded.

We are still looking into this.
<hr>

### Q: How to set an an injection delay in rivaTuner\/RTSS

1. Go to `C:\Program Files (x86)\RivaTuner Statistics Server\Profiles\\`
2. Open the **ffxiv_dx11.exe.cfg** file in your text editor of choice.
3. Find the `[Hooking]` section and change 2 parameters there:
```
InjectionDelay=15000
InjectionDelayTriggers=KERNEL32.dll,USER32.dll
```
If they are not present, add them

<hr>

### Q: Where can I find my FFXIV Installation?
(AKA: What does XIVLauncher mean by GamePath?)

FFXIV installs to a few different locations depending on whether you used the official installer or steam, when you installed it, and potentionally if you installed the free trial or not. Here are some of the common paths.

Whatever you do, DO NOT SELECT THE `BOOT` OR `GAME` FOLDER. But if you already have a copy of FFXIV installed, you'll want the folder that contains them.

Official Launcher:
`C:\Program Files (x86)\SquareEnix\FINAL FANTASY XIV - A Realm Reborn`

Steam:
`C:\Program Files (x86)\Steam\steamapps\common\FINAL FANTASY XIV Online`
`C:\Program Files (x86)\Steam\steamapps\common\FINAL FANTASY XIV - A Realm Reborn`
__NOTE__: If your steam library is on another drive, it will have a different, but similar structure. <br>
![Example](images/xivlaunchersSettings.png)
<hr>

### Q: How do I migrate ffxiv and\/or xivlauncher files from an old Wine prefix to a new one? \[Linux\]

Once you've made your new xivlauncher-based prefix, you can copy files from your old ffxiv prefix for the following:

**Copy a FFXIV Install from one prefix to another \(or move\/symlink as desired\)**
from:
`~/Games/<old prefix>/drive_c/Program Files (x86)/SquareEnix/FINAL FANTASY XIV - A Realm Reborn`
to:
`~/Games/<new prefix>/drive_c/Program Files (x86)/SquareEnix/FINAL FANTASY XIV - A Realm Reborn`

**Copy your user\/character settings:**
from:
`~/Games/<old prefix>/drive_c/users/<username>/My Documents/My Games/FINAL FANTASY XIV - A Realm Reborn`
to:
`~/Games/<new prefix>/drive_c/users/<username>/My Documents/My Games/FINAL FANTASY XIV - A Realm Reborn`

**Copy XIV Launcher config \(please reinstall plugins\)**:
from:
`~/Games/<old prefix>/drive_c/users/<username>/Application Data/XIVLauncher/pluginConfigs`
to:
`~/Games/<new prefix>/drive_c/users/<username>/Application Data/XIVLauncher/pluginConfigs`
<hr>

### Q: **How do I migrate ffxiv and\/or xivlauncher files from an old installation to a new one? \[Windows\]**

**Copy a FFXIV Install**
For the most part, FFXIV is portable. You just need to make sure you've installed Directx as needed. I recommend installing the launcher with SE's installer first, and then replacing the files with a backup if you don't want to patch.
__NOTE__: You shouldn't do this if you had textools installed. Or at least, make sure to restore indexes first as it probably broke your client.

**Copy your user\character settings:**
`%USERPROFILE%\Documents\My Games\FINAL FANTASY XIV - A Realm Reborn`

**Copy XIV Launcher config (please reinstall plugins)**:
__NOTE__: do not copy other config or folders as those are unique to that particular computer. You should set them up per machine.
`%appdata%\XIVLauncher\pluginConfigs`
<hr>

### Q: **I'm on Linux and I keep getting \"XIVLauncher failed to update\" errors**

On some more recent Linux distributions, TLS 1.0 and 1.1 has been disabled. This causes an issue with Wine and FFXIV/XIVLauncher because it may not always negotiate TLS correctly.

You can fix this by seting your `dssenh` DLL override to native if it isn't already. (dssenh=n as an environment variable or in Lutris)

This has also been added to the xivlauncher Lutris script as well.

Thank you to kainz0r for this tip!
![Example](images/LinuxConfigScreenshot.png)
<hr>

### Q: How do I get started with development?
This post is a work in progress and will be edited as new information and resources become available. It's generally easier to just ask in the <#Dev> channel.

__XIVLauncher__
The launcher itself.

The XIVLauncher source code can be found on the main project repo.
<https://github.com/goatcorp/FFXIVQuickLauncher>

__Dalamud__
Dalamud is the core addon/plugin system.

The Dalamud source code can be found on the main project repo.
<https://github.com/goatcorp/Dalamud>

Other assets required by Dalamud can be found here:
<https://github.com/goatcorp/DalamudAssets>

You can find the Dalamud API page below, which also lists functions you can use in plugins.
<https://goatcorp.github.io/Dalamud/api/index.html>

__Dalamud Plugins__
Karashiiro has a good starting document here:
<https://github.com/karashiiro/DalamudPluginGuide>

We also have a number of sample plugin templates to choose from:
<https://github.com/goatcorp/SamplePlugin>
<https://github.com/karashiiro/DalamudPluginProjectTemplate>
<https://github.com/lmcintyre/PluginTemplate>

You might also find the LivePluginLoad plugin to be handy, as it allows you to do rapid plugin testing and reload dynamically. It's available by source or Caraxi's repo.
<https://github.com/Caraxi/LivePluginLoad>
<http://repo.caraxian.com/>

To distribute a plugin, it does need to be packaged correctly. This can be done manually or with DalamudPackager.
<https://github.com/goatcorp/DalamudPackager>

When your plugin is ready for testing/release, it should be PRed over to the DalamudPlugins repo.
*Please place testing plugins in the testing folder*
<https://github.com/goatcorp/DalamudPlugins>
<hr>

### Q: Why do people keep asking about Steam so much?
Steam Integration = "I want the steam program to see I'm playing FFXIV and do the overlay thing"

Use Steam service account = "I bought FFXIV through Steam, which is not the same as the Windows platform."
<hr>

### Q: Can I repair my FFXIV installion?

Short answer: No, not without reinstalling the game.

#### General steps  to reinstall the entire game
1. Go to your ffxiv installation folder (refer to your gamepath)
2. Delete the `boot` and `game` folders
3. Open xivlauncher and login. It should ask to patch

Fun answer: XIVLauncher can asisst you in selectively reinstalling only certain portions of the FFXIV game client if needed. Or the entire game.

#### General steps to reinstall just ARR:

1. Go to your ffxiv installation folder (refer to your gamepath)
2. Go to the `game` folder
3. Select all the files except the `sqpack` folder
4. If you have reshade/reshade, unselect those files to preserve them (gshade-presets, gshade-shaders, GShade.ini, dxgi/d3d11)
5. Delete the selected files so only the sqpack folder remains (and reshade/gshade files if applicable)
6. Go to the `sqpack` folder now
7. Delete the `ffxiv` folder there
8. Open xivlauncher and login. It should ask to patch

#### General steps to reinstall one or more expansions:
1. Go to your ffxiv installation folder (refer to your gamepath)
2. Go to the `game` folder
3. Go to the `sqpack` folder now
4. Delete the corresponding expac folder[s] you want to reinstall.
    4a. ex1 = heavensward
	4b. ex2 = stormblood
	4c. ex3 = shadowbringers
5. Open xivlauncher and login. It should ask to patch

<hr>

### Q: How do I fix a version check error when trying to update FFXIV?
1. Go to `<your user folder>\Documents\My Games\FINAL FANTASY XIV - A Realm Reborn`
2. Open the `FFXIV_BOOT.cfg` file in your text editor of choice.
3. Change `BootVersionCheckMode` to `1`
4. Relaunch.

<hr>

### Q: I updated my game with TexTools mods installed. How do I fix crashes?
You'll know if you're affected by this because the official launcher will crash the game too. This issue is not caused by XIVLauncher.

While the last few game patches have been relatively fine to keep your Textools mods enabled as it will do minor adjustments to fix things up, please refer to the Textools Discord for best practices.

To fix the crash, open Textools, and "Start Over" to disable everything. Then download their index backups
<hr>

### Basic Title
FAQ content
<hr>

Want to add a new FAQ entry? Please use the template below and PR to the main [FAQ repo](https://github.com/goatcorp/faq)
```
### Basic Title
FAQ content
<hr>
```
Then add it to the Table of Contents using `[Name / Title here](#anchor here) <br>`

[Return to the top](#table-of-contents)<br>
[Return to the main Readme](https://goatcorp.github.io/faq)
