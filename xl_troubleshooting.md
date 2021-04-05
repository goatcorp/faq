Put XIVLauncher related FAQs here

Table of Contents

[How come the in-game addon \(Dalamud\) doesn't work and/or plugins don't display?](https://github.com/goatcorp/faq/blob/main/xl_troubleshooting.md#q-how-come-the-in-game-addon-dalamud-doesnt-work-andor-plugins-dont-display)
[How do I uninstall XIV Launcher?](https://github.com/goatcorp/faq/blob/main/xl_troubleshooting.md#q-how-do-i-uninstall-xiv-launcher)

<hr>

### Q: How come the in-game addon (Dalamud) doesn't work and/or plugins don't display?

Like many other game tools, Dalamud works by injecting into the FFXIV process and hooking DirectX. Occasionally, it conflicts with other tools or can't work because of them.

Some of the more common ones that may cause issues are:
- **Common Third-Party Antivirus** programs. See the dedicated FAQ for this using `f!faq av`
- **MacType** makes no changes to FFXIV because it doesn't use normal fonts anyways. Block it from hooking to FFXIV and you'll be fine.
- **MSI Afterburner** contains RTSS. See below.
-  **OBS** Some of the streaming modes involve hooking directx for better capture. This can cause plugins to render in streams or to not render at all. You may need to change your capture methods.
- **RivaTuner**/**RTSS** see if disabling the RTSS overlay helps. If not, blacklist FFXIV from automatic hooking. RTSS can be used after Dalamud loads without issues. You may also have luck with [Setting a RTSS delay](Link goes here)
<hr>

### Q: How do I uninstall XIV Launcher?

You can uninstall XIVLauncher like any normal windows program though the control panel or windows 10 setting app. If you want to purge any trace of it, check for and remove these folders.

Program installation and old versions:
`%localappdata%\XIVLauncher`
`%localappdata%\goatsoft`

Settings/plugins and other user config
`%appdata%\XIVLauncher`
<hr>

----
Want to add a new FAQ entry? Please use the temple below
```
cBasic Title
FAQ content
<hr>
```
Then add it to the Table of Contents using `[Name / Title here](Link with anchor here)`

[Return to the top](https://github.com/goatcorp/faq/blob/main/xl_troubleshooting.md)<br>
[Return to the main Readme](https://github.com/goatcorp/faq/blob/main/README.md)
