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

# AGENT\_CHARACTER\_EXP\_UPDATE

* Opcode `0x3056`
* Direction `S > C`

<pre class="language-csharp"><code class="lang-csharp">4   uint    Entity.UID       // Where EXP particles come from
8   ulong   GainedExpPoint
8   ulong   GainedSExpPoint

// Training Camp
// (MSB)                       (LSB)
// | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
// |  Accumulated  |   Cumulated   |
1   byte    TCBuffUpdateFlags
if( (TCBuffUpdateFlags &#x26; TCBuffUpdateMask.Cumulated) == 1 )
{
<strong>    4   uint    Cumulated
</strong>}
if( ((TCBuffUpdateFlags &#x26; TCBuffUpdateMask.Accumulated) >> 4) == 1 )
{
    4   uint    CharID // From TrainingCampData
    4   uint    Accumulated
}

// Level up (requires leveldata.txt to know)
if(Character.CurrentExp + GainedExpPoint > RequiredExpForCurrentLevel)
{
    2   ushort  GainedStatsPoints
}
</code></pre>

***

### TCBuffUpdateMask

```csharp
[Flags]
public enum TCBuffUpdateMask : byte
{
    Cumulated = 0x0F,   // 0000 1111
    Accumulated = 0xF0, // 1111 0000
}
```
