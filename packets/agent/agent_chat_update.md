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

# AGENT\_CHAT\_UPDATE

* Opcode `0x3026`&#x20;
* Direction `S > C`

```csharp
1   byte    ChatType
if( ChatType == ChatType.All ||
    ChatType == ChatType.AllGM ||
    ChatType == ChatType.NPC )
{
    4   uint    Message.Sender.UID
}
else if( ChatType == ChatType.Private ||
         ChatType == ChatType.Party ||
         ChatType == ChatType.Guild ||
         ChatType == ChatType.Global ||
         ChatType == ChatType.Stall ||
         ChatType == ChatType.Union ||
         ChatType == ChatType.Academy )        
{
    2   ushort  Message.Sender.Name.Length
    *   string  Message.Sender.Name
}
2   ushort  Message.Length
*   string  Message
```

***

{% hint style="info" %}
See also:

* [ChatType](agent_chat_req.md#chattype)
{% endhint %}
