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

# GATEWAY\_SHARD\_LIST\_ACK

* Opcode `0xA101`&#x20;
* Direction `S > C`

```csharp
// Farms
while(true)
{
    1   bool    CanRead
    if(!CanRead)
        break;

    1   byte    Farm.ID
    2   ushort  Farm.Name.Length
    *   string  Farm.Name
}
// Shards
while(true)
{
    1   bool    CanRead
    if(!CanRead)
        break;

    2   ushort  Shard.ID
    2   ushort  Shard.Name.Length
    *   string  Shard.Name
    2   ushort  Shard.PlayerCount
    2   ushort  Shard.PlayerCapacity
    1   bool    Shard.IsOperating
    1   byte    Shard.FarmID
}
```
