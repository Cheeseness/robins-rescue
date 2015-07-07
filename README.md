# Robin's Rescue
Robin's Rescue is an example point and click adventure game made using the LGPL licenced [SLUDGE engine](http://opensludge.github.io/). This game was made over the course of several days and has a number of rough edges. Wear gloves when handling!

Big thanks to Mim for character designs and animations, and a special thank you to all my Patreon supporters (see SUPPORTERS.md for details).

In this file, you can find:

* Licence information for code, assets and third party assets
* Instructions for playing the game
* Instructions for compiling and/or running the game 
* Notes on how to navigate the game's codebase and resources
* Some helpful/related URLs

I hope you find something useful from playing Robin's Rescue and exploring its code!

- Cheese


## Licences
All source code within this repository is licenced under the [GNU Lesser General Public Licence 3.0](http://www.gnu.org/licenses/lgpl.txt), allowing you to use, share, and modify any or all parts of the codebase so long as they retain this licence and that you make source changes available to anybody you distribute modified versions to. See the file COPYING for the full licence. Yay!

Excluding the files noted below, v [Attribution 3.0 Unported](http://creativecommons.org/licenses/by/3.0/), copyright and created by Josh "Cheeseness" Bush and Miriam "Mimness" Roser. Under these terms, you are free to use, share, make derivatives from the assets in this repository (the items noted below are subject to their own licence requirements), so long as they include a link to the above licence, credit us and indicate any changes that were made. Yay!

### Third Party Sound Effects
The timing and volume of these samples has been modified to suit Robin's Rescue and they have been reencoded as OGG Vorbis audio.

* ["door hinge squeak creak o,c.aiff"](http://freesound.org/people/kyles/sounds/51805/) (doorOpen.ogg) kyles, licenced under Creative Commons: [Creative Commons 0](http://creativecommons.org/publicdomain/zero/1.0/)
* ["crash.wav"](http://freesound.org/people/sagetyrtle/sounds/40158/) (guardCrash.ogg) sagetyrtle, licenced under Creative Commons: [Creative Commons 0](http://creativecommons.org/publicdomain/zero/1.0/)
* ["KeyPickup.wav"](http://freesound.org/people/wildweasel/sounds/39026/) (pickUp.ogg) wildweasel, licensed under Creative Commons: [By Attribution 3.0](http://creativecommons.org/licenses/by/3.0/)
* ["bridge.wav"](http://www.freesound.org/people/Sergenious/sounds/55820/) (gate.ogg) Sergenious, licensed under Creative Commons: [By Attribution 3.0](http://creativecommons.org/licenses/by/3.0/)

### Third Party Music Tracks
These music tracks have been reencoded as OGG Vorbis audio.

* ["Thatched Villagers"](http://incompetech.com/music/royalty-free/index.html?isrc=USUAN1100720) Kevin MacLeod (incompetech.com), licensed under Creative Commons: [By Attribution 3.0](http://creativecommons.org/licenses/by/3.0/)
* ["Pippin the Hunchback"](http://incompetech.com/music/royalty-free/index.html?isrc=USUAN1400005) Kevin MacLeod (incompetech.com), licensed under Creative Commons: [By Attribution 3.0](http://creativecommons.org/licenses/by/3.0/)


### Third Party Fonts
This font has been rendered to a bitmap font and then converted to SLUDGE's DUC spritebank format.

* Medieval Sharp wmk69, licenced under [SIL Open Font Licence](http://scripts.sil.org/OFL) (see _sprite_sources/medieval_sharp_ for TTF, sources and licence)

## Play Instructions
Play as Maid Marian and rescue Robin from Sherrif Nottingham's castle.

* Left click to move and interact.
* Right click to open inventory.
* . (period) to skip dialogue.
* F to show floor region outlines (for debugging).
* B to show hotspot outlines (for debugging)


## Running The Game
If you are using one of the packaged versions of this game available from the [Robin's Rescue repository](https://github.com/Cheeseness/robins-rescue/releases), double check the following platform specific notes:

### Linux
If you want to run the game without the bundled libraries, be sure to set the SLUDGE_DATADIR environment variable to point to the bin/shaders folder. This environment variable is not a part of vanilla SLUDGE. A diff of source changes can be found in the _sludge_ folder.

If you'd rather run the game with your distro's SLUDGE packages or with a copy of the SLUDGE engine that you've compiled yourself, call the sludge-engine executable with data/robins_rescue.slg as its last argument and it should run swimmingly (ho ho ho).

### Windows
Double click SLUDGEEngine.exe, or drag and drop Gamedata.slg onto SLUDGEEngine.exe.


## Compiling The Game
If you have downloaded [the game's source](https://github.com/Cheeseness/robins-rescue) to compile yourself, you can open _robins_rescue.slu_ in the _SLUDGE Project Manager_ and select _Compile_ from the _Project_ menu to compile the game.

Once compiled, you can select _Run Game_ from the _Project_ menu to start the game.

## Understanding The Source Code
Robin's Rescue has very few code comments (this may change in the future!). Here are some notes to help you navigate the codebase and resources.

### Code Files

* _robins_rescue.slp_ is the SLUDGE project file for the game. It is generated by the _SLUDGE Project Manager_ application and contains details on files that are a part of the project, and game specific settings.
* _init.slu_ includes game initialisation, UI logic code and scene transition code.
* _functions.slu_ includes code for generic functions that aren't implementation specific.
* _inventory.slu_ includes inventory specific rendering and logic code.
* _audio.slu_ includes logic for switching and fading between music tracks as well as variables pointing to audio assets.
* _scenes.slu_ includes functions that represent scenes, containing scene specific configurations (loading backgrounds, floor regions, etc.) as well as hotspots for scene exits.
* _objects.slu_ includes _objectTypes_ that represent in-game objects (interactive and non-interactive). Each object includes a _getDefaultCostume()_ function for accessing a visual representation. objects may also include. _actionuse_ and _actionInventoryUse_ events for handling user interaction logic and addtional events getting inventory specific visual representations.
* _hotspots.slu_ includes _objectTypes_ that represent non-visual regions of interactivity (or regions which are represented by part of a background image). Each object includes an _actionUse_ and/or _actionUseInventory_ event for handling user interaction logic, and most include an _isComplete()_ function for determining whether the puzzle or task it represents is completed.

### Resources

* The _audio_ folder contains all audio (sound effects and music) assets in OGG format.
* The _backgrounds_ folder contains all background images in PNG format, as well as all floor region filed in SLUDGE's FLO format.
* The _sprites_ folder contains all compiled spritesheets in SLUDGE's DUC format.
* The _sprite_sources_ folder contains TGA sources for all sprites and sprite animations. These are not necessary to compile the game.
* The _sludge_ folder contains information on SLUDGE licencing and Linux specific engine code changes for creating portable builds.


## Helpful URLs
* [More information on Robin's Rescue](http://robinsrescue.twolofbees.com)
* [Robin's Rescue Source Code and Assets](https://github.com/Cheeseness/robins-rescue)
* [SLUDGE Documentation](https://opensludge.github.io/opensludge/doc/SLUDGE_Help.html)
* [More of Cheese and Mim's Artwork](http://twolofbees.com)
* [Support Cheese Making Games](http://patreon.com/cheeseness)
