---
hidden: true
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Joymax Pack File

{% tabs %}
{% tab title="File Structure" %}
```csharp
// Header
30   char[]  Signature     //JoyMax File Manager!\n
4    byte[]  Version       //2.0.0.1
1    byte    IsEncrypted
16   byte[]  Checksum      // Used to test the blowfish key
205  byte[]  Reserved

// Block (First needs to be decrypted if required)
for (i = 0; i < 20; i++)
{
    // Entry
    1   byte    Entry.Type      // 0 = Empty, 1 = Folder, 2  = File
    89  char[]  Entry.Name
    8   ulong   CreateTime      // Windows time format
    8   ulong   ModifyTime      // Windows time format
    8   ulong   Position        // Position of data for files, position of the Block for folders
    4   uint    Size            // Size of files
    8   ulong   NextBlock       // Position of the next block in the chain from current directory
    2   byte[]  Padding         // So blowfish can be used directly on the struct
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct PackFileHeader
{
    char Signature[30];
    u8 Version[4];
    bool IsEncrypted;
    u8 Checksum[16];
    u8 Reserved[205];
};

struct PackFileEntry
{
    u8 Type;
    char Name[89];
    u64 CreateTime;
    u64 ModifyTime;
    u64 Position;
    u32 Size;
    u64 NextChain;
    u16 Padding;
};

struct PackFileBlock
{
    PackFileEntry Entries[20];    
};

PackFileHeader Header @ 0;
PackFileBlock RootBlock @ 256;
```
{% endtab %}
{% endtabs %}
