# LINK Archive

Fun fact, this is what RanseiLink is named after.

[Code to unpack](https://github.com/Deijin27/RanseiLink/blob/master/RanseiLink.Core/Archive/Link.cs)

The Link Archive is an archive format used in Pokemon Conquest (I assume it was made for this game as the word LINK is possibly a reference to the game). It seems to be made to group data of an image. Usually has the file extension G2GR. They tend to contain some of the Nintendo standard file formats:

- RNAN (Nintendo Animation Resource)
- RGCN (Nintendo Character Graphic)
- RECN (Nintendo Cell Resource)
- RLCN (Nintendo Color Resource)

The header has the structure:

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x00 | 4 byte magic number | This is just the Utf8 string "LINK" |
| 0x04 | Int32 | Number of files |
| 0x08 | Int32 | Multiplier used to scale the file offsets |
| 0x12 | 4 bytes | Always 0, maybe padding to make the header 16 bytes? |

After that is a file allocation table, with each 8 byte entry containing:

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x00 | Int32 | Scaled down offset of file |
| 0x04 | Int32 | Length of file |

To get a file, you go to its index in the file allocation table, then you multiply the offset in its entry by the multiplier found in the header.

Weirdly, there does seem to be some zero width files.

