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

# AGENT_GAME_LOGOUT_ACK

* Opcode `0xB005`
* Direction `S > C`

```csharp
1   byte    result
if(result == 1)
{
    1   byte    Countdown   //in seconds
    1   byte    LogoutMode
}
else if(result == 2)
{
    2   ushort  errorCode
}
```

***
### LogoutMode
```csharp
   /// <summary>
    /// Go to Process.CPSQuit
    /// </summary>
    Exit = 1, 
    
    /// <summary>
    /// Go to Process.CPSRestart
    /// </summary>
    Restart = 2,
```
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
