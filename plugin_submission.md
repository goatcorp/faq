# The plugin approval process
In this article, we want to talk a little bit about how we decide what plugins can be merged into the official repo, and how we make sure that what goes in is safe for us and for you. It's important to know that none of what is described in this post applies to third-party repos - we can only do this for developers that officially submit their plugin.

## The technical details
At the start, we should go a little bit into how our submission process for plugins in the official repo works. This is a bit simplified, but it's the basis upon which the approval process is built on.

* All plugins in the official repository are open source, and no closed source plugins are accepted(apart from one legacy exception). This means that their code can be inspected by anyone, should they wish so.
* Plugin developers submit their plugin by submitting a "commit hash", which is a cryptographical hash that points to a **specific version of their source code**. They can't change their code anymore after we approve this hash without changing the hash, which will then force them to resubmit the plugin.[^1]
* A cloud buildsystem then downloads that source code, builds the plugin, and outputs a "diff", which is a **list of all changes that were made** to the plugin. The buildsystem has no direct internet access, so plugin developers can't download additional code while the plugin is being built.

All of this, combined, means that we can always be sure that the code that runs on users' PCs is the code we approved and that it doesn't touch anyone's actual hardware before we do so. We've built this system with convenience for developers and reviewers in mind, so it ideally doesn't put any burden on them - they just have to use some specific variables in their project configuration.

## The Plugin Approval Team
The plugin approval team is a subjectively chosen group of 6 volunteers that are technical, security conscious, are themselves plugin developers, think that they know how the Dalamud plugin ecosystem is supposed to work and agree on a few core points regarding what plugins should and shouldn't do.

They approve new plugin submissions, and review proposed changes to existing plugins.

## New submissions
When a plugin is newly submitted, the team checks that it conforms to a set of [guidelines](https://goatcorp.github.io/faq/development#q-what-am-i-allowed-to-do-in-my-plugin) and [technical criteria](https://github.com/goatcorp/DalamudPluginsD17#approval-criteria). The team then votes on each newly submitted plugin - if a plugin clears 4 yes votes, it is approved and will appear in the repo. Every team member can veto a plugin, blocking it from being merged until the concern is resolved. This hasn't happened yet.

The most important guidelines include...
- that the plugin does not interact with the game servers in a way that is:
    - automatic, as in polling data or making requests without direct interaction from the user
    - outside of specification, as in allowing the player to do submit things to the server that would not be possible by normal means
- that the plugin does not augment, alter, or interfere with combat, unless it only provides information about your own party or alliance members that is otherwise available, but represents said information differently.
    - Note that there are plugins on the repository that do not abide by this rule, but they have been grandfathered. We think that removing them would be stupid, but a lot of these plugins were accepted very early into Dalamud's life and we've learned a lot since then. They probably wouldn't be accepted if they were submitted nowadays.
- that the plugin does not interfere with Square Enix's monetary interests (i.e. granting access to Mog Station items) 

Technical criteria include a thorough code review, that the plugin works and that it does not upload any personal data. All of this can take a while, which is why it's not uncommon for a new plugin to sit in the queue for more than a week - all of the team members are doing this in their free time, so they might not get to it before then.

We also encourage all new plugins to go through the plugin testing track beforehand, which distributes the plugin to testing users before it goes out to everyone using Dalamud. This helps tracking down potential issues and bugs.

## Updates to plugins
Updates to plugins only need to be approved by a single team member, which helps keep the queue size small. The changed code is reviewed carefully, and the updated plugin is then built and distributed.

<img width="360" alt="Discord_vSFHENlBBd" src="https://user-images.githubusercontent.com/16760685/217103831-de5c1af3-7244-438e-8e8e-7408d2545814.png">
<em>What a plugin approval team member sees when they are being called in to review a change to a plugin.</em>

## Caveat Emptor
While this is all fine - and it has been working very well for us, without any incidents - all of this work is done by volunteers, and they might miss or overlook things. We can't and don't want to give you a 100% guarantee that things will always be fine, but we think that we can give you a pretty good assurance that they will be.

It's up to you to decide who you trust!

## In closing
I hope that this cleared up a few details on how plugins end up in the official Dalamud plugin listing. If you have any questions or think that something here could be clarified, feel free to reach out.

[^1]: Technically, this is still possible, but you would need NSA-grade datacenters and a lot of time(at the moment, probably hundreds of years) to break the hash algorithm Git uses.
