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
  anchors:
    visible: true
---

# AGENT\_GAME\_NOTIFY

* Opcode `0x300C`
* Direction `S > C`

```csharp
2   ushort  GameNotifyType
if( GameNotifyType == GameNotifyType.UniqueSpawn )
{
    4   uint    RefObjID
}
else if( GameNotifyType == GameNotifyType.UniqueKilled )
{
    4   uint    RefObjID
    2   ushort  KillerName.Length
    *   string  KillerName
}
else if( GameNotifyType == GameNotifyType.Information )
{
    1   byte    MessageType // 1 = Popup (Blue), 2 = System (Right window)
    2   ushort  Message.Length
    *   string  Message
}
```

***

### GameNotifyType

```csharp
public enum GameNotifyType : ushort
{
    UniqueSpawn = 0x0C05,
    UniqueKilled = 0x0C06,
    Information = 0x0C1C,
}
```
