# XIVLauncher Linux Installation Guide

XIVLauncher for Linux is distributed in many different formats depending on your system setup. Please read below for the recommended way to install XIVLauncher for your system:

- **I am using a Steamdeck/Linux handheld with Steam big picture (regardless of if you own FFXIV on Steam)**: You should follow the [install as a compatibility tool guide](#install-xivlauncher-as-a-steam-compatibility-tool).
- **I am using a desktop Linux distro and own FFXIV through Steam**: You should follow the [install as a compatibility tool guide](#install-xivlauncher-as-a-steam-compatibility-tool).
- **I am using a desktop Linux distro and don't own FFXIV through Steam**: You should follow the [install as a Flatpak or system package guide](#install-xivlauncher-as-a-flatpak-or-system-package)
- **I am using a setup that is not listed here**: It may be the case that XIVLauncher may not be officially supported for your setup, but still refer to the [install as a Flatpak or system package guide](#install-xivlauncher-as-a-flatpak-or-system-package) to make sure.

## Install XIVLauncher as a Steam compatibility tool

The XIVLauncher Steam compatibility tool is handled by a project called [XLM](https://github.com/Blooym/XLM). Automatic install scripts are provided for all major system configurations that will do most of the setup work for you *(However if your system configuration is not covered here you can always manually download the XLM binary from the [GitHub Releases Page](https://github.com/Blooym/xlm/releases/latest) and install that way)*. Regardless of how you install XLM from it will always be kept up to date automatically.

Run one of the following commands to install XLM as a Steam compatibility tool. What command you need to run depends on how you have Steam installed. **These scripts CANNOT and SHOULD NOT be run with sudo or root permissions.**

**Steamdeck Install Script (also for Bazzite and other deck-interface distros)**:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Blooym/xlm/main/setup/install-steamdeck.sh)"
```

**Native Steam Install Script (Steam installed as a native package)**
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Blooym/xlm/main/setup/install-native.sh)"
```

**Flatpak Steam Install Script (Steam installed as a Flatpak)**
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Blooym/xlm/main/setup/install-flatpak.sh)"
```

---

#### Experimental

Snap Steam (Steam installed as a snap, for Ubuntu 24.04 and later) **[Unsupported - may be broken on Wayland]**
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Blooym/xlm/main/setup/install-snap.sh)"
```

---

After the installer has finished, please follow these steps to use the compatibility tool:
- Switch back to gaming mode (if on Steam Deck) or restart your Steam client otherwise.
- Navigate to your library and select "FINAL FANTASY XIV Online" or "FINAL FANTASY XIV Online Free Trial" if you are playing via the free trial or don't own the Steam edition of FFXIV. 
- Open the game properties menu and switch to the "compatibility" tab.
- Enable the "Force the use of a specific Steam Play compatibility tool" checkbox.
- From the box that appears select "XLCore [XLM]" (if this does not show, please make sure you properly restarted Steam).
- You can now launch the game as usual. XIVLauncher will be automatically installed and run for you.

### Optional Advanced Features

#### Using a fork of XIVLauncher

To use a fork of XIVLauncher you can add the flags `--xlcore-repo-owner` and `--xlcore-repo-name` to the Steam "Launch Arguments" section.

Forks of XIVLauncher can also offer their own install scripts that automate this process for you so you don't have to manually add these flags.

#### Pre + Post launch scripts (Advanced)

When installed as a Steam compatibility tool XLM supports running scripts before and after XIVLauncher has been ran. These scripts allow for extending the functionality of XLM or XIVLauncher. On startup, XLM will look for directories inside of the `XLM` compatibility tool folder named `prelaunch.d` and `postlaunch.d` and run all scripts contained inside. These scripts have to be placed manually after installing XLM and no support is offered if you create/use a script that breaks something.

## Install XIVLauncher as a flatpak or system package

### Flatpak

First, check to see if flathub is installed by running `flatpak remotes`. If you don't see an entry for flathub, check [https://flathub.org/setup](https://flathub.org/setup) for instructions on how to install it.

#### Via terminal

To install XIVLauncher as a flatpak using the terminal, run the command `flatpak install flathub dev.goats.xivlauncher` as a regular user ( without `sudo`).

#### Via your software store (GNOME/KDE)

Some desktop environments provide graphical frontends for Flatpak repositories, allowing you to browse an app store to install Flatpaks in a more intuitive way.

- If you are using GNOME, open Software and then search for `XIVLauncher`. Click on the XIVLauncher entry in the results. Click `Install`.

- If you are using KDE, open Discover and then search for `XIVLauncher`. Click on the XIVLauncher entry in the results. Click `Install`.

Other desktop environments may or may not have XIVLauncher available in their own Flatpak frontend applications. If XIVLauncher does not appear in GNOME Software or KDE Discover, verify that Flatpak is installed and running, and verify that you have the Flathub repos enabled.

#### Installing FFXIV to an external drive

If you would like to install Final Fantasy XIV to any folder outside of the default (`~/.xlcore/ffxiv`), you will also need `Flatseal` from the Discover Store.

Run Flatseal. On the left, scroll down to XIVLauncher. In the main part of the window, scroll down to `Filesystem`. Click the Folder icon next to Other files. Type the path where you would like to install Final Fantasy XIV.

### System package

A list of alternative packages and formats can be found [here](https://github.com/goatcorp/XIVLauncher.Core?tab=readme-ov-file#distribution). Please note that apart from the compatibility tool and the Flatpak, the rest are maintained by members of the community and are deemed unofficial. You will, however, still receieve community support as long as the package is up-to-date.

## FREQUENTLY ASKED QUESTIONS

### Q: Where are my configuration files kept?

Configuration files are saved to `~/.xlcore`, except when running the compatibility tool with the Steam flatpak wherein the configuration files are saved to `~/.var/app/com.valvesoftware.Steam/.xlcore`.

### Q: The game is disappearing randomly and won't resume after sleep mode on Steam Deck

Please make sure that FFXIV or the FFXIV Free Trial from the Steam Store is installed on your Steam Deck's **internal memory**.

### Q: My audio is crackling/distorted

Try adding `PULSE_LATENCY_MSEC=60` in your XIVLauncher environment variable settings.

### Q: I can't control my game

Change the control layout for the game SteamOS thinks FFXIV is running as. For non-Steam service accounts, this means `FINAL FANTASY XIV Online Free Trial`.

If that does not fix it, rename `~/.xlcore/ffxivConfig/FFXIV.cfg` to `FFXIV.cfg.bak` and run the game again from Gaming Mode. This will reset all Final Fantasy XIV System settings to default. Renaming `FFXIV.cfg.bak` back to `FFXIV.cfg` will restore these settings.

### Q: Final Fantasy XIV doesn't close properly / Steam constantly thinks Final Fantasy XIV is playing

Please [switch to the compatibility tool version of XIVLauncher](#install-xivlauncher-as-a-steam-compatibility-tool) and remove the old XIVLauncher flatpak to resolve this problem.

### Q: I can't enter my username/password on Steam Deck

Due to a limitation of Steam's text input API, please use the Steam Deck's Gaming Mode to finish setup.

### Q: I'm seeing "No secrets provider installed or configured"

This means that XIVLauncher was unable to find a secure way to store your passwords. This is usually because you don't have a secrets manager like GNOME Keyring or KDE Wallet installed on your system. It's recommended you install a recognised and well known secrets manager to solve this problem. Even with a secret provider installed, XIVLauncher will occasionally fail to find it. In that case, just restart the launcher.

If you are using a Steamdeck or are unable to install a secrets manager, you can run XIVLauncher with `XL_SECRET_PROVIDER=file` to store your credentials insecurely via a file. This will be done for you if you are using the compatibility tool on Steamdeck or with Flatpak Steam.

### Q: An Internal Dalamud error has occurred!
This can have several causes, but is usually caused by a broken wine prefix or by using an unpatched wine build. Go into the **Troubleshooting** tab in settings, and press the **Clear Prefix** button. If that doesn't work, try enabling the **Hack: Fix libicuuc Dalamud error**. If that fails as well, try going into the **Wine** tab and changing to Legacy or Stable (you may have to clear the prefix again).

[Return to the top](#xivlauncher-linux-installation-guide)
<a href="{{ site.github.baseurl }}/">Return to the main FAQ</a>
