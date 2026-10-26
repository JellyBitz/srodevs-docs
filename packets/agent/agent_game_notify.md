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
    1   byte    DisplayType // 1 = Popup (Blue), 2 = System (Right window)
    2   ushort  Textname.Length
    *   string  Textname
}
```

***

### GameNotifyType

```csharp
public enum GameNotifyType : ushort
{
    UniqueSpawn = 0x0C05, // UIIT_MSG_APPEAR_UNIC
    UniqueKilled = 0x0C06, // UIIT_MSG_ANYONE_DEAD_UNIC
    GuildEvent = 0x0C07,
    SpecialTrader = 0x0C08, // UIIT_MSG_SPECIALTY_ANNOUNCE_SELL_READY
    GateQinShiOpen = 0x0C10, // UIIT_TQ_F4_TELEPORT_OPEN
    GateQinShiClose = 0x0C11, // UIIT_TQ_F4_TELEPORT_CLOSE
    // ...
    Information = 0x0C1C,
}
```
