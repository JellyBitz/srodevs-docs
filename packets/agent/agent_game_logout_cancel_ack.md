# AGENT\_GAME\_LOGOUT\_CANCEL\_ACK

* Opcode `0xB006`
* Direction `S > C`

```csharp
1   byte    Result
if (Result == 2)
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
