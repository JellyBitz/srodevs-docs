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

# AGENT\_QUEST\_SCRIPT

* Opcode `0x3CA2`&#x20;
* Direction `S > C`

```csharp
2   ushort  Script.Length
*   string  Script        // Filename from media/script/q_script/
4   uint    unkUInt01
```

