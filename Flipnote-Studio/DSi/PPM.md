# Flipnote .PPM file (Flipnote)

> NOTE: This is only for `.ppm` files generated in Revision 2 of Ugoku Memo Chou, or base in Flipnote Studio

Flipnotes are stored in `.ppm` files, containing everything about a flipnote, including audio.

> • For SysNAND, the save directory is `nand:/title/00030004/4B4755xx/data/public.sav/ugo/yyy`  
> • For SD Card, the save directory is `sdmc:/private/ds/app/4B4755xx/yyy`  
> xx is region-dependant. EUR: 56, JPN: 4A, USA: 45  
> yyy represents a 3-digit number as a folder name  

## Flipnote Header `[0x00..0x10]`

> NOTE: All values are in little-endian.  

| Value           | Offset (Relative) | Length | Type       | Description                                                                            |
| --------------- | ----------------- | ------ | ---------- | -------------------------------------------------------------------------------------- |
| Magic Header    | 0x0               | 0x4    | Byte Array | Contains the magic header for the ppm file. Should always be `PARA (50 41 52 41)`      |
| Page Data Size  | 0x4               | 0x4    | Int        | Contains the size of the frame data.                                                   |
| Audio Data Size | 0x8               | 0x4    | Int        | Contains the size of the audio data.                                                   |
| Page Count      | 0xC               | 0x2    | Short      | **Zero-based** count of how many pages the flipnote contains. Maximum is 999 `(0x3E6)` |
| Version         | 0xE               | 0x2    | Short      | Contains the version of the flipnote. Latest should be 36 `(0x24)`                     |

## Flipnote Metadata `[0x10..]`

| Value                     | Offset (Relative) | Length | Type                      | Description                                                                                                                                                                                                                                                                                                     |
| ------------------------- | ----------------- | ------ | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Is Locked                 | 0x0               | 0x2    | Short                     | Defines whether or not the flipnote is locked. `0`: Unlocked, `1`: Locked                                                                                                                                                                                                                                       |
| Thumbnail Page            | 0x2               | 0x2    | Short                     | **Zero-based** index of which page the thumbnail is based off of.                                                                                                                                                                                                                                               |
| Original Creator Name     | 0x4               | 0x16   | UTF-16LE String           | Name of the original creator of the Flipnote.                                                                                                                                                                                                                                                                   |
| Previous Creator Name     | 0x1A              | 0x16   | UTF-16LE String           | Name of the previous editor of the Flipnote.                                                                                                                                                                                                                                                                    |
| Current Creator Name      | 0x30              | 0x16   | UTF-16LE String           | Name of the most recent editor of the Flipnote.                                                                                                                                                                                                                                                                 |
| Previous Creator ID       | 0x46              | 0x8    | Byte Array                | Flipnote Studio ID of the previous editor of the Flipnote.<br/>`NOTE: The ID is reversed`                                                                                                                                                                                                                       |
| Current Creator ID        | 0x4E              | 0x8    | Byte Array                | Flipnote Studio ID of the most recent editor of the Flipnote.<br/>`NOTE: The ID is reversed`                                                                                                                                                                                                                    |
| Previous Filename         | 0x56              | 0x12   | [Filename](#PPM-Filename) | The previous file name of the Flipnote.                                                                                                                                                                                                                                                                         |
| Current Filename          | 0x68              | 0x12   | [Filename](#PPM-Filename) | The current file name of the Flipnote. Must match the actual file name in the filesystem (aside from the first letter), otherwise it will be considered corrupted.                                                                                                                                              |
| Original Creator ID       | 0x7A              | 0x8    | Byte Array                | Flipnote Studio ID of the original creator of the Flipnote.<br/>`NOTE: The ID is reversed`                                                                                                                                                                                                                      |
| Original Partial Filename | 0x82              | 0x8    | Byte Array                | The partial original file name of the Flipnote. First 3 bytes are the creator's last 6 digits in hex, and the last 5 bytes consist of the first 10 characters of the second part of the filename in hex (not ASCII data).<br/>`Example:` `123456_0BD4F7DA9F305_000` = `0x12 0x34 0x56 0x0B 0xD4 0xF7 0xDA 0x9F` |
| Last Modified Timestamp   | 0x8A              | 0x4    | Int                       | Timestamp of when the Flipnote has last modified. Timestamp is in seconds since 2000-01-01 00:00:00.                                                                                                                                                                                                            |
| Padding                   | 0x8E              | 0x2    | Short                     | Just used for padding, so it will always be `0`.                                                                                                                                                                                                                                                                |



### PPM Filename

 `Size: 0x12`

| Value              | Offset (Relative) | Length | Type         | Description                                                                                    |
| ------------------ | ----------------- | ------ | ------------ | ---------------------------------------------------------------------------------------------- |
| Last 6 FSID Digits | 0x0               | 0x3    | Byte Array   | Contains the last 6 digits of the FSID in hex form. Makes up the first 6 digits of a filename. |
| Filename String    | 0x3               | 0xD    | UTF-8 String | The second part of the filename as a string in hex. Makes up 13 digits of a filename.          |
| Edit Count         | 0x10              | 0x2    | Short        | Amount of flipnote edits. Makes up the last 3 digits of a filename.                            |