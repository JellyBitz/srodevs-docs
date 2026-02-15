# AGENT\_ENTITY\_STATE\_UPDATE

* Opcode `0x30BF`
* Direction `S > C`

```csharp
4   uint    Entity.UID
1   byte    UpdateType
if(UpdateType == EntityStateUpdateType.LifeState)
{
    1   byte    Entity.LifeStateType
}
else if(UpdateType == EntityStateUpdateType.MotionState)
{
    1   byte    Entity.MotionStateType
}
else if(UpdateType == EntityStateUpdateType.BodyState)
{
    1   byte    Entity.BodyStateType
}
else if(UpdateType == EntityStateUpdateType.CombatState)
{
    1   byte    Entity.CombatStateType
}
else if(UpdateType == EntityStateUpdateType.InCombat)
{
    1   bool    Entity.InCombat
}
else if(UpdateType == EntityStateUpdateType.Scrolling)
{
    1   byte    Entity.ScrollingType
}
```

***

### EntityStateUpdateType

```csharp
public enum EntityStateUpdateType : byte
{
    LifeState = 0,
    MotionState = 1,
    BodyState = 4,
    CombatState = 7,
    InCombat = 8,
    Scrolling = 11,
}
```

{% hint style="info" %}
See also:

* [EntityBodyStateType](agent_character_bodystate_req.md#entitybodystatetype)
{% endhint %}
