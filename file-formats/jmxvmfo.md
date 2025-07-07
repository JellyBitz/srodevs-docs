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

# JMXVMFO

Contains the basic worldmap setup information with the enabled regions as bits.

{% tabs %}
{% tab title="File Structure" %}
```csharp
12    char[]  Signature      // "JMXVMFO 1000"
2     short   MapWidth       // 256 at max. (8 bits from RegionID)
2     short   MapHeight      // 128 at max. (7 bits from RegionID, 1 bit is used as dungeon indicator)
2     short   unkShort0
2     short   unkShort1
2     short   unkShort2
2     short   unkShort3
8192  byte[]  RegionData     // 256 * 256 = 65536 bits / 8 = 8192 bytes (1 byte has 8 region indicators)
                             // Sorted at the same direction from world map.
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct JMXVMFO
{
    char Signature[12];
    u16 MapWidth;
    u16 MapHeight;
    u16 unkShort0;
    u16 unkShort1;
    u16 unkShort2;
    u16 unkShort3;
    u8 RegionData[256*256/8];
};

JMXVMFO file @ 0;
```
{% endtab %}
{% endtabs %}
