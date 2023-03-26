![X3 Colour By Race - Header](https://i.imgur.com/X98MQ7l.jpeg)
# <span style="color:blue">C</span><span style="color:green">o</span><span style="color:magenta">l</span><span style="color:orange">o</span><span style="color:yellow">u</span><td><span style="color:red">r</span></td> By Race

* Colour By Race is an AL plugin for X3:AP which colours the names of ships and stations across the galaxy. It makes for a cool looking and easier to parse sector map.
* Most objects only have part of their name coloured, usually the name of their race or corporation.
* More screenshots of Colour By Race in action at [this Imgur gallery](https://imgur.com/a/TSrPT8c).

## Install

Download the latest release from Github. Unzip the download and copy paste files into the `X3/addon/` folder. Files in
the `scripts/` folder go into the `scripts/` folder. File in the `t/` folder go into the `t/` folder.

Launch the game and load a save or start a new game. Navigate to `Main menu->Gameplay->Artificial life Settings` and activate the plugin.

### Optional Files

Optionally you can also use the following optional files. They are included in the zip file under `optional/`.

* Modified `8513` translation files for **[Pirate Guild 3](https://forum.egosoft.com/viewtopic.php?t=244949)**. PG3 dynamically renames pirate stations which overwrites any previously set coloured names. I've modified PG3's t files so that pirate stations will include colour in their name. Paste these files into your `X3/addon/t/` folder overwriting existing files if necessary.  
* Modified ship naming script `plugin.mbase.create.ship.name.xml` for **[Military Base Response Revamp](https://forum.egosoft.com/viewtopic.php?t=254599)**. Colours the race name during ship creation. Without this optional script, MBBR ships will remain uncoloured for a few minutes after creation until Colour By Race notices them.
* Modified ship naming script `plugin.salv.al.ship.cfg.xml` for **[Salvage Commands & NPCs](https://forum.egosoft.com/viewtopic.php?t=221059)**. Colours the race name during ship creation. Also added setting of pilot name, skill, morale and aggression and addition of Explorer Command software.

## Uninstall

Colour By Race creates a global variable as part of its initialisation. It deletes the global as part of deactivation.
To make sure the global isn't recreated when you load a save, follow these steps.

* Launch the game and load your save.
* Navigate to `Main menu->Gameplay->Artificial life Settings` and deactivate the plugin.
* Save your game.
* Delete the plugin files.
    * Open the `X3\addon\script` folder in Explorer and delete the relevant scripts. They all
      contain `plugin.jj.colour.by.race` as part of their filename.
    * Open the `X3\addon\t` folder and delete the `9965` t
      files.
    * Delete the `9964` translation files if you aren't using the True Relations plugin. The `9964` t file is used by both plugins.
* Load the save you made after deactivation. Colour By Race should be gone from the Artificial Life menu and its global will be removed from this save.

## Debug

To log debugging information run this MSCI code.

    $pluginData = [THIS]-> call script 'plugin.jj.colour.by.race.init.global' :
    $pluginData[3] = [TRUE]

Info will be logged to `log09965.txt`. By default this file is saved to `C:\Users\Username\Documents\Egosoft\X3AP` but may differ for your installation.

## Bugs

Found a bug? I'm keen to hear about it. Report it as a Github issue or on the Egosoft forum thread.

## Race Colours

If you want to change a race colour you can edit the entries in the t file. No colours are hardcoded in script files.

<table style="text-align:left;">
<thead>
    <tr>
        <th>Race</th>
        <th>Colour</th>
        <th>Code</th>
        <th>Example</th>
        <th>Note</th>
    </tr>
</thead>
<tbody>
    <tr>
        <td>Argon</td>
        <td><span style="color:blue">Blue</span></td>
        <td>\033B</td>
        <td><span style="color:blue">Argon</span> Freight Transporter</td>
    </tr>
    <tr>
        <td>Boron</td>
        <td><span style="color:green">Green</span></td>
        <td>\033G</td>
        <td><span style="color:green">B.</span> Large Orbital Weapon Platform</td>
        <td>Example of colouring shortened race name.</td>
    </tr>
    <tr>
        <td>Split</td>
        <td><span style="color:magenta">Magenta</span></td>
        <td>\033M</td>
        <td><span style="color:magenta">Military</span> Base</td>
        <td>Example of an object without a race specific string. In this case I simply colour the first word of the name.</td>
    </tr>
    <tr>
        <td>Paranid</td>
        <td><span style="color:orange">Orange</span></td>
        <td>\033O</td>
        <td><span style="color:orange">Paranid</span> Trading Dock</td>
    </tr>
    <tr>
        <td>Teladi</td>
        <td><span style="color:yellow">Yellow</span></td>
        <td>\033Y</td>
        <td><span style="color:yellow">NMMC</span> Security Buzzard</td>
        <td>Corporation names are also coloured as per the race they fall under.</td>
    </tr>
    <tr>
        <td>Pirates</td>
        <td><span style="color:red">Red</span></td>
        <td>\033R</td>
        <td><span style="color:red">Pirate</span> Blastclaw Prototype</td>
    </tr>
    <tr>
        <td>Goner</td>
        <td><span style="color:blue">Blue</span></td>
        <td>\033B</td>
        <td><span style="color:blue">Goner</span> Ozias</td>
    </tr>
    <tr>
        <td>Independant</td>
        <td><span style="color:cyan">Cyan</span></td>
        <td>\033C</td>
        <td><span style="color:cyan">Privateer Trading Post</span></td>
        <td>XRM's privateer trading posts is currently the only independant object coloured.</td>
    </tr>
    <tr>
        <td>ATF</td>
        <td><span style="color:grey">Grey</span></td>
        <td>\033A</td>
        <td><span style="color:grey">ATF</span> Escort Vali</td>
    </tr>
    <tr>
        <td>Terran</td>
        <td><span style="color:grey">Grey</span></td>
        <td>\033A</td>
        <td><span style="color:grey">Orbital Defence Station</span></td>
        <td>A rare example of an object where the entire name is coloured. Some stuff just looks weird partially coloured or prepended with a race name.</td>
    </tr>
    <tr>
        <td>Yaki</td>
        <td><span style="color:red">Red</span></td>
        <td>\033R</td>
        <td><span style="color:red">Yaki</span> Assassin Raijin Raider</td>
    </tr>
</tbody>
</table>

## What is coloured and what isn't

* Objects that are coloured:
    * Most ships.
    * Fighter Drones.
    * Stations:
        * Shipyards.
        * Docks including Equipment Docks, Trading Docks and Stock Exchanges.
        * Corporate HQs.
        * XRM Weapons Dealers.
* Objects that are not coloured:
    * Any player property is untouched.
    * Factories.
    * Most freight drones unless they have a race name.
    * Jump beacons.
    * Xenon or Kha'ak. I saw little value in colouring ships which are always hostile.

## How It Works

Renaming ships to include their color should be a straightforward process, but due to some peculiarities of X3, it becomes more complex than it should be.

When the plugin is activated, it goes through all the ships and stations in the universe and adds colours to their names. This process is repeated every time you load a saved game.

To add colors to ships spawned during gameplay, the plugin uses the `[SIGNAL_CHANGESECTOR]` signal, which is triggered when a ship is created. This approach is much more performance-friendly than checking the universe for new ships repeatedly. The plugin sets a local variable on each ship to prevent it from checking its name every time it changes sectors.

When renaming an individual ship, the plugin checks its name against an array of strings. If one of these strings is detected, that part of the name is colored. For example, for Argon ships, the plugin checks for the following strings: "Argon", "A.", "OTAS", "Terracorp", "Jonferco", "Plutarch", "Beryll," and "Privateer."

Unfortunately there are several situations where an object is spawned but not detected by `[SIGNAL_CHANGESECTOR]` or any other signal. The first issue is with stations, which do not trigger any signal upon creation, at least not in Albion Prelude. To ensure that stations are colored, the plugin takes the following steps:

* Checks the universe once every 30 minutes for new unnamed stations, focusing only on shipyards and docks. Although not ideal, this approach does not waste a significant amount of CPU.
* Checks the universe when the player changes sector.
* When `[SIGNAL_CHANGESECTOR]` triggers for a lasertower, checks if it has a homebase to colour. This is because lasertowers are often spawned to guard stations, so if a lasertower is respawning there's a reasonable chance that the homebase it was guarding has also recently respawned.

The second problem is with mods that create ships and rename them as part of their creation script. Although we can colour the ship name, the mod immediately overwrites our change. Pirate Guild and Military Base Response Revamp are two examples of mods where this is a problem. To mitigate this, the plugin adds each new ship to a global array when it spawns. This global array is checked and purged every 3 minutes, giving the mod to chance to rename the ship without being overwritten.

The third problem is with ships that spawn in docking bays instead of in space. These do not trigger `[SIGNAL_CHANGESECTOR]` or any other signal until they leave the dock. To mitigate this stations are checked for docked ships when their own names are checked 

The third problem is ships that are created inside docking bays instead of in space. These do not trigger a signal until they leave the dock. To mitigate this the plugin adds newly spawned carriers to a global array which is regularly checked for docked ships and then purged. Whenever a station is checked it is also checked for docked ships.

These engine limitations mean you'll occasionally see an uncoloured ship or station. But the additional checks performed by the plugin should make this a rare occasion.

## Warning!

Colour By Race currently does not include functionality to restore the names of ships and stations to their original uncoloured status. So make sure to back up your saves in case you don't like it. 

## Compatibility

* AP - Yes.
* TC - I'm not sure. Try it and let me know!
* Farnham's Legend - I've never played it, but it should work fine. Try it and let me know!
* [XRM](https://forum.egosoft.com/viewtopic.php?f=94&t=304158) - Yes, I developed this while playing on an LxXRM installation. The plugin includes code to handle several XRM specific objects. 
* Litcube's universe - I've never played it, so I'm not sure. Try it and let me know!
* [Military Base Response Revamp](https://forum.egosoft.com/viewtopic.php?t=254599) - Yes, especially if you overwrite MBBR's ship naming script with the included optional script. 
* [Pirate Guild](https://forum.egosoft.com/viewtopic.php?t=244949) - Yes, though station names will be overwritten so I strongly advise the optional included translation files. 

## Ancilliary Stuff
### Languages

Currently English only. If there's demand for other languages I can probably add them. 

### Why an X3 mod in 2023?

Because I'm an idiot.

### Thanks

* Thanks Egosoft for making a great game.
* Thanks Cycrow who saw my proof of concept and wrote me a primer on global signals in X3. 
