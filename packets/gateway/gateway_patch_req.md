# GATEWAY\_PATCH\_REQ

* Opcode `0x6100`
* Direction `C > S`
* Encrypted

```csharp
1   byte    ContentID
2   ushort  Client.Name.Length
*   string  Client.Name         //SR_Client
4   uint    Client.Version      // From SV.T
```
