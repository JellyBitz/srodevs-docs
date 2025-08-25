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

# AGENT\_CHAT\_REQ

* Opcode `0x7025`
* Direction `C > S`

```csharp
1   byte    ChatType
1   byte    ChatWindow.RowIndex
if(ChatType == ChatType.Private)
{
    2   ushort  Receiver.Length
    *   string  Receiver
}
2   ushort  Message.Length
*   string  Message
```

***

{% hint style="info" %}
[ChatType](agent_chat_update.md#chattype)
{% endhint %}
