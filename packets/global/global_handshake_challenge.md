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

# GLOBAL\_HANDSHAKE\_CHALLENGE

* Opcode `0x5000`
* Direction `-`

```csharp
1   byte    SecurityFlag

// Blowfish
if( (SecurityFlag & SecurityFlags.Blowfish) != 0)
{
    8   uint    InitialKey
}
if( (SecurityFlag & SecurityFlags.SecurityBytes) != 0)
{
    4   uint    Seed.Count
    4   uint    Seed.CRC
}
if( (SecurityFlag & SecurityFlags.Handkshake) != 0)
{
    8   ulong   Handshake.Key
    4   uint    Handshake.g
    4   uint    Handshake.p
    4   uint    Handshake.A
}
if( (SecurityFlag & SecurityFlags.HandkshakeResponse) != 0)
{
    8   ulong   ChallengeKey
}
```

***

### SecurityFlags

```csharp
[Flags]
public enum SecurityFlags : byte
{
    None = 0x00,
    Blowfish = 0x01,
    SecurityBytes = 0x02,
    Handshake = 0x04,
    HandshakeResponse = 0x08,
    unk06 = 0x10,
    unk07 = 0x20,
    unk08 = 0x40,
}
```
