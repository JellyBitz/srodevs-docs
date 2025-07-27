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

# GATEWAY\_LOGIN\_IBUV\_CONFIRM\_ACK

* Opcode `0xA323`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 0x02)
{
    4   uint    MaxAttempts
    4   uint    CurAttempts
}
```
