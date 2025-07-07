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

# JMXVMAPM

Describes the map terrain mesh of a worldmap region.

{% tabs %}
{% tab title="First Tab" %}
```csharp
12  char[]  Signature      //JMXVMAPM1000

// Each region has 6 x 6 blocks
for (int yBlock = 0; yBlock < 6; yBlock++)
{
    for (int xBlock = 0; xBlock < 6; xBlock++)
    {
        4   uint    Block.Flag              // 0 = None, 1 = Culled
        2   ushort  Block.EnvironmentID     // See "environment.ifo"

        // Each block has 17 x 17 MapMeshVertices
        for (int z = 0; z < 17; z++)
        {
            for (int x = 0; x < 17; x++)
            {
                4   float   Vertex.Height
                // (MSB)                                                                        (LSB)
                // | 15  | 14 | 13 | 12 | 11 | 10 | 09 | 08 | 07 | 06 | 05 | 04 | 03 | 02 | 01 | 00 |
                // |             Scale            |                ID (tile2d.ifo)                  |
                2   ushort  Vertex.TextureInfo
                1   byte    Vertex.Brightness // Lighting direction indicator?
            }
        }

        1   byte    Block.WaterType        // 0xFF = None, 0 = Water, 1 = Ice
        1   byte    Block.WaterWaveID      // See "map/water/wave?.ddj"
        4   float   Block.WaterHeight
        
        // Each block has 16 x 16 MapMeshTiles
        for (int z = 0; z < 16; z++)
        {
            for (int x = 0; x < 16; x++)
            {
                2   ushort    Tile.Flag    // 0x01 = Blocked manually
            }
        }

        4   float   Block.HeightMax        // Highest point including objects
        4   float   Block.HeightMin        // Lowest point including objects
        20  byte[]  Block.Reserved         // Reserved[0] = 1 in some blocks
    }
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
#pragma pattern_limit 4294967296

enum WaterType : u8
{
    None = 0xFF,
    Water = 0,
    Ice = 1
};

bitfield TextureInfo {
    ID : 10;
    Scale : 6;
};

bitfield MapTileFlag {
    IsBlocked : 1;
    IsUnk01 : 1;
    IsUnk02 : 1;
    IsUnk03 : 1;
    IsUnk04 : 1;
    IsUnk05 : 1;
    IsUnk06 : 1;
    IsUnk07 : 1;
    IsUnk08 : 1;
    IsUnk09 : 1;
    IsUnk10 : 1;
    IsUnk11 : 1;
    IsUnk12 : 1;
    IsUnk13 : 1;
    IsUnk14 : 1;
    IsUnk15 : 1;
};

struct MapBlockVertex
{
    float Height;
    TextureInfo TextureInfo;
    u8 Brightness;
};

struct MapBlock
{
    u32 Flag;
    u16 EnvironmentID;
    MapBlockVertex Vertices[17*17];
    WaterType WaterType;
    u8 WaterWaveID;
    float WaterHeight;
    MapTileFlag Tiles[16*16];
    float HeightMax;
    float HeightMin;
    u8 Reserved[20]; 
};

struct JMXVMAPM
{
    char Signature[12];
    MapBlock Blocks[6*6];
};

JMXVMAPM file @ 0;
```
{% endtab %}
{% endtabs %}
