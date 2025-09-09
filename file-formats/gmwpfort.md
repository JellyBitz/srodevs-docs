---
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
  metadata:
    visible: true
---

# GMWPForT

Contains all warp points for GM instant teleport.\
Those points are saved from the current character location by console command `/addwp` and later on used as `/wp name`.

{% tabs %}
{% tab title="File Structure" %}
```csharp
4   uint    WarpCount
foreach(WarpCount)
{
    // Warp
    4   uint    Name.Length
    *   string  Name
    // Location
    2   ushort  RegionID
    2   ushort  _pad01
    4   float   PosX
    4   float   PosY
    4   float   PosZ
    4   uint    WorldID
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
#pragma array_limit 4294967296

struct Location
{
    u16 RegionID;
    u16 _pad01;
    float PosX;
    float PosY;
    float PosZ;
    u32 WorldID;
};

struct Warp
{
    u32 NameLength;
    char Name[NameLength];
    Location Location;
};

struct GMWPForT
{
    u32 WarpCount;
    Warp Warps[WarpCount];
};

GMWPForT file @ 0;
```
{% endtab %}
{% endtabs %}
