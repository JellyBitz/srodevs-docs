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

# AGENT\_CHARACTER\_BODYSTATE\_REQ

* Opcode `0x70A7`
* Direction `C > S`

```csharp
1   byte    EntityBodyStateType // Exploit vulnerability, only Berserk should be allowed
```

***

### EntityBodyStateType

```csharp
public enum EntityBodyStateType : byte
{
    None = 0,
    Berserk = 1,
    Untouchable = 2,
    GameMasterInvincible = 3,
    GameMasterUntouchable = 4,
    GameMasterInvisible = 5,
    Stealth = 6,
    Invisible = 7
}
```
