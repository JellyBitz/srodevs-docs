# AGENT_LOGOUT_CANCEL

* Opcode `0xB006`
* Direction `S > C`

```csharp
1   byte    result
if(result == 2)
{
    2   ushort  errorCode
}
```
***
### errorCode
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
