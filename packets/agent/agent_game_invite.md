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

# AGENT\_GAME\_INVITE

* Opcode `0x3080`
* Direction `S > C`

```csharp
1   byte    PlayerRequestType
4   uint    Player.UID

if ( PlayerRequestType == PlayerRequestType.PartyCreation || 
     PlayerRequestType == PlayerRequestType.PartyInvitation )
{
    1   byte    PartySetupFlags
}
```

* Direction `C > S`

{% tabs %}
{% tab title="Accept" %}
```csharp
/// Accept

1   byte    PlayerResponseType       //1 (Option)
1   byte    PlayerResponseOption     //1 (Accept)
```
{% endtab %}

{% tab title="Cancel" %}
```csharp
/// Cancel

if ( PlayerRequestType == PlayerRequestType.PartyCreation || 
     PlayerRequestType == PlayerRequestType.PartyInvitation )
{
    1   byte    PlayerResponseType   //2 (Error)
    2   ushort  ErrorCode            //11276
} 
else
{
    1   byte    PlayerResponseType   //1 (Option)
    1   byte    PlayerResponseOption //2 (Cancel)
}
```
{% endtab %}
{% endtabs %}

***

### PlayerRequestType

```csharp
public enum PlayerRequestType : byte
{
    ExchangeRequest = 1,
    PartyCreation = 2,
    PartyInvitation = 3,
    Resurrection = 4,
    GuildInvitation = 5,
    UnionInvitation = 6,
    Resurrection = 8,
    AcademyInvitation = 9,
    GuildWar = 10
}
```

### PlayerResponseType

```csharp
public enum PlayerResponseType : byte
{
    Option = 1,
    Error = 2,
}
```

### PlayerResponseOption

```csharp
public enum PlayerResponseOption : byte
{
    Accept = 1,
    Cancel = 2,
}
```
