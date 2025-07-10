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

# AGENT\_LOGIN\_AUTH\_ACK

* Opcode `0xA103`
* Direction `S > C`

***

```csharp
1   byte    Result
if(result == 0x02)
{
    1   byte    ErrorCode
}
```
