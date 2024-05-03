# XIVLauncher Linux (Flatpak/ Steam Deck) Installation Guide

## Installing XIVLauncher on Desktop Linux

**IMPORTANT:** Installation for the Steam Deck works a bit differently due to Valve's changes in SteamOS, please see the next section for Steam Deck instructions.

Generally, the recommended and supported way to install XIVLauncher on a desktop Linux distribution (Ubuntu, Fedora Workstation, etc.) is to install it as a Flatpak. Flatpaks are mostly self-contained and sandboxed applications, which means that they only have access to the parts of your system that they explicitly need in order to function. The `Flatseal` program is a useful tool for managing permissions for Flatpak apps, which you may install separately if you so wish.

To install XIVLauncher as a Flatpak, you will need to have Flatpak itself installed and the Flathub repository for flatpaks enabled on your system. Please see upstream (your distro's and/or Flatpak's) documentation on how to install Flatpak to your system and to enable the Flathub repositories.

### Install XIVLauncher as a Flatpak from the terminal

To install XIVLauncher as a flatpak using the terminal, run the command `flatpak install flathub dev.goats.xivlauncher` as a regular user ( without `sudo`).

### Install XIVLauncher as a Flatpak from your software store (GNOME/KDE)

Some desktop environments provide graphical frontends for Flatpak repositories, allowing you to browse an app store to install Flatpaks in a more intuitive way.

- If you are using GNOME, open Software and then search for `XIVLauncher`. Click on the XIVLauncher entry in the results. Click `Install`.

- If you are using KDE, open Discover and then search for `XIVLauncher`. Click on the XIVLauncher entry in the results. Click `Install`.

Other desktop environments may or may not have XIVLauncher available in their own Flatpak frontend applications. If XIVLauncher does not appear in GNOME Software or KDE Discover, verify that Flatpak is installed and running, and verify that you have the Flathub repos enabled.

### Install XIVLauncher from the Arch User Repository (UNOFFICIAL)

There are several **unofficial** packages for XIVLauncher on the Arch User Repository (AUR). These packages are an alternative method of installing XIVLauncher for Arch Linux and its derivative distributions (Manjaro, Endeavour OS, etc.) ONLY.

Currently, the `xivlauncher`, `xivlauncher-bin` and `xivlauncher-git` AUR packages are available. However, **AUR packages are community builds and only the Flatpak release of XIVLauncher is officially supported.**

For reference, `xivlauncher` downloads the source code and builds the `XIVLauncher` package on your system, `xivlauncher-bin` provides a prebuilt binary, and `xivlauncher-git` provides testing builds. We cannot guarantee the functionality or security of AUR packages.

Please see the [Arch Wiki](https://wiki.archlinux.org/title/Arch_User_Repository#Installing_and_upgrading_packages) or your distribution's documentation on official instructions for installing AUR packages. AUR packages can be insecure. Be vigilant.

## Installing XIVLauncher on Steam Deck

**IMPORTANT:** The following installation instructions are for the Steam Deck only. For installing XIVLauncher on a Linux desktop/laptop (including Arch Linux and/or KDE setups), please refer to the above section.

### Install the Steam version of FFXIV on your Steam Deck

To use XIVLauncher, the FFXIV Free Trial or the full version of FFXIV has to be installed on your Steam Deck's **internal memory**. You don't need to start it at any point in time, or need to create a Steam account, it just has to be installed. If you don't own FFXIV on Steam, please install the Free Trial.

To install the Trial, you will need to look for it in the Steam Store.  Depending on whether or not you have previously installed the Trial on this account, it may be hidden from search results. In this case, look for Demos within the Final Fantasy franchise in Desktop Mode, or [use this link to go to the Trial](https://store.steampowered.com/app/312060/FINAL_FANTASY_XIV_Online_Free_Trial/).

This is needed for Gaming Mode to see the game window.

### Switch to Desktop Mode

Press and hold the Power Button. Select `Switch to Desktop Mode`.

### Install XIVLauncher

Open the `Discover Store`, search for `XIVLauncher`, and press Install.

**For Any other linux distro,** the `Discover Store` is a GUI for flatpak. This is the package: <https://flathub.org/apps/dev.goats.xivlauncher>

**OPTIONAL:** If you would like to install Final Fantasy XIV to your Deck's MicroSD card or any folder outside of the default (`~/.xlcore/ffxiv`), you will also need `Flatseal` from the Discover Store. See documentation on enabling external folder access below.

### Add a Non-Steam Game

In Steam's Desktop mode, select `ADD A GAME`, scroll down to XIVLauncher, click the checkbox, and click `ADD SELECTED PROGRAM`

Right click on XIVLauncher in Steam, select `Properties`, and replace the `Launch Options` with the following: `XL_SECRET_PROVIDER=FILE %command% run --parent-expose-pids --parent-share-pids --parent-pid=1 --branch=stable --arch=x86_64 --command=xivlauncher dev.goats.xivlauncher`

**NOTE:** Recent versions of Flatpak have seemingly deprecated the `--parent-pid=1` option. If you encounter problems, remove `--parent-expode-pids --parent-share-pids --parent-pid=1` from the launch options listed above.

**NOTE:** With this configuration, XIVLauncher will save your password to a file on your Steam Deck, as Valve does not ship a safer way to store passwords by default. If this is a problem for you, please leave out `XL_SECRET_PROVIDER=FILE %command%` from the line above - XIVLauncher won't be able to save your password in that case.

(For desktop Linux users with a sudden performance drop after some time in game, this may be caused by the Steam overlay. Try adding `LD_PRELOAD=""` at the start to disable it.)

**Do not set a Compatibility mode for XIVLauncher.** XIVLauncher is a native Linux application. Setting Compatibility for it will break it.

### OPTIONAL: Allow external folder access to XIVLauncher

Run Flatseal. On the left, scroll down to XIVLauncher. In the main part of the window, scroll down to `Filesystem`. Click the Folder icon next to Other files. Type the location where you would like to install Final Fantasy XIV.

For Steam Deck users, your MicroSD is mounted to `/run/media/mmcblk0p1` by default.

For desktop Linux users, the paths for external drives vary by distribution and system.

### Switch to Gaming Mode

On the Desktop, tap `Return to Gaming Mode`.

### First time setup / Running the game

Run XIVLauncher in Steam. Once XIVLauncher has opened, click the Gear icon in the bottom left if you need to set the game data path, OTP macro, etc. (Use the mount location above for the data path if you're installing to the MicroSD.) After changing settings, click the check mark. Input your username and password, click login, and let XIVLauncher install the game (if it is not already present in your game data path).

When prompted, press the `Steam` button, select `FINAL FANTASY XIV Online` or `FINAL FANTASY XIV Online Free Trial` (the latter will appear for non-Steam service accounts). Final Fantasy XIV will appear on the screen after a few moments.

## FREQUENTLY ASKED QUESTIONS

### Q: Where are my configuration files kept?

Configuration files are saved to `~/.xlcore`.

### Q: The game is disappearing randomly and won't resume after sleep mode on Steam Deck

Please make sure that FFXIV or the FFXIV Free Trial from the Steam Store is installed on your Steam Deck's **internal memory**.

### Q: My audio is crackling/distorted

Try adding `PULSE_LATENCY_MSEC=60` to the beginning of the Launch Options in Steam.

### Q: I can't control my game

Change the control layout for the game SteamOS thinks FFXIV is running as. For non-Steam service accounts, this means `FINAL FANTASY XIV Online Free Trial`.

If that does not fix it, rename `~/.xlcore/ffxivConfig/FFXIV.cfg` to `FFXIV.cfg.bak` and run the game again from Gaming Mode. This will reset all Final Fantasy XIV System settings to default. Renaming `FFXIV.cfg.bak` back to `FFXIV.cfg` will restore these settings.

### Q: Final Fantasy XIV doesn't close properly / Steam constantly thinks Final Fantasy XIV is playing

A fix is in progress for newer versions of Flatpak.

If you are on an older Flatpak version, make sure you set the Launch Options in the "Add a Non-Steam Game" step. Specifically the `--parent-expose-pids --parent-share-pids --parent-pid=1` arguments allow XIVLauncher to communicate with Steam to report the game closing. (This does not work on newer versions of Flatpak, as `--parent-pid=1` has been deprecated for breaking the Flatpak sandbox.)

### Q: XIVLauncher immediately closes when trying to run it through Steam

Do not set a Compatibility mode for XIVLauncher in Steam. XIVLauncher is a native Steam application that does not need Proton to run.

### Q: I can't enter my username/password on Steam Deck

Due to a limitation of Steam's text input API, please use the Steam Deck's Gaming Mode to finish setup.

[Return to the top](# XIVLauncher Linux %28Flatpak/ Steam Deck%29 Installation Guide)
<a href="{{ site.github.baseurl }}/">Return to the main FAQ</a>
