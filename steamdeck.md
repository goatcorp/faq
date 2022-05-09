# XIVLauncher Steam Deck Installation Guide

## Switch to `Desktop Mode`
Press and hold the Power Button. Select `Switch to Desktop Mode`

## Install XIVLauncher
Open the `Discover Store`, search for `XIVLauncher`, and press Install.

**OPTIONAL:** If you would like to install Final Fantasy XIV to your Deck's MicroSD card, you will also need `Flatseal` from the Discover Store.

## Add a Non-Steam Game
In Steam's Desktop mode, select `ADD A GAME`, scroll down to XIVLauncher, click the checkbox, and click `ADD SELECTED PROGRAM`

Right click on XIVLauncher in Steam, select `Properties`, and replace the `Launch Options` with the following:  
`XL_SECRET_PROVIDER=FILE %command% run --parent-expose-pids --parent-share-pids --parent-pid=1 --branch=stable --arch=x86_64 --command=xivlauncher dev.goats.xivlauncher`

Please note that with this configuration, XIVLauncher will save your password to a file on your Steam Deck, as Valve does not ship a safer way to store passwords by default. If this is a problem for you, please leave out `XL_SECRET_PROVIDER=FILE` from the line above - XIVLauncher won't be able to save your password in that case.

## OPTIONAL: Allow MicroSD card access to XIVLauncher
Run Flatseal. On the left, scroll down to XIVLauncher. In the main part of the window, scroll down to `Filesystem`. Click the Folder icon next to Other files. Type the location where you would like to install Final Fantasy XIV. By default, your MicroSD is mounted to `/run/media/mmcblk0p1`.

## First time setup
Run XIVLauncher in Steam. Once XIVLauncher has opened, click the Gear icon in the bottom left to set game data path, OTP macro, etc. After changing settings, click the check mark. Input your username and password, click login, and let XIVLauncher install the game (if it is not already present in your game data path).

## Run the game in Gaming Mode
After everything has installed, close Final Fantasy XIV, and click the Return to Gaming Mode icon. Run XIVLauncher in Gaming Mode, and tap Login. After a few moments, press the `Steam` button, select `FINAL FANTASY XIV Online` or `Source SDK Base 2013 Multiplayer` (the latter will appear for non-Steam service accounts). Final Fantasy XIV will appear on the screen after a few moments.


# FREQUENTLY ASKED QUESTIONS
## Where are my configuration files kept?
Launcher configuration files are saved to `~/.xlcore`  
Plugin configuration files are saved to `~/.var/app/dev.goats.xivlauncher/config/XIVLauncher/`

## Why do non-Steam users show as playing `Source SDK Base 2013 Multiplayer`?
Due to how SteamOS shows active games, we need to trick it into playing a game that your Steam account definitely has access to.
