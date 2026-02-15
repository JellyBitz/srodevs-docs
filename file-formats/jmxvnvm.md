---
hidden: true
---

# JMXVNVM

Describes the navigation mesh from terrain, with all the setup about collisions for a worlmap region.

Internally known as `RTNavMeshTerrain`, is a type of `RTNavMesh`.

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature         //JMXVNVM 1000

// Objects (RTNavMeshObj)
2   short   ObjectCount
foreach(ObjectCount)
{
    // MapObject
    4   int     ResourceID    // See "object.ifo"
    12  string  LocalPosition // Relative to region where it belongs
    2   short   IsStatic      // 0 = No, -1 = Yes
    4   float   Yaw
    // (MSB)                                                                       (LSB)
    // | 15 | 14 | 13 | 12 | 11 | 10 | 09 | 08 | 07 | 06 | 05 | 04 | 03 | 02 | 01 | 00 |
    // |       UID.BlockIndex        |       UID.MapObjectIdentifier (non-zero)        |
    2   short   UID           // Unique identifier to track instances within the same region
    2   short   unkShort01
    1   bool    IsBig         // Exceeds region size, used for culling?
    1   bool    IsStruct      // Use "objectstring.ifo"
    
    // Links a GlobalEdge with another MapObject GlobalEdge within the same region
    2   ushort  LinkedEdgeCount
    foreach (LinkedEdgeCount)
    {
        // Values ​​of (-1) are invalid entries, removed perhaps
        2   short   LinkedEdge.OtherMapObjectIndex
        2   short   LinkedEdge.OtherEdgeIndex
        2   short   LinkedEdge.EdgeIndex     // See "PrimMeshNavEdge" from JMXVBMS
    }
}

// Cells (RTNavMeshCellQuad)
4   uint    CellCount
4   uint    WalkableCellCount
foreach (cellCount)
{
    // NavRect
    8   Vector2 Cell.Min
    8   Vector2 Cell.Max
    
    // Number of object instances within this cell
    1   byte    Cell.ObjectCount
    foreach (Cell.ObjectCount)
    {
        2   ushort  ObjectIndex // From Objects list
    }
}

// Global Edges (RTNavMeshEdgeGlobal)
4   uint    GlobalEdgeCount
foreach (GlobalEdgeCount)
{
    // NavLine
    8   Vector2 Edge.Min
    8   Vector2 Edge.Max

    1   byte    Edge.Flags              // See "EdgeFlag"
    1   sbyte   Edge.AssocDirection[0]  // See "EdgeDirection"
    1   sbyte   Edge.AssocDirection[1]  // -1 if Blocked
    2   short   Edge.AssocCellIndex[0]  // From Cells list
    2   short   Edge.AssocCellIndex[1]  // -1 if Blocked

    2   short   Edge.AssocRegionID[0]
    2   short   Edge.AssocRegionID[1]   // -1 if Blocked
}

// Internal Edges (RTNavMeshEdgeInternal)
4   uint    InternalEdgeCount
foreach (InternalEdgeCount)
{
    // NavLine
    8   Vector2 Edge.Min
    8   Vector2 Edge.Max

    1   byte    Edge.Flags              // See "EdgeFlag"
    1   sbyte   Edge.AssocDirection[0]  // See "EdgeDirection"
    1   sbyte   Edge.AssocDirection[1]  // -1 if Blocked
    2   short   Edge.AssocCellIndex[0]  // From Cells list
    2   short   Edge.AssocCellIndex[1]  // -1 if Blocked
}

// TileMap (96x96)
for (int i = 0; i < 96 * 96; i++)
{
    4   int     Tile.CellIndex   // From Cells list
    2   ushort  Tile.Flags       // See "TileFlag"
    2   ushort  Tile.TextureID   // See "tile2D.ifo" (Used for foot-step sounds)
}

// HeightMap (97x97)
for (int i = 0; i < 97 * 9; i++)
{
    4   float   Vertex.Height
}

// PlaneTypeMap (6x6)
for (int i = 0; i < 6 * 6; i++)
{
    1   byte    Plane.Type        // See "PlaneType"
}
// PlaneHeightMap 
for (int i = 0; i < 6 * 6; i++)
{
    4   float   Plane.Height
}
```
{% endtab %}

{% tab title="ImHex" %}
```cpp
// TO DO
```
{% endtab %}
{% endtabs %}

***

### EdgeFlag

```c#
[Flags]
public enum EdgeFlag : byte
{
    None = 0,
    BlockDstToSrc = 0x1,
    BlockSrcToDst = 0x2,
    Blocked = BlockDst2Src | BlockSrc2Dst,
    Internal = 0x4,
    Global = 0x8,
    Underpass = 0x10, // Actor passthrough from outside & blocked from inside
    Entrance = 0x20,  // From dungeons (obsolete?)
    Bit6 = 0x40,
    Siege = 0x80,    // Let attacks go through
}
```

### EdgeDirection

```csharp
public enum EdgeDirection : sbyte
{
    Invalid = -1,
    Bottom = 0,
    Left = 1,
    Top = 2,
    Right = 3,
}
```

### TileFlag

```csharp
[Flags]
public enum TileFlag : ushort
{
    Blocked = 0,
    IgnoreSlope = 1,
    // Everything else is kinda unknown.. Split into 2 bytes?
}
```

### PlaneType

```csharp
public enum PlaneType : byte
{
    Normal = 0,
    Water = 1,
    Ice = 2,
}
```
