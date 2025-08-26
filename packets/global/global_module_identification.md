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

# GLOBAL\_MODULE\_IDENTIFICATION

* Opcode `0x2001`&#x20;
* Direction `S > C`&#x20;
* Encrypted (client only)

```csharp
2   ushort  Service.Name.Length
*   string  Service.Name
1   byte    Service.Type // 0 = Client, 1 = Server
```
