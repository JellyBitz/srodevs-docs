# AGENT\_ENTITY\_SKILL\_CAST\_BEGIN

* Opcode `0xB070`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 1)
{
    1   byte    Skill.CastType
    1   byte    unkByte01
    4   uint    Skill.ID
    4   uint    EntitySrc.UID
    4   uint    Skill.UID
    4   uint    EntityDst.UID
    if(Skill.CastType == SkillCastType.Attack)
    {
        1   bool    HasDamage
        if(HasDamage)
        {
            1   byte    HitCount
            1   byte    TargetCount
            foreach(TargetCount)
            {
                4   uint    Target.UID
                4   uint    Target.SkillEffectFlags
                if( Target.SkillEffectFlags & SkillEffectFlag.Block ||
                    Target.SkillEffectFlags & SkillEffectFlag.Cancel )
                    continue

                1   byte    Target.SkillDamageFlags
                3   uint    Target.Damage
                4   uint    unkUInt01
            }
        }
    }
}
```

***

### SkillCastType

```csharp
public enum SkillCastType : byte
{
    Buff = 0,
    Attack = 2,
}
```

### SkillEffectFlag

```csharp
[Flags]
public enum SkillEffectFlag : byte
{
    None = 0,
    KnockBack = 1,
    Block = 2,
    Position = 4,
    Cancel = 8,
    Dead = 128
}
```

### SkillDamageFlag

```csharp
[Flags]
public enum SkillDamageFlag : byte
{
    None = 0,
    Normal = 1,
    Critical = 2,
    BadStatus = 4
}
```
