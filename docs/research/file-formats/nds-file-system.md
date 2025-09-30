# NDS File System Structure

This explains the relevant parts of the NDS File System.

## Header

The important parts of the header are

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x40 | Int32 | Start offset of Name Table |
| 0x48 | Int32 | Start offset of File Allocation Table |

## Name Table

The name table stores the names of the files and the structure of the file system. From the information stored, the index of the the file's entry in the File Allocation Table can be found.

It is split into two parts:

- Folder Allocation Table
- Name List

### Folder Allocation Table

Each folder in the file system has a 8 byte long entry. The first one is for the root folder, and acts as an entry point to the file system. Each entry looks something like this:

`DF 01 00 00 6F 01 02 F0`

Within the entry is the following information

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x00 | Int32 | Start offset of folder contents within Name List relative to start of NameTable |
| 0x04 | Int16 | Index of first file within folder in File Allocation Table |
| 0x06 | Byte/Int16 | Byte Index of parent folder in current table; for root folder this is an int16 which holds the number of entries in the table |
| 0x07 | Byte | Unknown, always 0xF0 except for root folder where it is part of above |

### Name List

The name list holds the names of the folders, and their contents in order, with references back to the Folder Allocation Table. 

Example:

`86 64 6C 5F 72 6F 6D 25 F0 `

Information Contained:

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x00 | Byte | The least significant 7 bits store the length of the name, and the most significant bit indicates whether it is a folder (1 = folder, 0 = file). |
| 0x01 ... | Utf8 String | The variable length name |
| Finally | UInt16 | Only there if it is a folder. Refers to the the index of it within the Folder allocation table, allowing its contents to be found. |

You can find the offset of a particular file within the File Allocation Table by keeping count of the file's index with a folder, and adding that to the index of the first file within the folder (stored within the entry of the folder within the Folder Allocation Table).

## File Allocation Table

The structure of the file allocation table is very simple, it's just a table of 8 byte entries, e.g.:

`00 A4 07 00 04 A8 07 00 `

The entry is just two int32 values referring to global offsets:

| Offset | Value Type | Used for |
| --- | --- | --- |
| 0x00 | Int32 | Start offset of file |
| 0x04 | Int32 | End offset of file (after this is padding) |




