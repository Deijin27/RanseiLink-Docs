---
icon: lucide/map-pinned
---

# Roadmap

## RanseiLink 7.1

There are many new findings to be incorporated thaks to progress made decompiling game-code. RanseiLink 7.1 will allow you to edit every property of the different data files stored in RomFS, with near 100% coverage, including things where we don't know what they do yet. This includes, but is not limited to:

- Scenario Army: A newly understood data type, including Army Leader, Money, and more.
- Gimmick and Gimmick Object: Many unknown properties
- Map Point: A newly understood data type, that seems to refer to initialisation of the transient state of battle-map cells.
- The exact Link-to-Exp formula used by the game.
- Various other little things, and recalibrations of understanding. Final release notes will clearly detail every little change.

## RanseiLink 7.2

With the intention of getting features into users hands asap for testing, current working idea is to handmake a bespoke patch that increases the number of pokemon you can add to your mods. There are a couple of challenges: many places that refer to the pokemon count need to be updated separately due to macro use, and scenario-pokemon needs to accommodate a number larger than 8 bits for the pokemon id. But I do think this is feasable to get done fairly quickly, and is a highly requested feature.

However, what might change these plans is if the code that specifies the team of the final battle, or monferno in viperia, is located. In order to modify these, the code must be unpacked and patched on the fly since the data to be input will be user-controlled. While it is the long-term plan to do this, it would be quicker to get a bespoke patch created.

## RanseiLink 7.X

Other highly requested features are also planned, but not yet prioritised:

- Figuring out how the event system works. This could be huge, allowing people to craft fully custom cutscenes and stories.
- Support for adding extra pokemon types (i.e. Fairy Type). Challenges with this are updating defaults and counts, and accounting for interaction with terrain.