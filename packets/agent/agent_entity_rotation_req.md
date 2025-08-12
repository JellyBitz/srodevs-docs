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

# AGENT\_ENTITY\_ROTATION\_REQ

* Opcode `0x7024`
* Direction `C > S`

```csharp
2   short   Angle
```

***

The character angle is handled as a signed short, with:

* Positive values  `[0,32767]`  as  `[0,180º]`
* Negative values  `[-32767,0]`  as  `[180,360º]`

<figure><img src="../../.gitbook/assets/agent_entity_rotation_diagram.png" alt=""><figcaption></figcaption></figure>
