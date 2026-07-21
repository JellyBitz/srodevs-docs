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
  tags:
    visible: true
  actions:
    visible: true
---

# AGENT\_ENTITY\_SKILL\_BUFF\_REMOVE

* Opcode `0xB072`
* Direction `S > C`

```csharp
1   byte    Result
if(Result == 1)
{
    4   uint    Skill.UID
}

```
