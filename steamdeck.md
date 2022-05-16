# XIVLauncher Steam Deck Installation Guide

## 1.) Install the Steam version of FFXIV on your Steam Deck
To use XIVLauncher, the FFXIV Free Trial or the full version of FFXIV has to be installed on your Steam Deck's **internal memory**. You don't need to start it at any point in time, or need to create a Steam account, it just has to be installed. If you don't own FFXIV on Steam, please install the Free Trial.

This is needed for Gaming Mode to see the game window.

## 2.) Switch to Desktop Mode
Press and hold the Power Button. Select `Switch to Desktop Mode`

## 3.) Install XIVLauncher
Open the `Discover Store`, search for `XIVLauncher`, and press Install.

**OPTIONAL:** If you would like to install Final Fantasy XIV to your Deck's MicroSD card, you will also need `Flatseal` from the Discover Store.

## 4.) Add a Non-Steam Game
In Steam's Desktop mode, select `ADD A GAME`, scroll down to XIVLauncher, click the checkbox, and click `ADD SELECTED PROGRAM`

Right click on XIVLauncher in Steam, select `Properties`, and replace the `Launch Options` with the following:  
`XL_SECRET_PROVIDER=FILE %command% run --parent-expose-pids --parent-share-pids --parent-pid=1 --branch=stable --arch=x86_64 --command=xivlauncher dev.goats.xivlauncher`

Please note that with this configuration, XIVLauncher will save your password to a file on your Steam Deck, as Valve does not ship a safer way to store passwords by default. If this is a problem for you, please leave out `XL_SECRET_PROVIDER=FILE` from the line above - XIVLauncher won't be able to save your password in that case.

## OPTIONAL: Allow MicroSD card access to XIVLauncher
Run Flatseal. On the left, scroll down to XIVLauncher. In the main part of the window, scroll down to `Filesystem`. Click the Folder icon next to Other files. Type the location where you would like to install Final Fantasy XIV. By default, your MicroSD is mounted to `/run/media/mmcblk0p1`.

## 5.) Switch to Gaming Mode
On the Desktop, tab `Return to Gaming Mode`.

## 6.) First time setup
Run XIVLauncher in Steam. Once XIVLauncher has opened, click the Gear icon in the bottom left to set game data path, OTP macro, etc. After changing settings, click the check mark. Input your username and password, click login, and let XIVLauncher install the game (if it is not already present in your game data path).

## 7.) Run the game in Gaming Mode
After everything has installed, close Final Fantasy XIV, and click the Return to Gaming Mode icon. Run XIVLauncher in Gaming Mode, and tap Login. After a few moments, press the `Steam` button, select `FINAL FANTASY XIV Online` or `FINAL FANTASY XIV Online Free Trial` (the latter will appear for non-Steam service accounts). Final Fantasy XIV will appear on the screen after a few moments.


# FREQUENTLY ASKED QUESTIONS
## Where are my configuration files kept?
Configuration files are saved to `~/.xlcore`  

## The game is disappearing randomly and won't resume after sleep mode!
Please make sure that FFXIV or the FFXIV Free Trial from the Steam Store is installed on your Steam Deck's **internal memory**.

## My audio is crackling/distorted
Try adding `PULSE_LATENCY_MSEC=60` to the beginning of the Launch Options in Steam.

## I can't control my game!
Change the control layout for the game SteamOS thinks FFXIV is running as. For non-Steam service accounts, this means `Source SDK Base 2013 Multiplayer`.
