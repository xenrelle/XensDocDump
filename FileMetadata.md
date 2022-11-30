# File Metadata

> NOTE: This is only for files generated in Terraria PC 1.4.3.6 - 1.4.4.9. (could be used in older versions, I haven't tested yet)

Every main file in terraria (`.wld`, `.map`, and `.plr`) all contain file metadata in the header of the files. They're all nearly identical, so it will be covered here. The size should *always* be 0x14 (20).

## Metadata

| Value            | Length | Type | Description                                                                                                                                                                                                                                                                          |
| ---------------- | ------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Signature + Type | 0x8    | Long | The signature and the file type bit shifted together. The first byte is the [file type](#File_Types). The last 7 bytes is the signature and should always be "cigoler" `( 63 69 67 6F 6C 65 72 )`, otherwise the file won't load.<br/>`(HINT: signature is "relogic" but backwards)` |
| Revision         | 0x4    | Int  | Revision number of the file.                                                                                                                                                                                                                                                         |
| Extra Bits       | 0x8    | Long | A long storing extra bits of metadata. So far, only one is "used".<br/>`Bit 0` - Is Favourited<br/>`Bit 1-63` - Unused                                                                                                                                                               |

## File Types

| Number | Type       |
| ------ | ---------- |
| 0      | Null       |
| 1      | Player Map |
| 2      | World      |
| 3      | Player     |
