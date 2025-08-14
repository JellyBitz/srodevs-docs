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

# AGENT\_ENTITY\_MOVEMENT\_REQ

* Opcode `0x7021`
* Direction `C > S`

```csharp
1   byte    HasDestination
if(HasDestination)
{
    1   ushort  Dst.RegionID
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
    1   byte    ControlType // 1 = Walking, 0 = Spinning (visually bugged, replaced by AGENT_ENTITY_ROTATION_REQ)
    2   short   Angle
}
```
