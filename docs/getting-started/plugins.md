# Plugins Explained 

RanseiLink supports plugins. This page explains each of the ones written by Deijin. Currently the latest versions of these are included with a ranseilink release as of the date of release. But these plugins are updated independently, thus you can be sure you have the latest ones from here: https://drive.google.com/drive/folders/1LQDr4OF5MiOdRu1AFNIN9P7eaCQLHSA_?usp=sharing

## Changelist Plugin

Provide this plugin with an unchanged mod, and your mod. This runs a check over most things and generates a list of things your mod has changed. This is useful to look through to remember everything you changed, and spot any unintentional changes. 

The output is either XML or TSV. XML is easy to read if you open it in an editor with syntax highlighting, notepad++ for example. And TSV is a spreadsheet format; it can be opened in a spreadsheet editor such as google sheets.

<details>
<summary>Changelog</summary>

**Version 2.4**

- Changelist of Gimmick Range
- Changelist for Move Range
- Changelist for Scenario Building

**Version 2.3**

- Compatibility update for RanseiLink 5.1  

**Version 2.2**
- Fix broken changelist generation due to certain names now containing spaces.
- Fix changelist generator incrementing id in wrong place, causing it to not work

**Version 2.1**

- Compatibility update for RanseiLink-4.1
- Changelist for episodes

**Version 2.0**

- Change name to from “Text Changelist Plugin” to “Changelist Plugin”
- Support changelists in many types

**Version 1.1**

- Safely handle when different number of messages in a block

**Version 1.0**

- Initial creation

</details>

## Disable Events Plugin

Pokémon Conquest's story runs on an event system. These events are defined in two files in the game's data. 

When you rename/delete these files, the game cannot find them so loads in a kind of sandbox state, where you are put directly onto the overworld map.

This sandbox state is useful for testing since you can challenge ignis, in whatever battle config you assign to ignis, immediately without watching any cutscenes or tutorials.

The people over at the Ransei Region Discord have also made use of this for competitive battling. They edit the pokemon, teams, and maps, then run an action replay code that gives you control over the opposing team.

<details>
<summary>Changelog</summary>

**Version 1.2**

- Fix the completion message being wrong

**Version 1.1**

- Compatibility update with RanseiLink 5.1

**Version 1.0**

- Initial creation

</details>

## Mass Action Plugin

This has a few things where you often want to set a lot of values to the same thing at once.
- Set all max-links at once
- Set all warrior capacities at once
- Set all IVs at once
- Set all scenario pokemon initial links at once (optionionally for a specific scenario)

<details>
<summary>Changelog</summary>

**Version 2.1**

- Compatibility update for RanseiLink-4.1

**Version 2.0**

- Compatibility update for RanseiLink-4.0

**Version 1.1**

- Warrior Capacity

**Version 1.0**

- Initial creation
- Max link
- IVs
- "At least" and "exact" options

</details>

## Partial Transfer Plugin

This allows you to transfer specific parts of a mod to another easily. For example, you may want to copy only changes to text from one mod to another.

There is the option of whether to transfer names. If unchecked, the names of pokemon, moves, items etc. will be preserved in the rom you are transferring to, but all other data will be transferred from the source mod.

<details>
<summary>Changelog</summary>


**Version 3.2**

- Transfer Banner
- Transfer Gimmick Range
- Transfer Scenario Building
- Scenario Warrior / Pokemon / Kingdom Merged as one

**Version 3.1**

- Compatibility update for RanseiLink 5.1

**Version 3.0**

- Option to not transfer names
- Block transferring invalid data between mods of different game codes

**Version 2.1**

- Compatibility update for RanseiLink-4.1
- Transfer Episode data

**Version 2.0**

- Compatibility update for RanseiLink-4.0
- Transfer new files used in mods including sprites, maps, battle configs, gimmicks, kingdoms

**Version 1.0**

- Initial creation
- Transfer all RanseiLink 3.0 supported files between mods

</details>

## Randomizer Plugin

This randomizes a mod. There is a guide for how to use it [here](https://github.com/Deijin27/RanseiLink/wiki/Randomizer-Guide). It's easy to cause early game softlocks when randomizing pokemon conquest, so this has lots of checks in place to try to prevent all that we know of.

You can currently randomize:
- Warrior's Pokemon
- Pokemon's Abilities
- Pokemon's Types
- Pokemon's Moves
- Move animations
- Warrior Skills
- Warriors
- Battle Maps
- Battle Background Colors
- Pokemon's Stats

<details>
<summary>Changelog</summary>

**Version 3.1**

- Fix potential infinite loop

**Version 3.0**

- Randomise pokemon’s stats
- Randomise Warrior skills
- Randomise Battle maps
- Randomise battle background colours

**Version 2.1**

- Compatibility update for RanseiLink-4.1

**Version 2.0**

- Compatibility update for RanseiLink-4.0
- Make randomised type not put NoType for Type1

**Version 1.7**

- Separate “Avoid Dummies” option into moves and abilities

**Version 1.6**

- Remove accuracy checks that are unnecessary because moves never miss during the tutorial
- Add check to make sure oichi doesn’t take out koroku (causes a bugged ‘back’ button)
- Add movement range checks for other tutorial pokemon (the base game has no <2 range pokemon, so this shouldn’t matter, but just in case someone randomises an edit)

**Version 1.5**  

- Fix certain things (e.g. ability id filtering) lingering between runs of the randomizer because properties of the randomizer class itself were used to store these. Fix moves all code into a separate randomizer class that is created and used in the plugin, making it safe to use properties where necessary.

**Version 1.4**  

- Stop softlock-causing animation from being picked
- Stop NoAbility from being picked when choosing an ability when scenario pokemon are randomised but abilities aren’t

**Version 1.3**  

- Fix bug of max link raising not applying
- Randomise what warriors are assigned to scenario warrior slots
- Randomise move animations

**Version 1.2**  

- Fix softlock minimization only applying if move randomization is selected
- Improvements to softlock minimization

**Version 1.1**  

- Softlock minimization

**Version 1.0**  

- Initial port of randomizer code into plugin

</details>

## Softlock Checker Plugin

This takes your mod and generates a report of known softlock causes it finds, plus a bit more useful information. Examples of things it will spot:
- Inability to complete tutorial
- Move animations that softlocks
- Scenario pokemon with abilities that dont match their 3 possibilities, which cases a softlock in mystery springs.
- Max link of 0 between an warrior and their starter scenario pokemon

<details>
<summary>Changelog</summary>

**Version 2.3**  

- Compatibility update for RanseiLink 5.1

**Version 2.2**  

- Add check for if a warrior has 0% max link with their scenario pokemon. This isn’t technically a softlock, but it’s still useful information for spotting mistakes.

**Version 2.1**  

- Compatibility update for RanseiLink-4.1

**Version 2.0**  

- Compatibility update for RanseiLink-4.0
- Fix WaitForInputIdle not working after windows11 notepad update which was leading to the temporary file being deleted before being opened

**Version 1.1**  

- Remove accuracy checks that are unnecessary because moves never miss during the tutorial
- Add check to make sure oichi doesn’t take out koroku (causes a bugged ‘back’ button)
- Add movement range checks for other tutorial pokemon than player

**Version 1.0**  

- Initial creation
- Checks
  - Tutorial can be completed
  - Scenario pokemon have an ability that is one of the pokemon’s abilities
  - Move animations are not causing softlocks

</details>

## Sprite Sheet Splitter

This is a tool to split a pokemon sprite sheet into it's constituent sprites. May be useful for some depending on how you design your custom pokemon sprites. You can learn about sprite editing with ranseilink [here](../guides/image-editing/image-types.md).

<details>
<summary>Changelog</summary>

**Version 1.2**  

- Compatibility update for RanseiLink 5.1

**Version 1.1**  

- Compatibility update for RanseiLink-4.1

**Version 1.0**  

- Initial creation released at the same time as RanseiLink-4.0

</details>


