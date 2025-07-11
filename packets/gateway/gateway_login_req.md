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
---

# GATEWAY\_LOGIN\_REQ

* Opcode `0x6102`
* Direction `C > S`
* Encrypted

```csharp
1   byte    ContentID
2   ushort  Username.Length
*   string  Username
2   ushort  Password.Length
*   string  Password
2   ushort  ShardID
```
