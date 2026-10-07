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

# AGENT\_SEND\_PACKET\_TO\_CLIENT

* Opcode `0x2209`
* Direction `S > S`&#x20;

```csharp
4   uint    Player.SessionID
2   ushort  Packet.Opcode
*   byte    Packet.Data        // Depends on Opcode
```

