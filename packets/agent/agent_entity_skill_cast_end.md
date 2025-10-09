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

# AGENT\_ENTITY\_SKILL\_CAST\_END

* Opcode `0xB071`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 1)
{
    4   uint    Skill.UID
    4   uint    EntityDst.UID
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
```

***

{% hint style="info" %}
See also:

* [SkillEffectFlag](agent_entity_skill_cast_begin.md#skilleffectflag)
* [SkillDamageFlag](agent_entity_skill_cast_begin.md#skilldamageflag)
{% endhint %}
