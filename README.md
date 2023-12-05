![X3 Colour By Race - Header](https://i.imgur.com/X98MQ7l.jpeg)
# <span style="color:blue">C</span><span style="color:green">o</span><span style="color:magenta">l</span><span style="color:orange">o</span><span style="color:yellow">u</span><td><span style="color:red">r</span></td> By Race

* Colour By Race is an AL plugin for X3:TC, X3:AP and X3:FL which colours the names of ships, stations across the galaxy. It makes for a cool looking and easier to parse sector and universe map.
    * Most objects only have part of their name coloured, usually the name of their race or corporation.
    * New ships and stations will have their names coloured as they spawn.
    * Default colours are editable in the t file.
    * Object names will change colour when they change owner or when a disguised smuggler is discovered. 
* As of version 2.0.0 you can also colour the names of sectors in X3:FL only. Sector colouring is activated as a separate AL plugin so you can use it standalone or alongside colouring ships & stations.
    * FL version of Colour By Race requires the [latest version of Cycrow's unofficial patch](https://www.xpluginmanager.co.uk/download/x3fl-unofficial-patch/).  
    * Border sectors can be set to use different colours to core sectors.
    * Sector colour will automatically change when the sector changes owner. 
* More screenshots of Colour By Race in action at [this Imgur gallery](https://imgur.com/a/TSrPT8c).
  
![X3 Colour By Race - Universe Map](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/ebde1362-fc89-41c0-8cbb-7fd49b45585f)

## Install

Download the [latest release](https://github.com/jamesjonesphoenix/colour-by-race/releases) from Github. You probably want to download the `.zip` file not the `.tar.gz` file. Unzip the download and copy paste files into the `X3/addon/` folder. Files in the `scripts/` folder go into the `scripts/` folder. Files in the `t/` folder go into the `t/` folder.

Launch the game and load a save or start a new game. Navigate to `Main menu->Gameplay->Artificial life Settings` and activate "Colour By Race" and/or "Colour By Sector".

### Farnham's Legend

If installing for Farnham's Legend put the files into the `X3/addon2` folder instead of the `X3/addon` folder. 

### Optional Files

Optionally you can also use the following optional files. They are included in the zip file under `optional/`.

* Modified `8513` translation files for **[Pirate Guild 3](https://forum.egosoft.com/viewtopic.php?t=244949)**. PG3 dynamically renames pirate stations which overwrites any previously set coloured names. I've modified PG3's t files so that pirate stations will include colour in their name. Paste these files into your `X3/addon/t/` folder overwriting existing files if necessary.  
* Modified ship naming script `plugin.mbase.create.ship.name.xml` for **[Military Base Response Revamp](https://forum.egosoft.com/viewtopic.php?t=254599)**. Colours the race name during ship creation. Without this you have a very small chance of seeing MBBR ships uncoloured for half a second after creation.
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
    * Open the `X3\addon\t` folder and delete the `9964` and `9965` t files.
* Load the save you made after deactivation. Colour By Race should be gone from the Artificial Life menu and its global will be missing from this save.

## Debug

As of v2.0.0, Colour By Race has a dedicated script for activating debugging. To log debugging information run this MSCI code.

    = [THIS]-> call script 'plugin.jj.colour.by.race.set.debug' :

Info will be logged to `log09964.txt`. By default this file is saved to `C:\Users\Username\Documents\Egosoft\X3FL` or similar. Your installation may differ. Note that the plugin will generate a large amount of data. The debug file can reach 25MB in size after just a few hours gameplay.

You can disable debugging by running the same script with the "disable" flag set to true:

    = [THIS]-> call script 'plugin.jj.true.relations.set.debug' : disable=[TRUE]

Deactivating Colour By Race in the AL game menu will also disable debugging. 

## Bugs

Found a bug? I'm keen to hear about it. Report it as a Github issue or on the Egosoft forum thread. I'm particularly keen to hear about uncoloured ships or stations that should be coloured. 

## Default Race Colours

If you want to change a race's assigned colour you can edit the entries in the `9964` translation file. No colours are hardcoded in script files. The t file contains extensive comments documenting settings.

| **Race** | - | **Colour** | **Code** | **Image Example** | **Note**  |
|:--- |:--- |:--- |:--- |:--- |:--- |
| Argon | ![#0000EE](https://placehold.co/15x15/0000EE/0000EE.png) | <span style="color:blue">Blue</span> | \033B | ![Argon Freight Transporter](https://user-images.githubusercontent.com/15099626/228219482-75818669-ecdc-4268-ae83-4bb1f1887ab5.jpg) | |
| Boron | ![#008000](https://placehold.co/15x15/008000/008000.png) | <span style="color:green">Green</span> | \033G | ![Boron Orbital Weapons Platform](https://user-images.githubusercontent.com/15099626/228237945-17f16d84-d1d3-4bd0-ada7-8c41388fefb1.jpg) | Example of colouring shortened race name. |
| Split | ![#FF00FF](https://placehold.co/15x15/FF00FF/FF00FF.png) | <span style="color:magenta">Magenta</span> | \033M | ![Military Outpost](https://user-images.githubusercontent.com/15099626/228248282-cd013b77-d9f9-46b3-9197-239d5f700a71.jpg) | Example of an object without a race specific string. In this case I simply colour the first word of the name. | 
| Paranid | ![#FFA500](https://placehold.co/15x15/FFA500/FFA500.png) | <span style="color:orange">Orange</span> | \033O | ![Paranid Trading Dock](https://user-images.githubusercontent.com/15099626/228232666-2519a51e-96ce-4d24-86aa-00be77520ba5.jpg) | |
| Teladi | ![#FFFF00](https://placehold.co/15x15/FFFF00/FFFF00.png) | <span style="color:yellow">Yellow</span> | \033Y | ![NMMC Security Buzzard](https://user-images.githubusercontent.com/15099626/228244404-c5f836de-389f-499f-80aa-500f9df5aa23.jpg) | Corporation names are coloured in the same way as a race. |
| Pirates | ![#FF0000](https://placehold.co/15x15/FF0000/FF0000.png) | <span style="color:red">Red</span> | \033R | ![Pirate Blastclaw Prototype](https://user-images.githubusercontent.com/15099626/228249210-a1d5deec-ec33-4b7b-9556-2ae8c0594628.jpg) | |
| Goner | ![#0000EE](https://placehold.co/15x15/0000EE/0000EE.png) | <span style="color:blue">Blue</span> | \033B | ![Goner Ozias](https://user-images.githubusercontent.com/15099626/228245381-bb185b8e-5e67-4299-8dae-9356240c4b18.jpg) | |
| Independant | ![#00FFFF](https://placehold.co/15x15/00FFFF/00FFFF.png) | <span style="color:cyan">Cyan</span> | \033C | ![Privateer Trading Post](https://user-images.githubusercontent.com/15099626/228241313-b8c904cc-9545-490c-b61b-e3cb9938924d.jpg) | Currently the XRM Privateer Trading Post and Strong Arms Weapons Dealer are the only "independant" race objects coloured. |
| ATF | ![#C0C0C0](https://placehold.co/15x15/FFFFFF/FFFFFF.png) | <span style="color:white">White</span> | \033W | ![ATF Escort Vali](https://user-images.githubusercontent.com/15099626/228246213-a201eb2d-3abb-48aa-8036-e87be42552cd.jpg) | |
| Terran | ![#C0C0C0](https://placehold.co/15x15/FFFFFF/FFFFFF.png) | <span style="color:white">White</span> | \033W | ![placeholder](https://user-images.githubusercontent.com/15099626/228250530-bf52200c-96e5-4a25-8163-967b99094c29.png)![Orbital Defence Station](https://user-images.githubusercontent.com/15099626/228242917-37940eb2-6438-48f5-b064-9a02bcbdaa84.jpg)![placeholder](https://user-images.githubusercontent.com/15099626/228250530-bf52200c-96e5-4a25-8163-967b99094c29.png) | A rare example of an object where the entire name is coloured. Some stuff just looks weird partially coloured or prepended with a race name. |
| Yaki | ![#FF0000](https://placehold.co/15x15/FF0000/FF0000.png) | <span style="color:red">Red</span> | \033R | ![Yaki Assassin Fujin Raider](https://user-images.githubusercontent.com/15099626/228247485-7b2fc47e-e2ca-4996-a84e-36ef93cf2f60.jpg) | Example of an enemy ship. X3's standard red text colour for an enemy contrasts with the \033R highlight red colour. |

### Default Farnham's Legend Corporation Colours

In FL, corporations exist as their own races independant from their parent races. 

| **Race** | - | **Colour** | **Code** | **Image Example** | **Note**  |
|:--- |:--- |:--- |:--- |:--- |:--- |
| OTAS | ![#0000EE](https://placehold.co/15x15/0000EE/0000EE.png) | <span style="color:blue">Blue</span> | \033B | ![OTAS Shipyard](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/ad7e13cb-a252-4093-9b8f-ef49d001433a) | | 
| Terracorp | ![#0000EE](https://placehold.co/15x15/0000EE/0000EE.png) | <span style="color:blue">Blue</span> | \033B | ![Terracorp Military Titan](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/84c880ea-ce56-4a4e-80ff-2e5375d44872) | |
| Atreus | ![#008000](https://placehold.co/15x15/008000/008000.png) | <span style="color:green">Green</span> | \033G | ![Atreus Police Enhanced Mako](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/6dbac025-51f3-4747-b5b4-6271f917d71d) | |
| NMMC | ![#FFFF00](https://placehold.co/15x15/FFFF00/FFFF00.png) | <span style="color:yellow">Yellow</span> | \033Y | ![NMMC Mineral Transporter](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/9418d5d8-7d6e-4032-9ddb-1e8fed8a4ea1) | |
| Strong Arms | ![#FF00FF](https://placehold.co/15x15/FF00FF/FF00FF.png) | <span style="color:magenta">Magenta</span> | \033M | ![Strong Arms HQ](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/b66ab864-8dd7-4fb6-902c-239e59b55edd) | |
| Beryll | ![#0000EE](https://placehold.co/15x15/0000EE/0000EE.png) | <span style="color:blue">Blue</span> | \033B | - | Beryll is not yet implemented in Farnham's Legend. | 
| Duke's | ![#FF0000](https://placehold.co/15x15/FF0000/FF0000.png) | <span style="color:red">Red</span> | \033R | ![Duke's Military Transport](https://github.com/jamesjonesphoenix/X3-Colour-By-Race/assets/15099626/ec7396d0-345a-4b26-8796-c9ab879f28a8) | |
| Darkspace | ![#C0C0C0](https://placehold.co/15x15/FFFFFF/FFFFFF.png) | <span style="color:white">White</span> | \033W | ![ATF Escort Vali](https://user-images.githubusercontent.com/15099626/228246213-a201eb2d-3abb-48aa-8036-e87be42552cd.jpg) | |
| Industritech | ![#FFA500](https://placehold.co/15x15/FFA500/FFA500.png) | <span style="color:orange">Orange</span> | \033O | - | Industritech is a Paranid corporation not yet implemented in Farnham's Legend. |

## What is coloured and what isn't

* Objects that are coloured:
    * Most ships.
    * Fighter Drones.
    * Stations:
        * Shipyards.
        * Docks including Equipment Docks, Trading Docks and Stock Exchanges.
        * Corporate HQs.
        * XRM Weapons Dealers.
    * Sector Names.
* Objects that are not coloured:
    * Any player property is untouched.
    * Factories.
    * Most freight drones unless they have a race name.
    * Jump beacons.
    * Xenon or Kha'ak (by default - you can change this). I saw little value in colouring ships which are always hostile.

## How It Works

When the plugin is activated, it goes through all the ships and stations in the universe and adds colours to their names. This process is repeated every time you load a saved game.

When renaming an individual object, the plugin checks its name against an array of strings. If one of these strings is detected, that part of the name is colored. For example, for Argon ships, the plugin checks for the following strings: "Argon", "A.", "OTAS", "Terracorp", "Jonferco", "Plutarch", "Beryll," and "Privateer". Once an object is coloured the plugin sets a local variable to prevent it from being recoloured and to allow it to be reset if necessary.

After activation, the plugin must detect new objects so their names can be coloured. In Farnham's Legend the plugin uses `[SIGNAL_CREATED]` signal to detect new ships & stations. This approach is much more performance-friendly than manually checking the universe for new ships regularly.

Once a new object is detected it is coloured once, then after about half a second it is coloured again and after a longer wait of about 15 seconds it is coloured a third time. This is to ensure that a colouring script runs after any creation scripts that might overwrite the name of the object. This is particularly an issue with mods such as [Military Base Response Revamp](https://forum.egosoft.com/viewtopic.php?t=254599) and [Pirate Guild 3](https://forum.egosoft.com/viewtopic.php?t=244949).

### Albion Prelude & Terran Conflict

`[SIGNAL_CREATED]` is not available in Albion Prelude and Terran Conflict so we use `[SIGNAL_CHANGESECTOR]` instead. This signal does trigger for many objects as soon as they are created but it has a few significant shortcomings. 

* `[SIGNAL_CHANGESECTOR]` triggers every time a ship goes through a gate.  
* Stations do not trigger `[SIGNAL_CHANGESECTOR]` or any other signal upon creation. 
* Ships that spawn in docking bays of carriers or stations do not trigger `[SIGNAL_CHANGESECTOR]` until they leave the dock.

To mitigate these issues, the plugin takes the following steps:

* We avoid going through the colour process each time a ship triggers `[SIGNAL_CHANGESECTOR]` by checking the local variable assigned to the ship but even this quick check leads to some wasted CPU cycles.
* Checks the universe once every 30 minutes for new unnamed stations and dockable ships. Although not ideal, this approach does not waste a significant amount of CPU.
* Does the same check when the player changes sector.
* When `[SIGNAL_CHANGESECTOR]` triggers for a lasertower, checks if it has a homebase to colour. This is because lasertowers are often spawned to guard stations, so if a lasertower is respawning there's a reasonable chance that the homebase it was guarding has also recently respawned.

The limitations of AP and TC mean you'll occasionally see an uncoloured ship or station, but the additional checks performed by the plugin should make this a rare occasion.

## Compatibility

* Terran Conflict - Yes.
* Albion Prelude - Yes.
* Farnham's Legend - Yes.
* X3 Reunion - No.
* [XRM](https://forum.egosoft.com/viewtopic.php?f=94&t=304158) - Yes, I originally developed this while playing on an LxXRM installation. The plugin includes code to handle several XRM specific objects. 
* Litcube's universe - I've never played it, so I'm not sure. Try it and let me know!
* [Military Base Response Revamp](https://forum.egosoft.com/viewtopic.php?t=254599) - Yes, especially if you overwrite MBBR's ship naming script with the included optional script. 
* [Pirate Guild](https://forum.egosoft.com/viewtopic.php?t=244949) - Yes, though station names will be overwritten so I strongly advise the optional included translation files. 

## Ancillary Stuff

### Languages

* English (my native language)
* German (checked by Olsch)
* French
* Spanish
* Italian
* Czech 
* Polish

### Why an X3 mod in 2023?

Because I'm an idiot.

### Thanks

* Thanks Egosoft for making a great game.
* Thanks Cycrow who saw my proof of concept and wrote me a primer on global signals in X3.
* Thanks Olsch for improving my dodgy German translation.

## Changelog
#### 2.0.0

* Added dynamic colouring of sector names available only in FL. 
    * Sector colouring is activated as a separate AL plugin so you can use it standalone or alongside colouring ships & stations. 
	* Sector colours are editable in the 9964 t file set as a red, green and yellow value to be combined into an RGB colour. By default these RGB colours are identical to the colours used for ship & station names.
	* Border sectors can be set to use different colours to core sectors. By default they are the same. You can set the border sector colours for individual races manually or set a general % value to lighten/darken the core sector colour.
	* Colour By Race in FL now requires the unofficial patch by Cycrow as sector colouring requires some of the new scripting functions. 
* Rewrote plugin to start a task on new ships and station for rechecking their names instead of adding them to a global array to be checked on a timer. More elegant and more efficient on CPU and less likely to show uncoloured objects while waiting on 180 second timer.
* Changed to use SIGNAL_CREATED instead of SIGNAL_CHANGESECTOR to detect new ships for colouring in FL. SIGNAL_CREATED is called once per ship only, meaning reduced CPU load. 
* Improved reset functionality.
	* Added check on game load to see if settings are changed from the last session due to a change in the t file. If a change is detected, the plugin will inform the player and reset and recolour all ships, stations and/or sectors to match the new settings. This way the player can change settings without needing to deactivate and reactivate the plugin - though this method is still possible.
	* The reset and recolouring is run in parallel for a seamless transition from the user's point of view - user won't see the entire universe uncoloured for a few minutes.
	* If a version update is detected, the plugin will inform the user of the update and reset and recolour ships, stations and/or sectors.
	* Old data from a previous game session is now stored to be used for any reset deemed necessary on session start. It's then deleted. 
    * Pirate Guild 3 Mob Bosses and special XRM stations such as "Farpoint Station" are now reset properly.
* Added script to check for short prepend on objects with short names and replace with the long prepend. This is run once on version upgrade. This was a mistake introduced to a couple of objects in earlier version of plugin. Only seen it in German translation so is fairly rare. 	
* More informational messages. Short messages now appear as a game tip in FL and AP.
* Changed Terran colour from "silver" to white as I can see it better. If you prefer to revert to silver, you can edit settings in the 9964 t file.
* t file improvements. 
	* Separated True Relations & Colour By Race into separate t files. 9964 is the main t file. 9965 now only contains hard coded coloured names of stations and is not used by FL as we can immediately detect creation of stations with SIGNAL_CREATED.
	* Added more documentation comments to the t file to explain editable settings. 
	* Moved some hardcoded settings into t file so they can be edited.
		* XRM command ship job IDs and relevant sector string IDs.
		* References to object names to be prepended with race name.
	* Replaced "Pirate Ship" entry at id="3771" with original uncoloured string.
	* Added some strings to German t file to ensure an entire word is coloured in stations. For example "Piratenhafen" was only getting "Piraten" coloured which looked odd.
* Added check to see if plugin is running processes. This stops the plugin from running two intensive processes at the same time and prevents breakage from conflicting processes. For example deactivating while init process is running would break things and vice versa.
* Added handling of OWNER_CHANGED signal to rename a ship when its owner changes. 	
* Improved debugging logging 
    * Added dedicated script for enabling debugging - plugin.jj.colour.by.race.set.debug.
	* Debug now set to text number (9964) rather than boolean true. 
* A bunch of refactoring including some functions from jj.colour.by.race to jj.lib.

##### 1.3.1
* Prevented search substrings from being deleted when processing a plugin update. This bug prevented the galaxy from being reset so objects could be recoloured from a "blank slate".

#### 1.3

* Improved plugin deactivation. Plugin will now remove the colour from the coloured part of the name of all ships and stations in the galaxy and remove all local vars and global vars. It will be as if Colour By Race was never installed.  
* Setup [SIGNAL_CREATED] for stations in FL. In FL stations will now be coloured as soon as they appear in the universe.
* Improved detection of FL. The plugin would fail to detect FL if X3 was running unofficial patch version 1.3.6 and later. Amongst other things, this would leave corporation ships uncoloured.
* Changed prepending of ships without a race substring to colour. Previously the plugin queried a list of approved jobs to prepend with a race name. This was cumbersome, it's quicker to query jobs which shouldn't be prepended with a race name. Currently the only job we make sure not to prepend is the UFO Unknown Ship job 8660 and any drones.
* Setup a feature where a set of station-only search substrings will be searched before any others. For example I added "Boronen" to this set for the German translation which will be searched and coloured before "Boron". These strings are set with IDs from x50 to x60 where x is the race ID. So for example strings 450 to 460 for the Paranid.
* Fixed some t file typos
* German translation:
  * Added "Militärischer" to German translation substrings and made sure it gets coloured before Militär.
  * Added "Herzogs" as a substring to search for Duke's 
* Added descriptions to all script files.

##### 1.2.2

* Added German translation - thanks to Olsch for checking and improving my initial attempt. 
* Added ability to add strings to t file to check for stations only, but checked before other strings - needed for German translation which has masculine and feminine noun modifiers.
* Made a dubious attempt at other French, Spanish, Italian, Czech and Polish translations. I took these translations straight from Google translate. 

##### 1.2.1    

* Forgot to version up event file to 1.2

#### 1.2

* Now compatibile with Terran Conflict.
  * Wrote alternate code for command `get race id for race`. This was the only plugin code which TC couldn't handle.
* Deleted extraneous files player.xml and init.xml
* Lasertower activation timer fix now called on lasertower change sector signal
* Now only check XRM stations if XRM is activated - was renaming McCallum station but couldn't find string. 

#### 1.1

* Now compatibile with Farnham's Legend.
  * Added FL corporations as races to search for. Includes conditional script which checks which engine version.
  * Added prepending of ship & station names with race name if none found for certain jobs. Uses shortened name if name length already quite long.
* Fixed bug where lasertower activation timer would be saved into the name.
* Added/Fixed search strings to be coloured:
  * FL - corps, The Marauder, Nikkonofune
  * Terraformers, Exterminator, ATF Orbital Defence Station
  * fixed Beryll string
* Added script to remove the local variable on all ships and stations. This is used when updating the plugin so we can re-check the galaxy and when the plugin is deactivated.

#### 1.0

* Initial Release

