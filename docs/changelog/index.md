# Changelog

## 6.1 <small>- Dec 13, 2024</small> { id="6.1" }

**Features**

- Map Editor Improvements
    - Support drag when editing so you can paint multiple cells in one mouse press and drag
    - New map view modes for Bounds and Orientation. Note, it's currently unknown what the difference is between the orientation stored in cells, and the orientation stored in gimmick and pokemon entries.
    - Reworked painting functionality, it now paints if you have the Painter tab selected. The painter tab shows a different palette dependent on what map view mode you have selected. Elevation palette is saved to user settings.
    - Realised that previous interpretation of pokemon data was wrong, now it's displayed correctly, with each pokemon having more data than just position.
- Move Workspace: Similar to the pokemon and warrior workspaces, moves are displayed in a list where items have a preview of the range of the move, and it's type, power, and name.
- Gimmick Data: Discovered some things such as where the attack power is stored. This is still very much in-progress.

**Fixes**

- Fix issue where mods would be left in a broken state where they crashed whenever opened if pokemon evolutions were modified in 6.0. Those mods will no longer crash, but the evolutions of pokemon will be messed up, you will need to manually go through and fix the evolutions, sorry about this.

## 6.0 <small>- Oct 26, 2024</small> { id="6.0" }

**Mod Features**

- Support for editing Animations ([Guide](https://github.com/Deijin27/RanseiLink/wiki/Cell-Animation-Editing-Guide))
    - Kingdom top-screen backgrounds
    - Kingdom bottom-screen backgrounds
    - Kingdom map icons
    - Building medium-size icons 
- Support for new still image types:
    - Building Small Icons
    - Battle Minimaps
    - Kingdom top-screen background (still version of the animation)

**Tool Enhancements**

- Re-added the copy-paste functionality for things such as Pokemon and Moves #59
- Mods now support tags, and you can filter the mod list based on these tags
- You can now pin mods to the top of the mod list
- Newly added mods are temporarily sorted the top of the mod list on creation
- Max link now has indicators if they are above the bronze silver and gold thresholds #34
- Max link has a "quick set" functionality which allows you to choose what number buttons you want to have to conveniently set many link values consecutively #36. Scenario pokemon ivs and link also support this functionality.
- The concept of "Overwritten" is now indicated by green checkmarks throughout the tool. So whenever you replace, for example, an animation, a green checkmark appears next to it indicating it's been modified.
- New "Building Workspace" where you can edit building and scenario info in one place, with buildings grouped by kingdom
- New "Pokemon Workspace". Pokemon are displayed in a list with pictures and you can filter the list by name and type.
- New "Warrior Workspace". Base warriors are displayed in a list with pictures and you canfilter the list by name and speciality
- Bug Report Button that autofills some of the information on the github issue form

**Bug Fixes**

- Fix crash that sometimes occurred when restoring window dimensions #62
- Fix text in button not changing color when disabled
- Fix minor unoptimisation on warrior name table filtering
- Added safety measures to make corrupted files less likely e.g. when saving messages they are saved to a temporary file first, then copied to the destination
- Name max lengths take culture into account

## 5.5 <small>- May 27, 2023</small> { id="5.5" }

**Mod Features**

- Edit pokemon [BattleIntroSpriteOffset](https://github.com/Deijin27/RanseiLink/wiki/Pokemon-Battle-Intro-Sprite-Offset)
- Battle Config minimap (plan to allow you to edit these minimaps to match custom maps) #35

**Tool Enhancements**

- Renamed pokemon and warrior graphics types to more sensible names "Small, Medium, Large, XLarge"
- 3D Map Viewer: You can view maps from either the map page, or the battle config page (on the battle config page, you can see the background colors too). Just supports viewing the map atm, it's not planned to support editing the 3D geometry, but it is planned to support editing the elevation, and moving around gimmicks in this 3D view. [Project](https://github.com/users/Deijin27/projects/2)
- On ability, move, and skill pages view the warrior / pokemon that get them in a list. #44
- Save and restore window dimensions, position, and state

**Bug Fixes**

- Fix crash modifying map dimensions
- Map Importer: 
    - Prevent infinite loop when material names are tool long
    - Automatically remove the prefixes maya adds

## 5.4 <small>- Mar 9, 2023</small> { id="5.4" }

**Mod Features**

- Edit wandering merchant item #21

**Tool Enhancements**

- Scenario Warrior Workspace: Scenario Warrior, Pokemon, and Kingdom in one streamlined view #23
- Mod selection screen is more compact and displays banner images
- Nice progress bar style
- Max link sorting by name and link #29
- Max link inverse page where you view warriors for a pokemon #29
- Max link displays images of pokemon/warriors #29
- Users are prompted to populate graphics defaults on tool launch if they haven't yet #30
- Main editor is overall more compact

**Bug Fixes**

- Fixed patch sprites setting not persisting #19
- Fixed episode name length being capped #25
- Partial transfer plugin, and others are fixed based on a rework of how plugin completion is handled #24

**Technical Background Changes**

- Normalized results to use FluentResults library
- Update RanseiLink.Core to .NET6 to accomodate ImageSharp 3.0.0

## 5.3 <small>- Dec 11, 2022</small> { id="5.3" }

- Fix crash on scenario warrior page
- Add a different way of specifying exact links, supporting every integer 0-100
- Label "Hit 5 times" move effect correctly
- Support editing scenario building information

## 5.2 <small>- Nov 17, 2022</small> { id="5.2" }

**Bug Fixes**

- Fix issue with map editor changes being applied to other mods opened due to improper disposal
- Fix crash when attempting to move pokemon/gimmicks outside of map area
- Fix gimmicks not being visually removed from map when deleted
- Fix map selected pokemon position not changing when clicking a new cell

**Features**

- Some useful buttons to set exp to a value that gives an exact link that has been tested to be exact in-game.

## 5.1 <small>- Nov 13, 2022</small> { id="5.1" }

- Compatibility with European rom VPYP. RanseiLink considers this cross-compatible with the North American VPYT, since there is only minor text differences.
- Text filters are now insensitive to accents. e.g. if you search No, it matches Nō
- Fixed that the window was cropped a little when full screen
- Basic support to adding and removing messages from the groups that have a message per speaker_id
- Fix map models were able to be patched without having populated graphics defaults, which caused crash
- Changes that are hopefully inconsequential to users: 
  - We have changed IOC to one that is faster, maybe not noticable, but it stacks up as the app grows
  - We are using an MVVM dialog api. This is a step towards complete separation of view and viewmodel, which would make moving to a different (Cross Platform) ui framework much easier.

## 5.0 <small>- Sep 11, 2022</small> { id="5.0" }

**Changes To Installation**

Now there is no longer a need for an installation guide. RanseiLink is published as [self-contained](https://docs.microsoft.com/en-us/dotnet/core/deploying/#publish-self-contained). This means the application is a lot bigger, but you no longer need to worry about installing .NET, as the necessary framework is bundled with the app. Just unzip and run.

**What's New**

- Extract battle map 3D models to OBJ, edit them, then re-import into the game. You can create fully custom maps. See the [Map Editing Guide](https://github.com/Deijin27/RanseiLink/wiki/Map-Editing-Guide) to learn more. (Big thanks for [Scurest](https://github.com/scurest), their documentation on NSBMDs helped a lot to getting this working)
- The elevation at which pokemon and gimmick sprites are placed on a map can now be edited to match your custom 3D model
- Disable pokemon and gimmick markers on the PSLM view, making it easier to see when editing elevation
- Pokemon sprite sheets also come with animations. These can now be edited. See the [updated guide](https://github.com/Deijin27/RanseiLink/wiki/Image-Editing-Guide#pokemon-battle-models), and an [tool to help you preview you sprites and animations](https://github.com/Deijin27/pkmdl-previewer). Also be sure to check out [Snap's Guide](https://github.com/Deijin27/RanseiLink/wiki/Pokemon-Battle-Sprite-Creation-Process) for creating pokemon sprites in the conquest style.
- Navigate to messages by warrior by clicking on the link next "Speaker ID" on the base warrior page "tactics tactics tactics"
- Renamed some text parameters in messages to make more sense.
- Omitted constant bits in text parameter values, (where you saw 48, 49, 50, now you will see 0, 1, 2.)
- In text search, include all 3 members of multi-start. messages.

## 4.9 <small>- Jul 26, 2022</small> { id="4.9" }

- Fix bug with image patching
- Fix "append new" not blocked in "Title" where it isn't possible
- Forward and backward navigation for page selection. Only for the which main tab is selected atm.
- List number of overrides on sprite pages
- Overriden sprites have purple number
- View and edit warrior and pokemon sprites on the warrior and pokemon pages

## 4.8 <small>- Jul 23, 2022</small> { id="4.8" }

- Compatibility with japanese rom
- Text and ScenarioWarrior DataGrids now remember scroll position
- Number boxes now allow you to type over selected text

**Important Notes**

VPYT = English rom, VPYJ = Japanese rom. Mods are not cross compatible atm, but you can use the [partial transfer plugin](https://github.com/Deijin27/RanseiLink/wiki/Plugins-by-Deijin#partial-transfer-plugin) to move most data across to a mod of the other game code.

You will need to run "populate graphics defaults" again because they are now stored per-gamecode. This is to allow japanese rom defaults to be accurate.

If you have no intention to use an older version of ranseilink again, you can delete the folder `%localappdata%\RanseiLink\DataProvider`. This is worth doing at some point as it will save you 120MB of storage space.

## 4.7 <small>- Jun 22, 2022</small> { id="4.7" }

- Significantly more accurate exp-to-link formula

## 4.6 <small>- Jun 20, 2022</small> { id="4.6" }

- Scenario pokemon only have their possible abilities listed

## 4.5 <small>- Jun 19, 2022</small> { id="4.5" }

**Bug Fixes**

- Fix gimmick max id incorrect which made many gimmicks not editable and map editor crashes
- Banner image of incorrect size is now correctly rejected

**New Editables**

- Move: Movement/Knockback (fully reproduce behaviour of flame wheel / volt switch / aqua tail / fiery dance etc.), plus a couple of values not sure what they do yet
- Building: Referenced buildings. Not sure what they do yet

## 4.4 <small>- May 29, 2022</small> { id="4.4" }

**Bug Fixes**

- Safely create new settings file if file is corrupt
- Fix image simplifier sometimes being one color over because the quantizer changed the transparency to a different color. Transparency is now preserved and the palette is simplified to the correct amount.
- Validation on text editing

**New Editables**

- Pokemon: Catch rate
- Scenario warrior: Item
- Move: Lv5 effects, additional animation
- Battle config: treasure items
- Banner (the title and image shown on the DS menu) (make a new mod to extract the default image)
- Title screen images (requires you to run "Populate Graphics Defaults" again)

## 4.3 <small>- Apr 25, 2022</small> { id="" }

- Bug fix: Fix pokemon evolution conditions breaking, and similar thing in warrior rank-up condition
- Grid editor for scenario pokemon
- Experimental editables for pokemon sprite values. Only use if you know what you're doing.

## 4.2 <small>- Apr 25, 2022</small> { id="" }

**Bug Fixes**

- Fix navigate to invalid ids causing crash
- Fix text changes not being saved
- Fix max link not visually updating when switching pages
- Fix item names in child selector of scenarioselectors not updating when switching scenario
- Fix some incorrently labelled item effect values
- Fix scenariopokemon changes done in scenariowarrior page not saving
- Safely ignore wpf bug where moduleid is occasionally set to null for no reason

**New Editables**

- Episode: Initial kingoms, unlocked kingdoms, clear condition

## 4.1 <small>- Apr 23, 2022</small> { id="" }

- Map editing bug fixes
  - Fix gimmick in cell not updating visually when changed
  - Fix gimmick parameters not getting set
- Ease of use changes
  - Comboboxes are filled in with user assigned names
  - Editing grids removed atm because of above change making them far more difficult
  - Improved edit interface for pokemon habitat values
  - View army summary by clicking on kingdom name in ScenarioKingdom page
- New Editables
  - **Episodes**: Scenario, Unlock condition, Difficulty, Convenient editing of name and description
  - **Item**: Crafting recipe, Category, Effect and duration, Required building level
  - **Pokemon**: Easy editing of pokemon evolutions, with unlimited adding and removing evolutions supported

## 4.0 <small>- Mar 2, 2022</small> { id="" }

- **Battle Maps**: pokemon start positions, gimmicks, terrain type

- **Battle configs**: which map, victory requirements, background colors, number of turns

- **Building**: battle config, sprite, function

- **Items**: where they can be purchased, quantity for effect

- **Gimmick ranges** can be modified the same way move ranges can

- **Scenario pokemon**: initial link

- **Scenario Warrior**: up to 8 pokemon on a warrior from the start

- **Pokemon**: idle animation

- **Sprites**: Still images, Screen Backgrounds, Battle Sprites

[Image editing guide](https://github.com/Deijin27/RanseiLink/wiki/Image-Editing-Guide)

## 3.1 <small>- Dec 29, 2021</small> { id="" }

- Bug fixes
    - Fix crash on mod selection page when multiple plugins
    - Fix item description setting wrong data
    - Prevent editing descriptions of dummys without allocated descriptions slots (which was overriding unrelated text)
- Text editing improvements
    - Loading: accented latin characters, better variable names, faster loads, etc.
    - Additional ease of access item and ability descriptions
- Utility features
    - common iv buttons
    - search warrior names
    - jump from scenario pokemon to scenario warrior
    - change editor page tab order
- New editables
    - Kingdom (name, which battle map to use, overworld connections)
    - Gimmick (name, attack type, destroy type, animations)

## 3.0 <small>- Dec 19, 2021</small> { id="3.0" }

- Base Warriors (wisdom, speciality, rank up conditions etc)
- Warrior Names
- Per scenario appear pokemon (use in combination with toggles on pokemon page)
- Per scenario army kingdom assignment
- Scenario Warrior class, kingdom and army assignment
- Minimal editing of Items and Buildings
- Text editing (huge thanks to [pleonex](https://github.com/pleonex/PokemonConquest))
- Event speakers
- Move animation editing with previewer so you know what the animation looks like (thanks to [WhatAUsernameIHave](https://allmylinks.com/evoking789) and [Snap](https://allmylinks.com/snarp1969) for the help)
- Visual updates including dark theme and light theme
- Plugin support. And move randomizer code into a plugin.
- Ease of use changes including jump navigation and grids ([some useful tips for grids](https://github.com/Deijin27/RanseiLink/wiki/Tips-for-using-grids-in-RanseiLink))

**Upgrading Mods from Version 2.0**

Mods created in older versions of RanseiLink require upgrading to work with this version (text editing requires extra data from the rom).
Using the windows app you will see a button on the left which you should click to upgrade your mods. You will be prompted to provide it with an unchanged copy of the rom.
For the console application, use the command `dotnet RanseiLink.Console.dll upgrade mods "C:\Rom\Path.nds"`


## 2.0 <small>- Oct 3, 2021</small> { id="2.0" }

- Project management system
- Scenario Pokemon
- Scenario Warrior
- Evolution Table
- Quantity for evolution condition
- Pokemon movement range
- Max Link
- Randomization

**Porting v0.1.0 projects**

Here is a short guide of how to transfer stuff you've worked on in RanseiLink v0.1.0 to this version:
https://github.com/Deijin27/RanseiLink/wiki/Version-1-to-2-Project-Transfer-Guide


## 1.0 <small>- Sep 5, 2021</small> { id="1.0" }

Initial Release