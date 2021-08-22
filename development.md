# Development FAQ

### Table of Contents
[How do I get started?](#q-how-do-i-get-started) <br>
[Where do I ask for help?](#q-where-do-i-ask-for-help) <br>
[How do I hot-reload my plugin?](#q-how-do-i-hot-reload-my-plugin) <br>
[How do I debug my plugin and/or the game?](#q-how-do-i-debug-my-plugin-andor-the-game) <br>
[How do I use FFXIVClientStructs in my own code?](#q-how-do-i-use-ffxivclientstructs-in-my-own-code) <br>
[What happens when there's an API version bump?](#q-what-happens-when-theres-an-api-version-bump) <br>
[How can I stay up to date with API changes?](#q-how-can-i-stay-up-to-date-with-api-changes) <br>
[What is the .NET5 upgrade?](#q-what-is-the-net5-upgrade) <br>
[What happens when the game is updated?](#q-what-happens-when-the-game-is-updated) <br>
[What am I allowed to do in my plugin?](#q-what-am-i-allowed-to-do-in-my-plugin) <br>
[Why do you discourage certain types of plugins?](#q-why-do-you-discourage-certain-types-of-plugins) <br>
[Are there any performance constraints to be aware of?](#q-are-there-any-performance-constraints-to-be-aware-of) <br>
[How do I get started with reverse-engineering the game so that I can do things Dalamud doesn't expose?](#q-how-do-i-get-started-with-reverse-engineering-the-game-so-that-i-can-do-things-dalamud-doesnt-expose) <br>
[How do I hook a game function?](#q-how-do-i-hook-a-game-function) <br>

<hr>

### Q: How do I get started?
The majority of the XIVLauncher and Dalamud ecosystem is written in C# for its usability, convenience, and robustness. It is recommended that anything you work on is also in C#, unless you're working on something with a significant amount of interoperation with native code (in which C++/CLI may be useful) or you're experimenting with other .NET languages.

To get started, you'll want to get the latest version of Visual Studio found [here](https://visualstudio.microsoft.com/downloads/); the Community edition will work fine. After doing so, you can clone any of the following projects and get to work with their Visual Studio solutions. Alternatively, you may want to use another IDE such as [JetBrains Rider](https://www.jetbrains.com/rider/). 

#### Dalamud Plugins
Plugins allow you to interact with the game and add features, modify functionality, and do much more. We ask you to be respectful of [our guidelines](#q-what-am-i-allowed-to-do-in-my-plugin) to ensure that your plugin is approved into the primary repository, and to minimise the risk of action by Square Enix. You can read more about this [here](#q-why-do-you-discourage-certain-types-of-plugins).

We recommend that you start by cloning one of the following templates, and then customising it to your requirements. While `SamplePlugin` is the most actively maintained, the others are updated as required:
- <https://github.com/goatcorp/SamplePlugin>
- <https://github.com/karashiiro/DalamudPluginProjectTemplate>
- <https://github.com/lmcintyre/PluginTemplate>

To distribute a plugin, it needs to be packaged correctly. This can be done manually or with DalamudPackager:
- <https://github.com/goatcorp/DalamudPackager>

When your plugin is ready for testing/release, it should be PRed over to the DalamudPlugins repo. **Please place testing plugins in the testing folder**.
- <https://github.com/goatcorp/DalamudPlugins>

#### Dalamud
Dalamud is the core addon/plugin system. It is loaded by XIVLauncher into your game, and is responsible for loading your plugins and providing them with a core set of functionality.

The Dalamud source code can be found in the repository or the project:
- <https://github.com/goatcorp/Dalamud>

Other assets required by Dalamud can be found here:
- <https://github.com/goatcorp/DalamudAssets>

You can find the Dalamud API page below, which also lists functions you can use in plugins.
- <https://goatcorp.github.io/Dalamud/api/index.html>


#### XIVLauncher
XIVLauncher is a custom launcher for FFXIV that offers a number of benefits, including faster launching, saved credentials, and automatically injecting Dalamud into the game.

The XIVLauncher source code can be found in the repository for the project:
<https://github.com/goatcorp/FFXIVQuickLauncher>

<hr>

### Q: Where do I ask for help?
The best place to ask for help is the [#dev channel](https://discord.gg/wwYXnzWYqY) of the Discord; we're a helpful bunch and will do our best to answer your query as long as you explain what you've tried and looked at so far.

<hr>

### Q: How do I hot-reload my plugin?
**.NET 5:** This functionality will be provided by the upcoming version of Dalamud (see [What is the .NET5 upgrade?](#q-what-is-the-net5-upgrade)).

**Current:**
To avoid manually copying the plugin to the plugins directory, Caraxi has developed the LivePluginLoad plugin that automatically reloads plugins when they change:
<https://github.com/Caraxi/LivePluginLoad>

To use it, open up Dalamud settings in-game with `/xlplugins`, click on Settings, go to Experimental, and add the following custom repository:
<http://repo.caraxian.com/>

LivePluginLoad can then be installed from the primary plugin list. After installing it, you can add your plugin to its list of tracked plugins. It will then be automatically loaded and reloaded when your plugin changes (e.g. is recompiled).

Note that `System.Reflection.Assembly.GetExecutingAssembly().Location` will return the wrong value if loaded through LPL. As a workaround, provide an `AssemblyLocation` property for LPL to fill in [as done in the SamplePlugin](https://github.com/goatcorp/SamplePlugin/blob/5251959ac02f0a57d76417a5abfbff680bfab4bf/SamplePlugin/Plugin.cs#L19).

<hr>

### Q: How do I debug my plugin and/or the game?
To debug, you'll need to attach a debugger to the game. This will usually be from your development environment, such as Visual Studio.

However, the game has antidebug protection on by default. To turn this off, use the Dalamud dev menu (`/xldev`), then go to Dalamud > Enable AntiDebug; this setting is persisted between launches, so you do not need to turn it on each time. 

Once you've done this, you can attach to the game with your debugger. In Visual Studio, you can go to Debug > Attach to Process (Ctrl+Alt+P), and then select the FF14 process. For the full debugging experience, make sure to change "Attach to" to include both `Native code` and `Managed (.NET 4.x) code`; this will ensure that the debugger will work for both the game and for Dalamud plugins.

This functionality is only supported for debugging your plugins. You will not receive support if you use it for anything else.

<hr>

### Q: How do I use FFXIVClientStructs in my own code?
[FFXIVClientStructs](https://github.com/aers/FFXIVClientStructs) is a communal project to provide an interface to the game's classes, data, and more to C# users and reverse engineers.

To use FFXIVClientStructs in your own code, you'll need to add a reference to it. This can be done by opening the `csproj` for your plugin and adding the reference with the other references:
```xml
    <Reference Include="FFXIVClientStructs">
      <HintPath>$(AppData)\XIVLauncher\addon\Hooks\dev\FFXIVClientStructs.dll</HintPath>
    </Reference>
```
or through right-clicking the project in VS, going to Add, and then adding an Assembly Reference to the same path. Note that you will likely need to still open the `csproj` after doing this to ensure that the path uses `$(AppData)` and not the path specific to your system.

However, the version of FFXIVClientStructs included with Dalamud is not updated very frequently, and may not feature the latest changes to the GitHub repository. To use the latest version, you'll need to pack it into your plugin using a tool like [ILRepack](https://github.com/gluck/il-repack).

<hr>

### Q: What happens when there's an API version bump?
When there's an API version bump, your plugin will no longer be loaded by Dalamud. To fix this, you'll need to update to the latest version of the API by updating the JSON file for your plugin and repackage your plugin for the repository.

<hr>

### Q: How can I stay up to date with API changes?
The best place to stay up to date with upcoming API changes is to frequent the [#dev channel of the Discord](https://discord.gg/wwYXnzWYqY). Changes will be announced with notice so that you can adapt your plugin as appropriate.

After submitting your first plugin to the repository, you will be given a Plugin Developer role so that you will be pinged whenever breaking changes occur.

<hr>

### Q: What is the .NET5 upgrade?
Currently, Dalamud is based on .NET Framework 4.7.2. .NET Framework is no longer seeing active development, with development efforts transitioning to .NET 5. Dalamud is adopting this new version of .NET which offers several benefits including, but not limited to, language and ecosystem improvements, simpler integrations, reduced friction with alternative execution environments (such as Linux), and more.

This is also being used as an opportunity to iron out longstanding issues in the Dalamud API, so there may be additional changes to your plugin other than switching which version of .NET you're targeting.

You can find more information about what to expect at the following links:
- _Roadmap_: https://github.com/goatcorp/Dalamud/discussions/479
- _General Breaking Changes_: https://github.com/goatcorp/Dalamud/discussions/458
- _Plugin API Redesign_: https://github.com/goatcorp/Dalamud/discussions/474
- _New Features_: https://github.com/goatcorp/Dalamud/discussions/471
- _Plugin Manifest Changes_: https://github.com/goatcorp/Dalamud/discussions/457

Additionally, the live-reloading functionaliy provided by LivePluginLoad has been integrated directly into Dalamud. More information on this can be found in the General Breaking Changes link above.

<hr>

### Q: What happens when the game is updated?
When the game is updated, it is likely that your plugin will stop working and/or Dalamud will refuse to load it. To fix this, you'll need to:

- Wait for Dalamud to update to accommodate the new game version.
- Update your plugin to ensure it's using the latest API version and still works with the game. Ensure that any non-Dalamud interactions with the game (e.g. direct interop, etc) have been updated.
- Repackage and reupload your plugin.

<hr>

### Q: What am I allowed to do in my plugin?
Dalamud plugin development, by its nature, interferes with the game's functioning and changes the experience as intended by Square Enix. This makes it very important to ensure that your plugin does not do anything that a human player could not do; Dalamud plugins should enhance the experience, not radically alter it.

Please make sure that your plugin does not interact with the game servers in a way that is:
- automatic, as in polling data or making requests without direct interaction from the user
- outside of specification, as in allowing the player to do submit things to the server that would not be possible by normal means

Plugins that violate this will not be accepted into the Dalamud plugin repository, and you will not receive support from the Dalamud community. 

<hr>

### Q: Why do you discourage certain types of plugins?
> Dalamud and XIVLauncher were made by me with the goal to do cool stuff with a game I love, and give others the chance to do so while making the game itself more accessible. I don't want to cause harm to the game, its community or Square Enix. Plugins that fall outside of the definition of "acceptable" that we set as a collective create a divide and debate that we don't want to be a part of.<br>This stance of mine has narrowed down as XIVLauncher has gained popularity, as you may notice by going through some of the first plugins to be added.
> 
> Obviously, this comes from a moral point of view, which may differ from yours - and the rules and decisions I make may sometimes seem unjustified - but I want to minimize the risk of Square Enix taking action and taking away the things we built, while degrading the general user experience of their game.
> 
> I can't and don't want to control anyone that makes free software based on my work, but I would like to ask you to consider and empathize with my opinion when creating software that depends on Dalamud.
- [goat](https://github.com/goaaats), the lead developer of XIVLauncher/Dalamud

<hr>

### Q: Are there any performance constraints to be aware of?
You should generally aim to not impact game performance too much as that can degrade the experience for the player and cause other issues. A good place to start debugging performance issues is through the Plugin Statistics window, which can be found through Plugins > Open Plugin Stats in the dev menu (`/xldev`).

<hr>

### Q: How do I get started with reverse-engineering the game so that I can do things Dalamud doesn't expose?
Reverse-engineering isn't easy, and it's even more difficult when reversing a large game like FFXIV. It's a large subject and hard to explore, but here are some rough pointers.

Fundamentally, the game is running on your machine, which means it's executing code constantly to run the game logic and to render the scene. In addition, it is constantly talking to the game server, which is what allows you to interact with other players and the world at large.

If you'd like to learn more about how the game communicates with the server, your best bet is the [Sapphire project](https://github.com/SapphireServer/Sapphire). The Dalamud project generally strays away from interfering with client-server communication for the reasons outlined in [What am I allowed to do in my plugin?](#q-what-am-i-allowed-to-do-in-my-plugin), but understanding the flow may help with other things.

Otherwise, you'll be reverse-engineering the game client, as that's what Dalamud hooks into. The game binary you have is compiled machine code; the original source code for the game is unavailable, which means you have to figure out what it's doing without knowing any of the original context.

To do this, you'll need an interactive disassembler/decompiler to conduct _static analysis_. The gold standard for this is [IDA Pro](https://hex-rays.com/ida-pro/), but it is very expensive for hobbyists and most people take an approach generally frowned upon by the Maelstrom. A popular free alternative is [Ghidra](https://ghidra-sre.org/), which is very powerful and extensible, if not a little clunky. There are other disassemblers, but these are the two primarily used by the Dalamud community.

Once you have your disassembler ready, you'll need to disassemble the `ffxiv_dx11.exe` file in the game's directory. After doing this, it is highly recommended that you use [the excellent script provided by FFXIVClientStructs](https://github.com/aers/FFXIVClientStructs/tree/main/ida); this script will automatically populate your disassembler's database with community findings for the current version, saving you a great deal of time.

After that, well... it's time for you to work on the puzzle. You'll want to find resources for how to reverse-engineer things online; there are tutorials that specifically look at reversing games, which may help you build up an intuition for the thought process you'll need.

Another approach you can take is _dynamic analysis_. You can attach a debugger to the game, like [x64dbg](https://x64dbg.com/) or [Cheat Engine](https://www.cheatengine.org/), and use these to explore the game's memory and execution at runtime (e.g. searching for a value and finding what changes it in the code). Both approaches are valid, but you'll likely need to use both to make headway as they can provide context for each other.

Reversing is a large and complex field, and it takes years to get proficient and recognise patterns. Asking the Discord for help is encouraged, but be aware that you have a long journey ahead of you regardless.

<hr>

### Q: How do I hook a game function?
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
