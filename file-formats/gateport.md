---
hidden: true
---

# GATEPORT

Contains the Gateway port to connect.

{% tabs %}
{% tab title="File Structure" %}
```csharp
8   char[]  GatewayPort //15779
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct GATEPORT
{
    char GatewayPort[8];
};

GATEPORT file @ 0;
```
{% endtab %}
{% endtabs %}
