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
  tags:
    visible: true
  actions:
    visible: true
---

# AGENT\_ENTITY\_POSITION\_UPDATE

* Opcode `0xB023`&#x20;
* Direction `S > C`

```csharp
4   uint    Entity.UID
2   ushort  Entity.RegionID
4   float   Entity.PosX
4   float   Entity.PosY
4   float   Entity.PosZ
2   short   Entity.Angle
```
