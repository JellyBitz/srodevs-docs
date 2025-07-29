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

# GATEWAY\_SHARD\_LIST\_PING\_ACK

* Opcode `0xA106`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 0x01)
{
    1   byte    Farm.ID
    4   uint    IPAddress //IPv4
}
else
{
    1   byte    ErrorCode
}
```
