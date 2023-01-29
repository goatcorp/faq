# XIVLauncher Security Specifics

---

Here are some additional details about XIVLauncher itself.

1. XIVLauncher is open source. You can audit the code in the main [XIVLauncher GitHub Repo](https://github.com/goatcorp/FFXIVQuickLauncher/).
2. XIVLauncher releases are now built directly on GitHub. Anything you download, you can be sure that it is from the version of the open source code that is listed on the GitHub repository. The XIVLauncher version check file is cached onto a private VPS to help reduce your chances of hitting GitHub API rate limits and country-specific ISP blocks. File downloads will show our proxy domain (`kamori.goats.dev`), but this redirects to GitHub. You may use a network analysis tool of your choice to verify this behavior. The VPS uses Cloudflare to cache the data in turn and is only accessible via VPN and a hardware key.
3. In the event that the launcher has been modified, or you are running a version intended for development, it will clearly denote that it is a debug build or otherwise a test/unsupported release. ![unsupported xivlauncher build](images/xivlauncher_unsupported.png).
4. XIVLauncher uses the Windows Credential Manager to safely store your account credentials, if you choose to save them. Your passwords are encrypted and can only be accessed by authorized programs. However, that does mean if someone manages to gain access to your computer, they can technically extract your password (but at that point, you likely have bigger issues).
5. XIVLauncher only communicates with our secured proxy, GitHub, and official FFXIV websites.
6. XIVLauncher has been designed to fully replicate the same login and authorization process as the official launcher. Steps have been taken to ensure that it will always match retail, down to experiencing the same login issues. Patch downloads are obtained from the same patchlist that SE provides the retail launcher, and all patch files are verified to be correct before they are applied.

#### Dalamud Security Specifics

Here are some additional details about Dalamud.

1. Dalamud **is** a code injection framework. By definition, it's going to look and act like a virus-like program. Your antivirus might even consider it harmful or potentially harmful software! You can read more about [whitelisting Dalamud](xl_win_help.md#q-how-do-i-whitelist-xivlauncher-and-dalamud-so-my-antivirus-leaves-them-alone) elsewhere on the FAQ. **We recommend whitelisting for the best experience, but your computing environment may not require it.**
2. Dalamud allows you to read game memory and network packets. Compare this to using ACT.
3. Dalamud's framework comes with the ability for modifying game memory/hooking into game client memory and functions that plugins can choose to use. We however only provide safe read-only(where it applies) access to game data in the official [Dalamud game data APIs](https://goatcorp.github.io/Dalamud/api/index.html).

#### Plugin Security Specifics

Here are some additional details about Dalamud plugins.

1. Dalamud plugins on our official plugin repository have been deemed "safe to use" by us.
2. Officially supported plugins should always be downloaded/installed directly in game from the `/xlplugins` plugin installer. You don't need to download them manually or install them manually.
3. Dalamud does support third party plugin repositories, with limited support.

Please note:

- We cannot provide support for unofficial plugins
- While many unofficial plugins are safe to use, others may do things that exploit the game or create unsafe conditions that could send invalid data to the game servers or could result in bans. Please exercise caution before using an unsupported plugin. We cannot take any responsibility for them.
- Unsupported plugin troubleshooting should be taken to the plugin developer or their relevant communities. Please do not ask for support on the XIVLauncher support discord for these plugins, even if they don't have proper support channels elsewhere.

#### Network Security Specifics

These are the non-FFXIV domains you should expect to see network traffic from. All connections are made with HTTPS where possible. (Square-Enix is dumb and some of their services do not use HTTPS. We do not like this, but have no control over it.)

You can find the source code for our additional web services here: <https://github.com/goatcorp/XLWebServices/tree/master/XLWebServices>

1. `kamori.goats.dev` - this is a private VPS behind Cloudflare, run by the maintainer of XIVLauncher, to proxy and cache some common files that XIVLauncher and Dalamud need to check their version. It's being used to reduce the number of network connections to GitHub so that users do not need to worry about hitting rate limits and having bad connections/being blocked by their countries' firewall, which then directs traffic to GitHub as needed. The VPS uses Cloudflare to cache the data in turn and is only accessible via VPN and a hardware key.
2. `github.com`, `raw.githubusercontent.com`, and `goatcorp.github.io` - It's GitHub. You're on it right now!
3. `is.xivup.com` - basic community site to check for server status.

<hr>
<a href="{{ site.github.baseurl }}/">Return to the main FAQ</a>