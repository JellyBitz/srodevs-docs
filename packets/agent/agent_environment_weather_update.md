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

# AGENT\_ENVIRONMENT\_WEATHER\_UPDATE

* Opcode `0x3809`
* Direction `S > C`

```csharp
1   byte    WeatherType
1   byte    Intensity
```

***

### WeatherType

```csharp
public enum WeatherType : byte
{
    Clear = 1,
    Rain = 2,
    Snow = 3
}
```
