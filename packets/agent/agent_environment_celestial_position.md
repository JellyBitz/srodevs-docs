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

# AGENT\_ENVIRONMENT\_CELESTIAL\_POSITION

* Opcode `0x3020`
* Direction `S > C`

```csharp
4   uint    Character.UniqueID
2   ushort  Moonphase   // See "map/sun/moon?.ddj" [00,30] 
1   byte    Hour        //0-23
1   byte    Minute      //0-59
```
