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
---

# AGENT\_LOGIN\_AUTH\_REQ

* Opcode `0x6103`&#x20;
* Direction `C > S`
* Encrypted

***

```csharp
4   uint    QueueID          // From GATEWAY_LOGIN_ACK
2   ushort  Username.Length
*   string  Username
2   ushort  Password.Length
*   string  Password
1   byte    ContentID        // Locale
6   byte[]  MACAddress
```
