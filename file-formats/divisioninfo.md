---
hidden: true
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

# DIVISIONINFO

Contains the Gateway addresses for the each server division.

{% tabs %}
{% tab title="File Structure" %}
```csharp
1   byte    ContentID               // Locale
1   byte    ServerDivisionCount
foreach(ServerDivisionCount)
{
    // ServerDivision
    4   uint    Name.Length
    *   string  Name
    1   byte    unkByte0            //0
    
    1   byte    GatewayCount
    foreach(GatewayCount)
    {
        // Gateway
        4   uint    Address.Length  // IP or hostname
        *   string  Address
        1   byte    unkByte1        //0
    }
}
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct Gateway
{
    u32 AddressLength;
    char Address[AddressLength];
    u8 unkByte1;
};

struct ServerDivision
{
    u32 NameLength;
    char Name[NameLength];
    u8 unkByte0;
    u8 GatewayCount;
    Gateway Gateways[GatewayCount];
};

struct DIVISIONINFO
{
    u8 ContentID;
    u8 ServerDivisionCount;
    ServerDivision ServerDivisions[ServerDivisionCount];
};

DIVISIONINFO file @ 0;
```
{% endtab %}
{% endtabs %}
