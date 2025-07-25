---
hidden: true
---

# JMXVDDJ

Describes a texture wrapper around the [DDS](https://en.wikipedia.org/wiki/DirectDraw_Surface) file format.&#x20;

{% tabs %}
{% tab title="File Structure" %}
```csharp
12  string  Signature            //JMXVDDJ 1000
4   int     TextureBufferLength  // -8, it counts the file itself but Signature
4   int     TextureType          // https://docs.microsoft.com/en-us/windows/win32/direct3d9/d3dresourcetype
*   byte[]  TextureBuffer        // https://learn.microsoft.com/en-us/windows/win32/direct3ddds/dx-graphics-dds
```
{% endtab %}

{% tab title="ImHex" %}
```c
struct JMXVDDJ
{
    char Signature[12];
    u32 TextureBufferLength;
    u32 TextureType;
    u8 TextureBuffer[TextureBufferLength-8];
};

JMXVDDJ file @ 0;
```
{% endtab %}
{% endtabs %}
