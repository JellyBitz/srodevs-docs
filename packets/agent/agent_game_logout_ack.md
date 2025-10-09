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

# AGENT\_GAME\_LOGOUT\_ACK

* Opcode `0xB005`
* Direction `S > C`

```csharp
1   byte    Result
if (Result == 1)
{
    1   byte    Countdown   //in seconds
    1   byte    LogoutMode
}
else if (Result == 2)
{
    2   ushort  LogoutErrorCode
}
```

***

### LogoutErrorCode

```csharp
public enum LogoutErrorCode : ushort
{
	/// <summary>
	/// Cannot close the game during combat.
	/// </summary>
	UIIT_MSG_LOGOUT_ERR_CANT_LOGOUT_IN_BATTLE_STATE = 0x801
	
	/// <summary>
	/// Cannot exit the game while teleporting.
	/// </summary>
	UIIT_MSG_LOGOUT_ERR_CANT_LOGOUT_WHILE_TELEPORT_WORKING = 0x802
}
```

{% hint style="info" %}
See also:

* [LogoutMode](agent_game_logout_req.md#logoutmode)
{% endhint %}
