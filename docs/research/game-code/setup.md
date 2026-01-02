

# Set up for reverse engineering code

I (deijin) am making rapid progress reverse-engineering the game code thanks to our large body of pre-existing knowledge on the data formats we've built up over the years. 

To get started, I followed this fantastic guide:

https://www.starcubelabs.com/reverse-engineering-ds/

Here are the high level steps with conquest-specific things I ran into:

1. Use DSLazy to unpack the rom
2. The pokemon conquest files are compressed using blz compression. Decompress arm9.bin and all the overlay files with the compression tool linked in the guide. (`blz.exe -d arm9.bin`)
3. Install the latest version of desmume (I had 9.0.9 originally, which doesn't have watchpoint functionality, so I updated to 0.9.11)
4. Install Ghidra (I had to install the [java sdk](https://www.oracle.com/java/technologies/downloads/#jdk25-windows) to get it working)
5. Set up ghidra project with arm9.bin. NOTE: The arm9.bin base address is 0x02004000, different to the one in the tutorial.

## Overlays

So far I've found that all of the relevant code is in arm9.bin, not the overlays. But regardless, I've yet to find a part of the game that 7 and 11 aren't loaded. 1 gets loaded and unloaded at different points.

Here are the offsets used by overlays, derived from information in `y9.bin`

```
// GROUP: Offset = 0x020F5860

overlay_0000.bin
overlay_0001.bin
overlay_0002.bin
overlay_0003.bin

// GROUP: Offset = 0x02160FA0

overlay_0004.bin
overlay_0005.bin

// GROUP: Offset = 0x02215BE0

overlay_0006.bin
overlay_0007.bin
overlay_0008.bin
overlay_0009.bin

// GROUP: Offset = 0x02227420

overlay_0010.bin
overlay_0011.bin
overlay_0012.bin
overlay_0013.bin
overlay_0014.bin
```

Loaded overlays at different points:

```
Player select screen: 7, 11

Intro conversation: 1, 7, 11

Tutorial battle: 7, 11

Back to overworld: 1, 7, 11

Inside kingdom (still tutorial): 1, 7, 11
```

## Going forward

I plan to set up a repository to share all the functions I've named and their parameters to share everything with people.

Hopes:

- Short Term: I've already found all the funcitions which read data formats. This has confirmed much of our pre-existing knowledge, but also many new values we didn't have before. Expect many new properties to be available for modificaion in RanseiLink soon.

- Medium Term: I hope we can get an understanding of completely new files. Particularly the event files.

- Long Term: Making code modifications will be possible. Things that seem simple may not be though, for example the number of pokemon, 200, is spread all over the place, due to a combination of macro usage and inlining. This means we have to find all the places where it's referred to be able to increase it. In addition the scenario pokemon data structure will need changing as currently it only has room for a maximum of 255 pokemon. 

- Extra Long Term: Setting up a full decomp. The dream we can freely make any edits to the code compile our own versions of the game.
