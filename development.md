# Development FAQ

## Table of Contents

### Getting started

- [How do I get started?](#q-how-do-i-get-started)
- [Where do I ask for help?](#q-where-do-i-ask-for-help)
- [How do I hot-reload my plugin?](#q-how-do-i-hot-reload-my-plugin)
- [How do I debug my plugin and/or the game?](#q-how-do-i-debug-my-plugin-andor-the-game)
- [How do I use FFXIVClientStructs in my own code?](#q-how-do-i-use-ffxivclientstructs-in-my-own-code)

### Updates

- [What happens when there's an API version bump?](#q-what-happens-when-theres-an-api-version-bump)
- [How can I stay up to date with API changes?](#q-how-can-i-stay-up-to-date-with-api-changes)
- [What is the .NET5 upgrade?](#q-what-is-the-net5-upgrade)
- [How do I fix `Nothing inherits from IDalamudPlugin`?](#q-how-do-i-fix-nothing-inherits-from-idalamudplugin)
- [What happens when the game is updated?](#q-what-happens-when-the-game-is-updated)

### Restrictions

- [What am I allowed to do in my plugin?](#q-what-am-i-allowed-to-do-in-my-plugin)
- [Why do you discourage certain types of plugins?](#q-why-do-you-discourage-certain-types-of-plugins)
- [Are there any performance constraints to be aware of?](#q-are-there-any-performance-constraints-to-be-aware-of)

### Development

- [How do the services in Dalamud work?](#q-how-do-the-services-in-dalamud-work)
- [What are the currently available Dalamud services?](#q-what-are-the-currently-available-dalamud-services)
- [How do I convert from world coordinates to map coordinates and vice versa?](#q-how-do-i-convert-from-world-coordinates-to-map-coordinates-and-vice-versa)

### Reverse engineering

- [How do I get started with reverse-engineering the game so that I can do things Dalamud doesn't expose?](#q-how-do-i-get-started-with-reverse-engineering-the-game-so-that-i-can-do-things-dalamud-doesnt-expose)
- [How do I hook a game function?](#q-how-do-i-hook-a-game-function)

---

## Q: How do I get started?

The majority of the XIVLauncher and Dalamud ecosystem is written in C# for its usability, convenience, and robustness. It is recommended that anything you work on is also in C#, unless you're working on something with a significant amount of interoperation with native code (in which C++/CLI may be useful) or you're experimenting with other .NET languages.

To get started, you'll want to get the latest version of Visual Studio found [here](https://visualstudio.microsoft.com/downloads/); the Community edition will work fine. After doing so, you can clone any of the following projects and get to work with their Visual Studio solutions. Alternatively, you may want to use another IDE such as [JetBrains Rider](https://www.jetbrains.com/rider/).

### Dalamud Plugins

Plugins allow you to interact with the game and add features, modify functionality, and do much more. We ask you to be respectful of [our guidelines](#q-what-am-i-allowed-to-do-in-my-plugin) to ensure that your plugin is approved into the primary repository, and to minimise the risk of action by Square Enix. You can read more about this [here](#q-why-do-you-discourage-certain-types-of-plugins).

We recommend that you start by cloning one of the following templates, and then customising it to your requirements. While `SamplePlugin` is the most actively maintained, the others are updated as required:

- <https://github.com/goatcorp/SamplePlugin>
- <https://github.com/karashiiro/DalamudPluginProjectTemplate>
- <https://github.com/lmcintyre/PluginTemplate>

To distribute a plugin, it needs to be packaged correctly. This can be done manually or with DalamudPackager:

- <https://github.com/goatcorp/DalamudPackager>

When your plugin is ready for testing/release, it should be PRed over to the DalamudPlugins repo. **Please place testing plugins in the testing folder**.

- <https://github.com/goatcorp/DalamudPlugins>

### Dalamud

Dalamud is the core addon/plugin system. It is loaded by XIVLauncher into your game, and is responsible for loading your plugins and providing them with a core set of functionality.

The Dalamud source code can be found in the repository or the project:

- <https://github.com/goatcorp/Dalamud>

Other assets required by Dalamud can be found here:

- <https://github.com/goatcorp/DalamudAssets>

You can find the Dalamud API page below, which also lists functions you can use in plugins.

- <https://goatcorp.github.io/Dalamud/api/index.html>

### XIVLauncher

XIVLauncher is a custom launcher for FFXIV that offers a number of benefits, including faster launching, saved credentials, and automatically injecting Dalamud into the game.

The XIVLauncher source code can be found in the repository for the project:
<https://github.com/goatcorp/FFXIVQuickLauncher>

---

## Q: Where do I ask for help?

The best place to ask for help is the [#dev channel](https://discord.gg/wwYXnzWYqY) of the Discord; we're a helpful bunch and will do our best to answer your query as long as you explain what you've tried and looked at so far.

---

## Q: How do I hot-reload my plugin?

As of API 4/Dalamud 6, hot-reloading is part of Dalamud. To use it, go to Dalamud Settings > Experimental > Dev Plugin Locations, and then add either the folder that your plugin is in or the plugin itself. If you add a folder, Dalamud will attempt to load all DLLs within the folder.

Your configuration should look something like this:
![image](https://user-images.githubusercontent.com/707827/166122747-97f0f7c7-e1a4-4093-adeb-5c7c8eab935c.png)

---

## Q: How do I debug my plugin and/or the game?

To debug, you'll need to attach a debugger to the game. This will usually be from your development environment, such as Visual Studio.

However, the game has antidebug protection on by default. To turn this off, use the Dalamud dev menu (`/xldev`), then go to Dalamud > Enable AntiDebug; this setting is persisted between launches, so you do not need to turn it on each time.

Once you've done this, you can attach to the game with your debugger. In Visual Studio, you can go to Debug > Attach to Process (Ctrl+Alt+P), and then select the FF14 process. For the full debugging experience, make sure to change "Attach to" to include both `Native code` and `Managed (.NET 4.x) code`; this will ensure that the debugger will work for both the game and for Dalamud plugins.

This functionality is only supported for debugging your plugins. You will not receive support if you use it for anything else.

[Detailed instruction available here.](debug.md)

---

## Q: How do I use FFXIVClientStructs in my own code?

[FFXIVClientStructs](https://github.com/aers/FFXIVClientStructs) is a communal project to provide an interface to the game's classes, data, and more to C# users and reverse engineers.

To use FFXIVClientStructs in your own code, you'll need to add a reference to it. This can be done by opening the `csproj` for your plugin and adding the reference with the other references:

```xml
    <Reference Include="FFXIVClientStructs">
      <HintPath>$(AppData)\XIVLauncher\addon\Hooks\dev\FFXIVClientStructs.dll</HintPath>
    </Reference>
```

or through right-clicking the project in VS, going to Add, and then adding an Assembly Reference to the same path. Note that you will likely need to still open the `csproj` after doing this to ensure that the path uses `$(AppData)` and not the path specific to your system.

However, the version of FFXIVClientStructs included with Dalamud is not updated very frequently, and may not feature the latest changes to the GitHub repository. To use the latest version, you'll need to pack it into your plugin using a tool like [ILRepack](https://github.com/gluck/il-repack).

---

## Q: What happens when there's an API version bump?

When there's an API version bump, your plugin will no longer be loaded by Dalamud. To fix this, you'll need to update to the latest version of the API by updating the JSON file for your plugin and repackaging your plugin for the repository.

---

## Q: How can I stay up to date with API changes?

The best place to stay up to date with upcoming API changes is to frequent the [Discord server](https://goat.place/). Changes will be announced with notice so that you can adapt your plugin as appropriate.

After submitting your first plugin to the repository, you will be given a Plugin Developer role so that you will be pinged whenever breaking changes occur.

---

## Q: What is the .NET5 upgrade?

Dalamud 6.0 has adopted .NET 5, the latest version of .NET, and has used this opportunity to improve the Dalamud API with version 4 of the API. All new plugins are on API 4 or above. If you are creating a new plugin, or have already updated your plugin, you can stop reading now.

If you are porting an existing plugin, please consult the following links:

- Roadmap: <https://github.com/goatcorp/Dalamud/discussions/479>
- General Breaking Changes: <https://github.com/goatcorp/Dalamud/discussions/458>
- Plugin API Redesign: <https://github.com/goatcorp/Dalamud/discussions/474>
- New Features: <https://github.com/goatcorp/Dalamud/discussions/471>
- Plugin Manifest Changes: <https://github.com/goatcorp/Dalamud/discussions/457>

---

## Q: How do I fix `Nothing inherits from IDalamudPlugin`?

This occurs because you have the dependencies for your plugin in the same folder as the plugin (e.g. `Dalamud.dll` and such). This was supported prior to .NET 5, but is no longer supported.

To fix this, open the `csproj` file and add `<Private>false</Private>` to each of your `Reference`s like so:

```xml
<Reference Include="Dalamud">
    <HintPath>$(AppData)\XIVLauncher\addon\Hooks\dev\Dalamud.dll</HintPath>
    <Private>false</Private>
</Reference>
```

After doing this, clean out your output folder and rebuild. It will no longer copy the dependencies, and your plugin should now be able to load correctly.

---

## Q: What happens when the game is updated?

When the game is updated, it is likely that your plugin will stop working and/or Dalamud will refuse to load it. To fix this, you'll need to:

- Wait for Dalamud to update to accommodate the new game version.
- Update your plugin to ensure it's using the latest API version and still works with the game. Ensure that any non-Dalamud interactions with the game (e.g. direct interop, etc) have been updated.
- Repackage and reupload your plugin.

---

## Q: What am I allowed to do in my plugin?

Dalamud plugin development, by its nature, interferes with the game's functioning and changes the experience as intended by Square Enix. This makes it very important to ensure that your plugin does not do anything that a human player could not do; Dalamud plugins should enhance the experience, not radically alter it.

Please make sure that your plugin does not interact with the game servers in a way that is:

- automatic, as in polling data or making requests without direct interaction from the user
- outside of specification, as in allowing the player to do submit things to the server that would not be possible by normal means

Plugins that violate this will not be accepted into the Dalamud plugin repository, and you will not receive support from the Dalamud community.

---

## Q: Why do you discourage certain types of plugins?

> Dalamud and XIVLauncher were made by me with the goal to do cool stuff with a game I love, and give others the chance to do so while making the game itself more accessible. I don't want to cause harm to the game, its community or Square Enix. Plugins that fall outside of the definition of "acceptable" that we set as a collective create a divide and debate that we don't want to be a part of.
>
> This stance of mine has narrowed down as XIVLauncher has gained popularity, as you may notice by going through some of the first plugins to be added.
>
> Obviously, this comes from a moral point of view, which may differ from yours - and the rules and decisions I make may sometimes seem unjustified - but I want to minimize the risk of Square Enix taking action and taking away the things we built, while degrading the general user experience of their game.
>
> I can't and don't want to control anyone that makes free software based on my work, but I would like to ask you to consider and empathize with my opinion when creating software that depends on Dalamud.

- [goat](https://github.com/goaaats), the lead developer of XIVLauncher/Dalamud

---

## Q: Are there any performance constraints to be aware of?

You should generally aim to not impact game performance too much as that can degrade the experience for the player and cause other issues. A good place to start debugging performance issues is through the Plugin Statistics window, which can be found through Plugins > Open Plugin Stats in the dev menu (`/xldev`).

---

## Q: How do the services in Dalamud work?

Dalamud is composed of many services, with the `Dalamud.IoC.PluginInterfaceAttribute` attribute, that provide you access to game and Dalamud state. You can opt into these services by including them in the constructor of the plugin, like so,

```csharp
public Plugin(
    [RequiredVersion("1.0")] DalamudPluginInterface pluginInterface,
    [RequiredVersion("1.0")] CommandManager commandManager)
```

or by including them as an appropriately-attributed static variables in a class, and then using the plugin interface you get in the constructor (it's mandatory!) to initialise said class:

```csharp
public class Dalamud
{
    public static void Initialize(DalamudPluginInterface pluginInterface) =>
        pluginInterface.Create<Dalamud>();

    [PluginService]
    [RequiredVersion("1.0")]
    public static DalamudPluginInterface PluginInterface { get; private set; } = null!;
    [PluginService]
    [RequiredVersion("1.0")]
    public static CommandManager Commands { get; private set; } = null!;
}

public Plugin(DalamudPluginInterface pluginInterface)
{
    Dalamud.Initialize(pluginInterface);
}
```

---

## Q: What are the currently available Dalamud services?

As of Dalamud 6.3, these are all of the currently available services. Please update this list if you spot a discrepancy!

- [`Dalamud.Data.DataManager`](https://goatcorp.github.io/Dalamud/api/Dalamud.Data.DataManager.html)
- [`Dalamud.Game.ClientState.Aetherytes.AetheryteList`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Aetherytes.AetheryteList.html)
- [`Dalamud.Game.ClientState.Buddy.BuddyList`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Buddy.BuddyList.html)
- [`Dalamud.Game.ClientState.Conditions.Condition`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Conditions.Condition.html)
- [`Dalamud.Game.ClientState.Fates.FateTable`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Fates.FateTable.html)
- [`Dalamud.Game.ClientState.GamePad.GamepadState`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.GamePad.GamepadState.html)
- [`Dalamud.Game.ClientState.JobGauge.JobGauges`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.JobGauge.JobGauges.html)
- [`Dalamud.Game.ClientState.Keys.KeyState`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Keys.KeyState.html)
- [`Dalamud.Game.ClientState.Objects.ObjectTable`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Objects.ObjectTable.html)
- [`Dalamud.Game.ClientState.Objects.TargetManager`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Objects.TargetManager.html)
- [`Dalamud.Game.ClientState.Party.PartyList`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.Party.PartyList.html)
- [`Dalamud.Game.ClientState.ClientState`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ClientState.ClientState.html)
- [`Dalamud.Game.Command.CommandManager`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Command.CommandManager.html)
- [`Dalamud.Game.Gui.ContextMenus.ContextMenu`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.ContextMenus.ContextMenu.html)
- [`Dalamud.Game.Gui.Dtr.DtrBar`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.Dtr.DtrBar.html)
- [`Dalamud.Game.Gui.FlyText.FlyTextGui`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.FlyText.FlyTextGui.html)
- [`Dalamud.Game.Gui.PartyFinder.PartyFinderGui`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.PartyFinder.PartyFinderGui.html)
- [`Dalamud.Game.Gui.Toast.ToastGui`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.Toast.ToastGui.html)
- [`Dalamud.Game.Gui.ChatGui`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.ChatGui.html)
- [`Dalamud.Game.Gui.GameGui`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Gui.GameGui.html)
- [`Dalamud.Game.Libc.LibcFunction`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Libc.LibcFunction.html)
- [`Dalamud.Game.Network.GameNetwork`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Network.GameNetwork.html)
- [`Dalamud.Game.Text.SeStringHandling.SeStringManager`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Text.SeStringHandling.SeStringManager.html)
- [`Dalamud.Game.ChatHandlers`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.ChatHandlers.html)
- [`Dalamud.Game.Framework`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.Framework.html)
- [`Dalamud.Game.SigScanner`](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.SigScanner.html)
- [`Dalamud.Interface.TitleScreenMenu`](https://goatcorp.github.io/Dalamud/api/Dalamud.Interface.TitleScreenMenu.html)

---

## Q: How do I convert from world coordinates to map coordinates and vice versa?

Please consult the [ffxiv-datamining documentation on MapCoordinates](https://github.com/xivapi/ffxiv-datamining/blob/master/docs/MapCoordinates.md), which details how to convert between the various kinds of coordinates.

---

## Q: How do I get started with reverse-engineering the game so that I can do things Dalamud doesn't expose?

Reverse-engineering isn't easy, and it's even more difficult when reversing a large game like FFXIV. It's a large subject and hard to explore, but here are some rough pointers.

Fundamentally, the game is running on your machine, which means it's executing code constantly to run the game logic and to render the scene. In addition, it is constantly talking to the game server, which is what allows you to interact with other players and the world at large.

If you'd like to learn more about how the game communicates with the server, your best bet is the [Sapphire project](https://github.com/SapphireServer/Sapphire). The Dalamud project generally strays away from interfering with client-server communication for the reasons outlined in [What am I allowed to do in my plugin?](#q-what-am-i-allowed-to-do-in-my-plugin), but understanding the flow may help with other things.

Otherwise, you'll be reverse-engineering the game client, as that's what Dalamud hooks into. The game binary you have is compiled machine code; the original source code for the game is unavailable, which means you have to figure out what it's doing without knowing any of the original context.

To do this, you'll need an interactive disassembler/decompiler to conduct _static analysis_. The gold standard for this is [IDA Pro](https://hex-rays.com/ida-pro/), but it is very expensive for hobbyists and most people take an approach generally frowned upon by the Maelstrom. A popular free alternative is [Ghidra](https://ghidra-sre.org/), which is very powerful and extensible, if not a little clunky. There are other disassemblers, but these are the two primarily used by the Dalamud community.

Once you have your disassembler ready, you'll need to disassemble the `ffxiv_dx11.exe` file in the game's directory. After doing this, it is highly recommended that you use [the excellent script provided by FFXIVClientStructs](https://github.com/aers/FFXIVClientStructs/tree/main/ida); this script will automatically populate your disassembler's database with community findings for the current version, saving you a great deal of time.

After that, well... it's time for you to work on the puzzle. You'll want to find resources for how to reverse-engineer things online; there are tutorials that specifically look at reversing games, which may help you build up an intuition for the thought process you'll need.

Another approach you can take is _dynamic analysis_. You can attach a debugger to the game, like [x64dbg](https://x64dbg.com/) or [Cheat Engine](https://www.cheatengine.org/), and use these to explore the game's memory and execution at runtime (e.g. searching for a value and finding what changes it in the code). Both approaches are valid, but you'll likely need to use both to make headway as they can provide context for each other.

Reversing is a large and complex field, and it takes years to get proficient and recognise patterns. Asking the Discord for help is encouraged, but be aware that you have a long journey ahead of you regardless.

---

## Q: How do I hook a game function?

Hooking a function refers to intercepting its execution, so that your code runs in lieu of or as an extension to it. This could allow you to, for example, detect when a certain action occurs in-game and change its behaviour.

Assuming that you've successfully found a function you'd like to hook through reverse-engineering, Dalamud and EasyHook make hooking functions fairly easy. You'll need the address of the function to hook; this can be retrieved from your disassembler, or by getting a "signature" for the function, which is a unique string of instructions that can be used to find the address.

Using signatures is preferred where possible as it improves the chances of your plugin surviving a game update (as addresses always change, while signatures do not). To get a signature, you'll need to look up how to do it with your preferred disassembler. For IDA, [Caraxi's fork of SigMaker-x64](https://github.com/Caraxi/SigMaker-x64) is recommended.

If you have a signature, you will need to resolve it to an address in your code. For a traditional string-of-instruction-bytes signature, you can use [ScanText](https://goatcorp.github.io/Dalamud/api/Dalamud.Game.SigScanner.html#Dalamud_Game_SigScanner_ScanText_System_String_). For other types of signatures, please look at the other methods for `SigScanner` and choose an appropriate one.

After that:

- Import `Dalamud.Hooking`.
- Create a delegate type with the same type signature as the function you're hooking.
- Create a `Hook<YourDelegateType>` variable to represent the hook.
- Create a function in which your custom code will execute. It should match the type signature of the delegate.
- In your `Initialize` function:
  - Get the address for the function (either as-is or through a signature).
  - Initialize your `Hook` variable by calling its constructor with the address, delegate-ified version of your custom code function, and `this`.
  - Enable the hook.
- In your `Dispose` function:
  - Disable the hook.
  - Dispose of the hook.

You should then be ready to go. An abbreviated example (only relevant portions shown) of hooking the main `Render` function for the game follows:

```c#
using Dalamud.Hooking;
using Dalamud.Plugin;

namespace SamplePlugin
{
    public class Plugin : IDalamudPlugin
    {
        public string Name => "SamplePlugin";

        private DalamudPluginInterface pi;

        public delegate IntPtr RenderDelegate(IntPtr renderManager);
        private Hook<RenderDelegate> renderDelegateHook;

        public void Initialize(DalamudPluginInterface pluginInterface)
        {
            this.pi = pluginInterface;

            // Render::Manager::Render
            var Signature = "40 53 55 57 41 56 41 57 48 83 EC 60";
            var renderAddress = this.pi.TargetModuleScanner.ScanText(Signature);

            this.renderDelegateHook = new Hook<RenderDelegate>(renderAddress, this.RenderDetour);
            this.renderDelegateHook.Enable();
        }

        private unsafe IntPtr RenderDetour(IntPtr renderManager)
        {
            PluginLog.Information("Before render");
            var res = this.renderDelegateHook.Original(renderManager);
            PluginLog.Information("After render");

            return res;
        }

        public void Dispose()
        {
            this.renderDelegateHook.Disable();
            this.renderDelegateHook.Dispose();
            this.pi.Dispose();
        }
    }
}
```

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
