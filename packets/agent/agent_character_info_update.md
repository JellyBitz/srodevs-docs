# AGENT_CHARACTER_INFO_UPDATE

* Opcode `0x304E`
* Direction `S > C`

```csharp
1   byte    type

if type == UpdateType.Gold) 
{
    8   ulong   Gold
}

else if(type == UpdateType.SkillPoints)
{
    4   uint    SkillPoints
}

else if(type == UpdateType.Berzerker)
{
    1   byte    BerzerkPoints
}
```
***
### UpdateType
```csharp
public enum UpdateType : byte
{
  Gold = 1,
  SkillPoints = 2,
  Berzerker = 4
}
```
