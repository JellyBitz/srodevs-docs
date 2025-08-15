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

# AGENT\_CHARACTER\_SELECTION\_JOIN\_ACK

* Opcode `0xB001`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 0x02)
{
    2   ushort  ErrorCode
}
```
