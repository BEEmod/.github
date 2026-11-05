# Frequently Asked Questions

This is a list of answers to questions that have been frequently asked by users. If you are having problems with BEE2.4 or have a general question, check here first.

If you can't find the answer to your question, ask in the [discussions section](https://github.com/BEEmod/BEE2-items/discussions) or on [Discord](https://discord.gg/hnGFJrz). Do not open an issue to ask a question.

Also see [Frequently Rejected Suggestions](https://github.com/BEEmod/.github/blob/master/rejected_suggestions.md) for features we're commonly asked to add but can't or won't.

## Troubleshooting

### Where is the executable?

The executable is located in the root of the extracted folder. If it's not there, you might have downloaded the wrong file. Make sure you download the mod from the [releases page](https://github.com/BEEmod/BEE2.4/releases), and not using the "download code" button on the main page, as this will download the mod's source code rather than a compiled release. If the executable is still not there, it may have been silently deleted/quarantined by antivirus software (see below).

### Why is my antivirus flagging BEE2.4 as malware?

This is a known issue, and happens largely because BEEmod is an "unsigned" application. Signing an app is a [complex and potentially expensive process](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/code-signing-options) which is not currently feasible for us to pursue, so every new version of BEEmod will generally be blocked by default until it's been proven safe by enough people downloading it. The situation is further worsened for BEE due to the fact that many *real* viruses are also written in Python (resulting in similar binaries), and that a number of BEE's behaviors (such as copying files into Portal 2's install folder) can potentially appear malware-like at a glance.

BEE2.4 is used by many Portal 2 mappers and we can assure you that it does not contain any malicious code. If you don't want to take our word for it, you can [audit the code yourself](https://github.com/BEEmod/BEE2.4/tree/master/src) and build it from source.

### How do I revert BEE2's modifications to a game / why are editor textures still styled after validating the game files?

To fully uninstall BEE2.4, choose *File > Uninstall from Selected Game* within the BEE2 app. This will completely remove BEE2.4 from the selected game, including editor textures and custom assets. Validating Portal 2's files will **not** fully remove BEEmod and is not recommended - although it will restore the editor items and style to default, editor textures will not be reverted and many custom assets added by BEE2.4 will be left in the game files.

The BEE2 application itself can be uninstalled by simply deleting the folder it is installed to, though it is recommended to perform the above steps first.

### I exported my BEE2.4 map to Hammer and it won't compile/music won't play/<some other issue\>.

`puzzlemaker_export` does not work with BEEmod, as the custom compiler isn't able to modify the map and make it actually functional. Before reading on however, keep in mind that exporting Puzzlemaker maps to Hammer is usually not the best idea. If you want to make extensive modifications to a map, or are just starting out learning Hammer, it's generally easier to build a map from scratch, as Puzzlemaker maps (and especially BEEmod maps) are generated in a complex way making them difficult to edit by hand. You should only consider exporting a map if you really know what you're doing.

If this hasn't deterred you, first go into the BEE2 app and set Spawn Point to Elevator and disable Restart When Reaching Exit. Compile your map in Puzzlemaker, then open `maps/styled/preview.vmf` in Hammer and resave it to a different location so it doesn't get overwritten. Additionally, check your Build Programs settings to make sure that you're using the BEE2 version of VRAD (simply called `vrad.exe`), as this is needed for some features such as music to work.

### Do people playing my BEEmod maps need to install BEEmod themselves? / Why do people playing my maps see missing textures/models/sounds/etc?

BEE2.4 includes an auto-packing system that is designed to automatically bundle custom content into the map, so that players do not need to install it themselves.

If you're making maps on Linux, some files will not currently be detected by the autopacker due to case sensitivity problems, so you will need to pack these into your maps manually or direct players to download BEEmod themselves. This will be fixed in a future update.

On Windows, all custom content should correctly be packed into maps automatically. If players are seeing missing assets in your maps, this is a bug; please report it on the issue tracker.

### When I change the angle of Portal 1 panels it makes a high-pitched/corrupted noise, how do I fix it?

This is a known issue which seems to be related to audio caching, as the audio files themselves sound correct. One fix that seems to work is running the commands `snd_updateaudiocache` and `sv_soundemitter_flush` in the console, in that order. There's no way currently to make the mod apply this automatically, so in the next release we are removing these sound overrides entirely, and P1 panels will just use the regular Clean editor sounds.

## Compatibility

### Does BEE2.4 run on Linux?

Technically yes, but support is a work in progress so we don't currently list it alongside the regular downloads. Additionally, the Puzzlemaker itself is currently [entirely broken](https://github.com/ValveSoftware/portal2/issues/403) on Linux without a [workaround](https://github.com/ValveSoftware/portal2/issues/403#issuecomment-2868773822) (blame Valve for this).

After applying the workaround, if you want to give BEEmod a try, you can download the latest Linux [CI artifact builds](https://github.com/BEEmod/BEE2.4/actions/workflows/build.yml). Note that there are currently a number of UI bugs, and certain files will not be packed into maps correctly due to case sensitivity problems, but it should generally be possible to export to Portal 2 and compile maps.

**Running the Windows version of BEE2.4 in Wine does not currently work**; this is out of our control and caused by a Wine bug breaking one of the libraries we use. This means that by extension you cannot use BEE2.4 with the Proton version of Portal 2. You will need to make sure the game is using the native "Steam Linux Runtime" version, which can be configured through the properties menu in Steam.

### Does BEE2.4 run on macOS?

It used to, but we dropped support after the release of macOS Catalina in 2019, which made Portal 2 unable to run natively on the platform anymore. The last version of BEE2.4 to officially support macOS is [v4.36.1](https://github.com/BEEmod/BEE2.4/releases/tag/2.4.36.1_), though some newer versions might potentially have enough macOS-specifc code left over to build them from source.

Running the Windows version of BEE2.4 through compatibility software will likely also not work due to many of these programs being based on Wine (which BEE does not work with as stated above). You're welcome to give them a try though.

### Does BEE2.4 run on older Windows versions?

The minimum Windows version required by BEE2.4 has gradually increased over time, generally due to Python itself increasing its minimum requirements. The current version requires a 64-bit system running Windows 8.1 at minimum.

* The last version to support Windows 7, as well as 32-bit Windows 8.1 and 10, was [v4.45.2](https://github.com/BEEmod/BEE2.4/releases/tag/2.4.45.2)
* The last version to support Windows XP was [Pre-Release 24](https://github.com/BEEmod/BEE2.4/releases/tag/2.4.0pr24)

Note that since these operating systems are no longer receiving security updates, you should probably not be using them on your main PC. The corresponding BEE versions are similarly out of date (extremely so in the latter case) and may contain bugs which have since been patched.

### What games does BEE2.4 support?

BEE2.4 currently supports Portal 2 and Aperture Tag. However, the latter has somewhat broken workshop functionality due to using very old Portal 2 binaries, so we are considering removing support in a future version and making an alternative paint gun available in the base game instead. Thinking With Time Machine support was once considered, but will likely no longer be implemented for the same reason. If other Puzzlemaker-enabled mods are released in the future, we may add support for them.

### Is BEE2.4 compatible with licensed mods such as Portal 2: Community Edition?

Valve does not give out the Puzzlemaker source code to licensed mod developers, so they do not include it and thus are incompatible with BEEmod. There is some work being done on standalone puzzlemaker projects that would solve this problem, but as of writing none have reached a stable version, and these projects would likely also not be compatible with BEEmod nor have a need for it as they could include its functionality by default.

### Is BEE2.4 compatible with pirated/cracked versions of Portal 2?

We do not support cracked versions of Portal 2. While BEE2.4 may still work, we will not help you if you run into any problems. We highly recommend that you buy the game legally, which will also allow you to publish your maps to the Steam Workshop. Portal 2 only costs $10 USD by default, and is [frequently on sale](https://steamdb.info/app/620/) for even less than this.

### Is BEE2.4 compatible with the console versions of Portal 2?

The Puzzlemaker is only present in the PC version of the game, so BEEmod cannot support the console versions.<br>
<sub>(Yes, we do occasionally get asked this.)</sub>

## Content

### How do I use Catwalks/Vactubes/Unstationary Scaffolds?

These items effectively act as nodes, which need to be connected to each other in order to do anything. The exact way in which this works is different for each item, see their wiki pages for more details: [Vactubes](https://github.com/BEEmod/BEE2-items/wiki/Vactubes), [Catwalks](https://github.com/BEEmod/BEE2-items/wiki/Catwalks), and [Unstationary Scaffolds](https://github.com/BEEmod/BEE2-items/wiki/Unstationary-Scaffold)

### When is the next update for BEE2.4?

"When it's done." We don't have a set schedule for updates and release them whenever we feel that there are substantial enough additions, changes, or fixes for a new release. If you want to help us test upcoming versions before they're out, you can download the latest [CI artifact builds](https://github.com/BEEmod/BEE2.4/actions/workflows/build.yml), which are automatically generated from our development branch.

### Where's the Breakable Glass item? It's mentioned in the Bomb Cube's description.

Breakable Glass hasn't been reimplemented yet, but it is planned, which is why it's mentioned in the Bomb Cube description.

### Old versions of BEE2 had a lot more items, what happened to them and are they coming back?

BEE2.4 is a complete rewrite of the app with a different internal item format, so all of the old items need to be manually ported. This is in progress, see issue [#95](https://github.com/BEEmod/BEE2-items/issues/95) for more details.

### How do I use bottomless pits/what happened to 3D Factory?

The bottomless pits originally featured in BEEmod had significant problems, so they've been removed for the time being. The plan is to implement a "chamber exterior" system which would allow generating areas surrounding the map, including improved bottomless pits. However, this feature is not yet being worked on.

### What happened to BTS style?

For context, earlier versions of BEE2.4 included an unfinished Behind the Scenes style, which attempted to mimic the factory levels seen during the escape sections of Portal 2. It was never finished, filled with bugs, and eventually removed.

The style was made in the early days of the BEE2, before we had really figured out our scope. We made the decision to remove BTS because it's fundamentally incompatible with the way normal test chambers (and by extension Puzzlemaker maps) are built. Test chambers are made up of modular, reusable test elements; BTS on the other hand has much more specialized machines, such as the turret production line from the campaign. In many ways, BTS maps are more similar to Half-Life's environmental puzzles than Portal's test chambers.

Building a BTS map following the structure of a test chamber results in something which doesn't feel like a BTS map, just a test chamber with a skin on top of it - which is really all BEEmod styles are. That works fine when the skin is also a test chamber (or an equivalent), but if it's not, then the fact that it's just a skin becomes extremely obvious.
