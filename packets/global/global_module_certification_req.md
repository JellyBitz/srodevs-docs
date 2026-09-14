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

# GLOBAL\_MODULE\_CERTIFICATION\_REQ

* Opcode `0x6003`
* Direction `C > S`

```csharp
2   ushort  Module.Name.Length
*   string  Module.Name
2   ushort  Module.IP.Length
*   string  Module.IP
```
