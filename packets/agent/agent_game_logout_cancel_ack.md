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

# AGENT\_GAME\_LOGOUT\_CANCEL\_ACK

* Opcode `0xB006`
* Direction `S > C`

```csharp
1   byte    Result
if (Result == 2)
{
    2   ushort  LogoutErrorCode
}
```

***

{% hint style="info" %}
See also:

* [LogoutErrorCode](agent_game_logout_ack.md#logouterrorcode)
{% endhint %}
