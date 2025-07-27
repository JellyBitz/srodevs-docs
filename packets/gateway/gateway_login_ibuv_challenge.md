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

# GATEWAY\_LOGIN\_IBUV\_CHALLENGE

* Opcode `0x2322`
* Direction `S > C`

```csharp
1   byte    Image.Flags
2   ushort  Image.Remaining           //in bytes
2   ushort  Image.CompressedLength
2   ushort  Image.UncompressedLength
2   ushort  Image.Width               //200
2   ushort  Image.Height              //64
*   byte[]  Image.CompressedData
```
