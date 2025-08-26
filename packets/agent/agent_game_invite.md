# AGENT_GAME_INVITE

* Opcode `0x3080`
* Direction `S > C`

```csharp
1   byte    requestType
4   uint    playerUniqueId


if( Type == requestType.PartyCreation || Type == requestType.PartyInvitation )
{
    1   byte   setupFlag
}
```
* Opcode `0x3080`
* Direction `C > S`
```csharp

```
***
### requestType
```csharp
public enum requestType : byte
{
	ExchangeRequest = 1,
	PartyCreation = 2,
	PartyInvitation = 3,
	Resurrection = 4,
	Resurrection = 8,
	GuildInvitation = 5,
	UnionInvitation = 6,
	AcademyInvitation = 9,
	GuildWar = 10
}
```
### setupFlag
```csharp
[Flags]
public enum Setup : byte
{
	ExpShared = 1,
	ItemShared = 2,
	AnyoneCanInvite = 4
}
```

