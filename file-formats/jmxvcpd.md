---
hidden: true
---

# JMXVCPD

Represents a resource compound of others resources, all merged in the same location.

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature                     //JMXVCPD 0101
4   uint    Header.CollisionOffset
4   uint    Header.ResourceOffset
4   uint    Header.unkUInt01
4   uint    Header.unkUInt02
4   uint    Header.unkUInt03
4   uint    Header.unkUInt04
4   uint    Header.unkUInt05

// ObjectGeneralInfo
2   short   ObjectGeneralInfo.Type         // See below "ObjectGeneralType"
2   short   ObjectGeneralInfo.Category     // See below "ObjectGeneralCategory"
4   uint    ObjectGeneralInfo.Name.Length
*   string  ObjectGeneralInfo.Name
4   int     ObjectGeneralInfo.unkInt01
4   int     ObjectGeneralInfo.unkInt02

// CollisionOffset
4   uint    CollisionResourcePath.Length
*   string  CollisionResourcePath

// ResourceOffset
4   uint    ResourceCount
foreach (ResourceCount)
{
    4   uint    ResourcePath.Length
    *   string  ResourcePath
}
```
{% endtab %}

{% tab title="ImHex" %}
```cpp
struct JMXVCPD_Header
{
    u32 CollisionOffset;
    u32 ResourceOffset;
    u32 unkUInt01;
    u32 unkUInt02;
    u32 unkUInt03;
    u32 unkUInt04;
    u32 unkUInt05;
};
enum ObjectGeneralType : s16
{
    None = u16(-1),
    Character = 0,
    NPC = 1,
    Building = 2,
    Artifact = 3,
    Nature = 4,
    Item = 5,
    Other = 6,
    Simple = 7
};
enum ObjectGeneralCategory : s16
{
    None = 0,
    Primitive = 1,
    Resource = 2,
    Compound = 3,
    Dungeon = 4,
};
struct ObjectGeneralInfo
{
    ObjectGeneralType Type;
    ObjectGeneralCategory Category;
    u32 NameLength;
    char Name[NameLength];
    s32 unkInt01;
    s32 unkInt02;
};
struct Resource
{
    u32 PathLength;
    char Path[PathLength];
};
struct JMXVCPD
{
    char Signature[12];
    JMXVCPD_Header Header;
    ObjectGeneralInfo ObjectGeneralInfo;
    // Header.CollisionOffset
    u32 CollisionResourcePathLength;
    char CollisionResourcePath[CollisionResourcePathLength];
    // Header.ResourceOffset
    u32 ResourceCount;
    Resource Resources[ResourceCount];
};

JMXVCPD file @ 0;
```
{% endtab %}
{% endtabs %}

***

### ObjectGeneralType

```csharp
public enum ObjectGeneralType : short
{
    None = -1,
    Character = 0,
    NPC = 1,
    Building = 2,
    Artifact = 3,
    Nature = 4,
    Item = 5,
    Other = 6,
    Simple = 7
}
```

### ObjectGeneralCategory

```csharp
public enum ObjectGeneralCategory : short
{
    None = 0,
    Primitive = 1,
    Resource = 2,
    Compound = 3,
    Dungeon = 4,
}
```
