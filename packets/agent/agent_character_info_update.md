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

# AGENT\_CHARACTER\_INFO\_UPDATE

* Opcode `0x304E`
* Direction `S > C`

```csharp
1   byte    UpdateType
if(UpdateType == CharacterInfoUpdateType.Gold)
{
    8   ulong   Gold
    1   bool    IsDisplayed  // Displays UIIT_MSG_STATE_GAIN_GOLD
}
else if(UpdateType == CharacterInfoUpdateType.SP)
{
    4   uint    SP
    1   bool    IsDisplayed // Displays UIIT_STT_SKILL_POINT_RECOVER_RESULT or UIIT_MSG_JSERR_SINCE_YOU_DIE_IN_MURDERER_SP_DEPRIVED_BY_SERVER
}
else if(UpdateType == CharacterInfoUpdateType.STP)
{
    2   ushort  StatPoints
}
else if(UpdateType == CharacterInfoUpdateType.HWAN)
{
    1   byte    HwanPoints
    4   uint    SourceGID    // where particles are coming from
}
else if(UpdateType == CharacterInfoUpdateType.EGYPT_AP)
{
    //UIIT_STT_EGYPT_AP_POINT_RECOVER_RESULT
    4   uint    APPoint
}
```

***

### CharacterInfoUpdateType

```csharp
public enum CharacterInfoUpdateType : byte
{
    ///<summary>
    /// New value from gold at inventory
    ///</summary>
    Gold = 1,

    ///<summary>
    /// New value from skill points to spend
    ///</summary>
    SP = 2,
  
    STP = 3, // Stat points

    ///<summary>
    /// New value for berserker mode (5 points = Ready)
    ///</summary>
    HWAN = 4,
    
    // UIIT_STT_EGYPT_AP_POINT_RECOVER_RESULT
    EGYPT_AP = 16,
}
```
