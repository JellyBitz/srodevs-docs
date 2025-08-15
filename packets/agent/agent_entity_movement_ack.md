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

# AGENT\_ENTITY\_MOVEMENT\_ACK

* Opcode `0xB021`
* Direction `S > C`

```csharp
4   uint    Entity.UID

// Destination
1   byte    Entity.HasDestination
if(Entity.HasDestination)
{
    2   ushort  Dst.RegionID
    if(Dst.RegionID & 0x8000) // IsDungeon
    {
        4   int     Dst.PosX
        4   int     Dst.PosY
        4   int     Dst.PosZ
    }
    else
    {
        2   short   Dst.PosX
        2   short   Dst.PosY
        2   short   Dst.PosZ
    }
}
else
{
    1   byte    Entity.ControlType  // 1 = Walking, 0 = Spinning (visually bugged, replaced by AGENT_ENTITY_ROTATION_ACK)
    2   short   Entity.Angle
}

// Source
1   byte    Entity.HasSource
if(Entity.HasSource)
{
    2   ushort  Src.RegionID
    if(Src.RegionID & 0x8000) // IsDungeon
    {
        4   int     Src.PosX  // It's multiplied by 10
        4   float   Src.PosY
        4   int     Src.PosZ  // It's multiplied by 10
    }
    else
    {
        2   short   Src.PosX  // It's multiplied by 10
        4   float   Src.PosY
        2   short   Src.PosZ  // It's multiplied by 10
    }
}
```
