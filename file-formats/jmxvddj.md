---
hidden: true
---

# JMXVDDJ

Describes a texture wrapper around the [DDS](https://en.wikipedia.org/wiki/DirectDraw_Surface) file format.&#x20;

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature      //JMXVDDJ 1000
4   int     TextureLength  // (+8) It counts TextureLength and TextureType bytes
4   int     TextureType    // https://docs.microsoft.com/en-us/windows/win32/direct3d9/d3dresourcetype
*   byte[]  Texture        // https://learn.microsoft.com/en-us/windows/win32/direct3ddds/dx-graphics-dds
```
{% endtab %}

{% tab title="ImHex" %}
```c
#pragma array_limit 4294967296

struct JMXVDDJ
{
    char Signature[12];
    u32 TextureLength;
    u32 TextureType;
    u8 Texture[TextureLength-8];
};

JMXVDDJ file @ 0;
```
{% endtab %}
{% endtabs %}
