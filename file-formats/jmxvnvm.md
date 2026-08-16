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
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# JMXVNVM

Describes the navigation mesh from terrain, with all the setup about collisions for a worlmap region.

Internally known as `RTNavMeshTerrain`, is a type of `RTNavMesh`.

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature         //JMXVNVM 1000

// [Objects...] (RTNavMeshObj)
2   short   ObjectCount
foreach(ObjectCount)
{
    // MapObject
    4   int     ResourceId    // See "object.ifo"
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
    1   ushort  RegionId      // Region ID this object belongs
    
    // Links a GlobalEdge with another MapObject GlobalEdge within the same region
    2   ushort  LinkedEdgeCount
    foreach (LinkedEdgeCount)
    {
        // Values ​​of (-1) are invalid entries, removed perhaps
        2   short   LinkedEdge.OtherObjectIndex // From [Objects...]
        2   short   LinkedEdge.OtherEdgeIndex
        2   short   LinkedEdge.EdgeIndex // See "PrimMeshNavEdge" from JMXVBMS
    }
}

// [Cells...] (RTNavMeshCellQuad)
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
        2   ushort  ObjectIndex // From [Objects...]
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
    1   sbyte   Edge.AssocDirectionFrom // See "EdgeDirection"
    1   sbyte   Edge.AssocDirectionTo
    2   short   Edge.AssocCellIndexFrom // From [Cells...]
    2   short   Edge.AssocCellIndexTo

    2   short   Edge.AssocRegionIdFrom
    2   short   Edge.AssocRegionIdTo    // -1 if Blocked
}

// Internal Edges (RTNavMeshEdgeInternal)
4   uint    InternalEdgeCount
foreach (InternalEdgeCount)
{
    // NavLine
    8   Vector2 Edge.Min
    8   Vector2 Edge.Max

    1   byte    Edge.Flags              // See "EdgeFlag"
    1   sbyte   Edge.AssocDirectionFrom // See "EdgeDirection"
    1   sbyte   Edge.AssocDirectionTo
    2   short   Edge.AssocCellIndexFrom // From [Cells...]
    2   short   Edge.AssocCellIndexTo
}

// TileMap (96x96)
for (int i = 0; i < 96 * 96; i++)
{
    4   int     Tile.CellIndex   // From [Cells...]
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
#pragma array_limit 4294967296
#pragma pattern_limit 4294967296

#include <std/sys.pat>

struct Vector2
{
    float X;
    float Y;
};

struct Vector3
{
    float X;
    float Y;
    float Z;
};
fn format_Vector3(Vector3 v) {
    return std::format("({:.2f}, {:.2f}, {:.2f})", v.X, v.Y, v.Z);
};

bitfield NavFlags
{
    LockedInside : 1;
    LockedOutside : 1;
    InternalEdge : 1;
    GlobalEdge : 1;
    Underpass : 1;
    Entrance : 1;
    Bit7 : 1;
    Siege : 1;
};

struct MapObject
{
    u32 ResourceId;
    Vector3 LocalPosition [[format("format_Vector3")]];
    s16 IsStatic;
    float Yaw;
    u16 UID;
    u16 unkShort01;
    bool IsBig;
    bool IsStruct;
    u16 RegionId;
};

struct LinkEdge
{
   u16 OtherObjectIndex;
   u16 OtherEdgeIndex;
   u16 EdgeIndex;
};

struct NavMeshObj
{
   MapObject MapObject;
   u16 LinkEdgeCount;
   LinkEdge LinkEdges[LinkEdgeCount];
};

struct Rect
{
    Vector2 Min;
    Vector2 Max;
};
fn format_Rect(Rect r) {
    return std::format("Min:({:.2f}, {:.2f}), Max:({:.2f}, {:.2f})", r.Min.X, r.Min.Y, r.Max.X, r.Max.Y);
};

struct Cell
{
    Rect Rectangle [[format("format_Rect")]];    
    u8 ObjectIndexCount;
    u16 ObjectIndices[ObjectIndexCount];
};

struct Line
{
    Vector2 Min;
    Vector2 Max;
};
fn format_Line(Line l) {
    return std::format("Min:({:.2f}, {:.2f}), Max:({:.2f}, {:.2f})", l.Min.X, l.Min.Y, l.Max.X, l.Max.Y);
};

enum EdgeDirection : s8
{
    Invalid = u8(-1),
    Bottom = 0,
    Left = 1,
    Top = 2,
    Right = 3,
};

struct GlobalEdge
{
    Line Line [[format("format_Line")]];
    NavFlags Flags;
    EdgeDirection AssocDirectionFromTo[2];
    u16 AssocCellIndexFromTo[2];
    u16 AssocRegionIdFromTo[2];
};

struct InternalEdge
{
    Line Line [[format("format_Line")]];
    NavFlags Flags;
    EdgeDirection AssocDirectionFromTo[2];
    u16 AssocCellIndexFromTo[2];
};

bitfield TileFlag
{
    Blocked : 1;
    IgnoreSlope : 1;
    Bit3 : 1;
    Bit4 : 1;
    Bit5 : 1;
    Bit6 : 1;
    Bit7 : 1;
    Bit8 : 1;
    Bit9 : 1;
    Bit10 : 1;
    Bit11 : 1;
    Bit12 : 1;
    Bit13 : 1;
    Bit14 : 1;
    Bit15 : 1;
};

struct Tile
{
    u32 CellIndex;
    TileFlag Flags;
    u16 TextureID;
};

enum PlaneType : u8
{
    Normal = 0,
    Water = 1,
    Ice = 2,
};

struct JMXVNVM
{
    char Signature[12];
    u16 ObjectCount;
    NavMeshObj Objects[ObjectCount];
    
    u32 CellCount;
    u32 WalkableCellCount;
    Cell Cells[CellCount];

    u32 GlobalEdgeCount;
    GlobalEdge GlobalEdges[GlobalEdgeCount];
    u32 InternalEdgeCount;
    InternalEdge InternalEdges[InternalEdgeCount];
    
    Tile TileMap[96*96];
    float HeightMap[97*97];
    PlaneType PlaneTypeMap[6*6];
    float PlaneHeightMap[6*6];
};

JMXVNVM file @ 0;
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
    Blocked = 1,
    IgnoreSlope = 2,
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
